What is This?
=============

Checkers (Draughts) game written in Prolog language.

This checkers follow [russian draights](https://en.wikipedia.org/wiki/Russian_draughts) rules.
The russian draughts was chosen among other draughts variants because the rules (especially rules for kings) offer more freedom and thus increased search space.
In other words, it was just slightly more complicated and fun to implement.

This whole project was done as a fun experiment and bears zero practical value.

Rules
=====

Rules are standard for [russian checkers](http://en.wikipedia.org/wiki/Russian_checkers):

* Board is an 8x8 grid
* There are two kinds of pieces (figures): men and kings
* Long-range kings
* Men can capture backwards

How to Play?
============

Install Prolog
--------------

For now only [SWI-Prolog](http://www.swi-prolog.org/) is supported.
You can download it from [here](http://www.swi-prolog.org/download/stable).

Start the Game
----------

To play you only need file **checkers.pl**.
Download it and open in SWI Prolog (in Windows usually you can just double click the file, alternatively type `consult('your_path/checkers.pl').` in Prolog terminal, where `your_path` is a full path to `checkers.pl` file).

To start game type `play.`. You will be prompted for the side selection (black or white).

Board
----------

Game board appears like this:

```
    0   1   2   3   4   5   6   7
  ---------------------------------
7 |   | o |   | o |   | o |   | o | 7
  ---------------------------------
6 | o |   | o |   | o |   | o |   | 6
  ---------------------------------
5 |   | o |   | o |   | o |   | o | 5
  ---------------------------------
4 | . |   | . |   | . |   | . |   | 4
  ---------------------------------
3 |   | . |   | . |   | . |   | . | 3
  ---------------------------------
2 | x |   | x |   | x |   | x |   | 2
  ---------------------------------
1 |   | x |   | x |   | x |   | x | 1
  ---------------------------------
0 | x |   | x |   | x |   | x |   | 0
  ---------------------------------
    0   1   2   3   4   5   6   7
```

Cells are numbered from 0 to 7.
Figures are marked as: `X` - white king, `x` - white man, `O` - black king, `o` - black man.

Making Moves
------------

When prompted for move (`Your move:`) you need to enter start and destination positions for your move.
Each position is entered as `X-Y.`. For example, to move white man from cell (2, 2) to cell (3, 3) enter: `2-2. 3-3.`. You will see board updated after your move, and a board updated after computer responded to your move.

Capturing
----------------

In russian checkers when you have possibility to make capture, then you have to do it.
If you have possibility to capture, you will be prompted to enter capture path: `Please input your capture path (type 'end.' to finish):`.

Capture path is a list of positions, ending with a term `end.`.
The first position in a list is a position of your man or king which is making a capture. The other positions are positions of intermediate cells on which your figure jumps during the capturing.

For example, for the board below you can enter two possible capture paths (for white):

```
    0   1   2   3   4   5   6   7
  ---------------------------------
7 |   | . |   | . |   | . |   | . | 7
  ---------------------------------
6 | . |   | . |   | . |   | . |   | 6
  ---------------------------------
5 |   | . |   | . |   | . |   | . | 5
  ---------------------------------
4 | . |   | . |   | o |   | o |   | 4
  ---------------------------------
3 |   | o |   | . |   | . |   | . | 3
  ---------------------------------
2 | x |   | . |   | . |   | . |   | 2
  ---------------------------------
1 |   | X |   | . |   | . |   | . | 1
  ---------------------------------
0 | . |   | . |   | . |   | . |   | 0
  ---------------------------------
    0   1   2   3   4   5   6   7
Please input your capture path (type 'end.' to finish):
```

The first is `0-2. 2-4. end.`, to capture one enemy men using our men. And a second one is `1-1. 5-5. 7-3. end.`, to capture two enemy men using our king.

End of The Game
---------------

When one of the sides can't make any move - other side is considered a winner.
There is no check for the draw.

Tweaking
========

In the beginning of the **checkers.pl** file there are some predicates you can change, like depth of decision tree for minimax algorithm, initial positions of men and kings on the board, and board evaluation function.

License
=======

This program is licensed under BSD 2-clause license (or Simplified BSD License, or FreeBSD License).


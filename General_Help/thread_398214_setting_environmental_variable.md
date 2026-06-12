---
title: "setting environmental variable"
date: 2007-03-31
forum: General Help
---

### Post by gatoruss on 2007-03-31
Hi. I installed xboard to play chess. I have been reading thru the sparse documentation, and have a few questions I am hoping someone can help with.

Q1 -

The documentation says that game and position files are stored as followed:

> 
Game and position files are found in a directory named by the ‘CHESSDIR’ environment variable. If this variable is
not set, the current working directory is used. If ‘CHESSDIR’ is set, XBoard actually changes its working direc&#8208;
tory to ‘$CHESSDIR’, so any files written by the chess engine will be placed there too.


How do I set the 'CHESSDIR' environment variable?

Q2 -

There are various options that you can set. The documentation says:

> 
Each option corresponds to an X resource with the same name, so if you like, you can set options in your ‘.Xde&#8208;
faults’ file or in a file named ‘XBoard’ in your home directory. For options that have two names, the longer one
is the name of the corresponding X resource; the short name is not recognized. To turn a boolean option on or off
as an X resource, give its long name followed by the value true or false (‘XBoard*longOptionName: true’).

How do I edit '.Xdefaults' so that I can set some of these options. Alternatively, how can I make a file named "XBoard" in my home directory. I assume that I use the text editor to enter the various options, what type of file do I save it as?

Thanks for any help.

---

### Post by nixclusive on 2007-04-01
Hello there, in the terminal, enter ```
export VARIABLE=VALUE
``` to set an environment variable. This is temporary, start xboard from the same terminal.

The files are normal ASCII text files. If it says the file name should be .Xdefaults, then save it as .Xdefaults. There is no use of file extensions here.

Good luck.

---

### Post by gatoruss on 2007-04-01
Thanks!  That worked like I thought it should.

I need to set the variable each time I open a terminal, correct?  Is there any way to have this done automatically?

Appreciate your help.

---


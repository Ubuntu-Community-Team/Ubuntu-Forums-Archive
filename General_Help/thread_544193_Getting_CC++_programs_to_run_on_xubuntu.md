---
title: "Getting C/C++ programs to run on xubuntu"
date: 2007-09-06
forum: General Help
---

### Post by bossmanx9 on 2007-09-06
I recently installed xubuntu on my computer and it works fine, except for one thing.  I want to use it to write programs in C and C++.  However, after I write the code and compile the file correctly, the program won't run.  Usually you just type the name of the file into a terminal and it will run, but it keeps giving me the error "bash: command not found."  For example, I wrote a small C++ program called "conversion."  I compiled it successfully with no errors.  But when I type in "conversion" on the command line, I get the error: "bash: conversion: command not found."  How do I get the terminal to run conversion.o?

---

### Post by angryhomer17 on 2007-09-06
I'm not sure on this, but I think the following will help:

Quick answer:  ```
./conversion.o
```


This could be completely wrong.....but: You won't be able to run scripts without adding ./ before them. (Not sure why) conversion.o won't show up as a command because it isn't a command, it's a file (script?) and you have to specify that it is to be run in the terminal.

Anyway, hope this helps if you haven't tried it. Otherwise I guess some guy with more experience will know. Good luck.

---

### Post by bigboy_pdb on 2007-09-06
angryhomer17, you are mostly correct (except for calling the executable file a script). The variable PATH (which you can examine the value of by typing "echo $PATH" on the command line) contains a list of directories that Ubuntu will search for an executable in when you type it on the command line. Windows attempts to search for the executable file within the current directory before checking for it in the directories within its PATH variable. Linux does not do this. Thus, since the current directory is not in your Linux path it fails to find the executable. By typing "./" in front of the executable you are telling it to check in the current directory (because the dot character represents the current directory without a trailing forward slash).

---

### Post by bossmanx9 on 2007-09-06
It works!  Thank you very much for the help.  It was such a simple problem but gave hours of frustration!

---

### Post by jamvegan on 2007-09-06
By default, Ubuntu (not sure about Xubuntu) checks to see if you have a bin directory in your home directory, and if so, it adds it to your path.  So, you could create a ~/bin/ directory and place all of your executables there if you want to be able to run them without the "./" (this has the benefit that you can run them from any directory without having to use the full path).  You can also add any directory to your path by adding a line like the following to the end of your ~/.bashrc file.
```
PATH=$PATH:/home/newdirectory
```
The "/home/newdirectory" part would be replaced with the actual full path to the directory you wish to add.

---

### Post by bossmanx9 on 2007-09-06
Got it.  Thanks very much for the help!

---


---
title: "wine from terminal?"
date: 2007-05-16
forum: General Help
---

### Post by kendase3 on 2007-05-16
Hi everyone.  This is my first post, and I wasn't sure where it should go exactly, but I've been having some problems getting my bearings using wine specifically.  While I am able to use Steam if I manually hunt down the Steam.exe file every time, I'm not sure how I can make it runnable from the terminal, something like "wine Steam."  The problem seems to be that steam's .exe is in a Steam folder under Program Files, while all the other applications are under windows for some reason.  Is there a way to adjust for this?  I've looked all over this broad internet but so far have been unable to find anything.  Thanks.

---

### Post by rich.bradshaw on 2007-05-16
Just find what you need to type e.g.

wine /home/you/blahblahblah/Steam.exe

and run it, if it works then just make launcher for it, or a script.

To make a script go into gedit

type

#!/bin/bash

wine PATHTOFILE

and save in your home directory as steam

then in a terminal

chmod +x steam

./steam

you can run it like that.

---

### Post by Nythain on 2007-05-16
the above mentioned script should work, and the blah blah blah might look something like
~/.wine/drive_c/Program\ Files/Steam/steam.exe
but im not sure exactly
if its the wine directory you are having troubles finding, its a hidden directory inside your home
/home/you/.wine
if its the Program Files thats giving you fits
/home/you/.wine/drive_c/Program\ Files/
will get you there... the \ before the space lets linux know a space is coming up, and remember, terminal is very case sensitive

---


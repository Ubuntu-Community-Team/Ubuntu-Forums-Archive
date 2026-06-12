---
title: "Terminal launcher will open terminal, then close (does not exicute)"
date: 2006-11-05
forum: General Help
---

### Post by ethulin on 2006-11-05
Hello,

I just recently started using Ubuntu as my operating system and so far have been quite happy.

One thing I want to be able to do is execute terminal commands from my desktop, and I think that using a launcher is the way to do so.

The command I am using is:
```
WINEDEBUG=fixme-all wine "C:/Program Files/Steam/Steam.exe" -fullscreen -width 1024 -height 768 -applaunch 10 -heapsize 256000 +map_background none "$@"
```
Which launches Steam Counter-Strike 1.6 under Wine.

If I execute this command from the terminal it works fine, but when I run the launcher I created it just opens the terminal, closes it very fast, and does nothing further.

What am I doing wrong?

---

### Post by amohanty on 2006-11-05
Does it work if you check the run in terminal box in the launcher properties dialog?

AM

---

### Post by ethulin on 2006-11-05
Yes, I did check the "run in terminal box".

If I were not to check it then the terminal would not pop up at all.

---

### Post by amohanty on 2006-11-05
Ok uncheck that and try the following:
add **gnome-terminal -e** to the front of the command in the launcher and see if you get any error

AM

---

### Post by ethulin on 2006-11-05
Ok, I tried:
```
gnome-terminal -e WINEDEBUG=fixme-all wine "C:/Program Files/Steam/Steam.exe" -fullscreen -width 1024 -height 768 -applaunch 10 -heapsize 256000 +map_background none "$@"
```
ran as an aplication, not as an application in terminal.

Nothing happened at all, no terminal popped up like before, just absolutely nothing.

---

### Post by amohanty on 2006-11-05
So when you run the app from the terminal originally, you ran it as yourself?
I am just trying to make sure that its not a permissions issue.

AM

---

### Post by ethulin on 2006-11-05
Correct, I did not have to "sudo" or anything, I just ran the command.

Also, I was able to create a bash script:
```
#! /bin/sh
WINEDEBUG=fixme-all wine "C:/Program Files/Steam/Steam.exe" -fullscreen -width 1024 -height 768 -applaunch 10 -heapsize 256000 +map_background none "$@"

```
which ran just fine.  But this is not really a viable alternative, I want to use the launcher.

---

### Post by amohanty on 2006-11-05
Whoops missed something: try removing the **"$@"** at the end for the launcher. Its a bash expansion var to indicate all other arguments for a script or command.

Else try pointing the launcher target to the bash script and see if that works.

AM

---

### Post by ethulin on 2006-11-05
Firstly, I tried removing the portion at the end, which made no difference.

The second does work, but that was exactly what I was trying to avoid, and was so happy that launchers were supposed to do.

It seems to me that as soon as it is done executing the command the launcher closes the command line.  Or, another thing that I see might be causing it is that maybe it closes when the app spits back an error, but when I keep the terminal open by running it from the terminal it works.

Just some ideas.

---

### Post by amohanty on 2006-11-06
How about making this the launcher target:

WINEDEBUG=fixme-all wine "C:/Program Files/Steam/Steam.exe" -fullscreen -width 1024 -height 768 -applaunch 10 -heapsize 256000 +map_background none | tee ~/Desktop/launcher.log

This will send stdout to a file on the desktop. Then see if something is recorded.

AM

---

### Post by ethulin on 2006-11-06
Hm.  Very odd.

I created a launcher with that command and it opened terminal very fast, closed it, but created no log file on the desktop.

---

### Post by amohanty on 2006-11-07
Wow, I am at a loss about this. Sorry but that's pretty much the end of my knowledge well. 

Just as a last shot, have you tried it without the WINDEBUG flag in front ie take it out with **wine** being the first arg. Also try the same with the run application launcher (Alt+F2).

AM

---


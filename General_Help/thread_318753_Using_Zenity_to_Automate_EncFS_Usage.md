---
title: "Using Zenity to Automate EncFS Usage"
date: 2006-12-14
forum: General Help
---

### Post by roachk71 on 2006-12-14
I don't know if this has been covered yet, but I would like to automate the mounting of EncFS directories using Zenity to send the password to the encfs utility. I've been arthritic just about everywhere in my body since age 18, and would appreciate making this easier.

Suggestions, anybody?

EDIT: This has been resolved by myself, using a couple of (very) simple shell scripts. Zenity won't work in this case; an encrypted password through ssh-askpass must be passed to encfs.

---

### Post by sefs on 2006-12-14
I have an icon on my desktop to a bash script that uses zenity to pop up a dialog box that i can enter a passord in to mount a truecrypt drive.  You can look at it to see if it can be adapted to anything you need.  Only thing is I'm trying to figure out why its stopped working in Edgy after an upgrade yesterday.

[http://ubuntuforums.org/showthread.php?t=318499](http://ubuntuforums.org/showthread.php?t=318499)

---

### Post by roachk71 on 2006-12-14
Thanks a lot; I'll study the script for a while. At first glance it's syntactically correct, but it would appear at least one of the upgrades broke Tcl/Tk. I'll search for possible problems with those libraries online.

---

### Post by roachk71 on 2006-12-14
Looks like I've found the problem: Tcl was removed by the updates, apparently. I can't find any installed Tcl libraries in Synaptic, so I'll try installing each in turn, and let you know how the script runs after that.

UPDATE: Looks like Tcl has nothing to do with this at all. I've found one potential problem: double braces. Still checking... ](*,)

---

### Post by roachk71 on 2006-12-14
Ugh!!!

No matter what I do, I can't adapt this script; I keep getting an internal error saying BytesToKey returned zero!

However, try using #!/bin/bash instead of #!/bin/sh on the first line. 8)

And, a possible workaround may be using "which ssh-askpass" instead of zenity; it would appear an encrypted password is required to unlock these volumes now. 

I've since written a couple of much simpler scripts to mount and umount my encfs directories.

---

### Post by sefs on 2006-12-15
It was the move to dash by ubuntu that lead to my problems.  So after going back to bash things look like they sorted them selves out again.

---


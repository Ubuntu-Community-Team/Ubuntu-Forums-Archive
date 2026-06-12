---
title: "I = am stupid"
date: 2006-12-19
forum: General Help
---

### Post by hovind on 2006-12-19
So, I was messing around with my panel (GNOME desktop), increasing the size (for no particular reason, really). Once I increased the size to 64 (or maybe 65, i forget which step caused this issue), I was immediately logged out and prompted to log back in.

Once I logged in, the desktop loaded normally, but froze after a few seconds and returned me to the login screen. This happens repeatedly, and I do not have enough time between the desktop loading and freezing to do anything about the problem.

Logging in failsafe gives the same results; I can still use the machine thanks to an older KDE install that I never really used but am now glad I didn't uninstall.

Any suggestions for a quick fix? Is there some file where these prefs are stored that I can just delete or edit, or am I in for a thrilling reinstall of Ubuntu and associated ganshing of teeth associated with nidswrapper et al?

---

### Post by zanglang on 2006-12-20
I *think* the values for gnome-panel's settings would be somewhere inside your home .gconf folder, which you can edit from a terminal (Ctrl-Alt-F1) with the command gconftool-2. Not on my Ubuntu machine atm so I can't lookup the exact syntax on reverting changes you might have made (sorry), but try looking around around for instructions on doing that maybe?

---

### Post by mdurham on 2006-12-20
You should be able to do a consul login from the login screen. It's an option in the lower left of screen menu. Options->Select session.
Maybe you have to create a new user to fix it up?

---

### Post by hikaricore on 2006-12-20
I posted a solution to a similar issue here:

[http://www.ubuntuforums.org/showthread.php?t=316647&highlight=.gconf](http://www.ubuntuforums.org/showthread.php?t=316647&highlight=.gconf)

Though you have a gui to use to do this, if you follow the same instructions you will be able to boot into gnome again, or you can find the panels file somewhere in that mess of folders and remove or edit it manually.  Either your gnome ui gets reset or you fix it manually.  Fun choice :/  I've had to do this a few times.

---

### Post by hovind on 2006-12-20
Thanks, I'll try this out.

---

### Post by hovind on 2006-12-20
worked perfectly! i am delighted.
weird bug, though. now i know not to mess too much with panel parameters.

thanks!

---

### Post by hikaricore on 2006-12-20
No problem :)  Last time I had this issue I accidently made the panel about 128px >.<  Gnome got pissed.

---


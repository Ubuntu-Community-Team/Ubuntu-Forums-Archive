---
title: "long time delay to start terminal or nautilus"
date: 2024-08-16
forum: General Help
---

### Post by sz3bbyla on 2024-08-16
I have a strange behave on ubuntu 24.04

example:
I start ubuntu and nautilus or terminal or other programs start normal and fast
after log out and log in 
nautilus or terminal have a long delay until start (30 seconds)

I don't know how to check or to view why apear this behave and to fix it

---

### Post by TheFu on 2024-08-16
Is the networking setup for 1 user or the entire system?  Slow DNS can make for a slow system.  There are lots of things that do DNS lookups that aren't obvious on first thought.

For any terminal, the startup process for the shell used can make those slow.  You'll need to trace all the startup scripts to figure out what might be slowing things down.  An easy tests is to mv ~/.login,  ~/.profile  and ~/.bashrc (if you use bash as your shell)  to bak files, then logout and login again.  See if that helps.  If it doesn't, then the issue is unlikely to be the startup files.  There are lots of possible shell programs, which your user may have been changed.  If you are new, best to stick with bash, regardless of what some friend claims about a different shell.

---

### Post by currentshaft on 2024-08-16
X3

---

### Post by sz3bbyla on 2024-08-17
I'm on x11 (xorg) and computer is with 2 display's

the only script at startup for the moment is to start with only one display
xrandr --output DP-0 --mode 2560x1440 --output HDMI-1-1 --off

---


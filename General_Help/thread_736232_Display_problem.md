---
title: "Display problem"
date: 2008-03-26
forum: General Help
---

### Post by saurish on 2008-03-26
Hi all,

After logging in to Ubuntu, I get a blank screen with the default background color (no taskbar, no desktop icons). I can switch to command line by pressing Alt-Ctrl-F1, but don't know the command that will fix the problem.

My system used to work fine. All this happened after I did a forceful shutdown while installing new updates (the computer was not responding to anything).

Can anyone help?

Thanks,
Saurish.

---

### Post by pseudo-random on 2008-03-26
Sounds like a broken Xserver. Could you use that terminal to 
```
cat /etc/X11/xorg.conf 
```
and post it here?

---

### Post by saurish on 2008-03-26
A long list comes up. It has these "Sections":

Files - empty
Keyboard
Mouse
Touchpad
3 sections with driver wacom and identifiers "stylus", "eraser" and "cursor"
device with identifier "ATI technologies ..."
Monitor
Server layout
Module
Extensions

I don't know how to copy the file somewhere.

---

### Post by saurish on 2008-03-29
An update fixed the problem. Thanks:lolflag:

---


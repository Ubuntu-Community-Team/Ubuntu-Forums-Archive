---
title: "The WM won't rezise after xranr rotate"
date: 2008-06-11
forum: General Help
---

### Post by pooljamn on 2008-06-11
I have a Toshiba Tecra M4 tablet.  When I use "xrandr -o right" to rotate the screen X does what it should, but the window manager doesn't resize.
Using Gnome/Compiz
Ubuntu 7.10

Example with cheesy ascii art:

Normal screen:
xxxx
xxxx
xxxx

Tablet screen:
xxxo
xxxo
xxxo
nnn

simple math here..  4 across and 3 down in normal mode or 3 across and 4 down as a tablet representing the aspect ratio of the screen resolution.  really 1400x1050 in normal or 1050x1400 as a tablet.
x being visible workspace
o being the part of the window manager that's off screen after rotation
n being new found real estate after rotation where the mouse can move but no windows can be dragged

Pretty much the WM needs to resize to 1050x1400 just like X does but it doesn't.  The mouse knows it's new boundaries, just not the WM.  Sorry, I tried to take a screen shot, but just got an image that's 1400x1050 with the last 350 columns of pixels on the right being black..  not very helpful.  It doesn't even know about the 350 new lines below.

To rotate I wrote a script to poll /proc/scp/button/lid/LID/state and the output of xrandr --query for current state (open and normal or closed and right, etc) every few seconds (runs backgrounded upon login).  On a side note it would be nice to make an ACPI event run this program for me, but that's another project..  pointers on using the built in ACPI mechanism instead of polling via shell script would be helpful too but for now I'd just like to be able to use the whole screen when configured as a tablet.

Thanks in advance for sharing your experience.

---

### Post by pooljamn on 2008-06-11
yea.. I should proof read..
resize not rezise and /proc/acpi, not /proc/scp.  you get the idea..  since when did 'nix geeks care about bad typing anyway ;)

---


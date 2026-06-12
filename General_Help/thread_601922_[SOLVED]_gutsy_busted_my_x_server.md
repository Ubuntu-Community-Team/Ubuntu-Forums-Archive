---
title: "[SOLVED] gutsy busted my x server"
date: 2007-11-03
forum: General Help
---

### Post by Chymera on 2007-11-03
ok, so i just upgraded to gutsy, and my x server just got jammed; it seems to work, plays that annoying login melody, then reverts back to the login screen, 
Tried a fail safe gnome session (needless to say, it failed)
Then i treid recovery mode, and the only error message i could make out is the following:

> fatal server error:
Caught signal 11. Server aborting
xinit:connection to xserver lost

---

### Post by Prospero2006 on 2007-11-03
ok, you have the option to do a console login from both gdm and kdm.
You should find that and log in using just a text shell.

Second, 
run startx from the command line.
Post the output here.

Third, 
Tell us what kind of graphics card you are running and post the xorg.conf file.

This will help you get your solution faster.

Pros

---

### Post by Chymera on 2007-11-04
10x for your suggestion.... i just ran ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and that got me up and running again

---


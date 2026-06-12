---
title: "GNOME troubles"
date: 2007-05-06
forum: General Help
---

### Post by edfredcoder on 2007-05-06
Hello. I have been having some problems with GNOME. I use a normal Ubuntu 7.04 install, but I normally use fluxbox, gotten through apt-get. Yesterday, I decided to switch back to GNOME, just to try out some new themes (Mac OS X clones, if I remember correctly). I downloaded them from gnome-look.org, and installed them as the directions say. While switching themes, the screen locked up after getting really slow. I killed X via control+alt+backspace, and tried logging in again to GNOME. Didn't work, although fluxbox does. When I log into GNOME, all I get is a screen that is all one color, a sort of light blue. A mouse does appear. Does anyone know what could cause this, and how to fix it?

-Kevin

---

### Post by z0phi3l on 2007-05-06
have you tried reinstalling GNOME?

---

### Post by edfredcoder on 2007-05-06
How do I do re-install GNOME?

---

### Post by glaeven on 2007-05-06
if you can: "sudo startx" should restart gnome using the default (root) settings.

you may have to reintall gnome (ubuntu, even).

---

### Post by edfredcoder on 2007-05-06
Running sudo startx doesn't fix it, I get a message saying that X is already running, even if I do this from the failsafe terminal or I am not logged in, and I go to a terminal via Control+Alt+F1, then log in, then run startx.

Any other suggestions?

-Kevin

---

### Post by edfredcoder on 2007-05-06
Bump, because this part of the forum is so active.

---

### Post by eggdeng on 2007-05-06
To be going on with, you could try Ctrl-Alt+Backspace if in graphical mode, then ```
ps -A
``` to list running processes, see if you get a pid for Xorg. If so, ```
kill your_Xorg_pid
``` then ```
startx
```

---

### Post by edfredcoder on 2007-05-06
Thank you for replying! I killed X like you said, but that didn't work. GNOME remains dead. Does anyone know how to re-install GNOME?

---

### Post by strabes on 2007-05-06
You can remove a program and its settings with ```
sudo aptitude purge <package>
```

Unfortunately there isn't a command specifically to remove gnome and I'm hesitant to say use ubuntu-desktop.

---


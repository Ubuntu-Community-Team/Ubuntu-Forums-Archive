---
title: "Refusing to initialize GTK+"
date: 2007-10-22
forum: General Help
---

### Post by evilc on 2007-10-22
I know there  have been other posts on this but I haven't seen any answers to fix it, could someone tell me how to fix this.


Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/clive:/tmp/.ICE-unix/5335
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
Initializing gnome-mount extension
** Message: Not starting remote desktop server
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format 

I have reloaded Gutsy as it started to play up and fall over all over the place, this error was in the 1st installation so I really don't want to do it all again.

tia

---

### Post by evilc on 2007-10-22
bump

---

### Post by evilc on 2007-10-23
51 views no suggestions?

There must be a fix for this problem I have reloaded 4 times as bits & pieces keep falling over, there was no problem in Feisty  why should there be in Gutsy? What's the point of having updated  programs/ operating files if they are going to fail as they have in Gutsy.

---

### Post by yitercel on 2008-01-14
perhaps permission error, for example:
/tmp/ 777

---


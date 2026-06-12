---
title: "Wrong screen resolution when I get into Gnome"
date: 2005-08-03
forum: General Help
---

### Post by FNM on 2005-08-03
How do I configure the screen resolution before I get into Gnome? Ubuntu sets it at something like 1280x1024, which is way to high, and makes the screen unusable. My screen is set for 1024x768. My plan was to boot the live DVD, make sure all my hardware was detected, and then do a hard disk install. So, if I can't configure the resolution for the live DVD, can I atleast configure it during the install process?

---

### Post by lol on 2005-08-03
You can try the following:

* After X (with gnome in your case) is started from the live CD:
- ctrl + alt + '-' (or ctrl + alt + '+') => if the live CD is correctly setup, this should change your resolution. You will end up with a virtual desktop larger than you screen, but you should be able to access the gnome preference menu and modify the resolution.

* Afer installation on you HD (and after X is started):
 - ctrl + alt + F1
 - then log on and edit the file /etc/X11/xorg.conf or /etc/X11/XF86Config-4 to specify a lower resolution
 - restart X the following way : /etc/init.d/gdm restart

hope this can help...

---


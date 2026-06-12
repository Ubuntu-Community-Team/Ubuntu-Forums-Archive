---
title: "xserver problem"
date: 2007-02-15
forum: General Help
---

### Post by Reder on 2007-02-15
hi...I'm italian...so...don't worry for my english..
when i login to my kubuntu edgy  i receive an error:

xsession:warning:unable to write to /tmp; xsession may exit with an error.

and after few seconds the desktop restart and appear the login window...repeating this for some times the desktop block...and i must restart the pc.. help mee!!!

---

### Post by Ramses de Norre on 2007-02-15
Have you messed with permissions or is your hard disk full?
Boot a live cd, mount root (at e.g. /media/root/) and use **ls -lA /media/root/ && ls -lA /media/root/tmp** to check the permissions, **df -h** prints the available space on the filesystems.

---

### Post by Reder on 2007-02-15
ok...i solve...the root directory was full.....thanxx!!!

---


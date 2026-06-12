---
title: "Is it possible to recover original config files."
date: 2008-06-02
forum: General Help
---

### Post by mempman on 2008-06-02
Is it possible to somehow obtain the original post-install config file (for example /etc/X11/xorg.conf). 

I understand the config files are custom made during install time for specific hardware combo's, based on this fact is it possible to recreate the config file (via ubuntu installer or something)?

---

### Post by NT4usB on 2008-06-03
What version you running? 
Hardy makes all sorts of copies and backups of xorg.conf while it's installing. 
You should be able to cd to /etc/X11/ and ls *xorg* to see them.
You can get a fresh xorg.conf (not original, but working) by:```
sudo dpkg-reconfigure -phigh xserver-xorg
```It too will make a backup of the existing before recreating it.

---


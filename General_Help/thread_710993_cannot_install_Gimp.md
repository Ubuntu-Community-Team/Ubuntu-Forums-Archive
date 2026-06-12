---
title: "cannot install Gimp"
date: 2008-02-29
forum: General Help
---

### Post by Maverynthia on 2008-02-29
I'm trying to install Gimp 2.4, when I do the ,/configure this comes up:

checking for GTK+ - version >= 2.10.13...
*** 'pkg-config --modversion gtk+-2.0' returned 2.10.14, but GTK+ (2.8.20)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GTK+. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: Test for GTK+ failed. See the file 'INSTALL' for help.

How do I uninstall gtk 2.8 or whatever, or fix this?

---

### Post by zvacet on 2008-02-29
You are trying to install Gutsy package in Feisty.That make you problems.

---

### Post by Maverynthia on 2008-03-02
So there's no way to uninstall gtk (or upgrade) and I'm stuck with an old version Gimp that I can't update :<

---

### Post by Oldsoldier2003 on 2008-03-02
> **Maverynthia said:**
> So there's no way to uninstall gtk (or upgrade) and I'm stuck with an old version Gimp that I can't update :<
You can always compile gimp from source and install it on your system.

---

### Post by Maverynthia on 2008-03-04
That's what I'm trying to do, or at least I thought I was doing when I was ./configure and make, make install :<

---

### Post by zvacet on 2008-03-04
if you want to upgrade gtk read [this.](http://www.gtk.org/download-linux.html)

---


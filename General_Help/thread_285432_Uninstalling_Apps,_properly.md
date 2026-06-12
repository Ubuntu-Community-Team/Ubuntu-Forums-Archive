---
title: "Uninstalling Apps, properly"
date: 2006-10-26
forum: General Help
---

### Post by lagerratrobe on 2006-10-26
I'd like to uninstall some of the apps that come with Ubuntu, and which are of no use to me at the moment.  I would like to do this in a way that does not remove all of their dependencies, which is what happened when I did a "sudi apt-get remove <blah>" last time.  The apps are most of the default "Sound and Video" apps that come with Dapper; Totem, Rhythm Box, Sound Juicer, etc.

Thanks in advance.

---

### Post by meng on 2006-10-26
sudo apt-get remove ----
does not remove the program's dependencies, but it will remove any packages which are dependent upon the program you are removing. In the case of Totem, Rhythmbox, Soundjuicer, this will include removing ubuntu-desktop. That's okay, ubuntu-desktop is an empty meta-package, and you can remove it without breaking your system.

---

### Post by learning curve on 2006-10-26
If you have enough hard drive space leave them where they are and don't take the chance of messing up something else.8)

---

### Post by beerfan on 2006-10-26
> **lagerratrobe said:**
> I'd like to uninstall some of the apps that come with Ubuntu, and which are of no use to me at the moment.  I would like to do this in a way that does not remove all of their dependencies, which is what happened when I did a "sudi apt-get remove <blah>" last time.  The apps are most of the default "Sound and Video" apps that come with Dapper; Totem, Rhythm Box, Sound Juicer, etc.

Thanks in advance.

Don't use apt-get. Uninstall programs from synaptic or "add/remove" and it will show you a list of what will be changed.

---

### Post by aysiu on 2006-10-26
> **beerfan said:**
> Don't use apt-get. Uninstall programs from synaptic or "add/remove" and it will show you a list of what will be changed.
*apt-get* also shows you a list of what will be changed.

---


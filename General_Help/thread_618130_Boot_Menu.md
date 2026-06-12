---
title: "Boot Menu"
date: 2007-11-20
forum: General Help
---

### Post by sudharma on 2007-11-20
I am new to Ubuntu.
On the boot menu, the following selections appears.:-
Ubuntu - Kernel - 2-6-20-16 - Generic
Ubuntu - Kernel - 2-6-20-16 -  Recovery Mode
Ubuntu - Kernel - 2-6-20-15 -  Generic
Ubuntu - Kernel - 2-6-20-15 -  Recovery Mode
Ubuntu - memtest 86+

Other OP System
Windows XP

Why there are 2 set of Ubuntu namely
 -16- generic / recoverey mode 
- 15- generic / recoverey mode 

Do I need this 2 Sets of Ubuntu. Can I remove one set and how do I do it.
1)    flash-plugin-9.0.48.0-release.i386.rpm
2)    adobe-release-i386-1.0-1.noarch.rpm

Any help to resolve these issue are much appreciated.

---

### Post by jespdj on 2007-11-20
You have two Linux kernels installed: the older 2.6.20-15 and the newer 2.6.20-16.

You can uninstall the older one with Synaptic.

---

### Post by anaconda on 2007-11-20
Or type:
```
sudo gedit /boot/grub/menu.lst
```
and comment the lines of the 15-generic kernel by adding a # in front of those lines..

I dont usually uninstall old kernels, because a couple of old kernels might come useful if you have problems and need to recover from some serious errors..

Why do you have hose .rpm files in the end of your post? If you want to install those programs you should rather use .deb packages.. .rpm:s are meant for redhat based distros. and sure it is possible to use .rpm :s in ubuntu, but native .deb :s are more reliable..

---


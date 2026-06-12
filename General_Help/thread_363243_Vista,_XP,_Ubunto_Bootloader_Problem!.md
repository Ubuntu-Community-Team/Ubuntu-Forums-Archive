---
title: "Vista, XP, Ubunto Bootloader Problem!"
date: 2007-02-16
forum: General Help
---

### Post by VelocyRaptor on 2007-02-16
hi!

I've got a big problem! I want to run three differen operating systems on my notebook (100 GByte HDD). First a created a 25 GB partition and installed Windows XP Prof., then I've installed Windows Vista on another 25 GByte partition. 

Everything worked very well!

At last I installed ubuntu 6.10. (Ubuntu works great!), but when I select the Vista/Longhorn-Loader in the GRUB, my PC restarts.

Does sombody know how to proceed to solve this problem?

thx VR

---

### Post by H.E. Pennypacker on 2007-02-16
Let's begin by taking a look at your GRUB list, which is the list that keeps track of all the operating systems you have installed.  It lists them, and even allows you to select in which order the operating systems are listed.

Please post /boot/grub/menu.lst.

We'll see if something's up.

---


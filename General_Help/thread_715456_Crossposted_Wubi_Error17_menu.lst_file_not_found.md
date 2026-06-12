---
title: "Crossposted Wubi Error17 menu.lst file not found"
date: 2008-03-04
forum: General Help
---

### Post by USFMD82 on 2008-03-04
So my battery died on my laptop while linux was in suspend mode, and now I cant boot up linux.. when I choose linux in the dual boot menu this comes up

Quote:
Booting 'find /wubi/boot/grubMenu.lst'
Booting 'find /menu.lst'
find--set-root--ignore-floppies/menu.lst
Error 17:File not found
Press any key to continue...
when I press a key this comes up
Quote:
find /ubi/boot/grubmenu.lst
find /menu.lst
find /boot/grub/menu.lst
find /grub/menu.lst
commandline
reboot
halt
When I click on any of the menu.lst files it just takes me back to the menu

When I click commandline it just brings up a "DOS-like interface" and ends with grub>

When I push halt it just goes to anotehr screen with the words halt and a few other characters

Reboot obviously reboots..

So I forgot to add that I checked my C: drive and I have wubildr.mbr, wubildr and boot.ini is not there

---

### Post by USFMD82 on 2008-03-04
Nevermind I booted up in xp and the system automatically ran a chkdsk.. and that seemed to fix that. so problem solved

---

### Post by sc4224751 on 2008-09-22
do you know if this works with vista? i ran into the same problem.


> **USFMD82 said:**
> Nevermind I booted up in xp and the system automatically ran a chkdsk.. and that seemed to fix that. so problem solved

---


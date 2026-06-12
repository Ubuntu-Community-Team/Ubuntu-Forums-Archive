---
title: "problem: two hard drives, two grub installations"
date: 2006-10-15
forum: General Help
---

### Post by vaskeli on 2006-10-15
i just added a second hard drive to my system. i used to the ubuntu live cd to format it, so consequently i have an ubuntu installation on each hard drive.

the second drive is supposed to be strictly for storage, but at bootup, grub is now loading from the grub directory on hdb, and ignoring the one on hda. this is backwards. i want grub to load from hda, so in the future i can reformat hdb without causing errors. how do i tell the system to load grub from hda?

---

### Post by jpkotta on 2006-10-15
Try this: [https://help.ubuntu.com/community/GrubHowto#head-62dd4ea50c42fb3113752a272d7100469d733668](https://help.ubuntu.com/community/GrubHowto#head-62dd4ea50c42fb3113752a272d7100469d733668)

---

### Post by Kateikyoushi on 2006-10-15
Follow [this guide]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub").

---

### Post by vaskeli on 2006-10-15
jpkotta

i followed the instruction in the link, but still have the same issue.

see, i have a boot/grub folder on each drive, and therefore two menu.lst files.

at bootup, the system insists on reading menu.lst on hdb1. i want it to read menu.lst on hda1.

no matter what modifications i make to menu.lst on hdb1, grub still needs to access hdb1 in order to load it. if i simply rename or delete the grub directory on hdb1, i get a boot failure.

---

### Post by dagnabit dang doohickey on 2006-10-15
You might be able to pick up some tips from this thread and also through the links that the OP provides.

[A grub menu booting 100+ systems of Dos, Windows, Linux, BSD and Solaris]("http://www.justlinux.com/forum/showthread.php?threadid=143973")

---

### Post by vaskeli on 2006-10-15
turns out the instructions in kateik's link were exactly what i needed. (i ran grub from a terminal and did "root (hd0,0)" and "setup (hd0)". now grub loads menu.lst from my first hard drive. i just wiped the 2nd drive and rebooted successfully.

thanks to everyone who replied. ubuntu "customer service" rules. :)

---


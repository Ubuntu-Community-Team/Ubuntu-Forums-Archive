---
title: "Windows XP boot flag changes after boot."
date: 2008-05-11
forum: General Help
---

### Post by adamprawitz on 2008-05-11
I have a dual boot, Ubuntu first, and then XP.  Everything works fine until I boot into Windows.  After I boot into Windows, it sets its own boot flag, so that I can't get to Grub (or Ubuntu) unless I use the Gparted boot disc or the Ubuntu live disc.  I then have to switch the boot flags around again.

This happens every time I boot into Windows!  I couldn't find anything in the forums about it.

---

### Post by rmbell on 2008-11-14
bump

I am having the same problem. Ubuntu partition on /dev/hda1 and xp on /dev/hda2 and everytime I boot XP, it changes the boot flag.

---

### Post by TeXtonyx on 2008-11-14
In menu.lst, do you have "makeactive" in your windows xp entry?

---

### Post by caljohnsmith on 2008-11-14
As TeXtonyx mentioned, probably in your /boot/grub/menu.lst your Windows entry as a "makeactive" line, which sets the boot flag; I just wanted to mention though that the boot flag does not need to be set on a partition for Grub to boot it. But even if you are using Grub, it is a good idea though that one partition on your HDD have the boot flag set, because some BIOSes will refuse to boot a drive that doesn't have a partition with the boot flag set (the BIOS assumes it is a data drive and unbootable).

---

### Post by rmbell on 2008-11-14
that was it, thank you so much!

---


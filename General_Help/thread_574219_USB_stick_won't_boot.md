---
title: "USB stick won't boot"
date: 2007-10-12
forum: General Help
---

### Post by alzaf on 2007-10-12
I am trying to install ubuntu onto a 2gb usb stick using the following link [https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html)

I am doing everything as instructed but when I boot laptop, it does not boot from the USB stick but goes to HDD on my laptop.

I have a 128MB usb stick and have managed to boot from that and was able to start the ubuntu installation. Unfortunately due to space, the installation could not be finished.

This rules out the possibiltiy that I am unable to boot from a USB stick.

I have tried to compare the two sticks using fdisk and can't  find any difference between the two. For reference, the fdisk output of the 2gb usb stick is as follows:

Disk /dev/sdb: 2062 MB, 2062548992 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          95      763056    6  FAT16
/dev/sdb2              96         250     1245037+  83  Linux


Is there anybody who knows what this issue is?

---


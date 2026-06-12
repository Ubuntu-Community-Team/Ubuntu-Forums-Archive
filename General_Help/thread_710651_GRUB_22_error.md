---
title: "GRUB 22 error"
date: 2008-02-28
forum: General Help
---

### Post by marrstu on 2008-02-28
I was running ubuntu 7.1 (64-bit) I left my computer on while I was at work and when I came home I was greeted to a GRUB error 22. I only have Ubuntu installed (no other OS). One SATA hard drive, I had a external but I tried booting with the external unplugged and same issue. I am able to boot of the live CD (which is what I am currently on). I am new to linux so bare with me, I have tried a couple things:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+22](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+22)
Someone with a simmilar problem mentioned that this resolved it however when I tried that after I typed in find /boot/grub/stage1 I got "could not find file"

I also tried playing around with the boot order in the BIOS because I saw that some people mentioned that if they had a bootable disk in a drive they where able to bypass the error message, that did not work for me.

I am a bit lost any advice would help.

---

### Post by Islington on 2008-02-28
Have you tried restoring it?

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by marrstu on 2008-02-28
Been trying some of the things listed there I will give a update once I have tried it all or once I got it working, hopefully the latter.

---

### Post by marrstu on 2008-02-28
Everything seems to fail, I run fdisk -l I get:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff1b5d64

   Device Boot      Start         End      Blocks   Id  System

If I open up partition editor it says there are no partitions, is it possible that my drive is the issue?

---


---
title: "Grub, Ubuntu, Vista"
date: 2007-05-03
forum: General Help
---

### Post by KocetoNs on 2007-05-03
Hi.
I have one HDD with several partitions:
hda1 is my Windows XP (NTFS)
hda5 is my Data partition (NTFS)
hda4 - linux swap
hda3 - Ubuntu Feisty Fawn (Reiserfs)
Now i`ll make new partition on wich i want to install Windows Vista.The problem is that Vista will overwrite my MBR.I think that the best i can do is to make boot partition.I have Ubuntu LiveCD wich i intend to use.
My question is how to chroot from the livecd and install grub into the new boot partition.
If there is a better way...

---

### Post by Famicommie on 2007-05-03
Windows will eat GRUB, but it is easy to reinstall.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---


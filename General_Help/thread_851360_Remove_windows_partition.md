---
title: "Remove windows partition"
date: 2008-07-06
forum: General Help
---

### Post by mcarro on 2008-07-06
Hello.  Like many other, I have a windows partition (with XP) which I have not used for very long.  As it is taking about 10% of the HD in my laptop, I'd like to devote it to Linux (probably reformat with ext3 and mount it on /var or /opt).

My question comes because it is the first partition in the disk and it is the boot partition:

[FONT="Fixedsys"]sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001787b

   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        1530    12289693+   c  W95 FAT32 (LBA)

/dev/sda2            1531        1655     1004062+  83  Linux

/dev/sda3           11889       12161     2192872+  82  Linux swap / Solaris

/dev/sda4            1656       11888    82196572+  83  Linux[/FONT]


Therefore, I am afraid that just deleting it will make my system unable to boot.  Needless to say, I do not want to "try and see".  What would the right way to proceed?  Would parted / gparted take care of this correctly?

Thanks a lot in advance!

---

### Post by PGScooter on 2008-07-06
Hey mcarro,

I did some searching around and I found a really cool utility to add to the tool box :)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
see here for the documentation:
[http://www.supergrubdisk.org/wiki/SuperGrubDisk](http://www.supergrubdisk.org/wiki/SuperGrubDisk)

Some of its uses (taken from the documentation site):
"* GNU/Linux is installed in your pc, you reinstall Windows and GNU/Linux no longer boots as Grub menu no longer appears on boot. You can restore Grub on your MBR automatically.
   * You have Windows installed in a second hard disk and it does not want to boot. If you swap it from Super Grub Disk you will be able to boot it.
   * You can not boot Windows because your MBR is corrupt or Grub installation is not well done or whatever. With Super Grub Disk you will be able to boot the partition where Windows reside.
   * No Active Partition Found message appears. With Super Grub Disk you can activate partitions.
"

In other words.. if things do go wrong when you get rid of that windows partition, super grub should be able to fix them. Nonetheless, ALWAYS MAKE BACKUPS of your important files.. if you want to make partition backups, try partimage.

Good luck with everything!

---


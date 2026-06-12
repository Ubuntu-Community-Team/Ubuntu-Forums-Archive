---
title: "Gparted doesn't see partition table"
date: 2007-10-14
forum: General Help
---

### Post by bobbarker on 2007-10-14
Trying to resize my NTFS partition, making more room for my ext3, windows stopped booting, so I did a fixmbr/fixboot commands and my entire HD was re-written as FAT16. After going through the motions with testdisk, and reinstalling grub, I'm back to where I was two days ago, although, gparted doesn't see my partitions as they were.
fdisk gives this:
```

adamsteele@bim:~$ sudo fdisk /dev/sda -ls
[sudo] password for adamsteele:

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69737369

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            3132        4278     9213277+  83  Linux
/dev/sda3            4737        4864     1028160   82  Linux swap / Solaris

```
That is correct but gparted doesn't see anything as it was. I desperately need gparted to work (or some other partition utility) because my ext3 partition is 100% full.

If it matters I'm using Gutsy, but the Feisty livecd shows the same stuff, so it shouldn't

EDIT:
The error I do get when starting gparted is
[b]The kernel is unable to re-read the partitiontables on the following devices:
- /dev/sda[/b]

---

### Post by Pumalite on 2007-10-14
Have you tried the Gparted Live CD?: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by bobbarker on 2007-10-14
I'll try it and see what happens.

---

### Post by bobbarker on 2007-10-24
Got around to trying the livecd, which I could not get to boot. I am booting from a USB CD drive, which the grub menu had an option for...but still wouldn't go. The error happened when it tries to load the /gparted.dat file.

Any other ideas?

EDIT:
Got the livecd gparted to work using a USB stick and it showed my disk as all fat16 like all the other gparted apps did.

DOUBLE EDIT:
Figured it out, boot to a livecd, delete the fat16 partition with gparted, restore the proper partitions with testdisk, and you're done. One thing that was odd was neither cfdisk nor gparted could resize my ext3 "to the right" although the gparted livecd could.

---


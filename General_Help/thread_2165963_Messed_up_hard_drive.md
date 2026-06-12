---
title: "Messed up hard drive"
date: 2013-08-07
forum: General Help
---

### Post by DisappearingOak on 2013-08-07
Hi, I installed another distribution (Rosa) and it failed to install grub, and upon reboot, I entered my Ubuntu 12.04 install, (my previous grub was safe) and when I updated grub, it wouldn't detect the new install, so I reinstalled grub to /dev/sda and it failed saying something like it couldn't access a sector of /dev/sda outside the disk (I don't have the exact error on hand :(.). Doing fdisk -l and gparted said the drive had an invalid partition table (so something got messed up). I looked online and using testdisk I did a partition 'quick search' and wrote a new partition table to disk. On reboot, everything boots into Ubuntu 13.04 including grub. fdisk -l doesn't have error anymore, but gparted shows my whole disk as unallocated!! And fdisk -l shows all partitions but something seems messed up (the sector of partitions seem to start with intervals in the middle, is that normal?). Since I can boot into a distro right now, I'm not too scared. But I really want to recover this without reinstalling (I have Windows and many distros on differnt partitions (which I can boot into right now and don't want to lose). Please help because gparted show unallocated and I need to extend space on my current partition.

fdisk -l

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes, 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b6818

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    69634047    34816000   83  Linux
/dev/sda2        69634048   131074047    30720000    7  HPFS/NTFS/exFAT
/dev/sda3       131074048   193984199    31455076   83  Linux
/dev/sda4       193984245   976784129   391399942+   f  W95 Ext'd (LBA)
/dev/sda5       193984512   255424503    30719996   83  Linux
/dev/sda6       255428608   316868055    30719724   83  Linux
/dev/sda7       316868608   346165247    14648320   83  Linux
/dev/sda8       346634568   408074567    30720000   83  Linux
/dev/sda9       408088576   469528575    30720000   83  Linux
/dev/sda10      501194815   746956798   122880992   83  Linux


```

Kpartition manager of kde is also showing invalid partition table now. is there a way to recover without borking anything including the grub boot process?

---

### Post by DisappearingOak on 2013-08-07
apparently /dev/sda4's end point is too large.
I'm trying to rewrite this partition table to disk using
sfdisk /dev/sda < file.txt

but it gives me blkrrpart disk busy error, I did sudo umount -a and also rebooted twice but still blkrrpart disk busy. how can I write this partition table from within the Ubuntu install itself (i don't have a cd drive or usb drive on hand) - apparently testdisk can do it so it should be possible!!!
```

sudo umount -a
umount: /run/user: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /run/shm: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /run: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

new partition table I made following tutorial at gparted website.
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 69632000, Id=83, bootable
/dev/sda2 : start= 69634048, size= 61440000, Id= 7
/dev/sda3 : start=131074048, size= 62910152, Id=83
/dev/sda4 : start=193984245, size=782788923, Id= f
/dev/sda5 : start=193984512, size= 61439992, Id=83
/dev/sda6 : start=255428608, size= 61439448, Id=83
/dev/sda7 : start=316868608, size= 29296640, Id=83
/dev/sda8 : start=346634568, size= 61440000, Id=83
/dev/sda9 : start=408088576, size= 61440000, Id=83
/dev/sda10: start=501194815, size=245761984, Id=83
```

Please help me install this new partition table. help!.

---

### Post by DisappearingOak on 2013-08-07
Nevermind. I went the drastic route and deleted partition 2-10 with fdisk. and then gparted started working so I made new partition and reinstalled my distro.

---


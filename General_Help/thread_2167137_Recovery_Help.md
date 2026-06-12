---
title: "Recovery Help"
date: 2013-08-12
forum: General Help
---

### Post by dean3 on 2013-08-12
Hi,

I have a laptop that was running windows before, and then I sucessfully put linux on it. It was going fine for a while, but then I got an unknown filesystem: grub rescue error. 
I saved many files on the desktop while using linux, and i'm trying to get them back.

I am able to run the laptop successfuly with an ubuntu live cd, but I could not find my saved files using nautilus from the live cd. 

Here is some info for you from the terminal:

ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow           1004M  225M  780M  23% /
udev            996M  4.0K  996M   1% /dev
tmpfs           402M  868K  401M   1% /run
/dev/sr0        694M  694M     0 100% /cdrom
/dev/loop0      663M  663M     0 100% /rofs
tmpfs          1004M   12K 1004M   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none           1004M  212K 1004M   1% /run/shm
/dev/sdb1       7.5G   79M  7.4G   2% /media/26B2-C81A
/dev/sda1       2.5G  1.7G  841M  68% /media/MEDIADIRECT

-

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008f73c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   307337216   312578047     2620416    c  W95 FAT32 (LBA)
/dev/sda2       308408318   312580095     2085889    5  Extended
/dev/sda5       308408320   312580095     2085888   82  Linux swap / Solaris

Disk /dev/sdb: 8004 MB, 8004304896 bytes
35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32    15633407     7816688    b  W95 FAT32

-

How can I get my files back? Thank you!

---


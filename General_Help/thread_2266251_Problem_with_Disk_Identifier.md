---
title: "Problem with Disk Identifier"
date: 2015-02-21
forum: General Help
---

### Post by marco84 on 2015-02-21
Hello,
I have a little problem with copy ISO into my Usb.

If if copy a disk image downloaded from the ubuntu web site, all it's great:
> dd bs=4M if=Desktop/trusty-desktop-i386.iso of=/dev/sdb && sync
244+1 records in
244+1 records out
1025507328 bytes (1.0 GB) copied, 89.6218 s, 11.4 MB/s

fdisk -l /dev/sdb


Disk /dev/sdb: 31.5 GB, 31466323968 bytes
64 heads, 32 sectors/track, 30008 cylinders, total 61457664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3eb8b2a3


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           0     2002943     1001472   17  Hidden HPFS/NTFS




The problem is when i change an iso. For changing an iso i mounted it and I copied all files into a directory and after i edited a file. Then i recreated a Iso from that folder:

> genisoimage -r -V "parrot" -b isolinux/isolinux.bin -c isolinux/boot.cat -cache-inodes -J -l -no-emul-boot -boot-load-size 4 -boot-info-table -o ../parrot_mod.iso .

When i use dd,fdisk command i get:

> dd bs=4M if=Desktop/parrot/parrot_mod.iso of=/dev/sdb && sync
451+1 records in
451+1 records out
1892157440 bytes (1.9 GB) copied, 184.489 s, 10.3 MB/s


fdisk -l /dev/sdb


Disk /dev/sdb: 31.5 GB, 31466323968 bytes
64 heads, 32 sectors/track, 30008 cylinders, total 61457664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdb doesn't contain a valid partition table



What is it wrong?

---

### Post by marco84 on 2015-02-21
What can i do?

---


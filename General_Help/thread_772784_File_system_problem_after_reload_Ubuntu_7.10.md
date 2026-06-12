---
title: "File system problem after reload Ubuntu 7.10"
date: 2008-04-28
forum: General Help
---

### Post by jeffsa12 on 2008-04-28
I reinstalled Ubuntu 7.10 after having some problems. I have a separate root and home partitions. I manually directed the installer to the appropriate partitions, and let the installer reformat my Ubuntu 7.10 root partition, and not reformat home. 

I have all my original desktop settings, etc. My problem is when I try to browse with Nautilus, it locks up on home. 

If I use me Ubuntu 8.04 install on the same computer, to browse the Ubuntu 7.10 home partition, everything is there. If I browse /media/2 Ubu 7.10 root/home, the file is empty. 

Is there or should there be a (link?) within the root, home, jeff file system in the root partition to direct to home partition?

Is this the problem and how do I fix it. 

I can file browse all the other files and partitions except home with no problems when running 7.10.




jeff@jeff-ubu804-desktop:~$ sudo fdisk -l
[sudo] password for jeff: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5436    43664635+   7  HPFS/NTFS
/dev/sda3            5437       19457   112623682+   f  W95 Ext'd (LBA)
/dev/sda5            5437        7646    17751793+   b  W95 FAT32
/dev/sda6            7647        7910     2120548+  82  Linux swap / Solaris
/dev/sda7            7911        8837     7446096   83  Linux
/dev/sda8            8838       11068    17920476   83  Linux
/dev/sda9           11069       11995     7446096   83  Linux
/dev/sda10          11996       12922     7446096   83  Linux
/dev/sda11          12923       19457    52492356    b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71d4ff44

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb3   *           7        9597    77039707+   f  W95 Ext'd (LBA)
/dev/sdb5               7        2250    18024898+   b  W95 FAT32
/dev/sdb6            2251        2512     2104483+  82  Linux swap / Solaris
/dev/sdb7            2513        3439     7446093   83  Linux
/dev/sdb8            3440        9597    49464100+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000543e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdc2            7650       15298    61440592+   7  HPFS/NTFS
/dev/sdc3           15299       19457    33407167+   7  HPFS/NTFS
jeff@jeff-ubu804-desktop:~$

---


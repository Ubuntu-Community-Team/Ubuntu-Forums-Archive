---
title: "Boot faliure / disc faliure?"
date: 2007-12-09
forum: General Help
---

### Post by hroey on 2007-12-09
My Ubuntu does not boot after the little one have pounded the keyboard during boot. Any help would be greatly appreciatet. System: Ubuntu 6.06 LTS on a Compaq nx6325 labtop. Dual boot with WIN XP.

Grub comes up OK and the splash screen too. But then I get a text something like:

Busybox v1.1.3 (debian 1:1.1.3-3ubuntu3) built-in shell (ash)

/bin/sh: can't access tty; job control turned off

The system is still responding. When I boot from a live CD and check the disc I get the following. Are my partitions messed up? Is there a cure? Please note that I am preatty green when it comes to linux...

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3935    31607856    7  HPFS/NTFS
/dev/sda2            6250        7297     8414280    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            3936        6151    17800020   83  Linux
/dev/sda4            6152        6249      787185    5  Extended
/dev/sda5            6152        6249      787153+  82  Linux swap / Solaris

Partition table entries are not in disk order


ubuntu@ubuntu:~$ cd /tmp
ubuntu@ubuntu:/tmp$ mkdir hd
ubuntu@ubuntu:/tmp$ sudo mount /dev/sda3 hd
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:/tmp$  dmesg | tail
[17180158.240000] Bluetooth: L2CAP socket layer initialized
[17180158.776000] Bluetooth: RFCOMM socket layer initialized
[17180158.776000] Bluetooth: RFCOMM TTY layer initialized
[17180158.776000] Bluetooth: RFCOMM ver 1.7
[17181944.560000] EXT3-fs error (device sda3): ext3_check_descriptors: Block bit map for group 128 not in group (block 2553887680)!
[17181944.564000] EXT3-fs: group descriptors corrupted !
[17182097.356000] SQUASHFS error: Can't find a SQUASHFS superblock on sda4
[17182760.416000] SQUASHFS error: Can't find a SQUASHFS superblock on sda4
[17182804.200000] EXT3-fs error (device sda3): ext3_check_descriptors: Block bit map for group 128 not in group (block 2553887680)!
[17182804.216000] EXT3-fs: group descriptors corrupted !

[END OF POST]

---


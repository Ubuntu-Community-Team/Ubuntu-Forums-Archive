---
title: "Dual booting gets Grub Error 13"
date: 2007-01-08
forum: General Help
---

### Post by PurplePenguin on 2007-01-08
I just got a new hard drive (200GB), so the first logical thing for me to do was partition the heck out of it and try to put a bunch of new distros on it. :D

My only problem seems to come from grub, though.  Every time I install a new distro, the grub installation picks up the other distros, but doesn't make them bootable for some reason (I get grub error 13).

Grub Error 13 is Invalid or unsupported executable format and is described by a grub error site as "This error is returned if the kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD)."

Here's a copy of what fdisk -l spits out at me:

```
localhost dave # fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         837     6723171   83  Linux
/dev/sda2             838        9729    71424990    5  Extended
/dev/sda5             838        9729    71424958+  83  Linux

Disk /dev/sdb: 5129 MB, 5129671680 bytes
255 heads, 63 sectors/track, 623 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         131     1052226   82  Linux swap / Solaris
/dev/sdb2             132         623     3951990    5  Extended
/dev/sdb5             132         623     3951958+  83  Linux

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2511    20169576   83  Linux
/dev/sdc2            2512        3033     4192965   83  Linux
/dev/sdc3            5309       24321   152721922+  83  Linux
/dev/sdc4            3034        5308    18273937+   b  W95 FAT32

Partition table entries are not in disk order
localhost dave # 

```

The last bit about partition table entries not being in order is because (somehow) sdc4, which is a FAT32-formatted area, somehow is mapped before sdc3 (that is, the partition order is sdc1, sdc2, sdc4, sdc3).  Couldn't tell you how that happened. :)

I don't actually have Windows installed, I just wanted to put a FAT 32 partition on there somewhere.

Here's my menu.1st, which seems to blatantly show that only one partition (Sabayon) is set up properly (the others all say rootnoverify, which seems to me to be my problem).  My big question is this... as a grub newbie, how do I set this up properly?  In Sabayon's installation, I tried to show it each partition and gave them all the following names... but it didn't manage to find the kernels, so nothing gets loaded.  What am I doing wrong?

Menu.1st: 

```
default=1
timeout=6
splashimage=(hd2,0)/boot/grub/splash.xpm.gz
title Sabayon Linux x86 3.25
	root (hd2,0)
	kernel /boot/kernel-genkernel-x86-2.6.19-gentoo-r4  root=/dev/ram0 ramdisk=8192 real_root=/dev/sdc1  quiet  init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 pci=nomsi
	initrd /boot/initramfs-genkernel-x86-2.6.19-gentoo-r4
title Ubuntu610
	rootnoverify (hd0,0)
	chainloader +1
title PCLinuxOS
	rootnoverify (hd2,1)
	chainloader +1
title Windows
	rootnoverify (hd2,3)
	chainloader +1
title Ubuntu606LTS
	rootnoverify (hd1,4)
	chainloader +1

```

I've tried reading up on grub, but I'm apparently a complete idiot when it comes to this. :D  I think that as soon as I fix this, I'll have a very good understanding, but as it is, I'm stuck!

Thanks to anybody with any ideas!

---


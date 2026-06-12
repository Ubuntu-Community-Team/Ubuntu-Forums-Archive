---
title: "GRUB dualbooting problems after Hardy Install"
date: 2008-04-27
forum: General Help
---

### Post by Steffy on 2008-04-27
I just installed Hardy, and my Grub files seem to have broken: I can't boot into Windows any more. Selecting Windows at startup gives a "no such partition" error message. I also had Sabayon Linux installed, and that's completely gone from the menu now.

I have 3 hard drives: sda, sdb and sdc. Ubuntu is installed on sda, sdb is just a general file storage drive, and Windows is installed on sdc, partition sdc1. Sabayon is installed on sdc5.

I've copied and pasted my menu.lst file, as well as my fdisk output below, if that helps at all.

```

default 0
timeout 10

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=d6ee89fa-f0d1-4ff9-867f-e6260c6a15ec ro quiet splash vga=791
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=d6ee89fa-f0d1-4ff9-867f-e6260c6a15ec ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows XP Home Edition
root (hd2,0)
chainloader +1
savedefault
makeactive

```

```

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbe9dbe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3493    28057491   83  Linux
/dev/sda2            3494        3649     1253070    5  Extended
/dev/sda5            3494        3649     1253038+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9729808

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2       38913   312560640    f  W95 Ext'd (LBA)
/dev/sdb5               2       38913   312560608+   7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0130012f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sdc2            6375        6387      104422+  83  Linux
/dev/sdc3           11853       24321   100157242+   7  HPFS/NTFS
/dev/sdc4            6388       11852    43897612+   5  Extended
/dev/sdc5            6388       11852    43897581   8e  Linux LVM

Partition table entries are not in disk order

```

Anyone got any ideas? Thanks in advance.

---


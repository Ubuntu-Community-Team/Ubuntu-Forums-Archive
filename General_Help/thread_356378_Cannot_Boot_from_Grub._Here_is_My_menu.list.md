---
title: "Cannot Boot from Grub. Here is My menu.list"
date: 2007-02-08
forum: General Help
---

### Post by IDeus on 2007-02-08
I cannot boot into Vista from grub. I have re-established my Vista boot and it works fine. Then when I restore grub it will not load??? I have tried (hd0,0) through (hd0,7) with no luck!
Here is the grub info:
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type is fat, partition type 0xb
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 6,  Filesystem type unknown, partition type 0x7
   Partition num: 7,  Filesystem type unknown, partition type 0x82

and my menu.list is:

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Vista 0
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Vista 5
root		(hd0,5)
savedefault
makeactive
chainloader	+1

title		Vista 6
root		(hd0,6)
savedefault
makeactive
chainloader	+1

title		Vista 7
root		(hd0,7)
savedefault
makeactive
chainloader	+1

---

### Post by taurus on 2007-02-08
Would be nice if you can also include the output of this command too.

```
sudo fdisk -l
```

---

### Post by IDeus on 2007-02-08
root@Chrome:~# cat /proc/partitions
major minor  #blocks  name

   8     0  156290904 sda
   8     1   50323581 sda1
   8     2          1 sda2
   8     5   51086668 sda5
   8     6   20137446 sda6
   8     7   28025361 sda7
   8     8    6715138 sda8
root@Chrome:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6265    50323581    7  HPFS/NTFS
/dev/sda2            6266       19457   105964740    f  W95 Ext'd (LBA)
/dev/sda5            6266       12625    51086668+   b  W95 FAT32
/dev/sda6           12626       15132    20137446   83  Linux
/dev/sda7           15133       18621    28025361    7  HPFS/NTFS
/dev/sda8           18622       19457     6715138+  82  Linux swap / Solaris

Thank you :)

---


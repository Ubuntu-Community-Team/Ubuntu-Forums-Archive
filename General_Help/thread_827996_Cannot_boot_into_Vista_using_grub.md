---
title: "Cannot boot into Vista using grub"
date: 2008-06-13
forum: General Help
---

### Post by StevenChan on 2008-06-13
Hi all,

My computer has two hard disks containing the following partitions:

HD0 (SATA):
C: Windows XP (NTFS) Pri, act
D: Documents (NTFS)
E: Documents (NTFS)

HD1 (IDE):
F: Documents (NTFS) Pri, act
Ext3: Ubuntu Pri (mount point /)
SWAP
Ext3: Ubuntu (mount point /home)
G: Vista (NTFS)

The sequence of installation was: XP, then Ubuntu and then Vista

After installing Ubuntu, grub was unable to boot into both XP and Ubuntu itself. This however could be fixed by editing the boot partitions of XP and Ubuntu to root hd(0,0) and root hd(1,2) respectively.

I then installed Vista to partition G:, and my computer was able to boot into Vista automatically without showing grub menu. After two reboots from Vista, grub menu appeared again with no entry of Vista. I tried to add an entry for Vista in grub menu - root hd(1,6), but the computer booted into XP instead of Vista, even if hd(1,6) is the partition where Vista resides!

What's wrong with my grub and how to fix it~?

Thanks all!

---

### Post by logos34 on 2008-06-13
You'll have to post your fdisk and mneu.lst so we can make sense out if it:

sudo fdisk -l

cat /boot/grub/menu.lst

cat /boot/grub/device.map

---

### Post by StevenChan on 2008-06-14
sudo fdisk -l

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3405    27350631    7  HPFS/NTFS
/dev/sda2            4014        9729    45913769+   5  Extended
/dev/sda3            3406        4013     4883760   83  Linux
/dev/sda5            4014        4262     2000029+  82  Linux swap / Solaris
/dev/sda6            4263        4864     4835533+  83  Linux
/dev/sda7            4865        8424    28595668+   7  HPFS/NTFS
/dev/sda8            8425        9729    10482381    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e142e13

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100        9725    37158345    f  W95 Ext'd (LBA)
/dev/sdb5            5100        6374    10241406    7  HPFS/NTFS
/dev/sdb6            6375        9725    26916876    7  HPFS/NTFS


cat /boot/grub/menu.lst

> default 4
timeout 10

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd1,2)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=fc74a1f0-0e22-4fe8-8f59-4b739417be01 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd1,2)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=fc74a1f0-0e22-4fe8-8f59-4b739417be01 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd1,2)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows XP Professional
root (hd1,0)
chainloader +1
savedefault

title Microsoft Windows Vista
root (hd0,7)


cat /boot/grub/device.map
> (hd0)	/dev/sda
(hd1)	/dev/sdb


Thanks a lot!

---

### Post by meierfra. on 2008-06-14
Try these: (You can put them all on menu.lst at the same time)

title Windows
rootnoverify (hd0,0)
chainloader +1


title Windows
rootnoverify (hd1,0)
chainloader +1


title Windows
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by meierfra. on 2008-06-14
> tried to add an entry for Vista in grub menu - root hd(1,6), but the computer booted into XP instead of Vista
 
Are you sure  that "root (hd1,6) " booted into XP?  That would be very strange. 

Did you move,  copied or deleted any partitions?

---


---
title: "Grub error"
date: 2008-05-15
forum: General Help
---

### Post by jcrnan on 2008-05-15
Im not able to load XP from grub.
```

nan@the-holy-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdabedabe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    14329979     7164958+  83  Linux
/dev/sda2       158433030   194611409    18089190    7  HPFS/NTFS
/dev/sda3        14329980   156055409    70862715   83  Linux
/dev/sda4       156055410   158433029     1188810   82  Linux swap / Solaris

Partition table entries are not in disk order
```

My grub

```

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=893bee1a-46aa-44e2-84f4-4d42258c5cd2 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=893bee1a-46aa-44e2-84f4-4d42258c5cd2 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

title              Windows XP
root               (hd0,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

```

Ive tried a lot of stuff and I can't figure it out. So many different problems and solutions everywhere and so many different answers. Could anyone please help with this?

---

### Post by NightwishFan on 2008-05-15
Try to boot with a super grub disk if all else fails.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by danwood76 on 2008-05-15
The map command is really used for for swapping disks.
Really you should place your windows partitions on the first partition.

You could try this:
```

title              Windows XP
root               (hd0,1)
hide               (hd0,0)
makeactive
chainloader        +1

```

This will hide the primary partition, though Im not sure if this only applies to multi booting dos partitions.

---

### Post by meierfra. on 2008-05-15
Try:


title              Windows XP
root               (hd0,1)
savedefault
makeactive
chainloader        +1

---

### Post by strabes on 2008-05-15
Just to clarify what the above two posts have said, replace the following section of your menu.lst with what they posted.> title              Windows XP
root               (hd0,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

---


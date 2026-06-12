---
title: "Unable to boot into Ubuntu from Windows boot menu"
date: 2008-06-17
forum: General Help
---

### Post by bkc_tamu on 2008-06-17
I installed ubuntu 8.04 through wubi on my Vista.

Wubi added an entry in my windows boot menu and it always worked fine.

One day, I deleted a few partitions and created one partition from all that space. This for some reason corrupted my windows boot manager. So I had to use windows DVD to repair.

After repair my windows boot menu was missing ubuntu. So I used EasyBCD to add an entry for Ubuntu.

Now here is the problem. I see a Ubuntu entry but when I select it, I am dropped to a grub prompt.

at this point to get into Ubuntu I have to type:

```

root (hd0,7)/ubuntu/disks/
kernel /ubuntu/disks/boot/vmlinuz-2.6.24-19-generic root=UUID=1053-ECE5 loop=/ubuntu/disks/root.disk
initrd /ubuntu/disks/boot/initrd.img-2.6.24-19-generic
boot

```

to get into linux. It boots perfectly, no issues at all. But

```

root (hd0,7)/ubuntu/disks/
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=1053-ECE5 loop=/ubuntu/disks/root.disk

```

(without the /ubuntu/disks/ after kenrnel) gives me ```
Error 17: File not found 
```

Here is my $ fdisk -l

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        2617    20971520    7  HPFS/NTFS
/dev/sda3   *        2617        3923    10485760    7  HPFS/NTFS
/dev/sda4            3923       19458   124782592    f  W95 Ext'd (LBA)
/dev/sda5            4589        8766    33554432    b  W95 FAT32
/dev/sda6            8766       12944    33554432    b  W95 FAT32
/dev/sda7           12944       17121    33554432    b  W95 FAT32
/dev/sda8           17121       19458    18766848    b  W95 FAT32
/dev/sda9            3924        4588     5341581    7  HPFS/NTFS

Partition table entries are not in disk order

```

Please help.
Kalyan

---

### Post by tinybit on 2008-06-17
The original GNU GRUB 0.97 features no "relative path". So thats no problem. You should just edit your menu.lst and let it work in your way.

---

### Post by ago on 2008-06-18
Or you can copy wubildr* from ?:\ubuntu\winboot\ to c:\ and point the vista entry to c:\wubildr.mbr (make sure there is no menu.lst in any root folder).

---


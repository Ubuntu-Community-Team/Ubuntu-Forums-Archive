---
title: "Help formating external HDD w/ previous linux install"
date: 2006-12-03
forum: General Help
---

### Post by kimro on 2006-12-03
I've got an external hdd that previously had linux install that I want to format to fat32.

I assume I'll need to first remove all the partitions, recreate one, and then format? If someone can help me out, it would be greatly appreciated. FYI, I'm using Edgy.

fdisk -l returns the following.

```
Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7111    57119076   83  Linux
/dev/sdb2            7112        7296     1486012+   5  Extended
/dev/sdb5            7112        7296     1485981   82  Linux swap / Solaris

```

---

### Post by LLRNR on 2006-12-03
Yes, this is the way to do it - depending on what you want, you can use the LiveCD or the WinXP install CD (boot from it and choose Recovery Console mode).

First thing to do - regardless of the method you choose - is to remove your existing partitions => they will be turned into unallocated space.

The second thing to do is to format the unallocated space to vfat if you use the Ubuntu LiveCD or to FAT32 if you use the WinXP install disc.

LLRNR

---

### Post by kimro on 2006-12-03
Thanks! Can someone teach me the actual commands to partition the usb drive?
I've searched google but there are so many mentions, I would like to confirm.

To start partitioning,
```
sudo fdisk /dev/sdb
```

To create fs,
```
sudo mkfs.ext3 /dev/sdb
```

Now, would 'mkfs.vfat' or 'mkfs.msdos' work to make it fat32?
Code would example would be great as I'm new to linux in general. Cheers!

---


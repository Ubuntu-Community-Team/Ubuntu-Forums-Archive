---
title: "Swap Automounting Issue"
date: 2008-06-22
forum: General Help
---

### Post by iXneonXi on 2008-06-22
Help, both "vol_id -u /dev/sda3" and "blkid" won't return a UUID for my swap partition. I am able to manually initialize it using "swapon". It will not auto-initialize (there seems to be a problem with UUID mismatch in fstab).

Running Hardy Heron 8.04 (LTS) on an Acer Aspire 5315-2153.

---

### Post by Vivaldi Gloria on 2008-06-22
What is the result of

```
sudo blkid
```

and

```
sudo fdisk -l
```

when you start your system?

---

### Post by iXneonXi on 2008-06-22
**sudo blkid**
```

/dev/sda1: UUID="F4D438F2D438B926" TYPE="ntfs" 
/dev/sda2: UUID="85e206e4-da9f-4fb5-8370-0a3b59d01333" TYPE="ext3" 
/dev/sda3: TYPE="swap" 

```

**sudo fdisk -l**
```


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcda7cda7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7768    62396428+   7  HPFS/NTFS
/dev/sda2            7769        9597    14691439+  83  Linux
/dev/sda3            9598        9729     1060290   82  Linux swap / Solaris

```

---

### Post by Vivaldi Gloria on 2008-06-22
What is the result of

```
udevinfo --query=all --name=/dev/sda3
```

---


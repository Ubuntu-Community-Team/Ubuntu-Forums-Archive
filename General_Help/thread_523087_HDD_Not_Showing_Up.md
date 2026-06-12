---
title: "HDD Not Showing Up"
date: 2007-08-11
forum: General Help
---

### Post by WastingBody on 2007-08-11
I was recently given a 40gb HDD by a friend. Ubuntu wont show it the Places->Computer, but GParted can see it. It has this warning in GParted.
> dumpe2fs 1.40WIP(14-Nov-2006)
dumpe2fs: No such file or directory while trying to open /dev/sdb1

---

### Post by apetresc on 2007-08-11
> **WastingBody said:**
> I was recently given a 40gb HDD by a friend. Ubuntu wont show it the Places->Computer, but GParted can see it. It has this warning in GParted.

Try this, and tell me if any errors occur:
```
sudo mkdir /mnt/test
sudo mount -t TYPE /dev/sdb1 /mnt/test
```
where "TYPE" is the filesystem that is currently on that partition. i.e, "ext3", "vfat", etc.

---

### Post by WastingBody on 2007-08-11
I get > mount: special device /dev/sdb1 does not exist

---

### Post by WastingBody on 2007-08-12
Bump

---

### Post by init1 on 2007-08-12
do a 
```

fdisk -l

```

---

### Post by strabes on 2007-08-12
Paste the output of these commands:```
sudo fdisk -l
``````
cat /etc/fstab
```

---

### Post by WastingBody on 2007-08-12
The output for sudo fdisk -l was
> Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4676    37559938+  83  Linux
/dev/sda2            4677        4863     1502077+   5  Extended
/dev/sda5            4677        4863     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux
and the output for cat /etc/fstab was
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=00c3819e-6566-4ad9-bcae-5327870849c8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6853393d-bf4d-f69d-ef35-be2bc4f00849 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


---

### Post by init1 on 2007-08-12
```

sudo mount /dev/sdb1 /mnt
ls /mnt

```
Does that work? If not, are you sure it's formated? Ubuntu does recognize it's existence.

---

### Post by WastingBody on 2007-08-12
I tried to format it to fat32 and ext3 with GParted, but neither of them work. Is there another application that I could or should use to format it?

---

### Post by init1 on 2007-08-13
> **WastingBody said:**
> I tried to format it to fat32 and ext3 with GParted, but neither of them work. Is there another application that I could or should use to format it?
```

mkfs.ext3 /dev/sdb1

```
That should work. If it does not, I will help you with repartitioning.

---

### Post by WastingBody on 2007-08-13
Thanks for helping so much, I'll try it when I get home.

---

### Post by init1 on 2007-08-13
> **WastingBody said:**
> Thanks for helping so much, I'll try it when I get home.
Your welome! :D

---

### Post by WastingBody on 2007-08-13
Yay! It finally works. Thanks again.

---

### Post by init1 on 2007-08-13
> **WastingBody said:**
> Yay! It finally works. Thanks again.
That is good to hear. I am glad to help. :D

---

### Post by WastingBody on 2007-08-13
>_< Well I have another problem now; I can't write to the mounted volume. How would I change the permissions for the drive?

---


---
title: "Partition the disk with Gparted"
date: 2014-08-27
forum: General Help
---

### Post by pugliesedaniele on 2014-08-27
hi,
 I have to the hardisk, in the picture below you can view the my harddisk. I tried to resize the partition but it not is possible. How can I do this ?

[IMG]http://s8.postimg.org/uz1k6lmxh/Screenshot_from_2014_08_27_18_09_51.png[/IMG]

---

### Post by pugliesedaniele on 2014-08-27
probably I have to login with a live version of ubuntu, but I not sure of it.

---

### Post by Dennis N on 2014-08-27
All the partitions you have are mounted (note the little key icons). The partition you plan to resize has to be unmounted. Do your resizing from a live CD.

---

### Post by sandyd on 2014-08-27
> **pugliesedaniele said:**
> probably I have to login with a live version of ubuntu, but I not sure of it.

This is correct, you cannot resize partitions while they are mounted (as indicated by the key icon) unless they are on a LVM-type setup.

---

### Post by pugliesedaniele on 2014-08-27
Oook, but if I resize (ext4 /home ) then can I allocate the free space at (ext 4 /) ?

---

### Post by sandyd on 2014-08-27
> **pugliesedaniele said:**
> Oook, but if I resize (ext4 /home ) then can I allocate the free space at (ext 4 /) ?

Yes, you should be able to, though it might take a while depending on how much space you want to free up as gparted has to move data around.

General Steps
a)Shrink sda5 (home), make sure the free space created is **before** the partition (i.e. on the left)
b)Shrink sda2 (extended partition), make sure the free space is **before** the partition (i.e. on the left)
c)Grow sda1 (root)

Know that with all disk resizing operations, there is a chance of data loss.

Please ensure that you have some kind of current backup before proceeding.

---

### Post by pugliesedaniele on 2014-08-27
Ookk I will try, thanks for your help

---


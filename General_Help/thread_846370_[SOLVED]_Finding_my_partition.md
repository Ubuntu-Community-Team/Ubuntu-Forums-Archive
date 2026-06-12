---
title: "[SOLVED] Finding my partition"
date: 2008-07-01
forum: General Help
---

### Post by jspolen on 2008-07-01
Just partitioned my hardrive using GParted.

Now I want to mount my new partition, but how do I now what to mount?

mount -t ext3 /dev/??? /mnt/new_partition

---

### Post by soccerboy on 2008-07-01
use fdisk -l to find the partition with the right amount of space and filesystem

---

### Post by Titan8990 on 2008-07-01
Use fdisk -l. If you didnt label it then the only way to distinguish it from the other partitions is its size.

---

### Post by zarqoon on 2008-07-01
gparted shows the /dev/???? path for the disks.
Just select your disk again and look at the left side

---

### Post by jspolen on 2008-07-01
Thanks, fdisk -l as root or with sudo helped.

---

### Post by Titan8990 on 2008-07-01
Yes, fdisk as a user will only show removable media.

---


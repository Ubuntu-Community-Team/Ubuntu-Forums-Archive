---
title: "Need to recover partition after mdadm -create"
date: 2008-06-21
forum: General Help
---

### Post by alarmer on 2008-06-21
Please, help me with my lost data.

I have sda1 and sdb8 partitions i want to use in raid1. They are ext3, identical size.
sda1 was ampty, sdb8 contained important data.
I did: mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb8
Now those partitions are inaccessible from nautilus, gparted shows sdb8 empty.
recover doesn't find any inodes on sdb8.

How to save lost data at least a part of them?

---

### Post by starscalling on 2008-06-21
ouch..... thats not very forgiving..
[http://aivipi.blogspot.com/2007/05/how-to-recover-ext3-partitions.html](http://aivipi.blogspot.com/2007/05/how-to-recover-ext3-partitions.html)

---

### Post by alarmer on 2008-06-21
What makes me panic is not that the nautilus cannot access the partition, but that gparted shows it empty.

---

### Post by geo909 on 2008-06-21
Unmount your drive and take at look at [systemrescueCD.]("http://www.sysresccd.org/Main_Page")
Never used it but they say it very good for restoring data

---


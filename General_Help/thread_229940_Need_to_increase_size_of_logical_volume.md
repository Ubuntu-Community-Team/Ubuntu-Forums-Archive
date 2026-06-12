---
title: "Need to increase size of logical volume"
date: 2006-08-05
forum: General Help
---

### Post by cemptor on 2006-08-05
I have LVM and a volume group of 100GB with reiserfs. HAve about 20 GB free space on my hard disk/ Want to allocate 1GB of that 20 GB to one of my logical volumes.

When I try using lvextend, it tells me 
"Insufficient suitable allocatable extents for logical volume home: 32 more required"

How can I do this?

---

### Post by cemptor on 2006-08-05
Sorry for the newbie q. Here's how I did it

1. Add another Physical volume by using pvcreate 
2. Extend my volume group by adding the PV to it using vgextend
3. Extend the LV with lvextend
4. Increased the size of the file system (reiserfs) by resize_reiserfs

All this from [http://www.tldp.org/HOWTO/LVM-HOWTO/index.html](http://www.tldp.org/HOWTO/LVM-HOWTO/index.html)

---


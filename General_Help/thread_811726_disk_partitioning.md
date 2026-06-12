---
title: "disk partitioning?"
date: 2008-05-29
forum: General Help
---

### Post by crazyfuturamanoob on 2008-05-29
how do I didive my hard drive into two partitions?
I cant find the partitioning icon (kinda stupid problem!?)

---

### Post by timcredible on 2008-05-29
the installer will automatically create a swap and a / partition if you choose to use the entire disk.  the installer will leave windows alone and create 2 new partitions if you want that.  if you just want to partition a disk, use gparted (System -> Administration -> Partition Editor).  That app isn't there by default after an installation, add it with synaptic.

---

### Post by bingoUV on 2008-05-29
Try timcredible's suggestions, but the disk partition tool might not be able to partition the disk because the OS is running out of the partitions. Boot from a live CD, and start the partition tool from here. In this state, it can add/create/modify all sorts of partitions.

---


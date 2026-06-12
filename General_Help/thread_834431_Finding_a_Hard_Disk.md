---
title: "Finding a Hard Disk?"
date: 2008-06-19
forum: General Help
---

### Post by Venatu on 2008-06-19
I am running the latest release of ubntu server, as I wanted a minimal install for old hardware. I am trying to use an external hard drive with it, but if I use mount it does not appear to be there. I have used  a bunch of 'trail' commands to look at the logs, and I see references to 'sdb' 'sg2' but if I use fdisk sdb, it says it does not exist.

So my question is, how can I find out if the device is present and working, and then set it to mount automatically? As im using the server I have no GUI by the way.

Thanks, 
Mike

---

### Post by russlar on 2008-06-19
> **Venatu said:**
> I am running the latest release of ubntu server, as I wanted a minimal install for old hardware. I am trying to use an external hard drive with it, but if I use mount it does not appear to be there. I have used  a bunch of 'trail' commands to look at the logs, and I see references to 'sdb' 'sg2' but if I use fdisk sdb, it says it does not exist.

So my question is, how can I find out if the device is present and working, and then set it to mount automatically? As im using the server I have no GUI by the way.

Thanks, 
Mike

fdisk -l will list all drives recognized by the system, mounted or not. df -h shows all mounted filesystems. if you want the disk to mount automatically, add it to /etc/fstab

---

### Post by plucky on 2008-06-19
```
sudo fdisk -l
``` lowercase L not a 1 should tell you if the disk is there.

---


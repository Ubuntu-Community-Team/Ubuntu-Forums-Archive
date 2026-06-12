---
title: "Home Folder - Places"
date: 2008-06-05
forum: General Help
---

### Post by vern1923 on 2008-06-05
I am using Ubutunu 8.4 with two internal HD's and a USB HD and have the following problem:

In the Home Folder – Places all partitions are shown as xx.x GB Media instead of /dev/sdx.x.

In /etc/fstab not all the partitions are shown and the there are problems as follows:
# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/sdb6 
UUID=cf2a3dde-762b-420d-a2da-03742a3dd961 /               ext3    relatime,errors=remount-ro 0       1 
# /dev/sdb9 
UUID=afeae218-3428-4ebe-82e7-6411070ba119 none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 

Gparted shows all partitions as the should be, that is /dev/sdx.x

Is there a fix for this problem?

Thanks
Clay Stapleton

---

### Post by plucky on 2008-06-05
The behavior of partitions changed in Hardy.In previous versions,other partitions were mounted and displayed on the desktop.

Here is a guide for [mounting linux partitions](http://www.psychocats.net/ubuntu/mountlinux) if you want your other partitions mounted.You will need to do this for each partition.

Good Luck

---

### Post by cariboo on 2008-06-05
Follow this link for a really quick and easy fix to get your internal drives displayed on the desktop

[http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html](http://onlyubuntu.blogspot.com/2008/05/auto-mounting-internal-drives-in-ubuntu.html)

Jim

---


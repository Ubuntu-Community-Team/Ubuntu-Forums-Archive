---
title: "fix fstab"
date: 2007-08-21
forum: General Help
---

### Post by atlfalcons866 on 2007-08-21
i formatted my home and backed up my settings back to the home. The problem is that it isnt detecting my fstab here is my ftsab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6d326b8a-1af4-4b72-a93f-d21a0a3d1749 /               jfs     defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=5216fef3-6ceb-43f9-a2fb-90b5beb65c8f /home           jfs   defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=1615ca10-b91e-41b2-b67f-8a6ead7abad2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

i changed the ext3 to JFS on /home

---

### Post by merlinus on 2007-08-21
UUIDs may have changed.

```

blkid

```

and compare with /etc/fstab.

-merlin

---

### Post by atlfalcons866 on 2007-08-21
how do i use blkid

---

### Post by merlinus on 2007-08-21
It is a command entered into a terminal window.

Compare with results of 
```

sudo fdisk -l

```to get the UUIDs for your partitions, and then compare those with the entries in /etc/fstab.

-merlin

---


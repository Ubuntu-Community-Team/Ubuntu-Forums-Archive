---
title: "Whats wrong with my fstab?"
date: 2007-07-06
forum: General Help
---

### Post by Lolicon on 2007-07-06
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=8b588b96-917d-4b49-8357-316281e95984 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda9
UUID=c0f3b1dd-4de8-4a96-8609-4325b5a96887 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/sda5               ext2	auto,user,exec,rw 0       0

/dev/sda6               ext2	auto,user,exec,rw 0       0

/dev/sda7               ext2	auto,user,exec,rw 0       0

```
it doesn't automount and it says "You are not privileged to mount this volume." when I try to mount it with nautilus.

---

### Post by Mr. C. on 2007-07-06
By "automount", do you mean upon boot?  Or upon first use?  Your configuration does the former.

Your sda5, sda6, and sda7 are missig the second field, the mount point.  Where do you want those disks mounted, as in :

```
/dev/sda7             /mnt/disk7    ext2	auto,user,exec,rw 0       0
```

MrC

---

### Post by Lolicon on 2007-07-06
Yes I would like them on boot. The mount point is... how do I find it?

---

### Post by Mr. C. on 2007-07-06
*You* specify the mount point. Each mount point is just an empty directory indicating where you want a disk to mount.

For example, you might want them to mount in the directory /mnt, as in :

```
/mnt/partition5
/mnt/partition6
/mnt/partition7
```

or perhaps:

```
/media/sda5
/media/sda6
/media/sda7
```

MrC

---

### Post by roddersg on 2007-10-03
Sorry, I posted a more detailed problem (similar to yours) here:

[http://ubuntuforums.org/showthread.php?t=471551](http://ubuntuforums.org/showthread.php?t=471551)

still no solution yet

---


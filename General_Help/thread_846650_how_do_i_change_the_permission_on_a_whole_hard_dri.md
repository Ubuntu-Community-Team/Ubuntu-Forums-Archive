---
title: "how do i change the permission on a whole hard drive?"
date: 2008-07-01
forum: General Help
---

### Post by lime4x4 on 2008-07-01
Curretnly running ubuntu hardy. I have a 120 gig hard drive that i use for storage. But i can't currently delete or write to the disk. How can i fix that

---

### Post by django0909 on 2008-07-01
Is it an internal or external drive?

---

### Post by soccerboy on 2008-07-01
do you want to change permissions or ownership
permission: ```
chown 755 -R /mount/for/disk
```

only use that if this drive doesn't have the root filesystem on it.  Be very careful with that command!  Only works on ext partitions.

---

### Post by sisco311 on 2008-07-01
fat, ntfs or ext3?

---

### Post by nikgare on 2008-07-01
PLease post te contents of the file:

/etc/fstab

---

### Post by lime4x4 on 2008-07-01
it doesn't show up in fstab but it's mounted in /media/disk and it's ext3

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d452829f-b123-4d93-81e6-5a545c66628a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=6aa89803-403c-4930-bee6-3a3117cdacb2 /boot           ext3    relatime        0       2
# /dev/sdc1
UUID=671fe8e4-bbec-4439-89a8-caa5be0f478f /home           ext3    relatime        0       2
# /dev/sdb1
UUID=78ed9851-28d9-429d-8802-4f103ae75d6b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by sisco311 on 2008-07-01
Change the owner and group:
```
sudo chown -R username:username /media/disk
```assuming username is your login name.

---


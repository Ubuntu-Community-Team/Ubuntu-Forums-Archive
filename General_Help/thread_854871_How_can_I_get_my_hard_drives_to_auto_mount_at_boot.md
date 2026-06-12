---
title: "How can I get my hard drives to auto mount at boot?"
date: 2008-07-09
forum: General Help
---

### Post by jimartin8219 on 2008-07-09
I have 4 hard drives.  My machine boots fine but I have to manually click on the other 3 drives in order for them to mount.  How can I get my hard drives to auto mount at boot?

---

### Post by jgomo3 on 2008-07-09
edit the fstab. Insert a line for each harddisk like this:
/dev/sdb1 /mount/sdb1               ext3    defaults,errors=remount-ro 0       1
/dev/sdb2 /mount/sdb2               ext3    defaults,errors=remount-ro 0       1
.
.
.
and so on.

---

### Post by tamoneya on 2008-07-09
you have to add them to fstab which is in /etc/
No use in me going into detail since there is a rather in depth thread here:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by iaculallad on 2008-07-09
> **jgomo3 said:**
> edit the fstab. Insert a line for each harddisk like this:
/dev/sdb1 /mount/sdb1               ext3    defaults,errors=remount-ro 0       1
/dev/sdb2 /mount/sdb2               ext3    defaults,errors=remount-ro 0       1
.
.
.
and so on.

And that depends on the filesystem used to format the OP's 3 physical drives.

---

### Post by jimartin8219 on 2008-07-09
> **jgomo3 said:**
> edit the fstab. Insert a line for each harddisk like this:
/dev/sdb1 /mount/sdb1               ext3    defaults,errors=remount-ro 0       1
/dev/sdb2 /mount/sdb2               ext3    defaults,errors=remount-ro 0       1
.
.
.
and so on.

This is what is showing now and it still didn't work.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=61b462ea-7fd5-40c2-beaa-d1278ab910e7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7114ceb3-b4aa-4073-a1c5-684a231acc3d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sde        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sdb1 /mount/sdb1 ext3 defaults,errors=remount-ro 0 1
/dev/sdc1 /mount/sdc1 ext3 defaults,errors=remount-ro 0 1
/dev/sdd1 /mount/sdd1 ext3 defaults,errors=remount-ro 0 1

---

### Post by tamoneya on 2008-07-10
post the output of ```
sudo fdisk -l
``` so that we know your drive configuration and partitioning scheme.

---


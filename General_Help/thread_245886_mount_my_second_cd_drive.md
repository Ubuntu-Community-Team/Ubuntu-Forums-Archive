---
title: "mount my second cd drive"
date: 2006-08-28
forum: General Help
---

### Post by darklemming54 on 2006-08-28
I have 2 hard drives and 1 cd drive mounted, but to mount a second cd drive, I'd have to call it /dev/hdd (right?) , which doesnt exist. how do i go about mounting it

heres my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1 /home/shared vfat iocharset=utf8,umask=000 0 0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/ /media/cdrom1 udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2006-08-28
It depends how you connect your second harddrive to your mobo!  It looks to me like it will be /dev/hdb, NOT /dev/hdd.  I assume you connect the second harddrive to the same cable with the first harddrive and your CD-ROM is on a seperate cable--/dev/hdc.  So, the first partition of the second harddrive is known as /dev/hdb1 and the second is /dev/hdb2 and on and on...

By the way, I think the last line in your /etc/fstab is wrong!!!

---

### Post by Ocxic on 2006-08-28
/dev/ /media/cdrom1 udf,iso9660 user,noauto 0 0 <---change this

/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0 <----to this

---


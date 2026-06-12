---
title: "DVD problem"
date: 2008-03-01
forum: General Help
---

### Post by madzombie on 2008-03-01
I have a DVDrom. I can use CD. But when i want to run a DVD, it give me an error "UDF VOLUME"
my /etc/fstab file :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8d03e2f8-be79-4c47-9702-c4bb855816c2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=26ACFF34ACFEFD5D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=841ea6ae-10c0-4132-9967-c8e6286ee307 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   auto,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

Sory I don't know English very well.....

---

### Post by Gillingham on 2008-03-01
Not sure if this will help but I have a CD-RW and a DVD drive in my computer.  The equivalent  lines in my fstab file are: 

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

i.e. I have udf instead of auto (I do have auto for my floppy drive).

---

### Post by madzombie on 2008-03-02
> **Gillingham said:**
> 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

Thanks for your message. but I  tried it and it didn't work

---

### Post by Slingshot on 2008-03-05
Hi **madzombie**, I too have this problem now with DVD's that were burnt in Vista. Have you been able to resolve this?

Thanks
Slingshot

---


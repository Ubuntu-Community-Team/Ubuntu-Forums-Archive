---
title: "mount point   udf,iso9660 does not exist"
date: 2007-10-26
forum: General Help
---

### Post by emavio on 2007-10-26
I'm an  Unbuntu 7.04 user. I  cannot read a CD.

my /etc/fstab looks ok:
/dev/cdrom/media/cdrom0   udf,iso9660 user,noauto     0       0

but in File System the cdrom folder exhibits a downward pointer, as well as, the following files in /dev:

fd, cdrom, cdrw, core, MAKEDEV

How could I remove the problem, please?

ema

---

### Post by ddrichardson on 2007-10-26
By putting a space in:```
 /dev/cdrom /media/cdrom0   udf,iso9660 user,noauto     0       0
```Currently you are trying to mount /dev/cdrom/media/cdrom0 to udf,iso9660 ;-)

---

### Post by emavio on 2007-10-27
Thank you very much! 
While I was editing the /etc/fstab I lost the space between  cdrom and /media

Ema

---


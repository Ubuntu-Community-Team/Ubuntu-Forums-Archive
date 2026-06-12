---
title: "Cant mount cdrom drive"
date: 2007-09-28
forum: General Help
---

### Post by ndnkyd on 2007-09-28
Having trouble mounting my cdrom and cdrom0 drives.  After investigation: $cat /etc/fstab | grep cdrom      gave me, 

/dev/hdc    /media/cdrom0   udf,iso9660   user,noauto    0    0

So, I trivially commanded:    sudo mount /dev/hdc /media/cdrom0   which returned:

mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
            missing codepage or other error
 
Please help!!

$dmesg | grep cd    returned:

hdc: sony dvd+rw dw-p50a, atapi cd/ded-rom drive
hdc: atapi 24x dvd rom cd-r/rw drive, 8192kb cache, usma(33)
uniform cd-rom driver revision: 3.20
unable to identify CD-ROM format

---

### Post by nonewmsgs on 2007-09-29
could it be the disc?

have you tried other cds?

---


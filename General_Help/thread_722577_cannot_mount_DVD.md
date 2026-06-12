---
title: "cannot mount DVD"
date: 2008-03-12
forum: General Help
---

### Post by robertchahine on 2008-03-12
I need some help.
when i insert a DVD in the dvd rom
an error appear "Cannot mount volume. Invalid mount option when attempting to mount the volume 'UDF Volume".
what to do?

here's the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=b41a8834-7e49-472c-a1e6-308eddeaa2db / ext3 defaults,errors=remount-ro 0 1
# /dev/sda6
UUID=a3f59982-166b-4fdc-9922-b5102cb6533e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

---

### Post by robertchahine on 2008-03-12
any help? :(

---

### Post by prshah on 2008-03-12
> **robertchahine said:**
> I need some help.
when i insert a DVD in the dvd rom
an error appear "Cannot mount volume. Invalid mount option when attempting to mount the volume 'UDF Volume".
what to do?

here's the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=b41a8834-7e49-472c-a1e6-308eddeaa2db / ext3 defaults,errors=remount-ro 0 1
# /dev/sda6
UUID=a3f59982-166b-4fdc-9922-b5102cb6533e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

A UDF volume is another name for a DVD volume: are you trying to play a DVD? In that case, install the restricted "extras" ```
sudo aptitude install ubuntu-restricted-extras
``` then try again?

---

### Post by robertchahine on 2008-03-13
no, it didn't work

---


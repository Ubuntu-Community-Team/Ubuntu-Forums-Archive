---
title: "how to burn xbox360 backups with gutsy ?"
date: 2007-11-16
forum: General Help
---

### Post by kraymore on 2007-11-16
how to burn xbox360 backups in gutsy ?  (i own the games)

i'm using gusty and i've tried this command all always get the following output

i'll copy my /etc/fstab entry too

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/scd0=-image.iso
Executing 'builtin_dd if=image.iso of=/dev/scd0 obs=32k seek=0'
write failed: Input/output error

doesn't even prompt me to enter media. cannot get imgburn to work either it gives me the folllowing error (imburn) Invalid or supported image format! reason: first image a file part is less than 2048 bytes in size.

would really appreciate some help. dont want to run windows on a secondary computer here

---

### Post by kev82 on 2007-11-27
Good info here:
[http://www.bross.eu/2007/08/29/how-to-burn-xbox-360-backups-in-linux/](http://www.bross.eu/2007/08/29/how-to-burn-xbox-360-backups-in-linux/)

---


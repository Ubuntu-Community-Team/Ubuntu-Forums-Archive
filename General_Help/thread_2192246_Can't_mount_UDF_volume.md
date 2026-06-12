---
title: "Can't mount UDF volume"
date: 2013-12-06
forum: General Help
---

### Post by nxexile on 2013-12-06
I can't mount my UDF volume, and I have no idea what to do about it.

This is what message pops up when I try to: 

Error mounting /dev/sr0 at /media/nxexile/UDF Volume: Command-line `mount -t "udf" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,umask=0077" "/dev/sr0" "/media/nxexile/UDF Volume"' exited with non-zero exit status 32: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0: can't read superblock

---

### Post by heir4c on 2013-12-07
I find this:
[http://askubuntu.com/questions/359264/how-to-open-udf-volume](http://askubuntu.com/questions/359264/how-to-open-udf-volume)

---


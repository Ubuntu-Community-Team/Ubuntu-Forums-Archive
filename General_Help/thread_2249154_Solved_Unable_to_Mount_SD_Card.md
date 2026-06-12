---
title: "Solved: Unable to Mount SD Card"
date: 2014-10-20
forum: General Help
---

### Post by christian45 on 2014-10-20
This is the error I get. Any help?

Error mounting /dev/mmcblk0p1 at /media/xtian/FLASH: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/mmcblk0p1" "/media/xtian/FLASH"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

---

### Post by Dennis N on 2014-10-20
You may need to install a couple of extra packages:

> Install **exfat-utils** and **exfat-fuse** packages from the official repos:
**sudo apt-get install exfat-utils exfat-fuse**
Reboot your computer.

Information found at: [http://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working](http://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working)

---

### Post by christian45 on 2014-10-20
IT WORKED! Thank you so much. :)

---

### Post by Bucky Ball on 2014-10-20
Please mark the thread as solved by following the second link in my signature. Thanks. ;)

---

### Post by Dennis N on 2014-10-20
> **christian45 said:**
> IT WORKED! Thank you so much. :)

You are welcome. And thanks for your feedback!

---


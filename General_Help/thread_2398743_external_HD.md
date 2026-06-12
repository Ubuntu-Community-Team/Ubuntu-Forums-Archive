---
title: "external HD"
date: 2018-08-16
forum: General Help
---

### Post by hmiersch on 2018-08-16
hi.  i have my media files on an external HD formatted under OSX (before i switched to ubuntu). the problem is that i can only read from that HD but when i try to save something to that HD, i get an error "read-only file system". is there anything i can do to solve this problem that does not involve buying a new HD and copying the files over?

---

### Post by ajgreeny on 2018-08-16
Formatted to what filesystem?

If it's hfs or hfs+ I believe you need to install hfsplus and hfsutils packages.

You may also have to use the chown command on the mountpoint to make it yours as I think the apple filesystems follow permissions like linux filesystems, though I may be incorrect about this point as I have never used any Apple hardware.

---

### Post by hmiersch on 2018-09-29
i've installed hfsplus and hfsutils but i still get the same error. so i tried chown harry /dev/sdb (thats the mount point, innit?) and yes, i tried /sdb2 too but no bueno. when i look at the permissions, it still says the HD is owned by "user #99". argh! what am i doing wrong?

---

### Post by dragonfly41 on 2018-09-29
If you dig around (search "user 99") this UID 99 is a Mac thing.

[https://www.linuxquestions.org/questions/linux-desktop-74/permissions-between-mac-os-x-snow-leopard-and-linux-ubuntu-9-10-a-788887/](https://www.linuxquestions.org/questions/linux-desktop-74/permissions-between-mac-os-x-snow-leopard-and-linux-ubuntu-9-10-a-788887/)

---

### Post by hmiersch on 2018-09-29
now i have another problem: i went to this site:  > [https://www.linuxquestions.org/questions/linux-desktop-74/permissions-between-mac-os-x-snow-leopard-and-linux-ubuntu-9-10-a-788887/](https://www.linuxquestions.org/questions/linux-desktop-74/permissions-between-mac-os-x-snow-leopard-and-linux-ubuntu-9-10-a-788887/)  and someone said to change the user id using usermod. i decided to try it but now my user account doesn't appear on the login screen. i have to click "not listed" and then enter the username and password. what can i do about this?

---


---
title: "played with and messed my cd mounting in fstab"
date: 2007-09-25
forum: General Help
---

### Post by akumudzi on 2007-09-25
Out of curiosity I opened /etc/fstab (with sudo rights) and changed /etc/cdrom0 in the /dev/scd0 row to /mnt/cdrom0. i.e. it now looked like this:

/dev/scd0       /mnt/cdrom0   udf,iso9660 user,noauto     0       0

I did this using vim. now when Ubuntu is loaded I cant access my CDs/DVDs. Tried to change it back to /etc/cdrom0 and restarting the machine but this didn't help. The error I get in Nautilus is:

"Unable to mount the selected volume" and under details:
"mount: mount point /etc/cdrom0 does not exist"

I urgently need to load something from a CD.

thanx

---

### Post by reckless2k2 on 2007-09-25
well /etc/ is not a mount point for the cdrom. 

try /media/cdrom0

then sudo mount -a int he terminal or just reboot.

---

### Post by akumudzi on 2007-09-25
it worked. thanks a mil.

---

### Post by reckless2k2 on 2007-09-25
mark it SOLVED baby!!! i racking up fancy mugs here. hahaha

---


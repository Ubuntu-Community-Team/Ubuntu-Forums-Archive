---
title: "/boot problem"
date: 2007-09-12
forum: General Help
---

### Post by bsomers on 2007-09-12
hi all.


Due to filesystem errors, and trying to repair them with fsck, my boot directory is now a file instead of a directory,,, and i cant boot anymore, does anybody know how to fix this? 

thanks a lot

---

### Post by prince_niceguy on 2007-09-12
do you have a entry for /boot in fstab?

if yes, then check which hard disk it corresponds too. Seems your boot mount is not getting mouted.

---


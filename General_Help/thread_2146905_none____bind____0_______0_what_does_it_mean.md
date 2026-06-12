---
title: "none    bind    0       0 what does it mean?"
date: 2013-05-20
forum: General Help
---

### Post by SyncHot on 2013-05-20
Could anyone please tell me what does none and 0 0 mean in my fstab?

/var/www/  /home/administrator/www    none    bind    0       0

---

### Post by Cheesemill on 2013-05-20
[https://help.ubuntu.com/community/Fstab#Fstab_File_Configuration](https://help.ubuntu.com/community/Fstab#Fstab_File_Configuration)

A bind mount is a special type of entry which mirrors an existing file system in a different location. It has none as it's filesystem type as this has already been set when mounting the original location.

---


---
title: "mount fat32 at startup so i can read/write as user"
date: 2007-03-08
forum: General Help
---

### Post by Balinsky on 2007-03-08
alrighty i want to mount my fat32 partition at startup so i can read and write right now i can just read my fstab entry is as follows:
```
/dev/sda5       /home/jebsky/Docs vfat defaults         0       0
```

any help would be awesome

---

### Post by yabbadabbadont on 2007-03-08
```
/dev/hda1       /media/win      vfat         defaults,utf8,umask=007,gid=46     0       1
```
This is how mine is mounted.

---

### Post by Azakus on 2007-03-08
You'll want umask=000

---

### Post by yabbadabbadont on 2007-03-08
> **Azakus said:**
> You'll want umask=000

That will give everyone write access to the drive.  The line I posted is the one used by default by the Ubuntu installer in Edgy.  It makes the drive writable to anyone in the plugdev group.  (your user should already be in that group)

---


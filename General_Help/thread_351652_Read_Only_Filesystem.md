---
title: "Read Only Filesystem"
date: 2007-02-02
forum: General Help
---

### Post by ngms27 on 2007-02-02
Following the machine being accidently turned off, one of my FAT partitions is now showing as a read only filesystem. the entry in fstab hasn't changed.

Any idea's how I can fix this?

---

### Post by an.echte.trilingue on 2007-02-02
Have you tried to umount and then mount manually with the -rw flag?

---

### Post by ngms27 on 2007-02-02
No but I have rebooted and the fstab is correct showing the same settings for other FAT partitions that can be written to

---

### Post by an.echte.trilingue on 2007-02-02
If it it is being mounted -ro because there is a problem with the drive, the problem will not be corrected by mounting it -ro; it will just persist.  Besides, by trying to mount it -rw, there will at least be an error message that will tell you what the problem is and then we can fix it.

Trust me, this will help you.
```
sudo umount /dev/hd??
sudo mount -rw /dev/hd??
```

Take care
-mat

---

### Post by ngms27 on 2007-02-02
Drive unmounts OK and remounts without any error. I still cannot write to the drive!

The drive works from XP but seems unwriteable from Ubuntu.

---


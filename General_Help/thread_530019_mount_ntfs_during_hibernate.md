---
title: "mount ntfs during hibernate?"
date: 2007-08-20
forum: General Help
---

### Post by ZiVvmO on 2007-08-20
i know you aren't allowed to mount using ntfs-3g if the drive is hibernated.  however, i would like to still have access to the drive even if it is read only.

so is there a way to tell fstab (or whatever else...), "hey try to mount w/ ntfs-3g, but if that doesnt work, just mount it as read only"?

---

### Post by dialectic on 2008-05-11
yes the **ro** option for **ntfs-3g**, for example

```
sudo mount -t ntfs-3g /dev/sda3 /mnt/windows -o ro
```

---


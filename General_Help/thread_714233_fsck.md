---
title: "fsck"
date: 2008-03-03
forum: General Help
---

### Post by Dakillakan on 2008-03-03
I was wondering if you could run fsck on a partition and if so, how?

---

### Post by taurus on 2008-03-03
You can run fsck on a partition if the partition is not currently mounted.  You need to unmount it first before you can run fsck.  If you want to run it, try

```
sudo fsck -y /dev/sda1
```
_assuming_ /dev/sda1 is the one you want to fsck.

---

### Post by Dakillakan on 2008-03-03
Wow, that seemed to work.  Apparently 25% was corrupted.

---


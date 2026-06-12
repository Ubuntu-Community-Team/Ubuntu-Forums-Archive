---
title: "Don't know how to add new partitions in fstab now with the UUIDs (Feisty)"
date: 2007-04-25
forum: General Help
---

### Post by billdotson on 2007-04-25
When I installed Feisty I noticed that in the fstab all the devices have UUIDs now.  I do not know how to read a UUID or do anything w/ one.  I have a partition /dev/sdb5 /dev/sdb6 /dev/sdb7 that I want to have in the fstab to automount but now I don't know how.  The partitions are ext3, and should have rw access.

Thanks!

---

### Post by m.musashi on 2007-04-25
You can add them to fstab just as you did in the past. You don't need the UUIDs for them to mount.

EDIT: sorry, that's not overly helpful. You can add them like this...
```
/dev/sdb5    /media/sdb5     ext3    defaults        0       2
```
I've also noticed that UUIDs change if you make changes to partitions so other partitions also won't mount. I don't know how to rebuild UUIDs so if that happens I just go back to using /dev/sdb5 or whatever.

---

### Post by billdotson on 2007-04-25
thanks

---


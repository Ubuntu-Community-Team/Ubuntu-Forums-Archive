---
title: "obtaining an iso from the cd"
date: 2008-06-01
forum: General Help
---

### Post by Mchl923 on 2008-06-01
Is there a way that I can get an iso image from a boot disk.  If not is there a way to copy the disk so that it is bootable?

---

### Post by quelx on 2008-06-01
Can you restate your question and/or explain what you are trying to accomplish?

---

### Post by Mchl923 on 2008-06-01
sorry if I was not clear.  I would like to burn a new copy of the Ubuntu live cd for a friend with slow internet, but I lost my .iso file due to a bad backup.  It would also be nice to have the iso on my hard drive in case I lose the disk.

---

### Post by WRDN on 2008-06-01
It is possible.
Put the disk in, and unmount it if it automatically mounts.

Then use the command

```
dd if=/dev/dvd of=dvd.iso
```

(Replace "if=/dev/dvd" with "if=/dev/cdrom" if its a CD.

EDIT: You could also right click on the disk and click Copy Disk (if available).

---

### Post by Mchl923 on 2008-06-03
awesome, right click copy works great.

---


---
title: "how do i identify hard drive labels?"
date: 2007-09-04
forum: General Help
---

### Post by creamcheeze77 on 2007-09-04
hey i just loaded an update and it seems to have erased my "vista" entry in the grub.  i tried to redo it, but i can't seem to find the right label.  i have four SATA hard drives.  here is my entry for the grub:
```
title            Vista
rootnoverify     (sdc,2) 
savedefault
makeactive
chainloader      +1
```
is there a way to identify which drive is which? the vista partition is smaller than the others and has all the windows stuff in it.  thanks in advance you guys are always great!

---

### Post by ebash on 2007-09-04
You can use fdisk -l to list a summary of the partitions that are available in a disk. If all you have is SATA disks you could use the following command to list all the partitions that are available in your system:

```
sudo fdisk -l /dev/sd[a-z]
```

---

### Post by vanadium on 2007-09-04
I need to add here that this will help to a limited extend only, because grub uses its own scheme to address drives and partitions (grub starts before linux!).

---

### Post by creamcheeze77 on 2007-09-04
so this should be in the format of (hd#,#), not (sd[letter],#) correct?

---

### Post by creamcheeze77 on 2007-09-04
i figured it out, it is (hd1,0) :) thanks guys

---


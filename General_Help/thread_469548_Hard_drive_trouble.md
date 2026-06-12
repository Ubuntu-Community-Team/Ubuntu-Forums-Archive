---
title: "Hard drive trouble"
date: 2007-06-10
forum: General Help
---

### Post by dbvanhorn on 2007-06-10
My fourth drive is really giving me fits.
A WD 500G drive, I've been unable to mount it R/W..
It's formatted EXT3, and from everything I can see it should "just work", but it's not.

Any ideas?

---

### Post by taurus on 2007-06-10
Can you post the outputs of these two commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by dbvanhorn on 2007-06-10
The relevant sections:

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux


/dev/sdd1                                  /media/sdd1     ext3
errors=continue,nodiratime,user,noatime,data=journal  0  0

---


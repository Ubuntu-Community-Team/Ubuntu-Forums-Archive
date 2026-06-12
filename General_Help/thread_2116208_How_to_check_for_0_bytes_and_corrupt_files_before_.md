---
title: "How to check for 0 bytes and corrupt files before backup"
date: 2013-02-15
forum: General Help
---

### Post by looreenzoo on 2013-02-15
Hi all,
I would like to know what is the best way to check my hard drive for corrupt and 0 bytes files before backing it up with Déjà Dup. I had troubles with some documents getting completely blank (meaning file size = 0 bytes) after an online sync and want to prevent them (or other corrupt files) from being written over my existing backup.
Thank you in advance!

---

### Post by schragge on 2013-02-15
Put any directory you like instead of [color=green]/home[/color]
```

find [color=green]/home[/color] -size 0 -type f

```

---

### Post by looreenzoo on 2013-02-15
Thanks! and what about corrupt files?

---

### Post by sudodus on 2013-02-15
> **looreenzoo said:**
> Thanks! and what about corrupt files?
If it is an ext file system, you can check it before backing up. Unmount the partition, and run

```
sudo e2fsck -f /dev/sdxy
```
where x is the drive letter and y is the partition number.

*Edit*: Another and simpler way would be to run ***md5sum*** on all the candidate files to be backed up. Probably md5sum won't succeed with corrupted files.

---

### Post by looreenzoo on 2013-02-15
Thank you!

---


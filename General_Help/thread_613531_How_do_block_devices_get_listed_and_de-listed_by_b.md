---
title: "How do block devices get listed and de-listed by blkid?"
date: 2007-11-15
forum: General Help
---

### Post by davidkahn on 2007-11-15
We have successfully  removed a RAID0 array, /dev/md1 on two PCs, yet blkid continues to list it on both.

We created primary partitions formated for swap on the same two computers.  On one, the new partitions appeared in the blkid output but not in /dev/disk/by-uuid, which prevented using their UUIDs in /etc/fstab, while on the other PC they appeared in /dev/disk/by-uuid but do not show up in the output of blkid.

Everything seems to be working fine on both PCs, after creating the missing symbolic links in /dev/disk/by-uuid.  But mysteries sometimes come back and bite (byte?) you?


Thanks for any help.

---


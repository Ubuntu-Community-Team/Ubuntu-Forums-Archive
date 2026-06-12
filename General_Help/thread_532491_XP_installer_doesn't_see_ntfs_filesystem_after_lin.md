---
title: "XP installer doesn't see ntfs filesystem after linux install"
date: 2007-08-22
forum: General Help
---

### Post by scubashoes on 2007-08-22
So I was having problems with grub so I deleted all partitions with gparted, an ntfs, and an unallocated for ubuntu.  I installed ubuntu and everything is working great on that spectrum. . . . but the remaining 100GB NTFS file system. . which ubuntu has no trouble seeing. . . is unseen by the XP install cd.  IN fact. . when I try to install windows it says I don't have any hard drives installed.  


help plz :(

---

### Post by merlinus on 2007-08-22
Post results of:

```

sudo fdisk -l

```

-merlin

---


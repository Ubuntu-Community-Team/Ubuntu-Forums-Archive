---
title: "Disk repair Utility"
date: 2007-10-23
forum: General Help
---

### Post by shoaibnawaz on 2007-10-23
Is there any software utility that can be available on Ubuntu to diagnose and heal logical bad sectors. Any other tool for Data recovery from Ext3, FAT or NTFS partitions.

---

### Post by anaconda on 2007-10-23
Photorec can restore files from bad hd, and testdisk can find lost partitions..

[http://en.wikipedia.org/wiki/PhotoRec](http://en.wikipedia.org/wiki/PhotoRec)

---

### Post by Nunu on 2007-10-23
> **anaconda said:**
> Photorec can restore files from bad hd, and testdisk can find lost partitions..

[http://en.wikipedia.org/wiki/PhotoRec](http://en.wikipedia.org/wiki/PhotoRec)

Are these applications installed by default or do we need to add them in from some ware else?

---

### Post by az on 2007-10-23
> **shoaibnawaz said:**
> Is there any software utility that can be available on Ubuntu to diagnose and heal logical bad sectors. Any other tool for Data recovery from Ext3, FAT or NTFS partitions.

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)


Use badblocks to look for bad blocks.  It's installed on any Ubuntu system as part of the ext2/3 tools library.

It can do a non-desctructive read-only test.

In any circumstance, I recommend you image your drive before trying to repair the filesystem on it.

You can fix ext or ntfs filesystems using the appropriate libs (dosfstools,  ntfsprogs, ntfs-3g ...)

If your filesystem is not fixable, you can use data carving to recover lost files.  Photorec was mentioned, you can also use foremost.  Again, you will need another hard disk on which to store the recovered files.  Anyway, it would not be smart to recover the files in-situ, since the disk may be bad.

---


---
title: "Error messages when running e2fsck on damaged partition"
date: 2007-08-10
forum: General Help
---

### Post by twiggy_trippit on 2007-08-10
I can no longer mount an ext3 partition that was seemingly damaged because of hardware issues. The partition is still present on the drive and the partition table looks fine; TestDisk can also display the filenames on the partition. But whenever I try to run e2fsck to check and fix the ext3 partition I want to recover, I get the following messages:

***

e2fsck 1.38 (30-Jun-2005)
Storage: Attempt to read block from filesystem resulted in short read while reading block 529

Storage: Attempt to read block from filesystem resulted in short read reading journal superblock

fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for Storage

***

What should I do to recover my data?

Thanks.

---

### Post by twiggy_trippit on 2007-08-11
Just posting again to put this back on top of the forum - it scrolled back pretty far.

---


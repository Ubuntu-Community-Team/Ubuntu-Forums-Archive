---
title: "What type of partition table does Ubuntu create by default?"
date: 2007-08-10
forum: General Help
---

### Post by twiggy_trippit on 2007-08-10
I'm trying to rebuild my partition table in order to recover lost data, and I'd like to know if by default Ubuntu creates a Dos or a Sun partition table.

Does it matter if I choose the wrong type?

Thanks.

---

### Post by splintercellguy on 2007-08-10
Ubuntu creates an ext3 partition for all the data, and usually a linux-swap partition for swapping. What tool are you using?

---

### Post by twiggy_trippit on 2007-08-10
I'm using TestDisk. 

I found that the partition table was Dos, but whenever I try to run e2fsck to check the ext3 partition I want to recover, I get the following messages:

e2fsck 1.38 (30-Jun-2005)
Storage: Attempt to read block from filesystem resulted in short read while reading block 529

Storage: Attempt to read block from filesystem resulted in short read reading journal superblock

fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for Storage

Do you have any idea of what I should try (it's no longer possible to mount this partition, btw)?

---


---
title: "e2label: Bad magic number in super-block"
date: 2007-06-27
forum: General Help
---

### Post by Buendia on 2007-06-27
Running

sudo e2label /dev/sdb1 Windows

I get

e2label: Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

/dev/asb1 is umounted. What's wrong with what?

---

### Post by dcstar on 2007-06-28
> **Buendia said:**
> Running

sudo e2label /dev/sdb1 Windows

I get

e2label: Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

/dev/asb1 is umounted. What's wrong with what?

Well, most likely you are using an EXT2 utility on an non-EXT2 filesystem.

---

### Post by mcduck on 2007-06-28
Yep, trying to rename the label into 'Windows' sounds like the drive is either NTFS or FAT. e2label only works on Ext2/Ext3 file systems.

---

### Post by jonspraggins on 2008-02-15
I am dual-booting Ubuntu 7.10 with windows Vista.  I've tried to e2label my linux partition but I get the same message.  I take it that I can't do this with a drive thats partitioned like this?

---


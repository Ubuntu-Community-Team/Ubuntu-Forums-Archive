---
title: "help deciphering partition lists"
date: 2006-12-06
forum: General Help
---

### Post by Bartender on 2006-12-06
Good morning!

I need someone's help on this...

Device Boot Start End Blocks Id System
/dev/hda1 5106 6380 10241437+ 83 Linux
/dev/hda2 * 7 5105 40957717+ 7 HPFS/NTFS
/dev/hda3 6381 7296 7357770 5 Extended
/dev/hda5 6381 6635 2048256 82 Linux swap / Solaris
/dev/hda6 6636 7296 5309451 b W95 FAT32

Has anyone found a website that explains all the components?  I understand some parts, but what exactly do the characters 83, 7, 5, 82, and b mean?

---

### Post by MrEinstein on 2006-12-06
Try
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4#doc_chap3](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4#doc_chap3)

regards

---

### Post by steve.horsley on 2006-12-06
> what exactly do the characters 83, 7, 5, 82, and b mean?

They are the value of the ID byte of that partition (in hex). This byte is intended to indicate what sort of filesystem is contained within that partition. Linux uses ID 82 for swap and 83 for things like ext2/3, reiserfs. So basically, it's the numeric value for the text string just to the right of it in the listing.

---


---
title: "Restore clonezilla image onto different file system"
date: 2013-11-29
forum: General Help
---

### Post by adec2 on 2013-11-29
Hi,

May i ask if it possible to restore an already backed up image (ext4 format) to a partition formatted as btrfs?

Thanks

---

### Post by sudodus on 2013-11-29
I think ***Clonezilla*** will overwrite the file system. But you can do it in two steps.

- Restore to an empty partition or and let ***Clonezilla*** create the same file system. The partition should have the same or larger size.

- Copy the directories and files with ***rsync*** to a partition with the other file system. The partition must be big enough to contain all the files, but it can be smaller than the original file system.

---

### Post by adec2 on 2013-11-29
ah yes, good thinking. I will need to re-write grub after too?

---

### Post by sudodus on 2013-11-29
Yes I think so, if it is a system partition or boot partition.

It might work with the same grub, if you put the intermediate copy onto another drive, and keep the original partition (particularly the head end should be at the same place, and grub should be in the same directory, normally /boot/grub).

Is this a simple system or is the backed up partition part of a dual boot or multi boot system?

---

### Post by adec2 on 2013-11-29
It's just a simple system with just Ubuntu 13.10 on. Many thanks sudodus

---


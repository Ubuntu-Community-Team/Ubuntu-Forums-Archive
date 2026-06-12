---
title: "GParted nuked a 1 TB NTFS partition"
date: 2007-10-23
forum: General Help
---

### Post by justmoon on 2007-10-23
Turns out GParted doesn't work well with fakeraid. I tried to create a new reiserfs partition after the main NTFS partition. GParted called makereiserfs on the device instead of the partition (gui tools, d'oh), essentially nuking the partition table and most of the important sectors of the NTFS partition.

I recovered the partition table with fdisk. The NTFS bootsector was copied from it's backup with testdisk. The disc is now mountable again, but when I do so, I only get ghost files:

```
?---------  ? ?    ?            ?                ? WINDOWS
```

When I try to access any of them I get a message that the file does not exist.

Testdisk and ntfsundelete both give a complete perfect file structure and whatever file I recover is in perfect working order.

The thing is: I don't have a place to backup 1TB of data to. (Nor the time to reinstall Windows and 300 GB of programs.) **So is there any way to undelete these files in place?**

Any help would be very, very much appreciated!

Cheers,

Stefan

---


---
title: "Wrong size being reported"
date: 2007-03-02
forum: General Help
---

### Post by Physonius on 2007-03-02
I have a USB drive that is FAT32, and has 400 megabytes of free space.  However, my Ubuntu 6.10 only sees 2.5 GBytes of free space.  When I run the DF command it also reports 2.5 megabytes of free space.

What I can I do to correct the issue?  There aren't any hidden files on the USB drive, just to add that in.

Thanks

---

### Post by dcstar on 2007-03-02
> **Physonius said:**
> I have a USB drive that is FAT32, and has 400 megabytes of free space.  However, my Ubuntu 6.10 only sees 2.5 GBytes of free space.  When I run the DF command it also reports 2.5 megabytes of free space.

What I can I do to correct the issue?  There aren't any hidden files on the USB drive, just to add that in.

Thanks

Windows seems to see large FAT32 drives differently to Linux - it may be advisable to use cfdisk to see if the disk is seen as a "W95 FAT32 (LBA)" partition or just "W95 FAT32"

---

### Post by Physonius on 2007-03-03
All right, I'll try that tomorrow and see what happens...

---


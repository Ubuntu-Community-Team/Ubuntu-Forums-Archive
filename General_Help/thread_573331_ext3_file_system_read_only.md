---
title: "ext3 file system read only?"
date: 2007-10-11
forum: General Help
---

### Post by artesvida on 2007-10-11
I have an Ubuntu 7.04 server installed on some older PC hardware, and for some reason the ext3 file system periodically (every few days) falls into read-only mode.  Everything I have read about this points to some sort of hardware failure, but I have used e2fsck with both -c and the -cc options (check for bad blocks, read only; check for bad blocks read/write) and the hard drive gets a clean bill of health.  I've tested the memory with memtest86 (about 10 cycles) and it found no errors.  What gives?  While it's up the system seems to work normally.  But then, when I'm not looking, the file system locks up.  Any suggestions?

---


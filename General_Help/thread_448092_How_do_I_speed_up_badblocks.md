---
title: "How do I speed up badblocks"
date: 2007-05-18
forum: General Help
---

### Post by madoka on 2007-05-18
I just got 3 brand new disks, and I'm running badblocks on them to see if they are DOA.  However, the process is very slow: at the current rate I think it'll take 2 continuous days for one pass.

I know I can specify different block sizes and a different # of blocks to test, but I don't know what values would yield the best performance without sacrificing accuracy.  I'm only interested in if bad sectors *exist*, not where they are.

---

### Post by madoka on 2007-05-20
Well, since nobody answered, I decided to experiment a bit on one of the drives.  Running badblocks on a 1 GB partition somewhere in the middle of the disk, it appears that -c (# of blocks to test) has no effect, unless it's so big that swapping occurs.  Setting -b (block size) to 2048 seems to speed things up by about 40%, but no improvement results from setting it any bigger.

---


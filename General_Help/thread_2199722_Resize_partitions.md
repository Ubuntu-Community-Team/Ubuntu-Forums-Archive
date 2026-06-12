---
title: "Resize partitions"
date: 2014-01-15
forum: General Help
---

### Post by mayagrafix on 2014-01-15
The mounting point / partition only uses a small fraction (7%) of the 132 GB originally allocated by the installer. I already have separate /home and /swap partitions. Can I safely reallocate space from the / partition to the /home partition? can I reduce / to 30 GB and add 100 GB to /home? 

Thanks for ur input :>)

---

### Post by CharlesA on 2014-01-15
How much space is / actually using? If you have plenty of space after resizing the root partition down to 30GB, then go for it.

Just be sure to make backups before messing with partitions in case something goes wrong.

---

### Post by Bucky Ball on 2014-01-15
*Thread moved to** General Help**.*

If you are going to resize the / partition you need to do so from a Live boot, e.g. when booted from the Live disk or USB. This is because the / partition needs to be unmounted to resize it and that can't be the case if you are running the OS from it.

Apart from that, go ahead! My only other advice is with partitioning always make sure you have a solid plan before you dive in (on paper if a complex setup). This can help avoid mistakes.

Good luck. ;)

---


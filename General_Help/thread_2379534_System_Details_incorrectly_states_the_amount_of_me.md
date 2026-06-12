---
title: "System Details incorrectly states the amount of memory in my new SSD"
date: 2017-12-06
forum: General Help
---

### Post by lusbyclark2 on 2017-12-06
I recently had a SSD crash and had it replaced with a larger SSD.  The technician at the shop where this work was done was able to recover most of my data from the original SSD.  My problem is that the System Details indicates that my new SSD only has 109.9 Gbytes when it really has 250 Gbytes.  How can this indication be corrected?

---

### Post by timgood on 2017-12-07
What does gparted say? It may be that the technician did a dd copy of the old to the new and you have unallocated space. If this is the case, you should be able to boot from a USB or DVD and use gparted to expand your existing partition to the whole of the disk.

---


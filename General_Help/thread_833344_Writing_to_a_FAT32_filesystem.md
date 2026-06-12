---
title: "Writing to a FAT32 filesystem"
date: 2008-06-18
forum: General Help
---

### Post by macduy on 2008-06-18
Hi,

I just have this general question: how reliable and safe it is to write to a FAT32 partition, which I am using under Windows as well? I don't have windows installed on that partition, so it's just a separate partition for data really and I'd like to write to it under linux as well.

Thanks.

Hai

---

### Post by prshah on 2008-06-18
> **macduy said:**
> 
how reliable and safe it is to write to a FAT32 partition, which I am using under Windows as well


Totally safe; I have a FAT32 partition on my Fujitsu laptop with XP Home and across 1 year in all kinds of conditions, I've had absolutely no problems. Improper shutdowns in both XP and Ubuntu, fsck thru Ubuntu instead of chkdsk in XP, regular reading, writing, low-level hex viewing, all perfectly done without hassles.

However standard disclaimers apply: YMMV.

---

### Post by macduy on 2008-06-18
Hehe, oh yeah :).

Thanks very much for your prompt reply, I feel much more confident now.

---


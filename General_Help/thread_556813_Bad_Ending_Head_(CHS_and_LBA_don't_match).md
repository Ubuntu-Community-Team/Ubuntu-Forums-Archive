---
title: "Bad Ending Head (CHS and LBA don't match)"
date: 2007-09-21
forum: General Help
---

### Post by Sef on 2007-09-21
Test Disk told me this:  Bad Ending Head (CHS and LBA don't match.)  What does it mean exactly?  What can I do to fix it?

Update:  TD said that I could change the geometry from 16 to 25.   Is this advisable or will it likely cause more problems?

Ubuntu 7.04, P3, 512 ram, 20 gb hd

---

### Post by dcstar on 2007-09-21
> **Sef said:**
> Test Disk told me this:  Bad Ending Head (CHS and LBA don't match.)  What does it mean exactly?  What can I do to fix it?

Update:  TD said that I could change the geometry from 16 to 25.   Is this advisable or will it likely cause more problems?

Ubuntu 7.04, P3, 512 ram, 20 gb hd

It means that the Physical (Cylinders-Heads-Sectors) versus Logical (Logical Block Addressing) disk parameters don't match in your partition table, you can probably repair this using things like the Ranish boot CD (spelling?), but the tool to manually modify your partition table is a bit tricky to use and you risk totally stuffing up your existing partitions.

If you are going to try and change things, make sure you have backed up any important data as things could go pear-shaped quite easily.

---


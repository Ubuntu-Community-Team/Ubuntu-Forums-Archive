---
title: "Partitions Got Blasted"
date: 2008-04-24
forum: General Help
---

### Post by Raptor45 on 2008-04-24
I had a regular partition for my windows install a regular partition for my linux install, and then an extended partition containing an NTFS partition for all my data. Using Gparted, I attempted to move the linux install to within the extended partition by deleting linux, growing the extended partition, and then recreating the partition again inside. Unfortunately gparted failed, and now the entire extended partition is reported as unallocated.

I know all my data is still there, as none of the operations affected that partition itself, but is there any way I could recover it?

Thanks

---

### Post by dstew on 2008-04-24
You can try the TestDisk program. It is a partition recovery program, and it is available through synaptic.

---

### Post by Raptor45 on 2008-04-24
Was able to fix it with a different downloadable tool.

---


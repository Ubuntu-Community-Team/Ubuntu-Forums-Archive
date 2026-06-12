---
title: "How to change the ID"
date: 2014-02-23
forum: General Help
---

### Post by mavik1 on 2014-02-23
Hi,
How to change Id 83 to c 
i tried with sfdisk and fdisk could not get it. Can any one sort this out.

Device Boot         Start         End        Blocks   Id  System
/dev/sdb1           25600       58802       16601+  83  Linux

Thanks

---

### Post by Dave_L on 2014-02-23
83 is GNU/Linux.

I don't see "c" at [https://en.wikipedia.org/wiki/Partition_type#List_of_partition_IDs](https://en.wikipedia.org/wiki/Partition_type#List_of_partition_IDs)
Is it intended to be NTFS? If so, it's best to use Windows to format it.

---


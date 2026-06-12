---
title: "swap"
date: 2007-08-11
forum: General Help
---

### Post by atlfalcons866 on 2007-08-11
can ubuntu install from a live cd on a computer with 512MB ram and no swap? I had to delete my swap parition cuz of windows not wanting to install with more than 3 Partitions

---

### Post by apetresc on 2007-08-12
> **atlfalcons866 said:**
> can ubuntu install from a live cd on a computer with 512MB ram and no swap? I had to delete my swap parition cuz of windows not wanting to install with more than 3 Partitions

Ubuntu will run but you will not be very happy with it. Whenever the memory fills up you will experience very lengthy freezes as the OS struggles to free up some memory.

You should read up on partitioning your drive with "extended partitions", so that you can override the 4-logical-partition-per-drive limitation. It will be much easier for you in the long run.

---

### Post by heimo on 2007-08-12
Or instead of swap partition, you could create swap file.

---


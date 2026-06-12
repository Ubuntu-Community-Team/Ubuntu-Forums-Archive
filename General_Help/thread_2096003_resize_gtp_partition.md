---
title: "resize gtp partition"
date: 2012-12-18
forum: General Help
---

### Post by odror on 2012-12-18
OS: ubuntu 12.10

I just got a 3TB drive. I would like to resize a partition in the drive to the entire disk. Is there a gui (kde version) that can help me with that. partition manager does not work (? because it is a gpt partition)

Thanks

---

### Post by Cheesemill on 2012-12-18
[Gparted]("apt://gparted") works fine with GPT partitioned disks.

---

### Post by odror on 2012-12-18
> **Cheesemill said:**
> [Gparted]("apt://gparted") works fine with GPT partitioned disks.
thanks, but I am looking for KDE/QT version.

---

### Post by Cheesemill on 2012-12-18
I've not used it myself but it took 2 seconds on Google to find [KDE Partition Manager]("apt://partitionmanager") (the package is just called partitionmanager), it uses the same backend as gparted so it should work with GPT partitioned disks.

---

### Post by odror on 2012-12-18
> **Cheesemill said:**
> I've not used it myself but it took 2 seconds on Google to find [KDE Partition Manager]("apt://partitionmanager") (the package is just called partitionmanager), it uses the same backend as gparted so it should work with GPT partitioned disks.
Thanks. I actually tried partitionmanager. I was not able to resize the partition. I thought because it is a gpt partition. I found kvpm that seems to work.

---


---
title: "boot partition filling up!"
date: 2012-11-16
forum: General Help
---

### Post by Ceiber Boy on 2012-11-16
when i installed ubuntu 12.04 (on SSD), i used the alternate ISO to make two primary partitions:

first a /boot partition 300MB
second /encrypted partition (rest of the space on the SSD!)

when i update the system, more and more space is being used from the /boot partition and is currently 78% full.

Question: how do i clear out unused / old files from the /boot partition?

I don’t want to be doing an update and run out of room!

Thanks

---

### Post by Impavidus on 2012-11-16
You could try uninstalling old kernels. Use synaptic, search for "linux-image" and purge the old versions.

---


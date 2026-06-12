---
title: "Partitioning. Have I done this right"
date: 2013-11-18
forum: General Help
---

### Post by ballistic turtle on 2013-11-18
This should probably be in the Wubi megathread, but hear me out. I installed Ubuntu 12.04 through Wubi and set install size as 20GB. Now in Ubuntu, it sees

 dev/loop0 which is 18GB, I assume that's what was created when I installed.
dev/sda3 /host, 181GB which is also the value Windows sees as the remaining storage. So is this just remaining storage?
dev/sda2 /media/systemRESERVED 100MB What is this one??

---

### Post by bantuvez on 2013-11-18
That is the Windows boot partition, which was created when you installed Windows. (For Vista and newer)

---

### Post by grahammechanical on 2013-11-18
I would guess that /dev/sda3/host is the Windows partition with the Windows OS and all available disk space. Do not forget that Ubuntu is installed inside Windows with Wubi.

Regards.

---


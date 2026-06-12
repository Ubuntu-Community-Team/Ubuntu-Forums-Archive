---
title: "Pros/Cons of ntfs or ext3?"
date: 2007-11-17
forum: General Help
---

### Post by pablo66 on 2007-11-17
I am repartitioning an external drive(Freeagent 250G) for use with winXP and Ubuntu 7.10. Are there any advantages or disadvantages to formatting as ext3 or ntfs or fat32?

---

### Post by geirha on 2007-11-17
If you're going to access it using both windows and ubuntu, I would not reccomend using ext3. Windows can't access ext3 partitions out of the box, but Ubuntu can access both fat32 and ntfs out of the box. Fat32 has a size limit of 20 or 40GiB if I remember correctly, so I think ntfs would be the logical choice.

---

### Post by zekopeko on 2007-11-17
go with ntfs. it has less overhead than ext3 so you will get more space on the disk.

---


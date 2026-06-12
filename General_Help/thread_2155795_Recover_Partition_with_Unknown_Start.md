---
title: "Recover Partition with Unknown Start"
date: 2013-06-19
forum: General Help
---

### Post by Kodeine on 2013-06-19
So I had several partitions on one of my disks. Only one of them I wish to recover and I so set off using GNU parted. I recovered one, unwanted, partition by starting at zero and going to the end of the disk. The partition I do want was at the very end so it must finish at 100%. But I'm unware of it's start. How can I attempt to rescue the partition? Currently I'm attempting

rescue 98% 100%
rescue 97% 200%

But so far it's not got me anywhere.

**Tried 'testdisk' from the repositories, far more helpful. Showed me all the partitions on the disk and allowed me to write them back. Rebooted and there they were.

---


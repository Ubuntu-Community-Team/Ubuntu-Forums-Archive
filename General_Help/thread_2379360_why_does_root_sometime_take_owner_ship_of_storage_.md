---
title: "why does root sometime take owner ship of storage device?"
date: 2017-12-04
forum: General Help
---

### Post by cdoublejj on 2017-12-04
So i ran in to this after testing and formatting a drive after the file system corrupted. I zeroed it out with a destructive read write test and and deleted all partitions and tables with gparted and spun up a new Ext4 FS only fora big fat permission denied when trying to copy to it.

THIS SOLVED my problem; [B][https://ubuntuforums.org/showthread.php?t=1334840](https://ubuntuforums.org/showthread.php?t=1334840)

[/B]but, WHY!? Why did root claim my device? Is that a simple answer or default behaviour?

---

### Post by The Cog on 2017-12-04
When you format a partition, it is automatically owned by root. This is more than a default, it is not optional. If you need to give access to other users then root can change permissions accordingly.

P.S. I've never tried, but I suppose it's possible that if a user other than root had write access to the device then they might be given ownership when they formatted it. But I doubt it.

---


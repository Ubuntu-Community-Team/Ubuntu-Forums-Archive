---
title: "Partitioning question"
date: 2006-09-08
forum: General Help
---

### Post by canadianwriterman on 2006-09-08
Running a dual boot of Windows XP and Dapper. When I installed Dapper, it resized the NTFS partition and then filled the rest of the HD with Ubuntu and the swap. I'd like to enlarge the NTFS partition a bit. Does anyone know if an NTFS parition can move onto disk territory that has previously been formatted as ext3? Seems to me I heard once that you can't. Thanks.

---

### Post by link141 on 2006-09-08
After the partitions are using all the disk space, you must shrink your ext3 partition and grow your NTFS partition to the size you want after freeing space.  If need a good app. for this, try the G-parted live-cd (or use the desktop version on dapper), [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/).

---

### Post by canadianwriterman on 2006-09-08
Thanks Link141. I have gparted CD and find it very useful.

---


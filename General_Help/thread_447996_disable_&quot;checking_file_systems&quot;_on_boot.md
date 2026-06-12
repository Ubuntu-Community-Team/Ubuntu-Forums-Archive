---
title: "disable &quot;checking file systems&quot; on boot"
date: 2007-05-18
forum: General Help
---

### Post by cmat on 2007-05-18
Every time I boot there is a step that checks my Windows FAT32 files system. This process takes ~ 2 minutes and is not necessary since I boot into windows once in a while to check it. How can I disable it or even better run the check ever *n* number of boots?

---

### Post by yabbadabbadont on 2007-05-18
Find the entry in /etc/fstab for your windows partition.  Change the "1" at the end of the line to a '0" (zero).  That will disable the check.  Unfortunately, there isn't an easy way to check an ntfs or fat filesystem every N boots.  (At least none that I know of)

---

### Post by cmat on 2007-05-19
Thank you for the solution.

---


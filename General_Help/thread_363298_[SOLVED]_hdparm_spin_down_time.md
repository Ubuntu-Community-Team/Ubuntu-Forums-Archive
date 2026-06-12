---
title: "[SOLVED] hdparm spin down time"
date: 2007-02-16
forum: General Help
---

### Post by olejorgen on 2007-02-16
Is it possible to figure out the current spin down time of a disk? I tried hdparm, but it could only set it..

---

### Post by mlord on 2007-02-16
> **olejorgen said:**
> Is it possible to figure out the current spin down time of a disk? I tried hdparm, but it could only set it..

There is no standard drive command to query the current standby timer value of a drive.  The best one can do here is "hdparm -C", which will simply tell you whether or not the drive is currently in "standby (spun down)".

Cheers

(hdparm author)

---

### Post by olejorgen on 2007-02-17
Ok, thanks for clearing that up, even if it wasn't the answer I wanted :)

---


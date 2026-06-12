---
title: "LVM Data Recovery"
date: 2008-01-18
forum: General Help
---

### Post by crshman on 2008-01-18
Hello,

I accidentally resized my LVM to the wrong size. I haven't made any changes to the disk and i wanted to know if there was a remote possibility of recovering my data?

I have an array of 7 drives that are used in a Software raid 5 (/dev/md0)

I then have a PV that is made up of /dev/md0

From there i have a Volume Group (VolGroup00) that is made from the /dev/md0 PV

Finally i have a Logical Volume (LogVol00) that is made from VolGroup00

I resized the LogVol00 and i wanted to know if anyone could help me go about getting my data recovered.

---

### Post by aysiu on 2008-01-19
Try booting a live CD, installing *testdisk* and then using *photorec*.

---


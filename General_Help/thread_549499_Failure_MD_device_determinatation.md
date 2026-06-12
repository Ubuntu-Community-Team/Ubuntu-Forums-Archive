---
title: "Failure MD device determinatation"
date: 2007-09-12
forum: General Help
---

### Post by fjgaude on 2007-09-12
Is there a preferred way to physically know which drive has failed in an MD (raid) array after the software indicates a particular drive by name, UUID, /dev/sda, etc., has failed?

How do I know which drive to pull off of the slot?

I cannot think of a good way to mark the drives to know which is which.

frank

---

### Post by garretwp on 2007-10-22
I want to bump this message up. I would like to know the same. I just did a raid1 and will upgrade to a raid5 very soon. But I would like to know of a good way to know which drive actually failed for removal and replacement. Anyone have any tips?

- Garrett

---

### Post by fjgaude on 2007-10-22
It seems those who know don't speak. <smile>

---

### Post by bsmith1051 on 2007-11-19
what about the generic mdadm detail?
```
> sudo mdadm -D /dev/md0
> sudo mdadm -D /dev/md1
etc
```

I just tried it on a test system, yanking the power cord on the 2nd drive, and here's what mdadm shows:
```
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0

           UUID : e009b3c0:b5a74922:984880c3:eb8ecc9d
         Events : 0.23

    Number   Major   Minor   RaidDevice State
       0       3        1        0      active sync   /dev/hda1
       1       0        0        1      removed
```
As long as you know which drive has which label, you should be all set?

---

### Post by bsmith1051 on 2007-11-19
or, were you talking about HOW to match-up drives and labels?  What about the hdparm info?
```
> sudo hdparm -i /dev/hda

Model=ST380011A, FwRev=3.06, SerialNo=3JV4P197
```

---


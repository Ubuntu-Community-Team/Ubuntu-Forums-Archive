---
title: "Something taking up hard drive space."
date: 2008-04-16
forum: General Help
---

### Post by RangerDanger on 2008-04-16
For some reason my filesystem says it is taking up 6.6 GB but my file system capacity says it is using 36 GB.  Somewhere 30 GB has gone missing.   I can't find it anywhere.

---

### Post by ss08 on 2008-04-16
Do you have any other partitions? What does gparted show?

---

### Post by RangerDanger on 2008-04-16
> **ss08 said:**
> Do you have any other partitions? What does gparted show?

I have a Windows partition, but that is separate.  The info I posted is for my Ubuntu partition alone.  My Windows partition is just fine.

---

### Post by Bubba64 on 2008-04-16
> **RangerDanger said:**
> For some reason my filesystem says it is taking up 6.6 GB but my file system capacity says it is using 36 GB.  Somewhere 30 GB has gone missing.   I can't find it anywhere.

When you put your cursor over any area in the diagram on the right it wil tell you what is there.

---

### Post by IanW on 2008-04-16
Is your Windows partition 30GB by any chance?
Because the part of the screenshot you've ringed refers to the physical capacity of the drive, not the partition.

---

### Post by RangerDanger on 2008-04-17
> **IanW said:**
> Is your Windows partition 30GB by any chance?
Because the part of the screenshot you've ringed refers to the physical capacity of the drive, not the partition.

Actually it does refer to the size of the Linux partition, my hard drive is 160 GB and my windows partition is 80 GB.

---

### Post by TeoBigusGeekus on 2008-04-17
Do you have vmware installed by any chance?

---

### Post by fguilhon on 2008-04-17
You can search for big files using find. For example:
```
find / -size +1G
```
This searchs for more than 1 gig files

---


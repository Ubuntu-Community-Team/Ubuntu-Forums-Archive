---
title: "Small pieces of unused space on hard drive."
date: 2018-04-28
forum: General Help
---

### Post by CaptainMark on 2018-04-28
When I first partitioned my harddrive I made 1 small root partition formatted as ext4, 1 large home partition also formatted as ext4 and one very small swap partition. I never asked the installer to leave any free space. 

The next time I look at my harddrive layout I have small areas of unformatted space between the partitions, they are usually only a few bytes or mb in size. Throughout the years these small gaps seem to change at random, sometimes they are at the start or between partitions or at the end, they seem to change in size and quite simply, they annoy me. 

My multifaceted question is/are:
1. Why do we get these small areas of unused space.
2. Do they have any negative impact apart from confusing me when setting up my partitions during the install procedure.
3. Is there any way to get rid of them and stop them from appearing that is simple, without impacting the system, or confusing my tiny mind.

Many thanks.
Mark

---

### Post by pqwoerituytrueiwoq on 2018-04-28
I know you can get rid of them using a old version of gparted try the 0.18 version
I have just assumed the space was added for good reason as gparted hides it
if gparted shows the space it was the result of rounding the partition to MiB or cylinder

I have seen gparted leave space when adding multiple partitions at the same time

---


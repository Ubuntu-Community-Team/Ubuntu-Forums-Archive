---
title: "gParted has wrong drive sizes"
date: 2007-01-28
forum: General Help
---

### Post by OrbitEleven on 2007-01-28
I decided to do a wipe of my system with the install of a 300Gb drive to complement my 80Gb drive.  Ultimately, it will be a MythTV box.

Anyway, when I run the Edgy installer from the liveCD, it tells me the correct drive sizes.  However, when I go to "Manual Partition", the drive sizes are 76Gb and 279Gb.  What happened?  Nothing I do seems to make it report correctly. 

BIOS has them correct, the installer does, but not gParted.

Ideas?

---

### Post by chalex on 2007-01-28
Those are the correct sizes.  It all depends on your definition of "GB".  Disk manufacturers define that to be one billion bytes, when it should really be a power of two.  Take a look at this page for more info: [http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

---

### Post by matthew on 2007-01-28
gParted is probably using actual [Gigabytes]("http://en.wikipedia.org/wiki/Gigabytes"), appropriately measured, instead of as a synonym for [Gibibytes]("http://en.wikipedia.org/wiki/Gibibyte")[]("http://en.wikipedia.org/wiki/Gigabytes"). Hard drives are generally sold using a misunderstanding of which is appropriate and it has lead to confusion.

Click the links...they will explain the problem better than I will...especially this one: [http://en.wikipedia.org/wiki/Gibibyte](http://en.wikipedia.org/wiki/Gibibyte)

---

### Post by OrbitEleven on 2007-01-28
Cool.  Thanks for the clarification.

Damn marketing folks...

---

### Post by pickarooney on 2007-07-16
Apparently the filesystem takes up about 5% of the total disk size (en after gigglybytes have been taken into account). This is a whopping 25 GB (or GiB or whatever) on a new 500GB/GiB hard drive. That's about 6 DVDs worth of fresh air!

---

### Post by pickarooney on 2007-07-21
Weird... I just emptied a 200GB disk and gparted told me there was 3GB used. So I formatted it (still in ext3) and now there's 10GB used! That can't be healthy

---


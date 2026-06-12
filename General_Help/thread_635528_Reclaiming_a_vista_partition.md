---
title: "Reclaiming a vista partition"
date: 2007-12-08
forum: General Help
---

### Post by splitpane on 2007-12-08
My laptop came with Vista.  I partitioned the drive and installed ubuntu, while leaving vista in place.  (Should have just wiped the whole thing and installed ubuntu...)  Everything is great with ubuntu but now I want to get rid of the vista partition, or rather merge it into the linux partition.  Is it better to just reformat the vista partition and then mount it?  Or should I repartition?  I'd like to have the space available in my home directory, is the thing.  Suggestions?

---

### Post by rsambuca on 2007-12-08
You can always just format it as ext3 and then move your /home to that partition.

---

### Post by markusf21 on 2007-12-08
Back up any valuable data
```
sudo apt-get install gparted
```
then run System --> Administration --> Partition Editor 
Click on your windows partition then delete it and merge it with your ext3 partition

---

### Post by rsambuca on 2007-12-08
> **markusf21 said:**
> Back up any valuable data
```
sudo apt-get install gparted
```
then run System --> Administration --> Partition Editor 
Click on your windows partition then delete it and merge it with your ext3 partition

I don't think you can merge it into a mounted partition.  You would have to use the liveCD to do that.

---

### Post by markusf21 on 2007-12-08
> **rsambuca said:**
> I don't think you can merge it into a mounted partition.  You would have to use the liveCD to do that.

You're right the ubuntu live cd has gparted on it just make sure both of the partitions are unmounted

---


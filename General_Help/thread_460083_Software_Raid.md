---
title: "Software Raid?"
date: 2007-05-31
forum: General Help
---

### Post by nami on 2007-05-31
Hi

I have 2x 250Gb HDDs IDE 133 (I think), and want to install ubuntu on one of these.  I want the other harddrive to mirror whatever happens on the first drive, so if the first one ever fails, I can easily switch to the second drive via the motherboard bios.

Is it possible to do with with ubuntu?

---

### Post by eyelessfade on 2007-06-01
sure. but its not how it works. both hard drive is only accessible through /dev/mbx and if one goes the other will still give you your data. its raid 1 you want. I guess  mdadm and or dmraid is what you want.

and 2 sec with google gave me this:
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

have fun!

---

### Post by tszanon on 2007-06-01
If you are going to install ubuntu, then you can just use the Alternate CD to install. Once you reach the partitioner, you set up RAID 1. That's the only difference in installation.

If I recall correctly, the steps are:
1. create the partitions;
2. set each of them as a RAID volume;
3. create a RAID array. The partitioner will save the partition table;
4. select RAID 1;
5. select which partitions will be used to create the array.

Then, select the new raid array (it will appear in the partitions list) to be your installation partition.
Repeat the steps above for each raid array you want to create.

---


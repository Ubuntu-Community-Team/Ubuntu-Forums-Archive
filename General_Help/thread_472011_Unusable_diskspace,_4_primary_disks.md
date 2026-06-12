---
title: "Unusable diskspace, 4 primary disks"
date: 2007-06-12
forum: General Help
---

### Post by rockstar82 on 2007-06-12
I am using Feisty Fawn since a couple of days, and during the install i used the manual partitioner. I got a windows ntfs-partition that i wanted to keep, and i also wanted to leave 70 Gb if i needed it later, for a vfat, ntfs or another dist,

As i made the partitions, i was only able to make 3 partitions. I thought "ok, i make the last one later", and went on with the installation.

Now i wanted to use the empty diskspace for a vfat-partition, but was unable to do that. I ran *cfdisk -P s*, and realised that all partitions was Primary ones, and i cannot have more than 4. DOH!...

```
-- ------- ----------- ----------- ------- ---------- -------------------- ----
   None     0        	2047*      0#  2048			*Unusable            None
 1 Primary  2048*   	25171967*  0   25169920	*HPFS/NTFS  	(07) 		     Start
   None     25171968*   25173854   0   1887			*Unusable            None
 2 Primary  25173855    41174594   0   16000740 		Linux 	    	(83) None
 3 Primary  41174595    43166654   0   1992060 			Linux swap / So (82) None
 4 Primary  43166655    343164464  0   299997810 		Linux 		(83) None
   None     343164465   488392064  0   145227600 		Unusable             None
```

What is the easiest way to get myself either a vfat-partition, or a ntfs, without ending up messing with Grub or someting similar..?

Thanks in advance!

---

### Post by merlinus on 2007-06-12
What is the output of:
```

sudo fdisk -l

```

-merlin

---

### Post by rockstar82 on 2007-06-12
sudo fdisk -l
```
Disk /dev/sda: 250,0 GB, 250059350016 byte
255 heads, 63 sectors, 30401 cylinders
Devices = cylinders of 16065 · 512 = 8225280 byte

Device     Start     Beginning    End     Block    Id    System
/dev/sda1   *           1        1567    12584960    7  HPFS/NTFS
/dev/sda2            1568        2563     8000370   83  Linux
/dev/sda3            2564        2687      996030   82  Linux swap / Solaris
/dev/sda4            2688       21361   149998905   83  Linux
```

---


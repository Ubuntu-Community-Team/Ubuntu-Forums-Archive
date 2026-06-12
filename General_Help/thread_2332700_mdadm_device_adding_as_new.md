---
title: "mdadm device adding as new"
date: 2016-08-03
forum: General Help
---

### Post by chrissi2 on 2016-08-03
Hi, 

i need some help with my raid configuration. I got a raid 6 with 2TB disks. Im currently updating to 4TB disks when an old one fails. I'm planning to convert to 4TB/disk when enough old 2TB disks failed. 
Now i partitioned one new 4TB disk wrongly (MBR not GPT). It was already in the raid and synced and worked. 
Now I failed and removed it and repartitioned it as GPT with 4TB. Then I readded it but it doesn't resync. Instead it sais: 
```
gc@gc-desktop:~$ sudo mdadm /dev/md0 --add /dev/sda1mdadm: re-added /dev/sda1
gc@gc-desktop:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sda1[9] sdc1[10] sdb1[5] sdd1[3] sdf1[7] sdh1[8] sde1[6]
      9766909440 blocks super 1.2 level 6, 512k chunk, algorithm 2 [7/7] [UUUUUUU]
      bitmap: 0/15 pages [0KB], 65536KB chunk


unused devices: <none>

```

How can this be? By repartitioning I deleted all data on sda haven't I? How do I add it as a fresh disk?

---

### Post by chrissi2 on 2016-08-03
I think I worked it out. 
I removed the disk in question (/dev/sda1) and did: 
```
sudo mdadm --zero-superblock /dev/sda1
```
Then I added it again and it is recovering now.

---


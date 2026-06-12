---
title: "Seeking repartition advice"
date: 2013-11-17
forum: General Help
---

### Post by Lloydb39 on 2013-11-17
I have a 1 TB drive, and I'm using less than 20 percent, according to disk utility. I would like to move home folder to a new partition. I've searched but most people are trying to dual boot and all that. I just have one OS, Ubuntu 12.04, and it should be simple but I don't want to muck it up, so I'm looking for a step by step procedure. I THINK I should unmount the drive, shrink the main partition to about 15 G and then create a new partition. If that much is right, then do I exit and somehow move the entire home folder to the new partition? If so, how, or if not, what? Thanks.

---

### Post by Bucky Ball on 2013-11-17
There is SO much information about moving /home directory to a separate /home partition out there:

[https://duckduckgo.com/?q=move+home+to+partition+ubuntu](https://duckduckgo.com/?q=move+home+to+partition+ubuntu)

---

### Post by oldfred on 2013-11-17
A good set of instructions.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Another alternative:
I have multiple installs, so instead of /home I have /mnt/data. Then I can use the data partition in all my installs and do not have conflicts or can have different user settings in each install.

---


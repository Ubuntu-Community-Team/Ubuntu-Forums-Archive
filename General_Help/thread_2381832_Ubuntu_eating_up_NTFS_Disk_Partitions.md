---
title: "Ubuntu eating up NTFS Disk Partitions"
date: 2018-01-05
forum: General Help
---

### Post by kwasiowusu25 on 2018-01-05
I have a Dell Inspiron 3541 AMD A6 with Raedon R4 Graphics.
I dualbooted it recently...I have W10 Creators Update and Ubuntu 16.04 LTS Running on it.
I have recently run into a situation where ubuntu seems to be using up space on all my disk partitions.
I have found a way to clear the unneeded space on the main or root linux partition. But I can't free up space on the NTFS Folder which holds all my data.
Windows OS Partition shows 159 GB (NTFS)
25 05 (Partition that holds my data) shows 240GB (NTFS)
Linux OS Partition shows 100GB.

I have 86GB free of the 240GB and 90GB free off the 159GB.

Can someone help me get back the used space because what I have on the NTFS Drives is not up to a 100GB (on the 240GB Drive) and 60GB (on the 159GB drive) respectively.

Ubuntu is just eating up all the space and I don't know how.

---

### Post by yancek on 2018-01-05
I'm not really sure what the problem is based on your post.  You seem to be jumping to a conclusion which has no basis in fact.  Neither Ubuntu nor any Linux system will run on or use an ntfs filesystem unless specifically told to by a user for example, by specifically copying data to that partition.  To get some information, run the following command and post the output:

```
sudo parted -l
``` Lower Case Letter L in the command  
With the various partitions you reference mounted, run:

```
df -h
```

Post the output here also.

---


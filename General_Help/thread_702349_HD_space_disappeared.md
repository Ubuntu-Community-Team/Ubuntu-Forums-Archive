---
title: "HD space disappeared"
date: 2008-02-20
forum: General Help
---

### Post by Magatsu Taito on 2008-02-20
First of all, I read the threads close to my title, and searched on the forums, but I didn't find anything that I could use to solve this.

Right now, I have 2 500GB harddrives, where one is NTFS and the other on is EXT3. The 500GB is everything I want to save, on the other 500GB harddrive. When I was going to copy everything over, this error ppped up, telling me that the space on the ext3 disk wasn't enough. Knowing that both are exactly the same, and the ntfs disk ain't full or anything, this problem bothered me.

I looked around and found out that the ext3 disk only housed 381GB, of the 500GB it really is. I mean, I have heard about rounding errors in the computer world, but no 120GB that just vanishes into thin air.

Fdisk shows that both are 500GB in size, so it has to go somewhere?

---

### Post by notwen on 2008-02-20
Use GParted and see if there are additional partitions using this missing 120GB of space.  Also just wondering do you have an OS installed on either of these 2 500GB HDDs?

---

### Post by petehall on 2008-02-20
You could also check what percentage of the disc is being reserved for root, using tune2fs -l

---

### Post by Magatsu Taito on 2008-02-20
GParted sayd the following about my 500GB disc, which is all empty.

Size: 465GB
Used: 61.22GB
Unused: 404GB

When browsing the folder normally, it shows 
Free space: 381GB

The disc is not partitioned, it has nothing inside except a lost+found folder.

---

### Post by petehall on 2008-02-20
> **Magatsu Taito said:**
> GParted sayd the following about my 500GB disc, which is all empty.

Size: 465GB
Used: 61.22GB
Unused: 404GB

Okay, so firstly it's not empty. There's 60GB of data in there. That could either be in your lost+found folder, or in the Trash, or some other hidden folder. Use ls -al to reveal anything that might be lurking.

> **Magatsu Taito said:**
> When browsing the folder normally, it shows 
Free space: 381GB

The disc is not partitioned, it has nothing inside except a lost+found folder.

The difference between free space and unused space is the "reserved for root" portion, as I mentioned earlier. By default, 5% of a partition is reserved, and this is consistent with your 20 GB discrepancy. If you need this 20 GB back, you should use tune2fs -m 0 to set the reserved percentage to zero.

If you need any further guidance using these commands, I'm happy to help.

---

### Post by oldb0y on 2008-02-20
Don't forget the swap-partition, this is not 120GB, but you may want to check it as well.

---

### Post by notwen on 2008-02-20
You could also use CTRL+H in Nautilus to view hidden folders/files.

---


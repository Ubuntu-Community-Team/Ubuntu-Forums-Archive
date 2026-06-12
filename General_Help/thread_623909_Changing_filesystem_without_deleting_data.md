---
title: "Changing filesystem without deleting data"
date: 2007-11-26
forum: General Help
---

### Post by retrow on 2007-11-26
I have dual boot XP and Gutsy on my older desktop. I plan to completely get rid of windows on that one and use it as a fileserver under Gutsy. Unfortunately most of my files are under NTFS partition (over 40 GB). 

I know its possible to burn DVDs to back up the data and reformat the partition to ReiserFS and then trandfer it over to the HDD, but I was curious to know if its possible to change the NTFS filesystem to ReiserFS while keeping the data intact? Everyone I've asked at my office said that they didn't quite know of any other way. I just wanted to make sure before I start burning those 10-12 DVDs.

Thanks.

---

### Post by PeterJS on 2007-11-26
Well if you've got the free space to do it, you could format half the disk as reiserfs, copy the files over to that parition, delete the ntfs parition and then grow the reiserfs parition to take up the entire disk. But there really is no gracefully way to transition one filesystem to another.

---

### Post by retrow on 2007-11-26
Thanks Peter! The option you mentioned can work but unfortunately it will require iterative resize/reformat operations given the way I've partitioned by drive and it might need fair amount of supervision until the job is done. I guess burning DVDs might be the way to go in my case.

---


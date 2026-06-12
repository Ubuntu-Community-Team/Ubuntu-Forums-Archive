---
title: "/ Full Up Again"
date: 2015-10-13
forum: General Help
---

### Post by Quarkrad on 2015-10-13
Running 14.04.   I think(?) I know what my problem is - just cannot get it sorted.   I have seperate \ and \home partitions and as you can see on full2 my sda1 \ partition is full.  The last time I had this happen it was because I Backup from HD1 to HD2 and when there is a problem with HD2 (which I had the other day) it seems that rsnc has to backup somewhere so it defaults to \ - hence it gets full up.  I have run Disk Usage Analyser/baobab  to see what is filling up \ but confused (yet again) because full3 shows lizubuntu as 29.4GB / 29.4 GB (which matches with sda1 as shown on full2) - but when I click on the arrow head to the right of 29.4GB / 29.4GB to expand it I get full1 which shows only 9.2GB. How do I 'see' what is filling up sda1?

---

### Post by ian-weisser on 2015-10-13
> **Quarkrad said:**
> How do I 'see' what is filling up sda1?
Return to the circular chart on Disk Usage Analyzer.
Roll your mouse over the larger blocks.

EDIT: Sorry, misunderstood

---

### Post by Quarkrad on 2015-10-13
Assuming you mean full1 - yes, I can see what all the blocks are but this is only the make-up of 9.2GB, sda1 is 29GB.  On my other machine, that also has a separate \ and \home  I'm only using 6GB out of the 30G  partition.   On this machine I'm using all 30GB (although ubuntu reports it as 29GB).

---

### Post by TheFu on 2015-10-13
rsync backs up to the directory structure. It doesn't  know anything about file systems  or mount points. If the storage where you'd like to backup isn't mounted, then rsync will happily write to a directory structure that it creates which happens to be on /.

Further, if the storage is mounted back to the old mount point, it is possible for all those files under that location to be completely inaccessible, but still using all the storage.

So - if this happened  to you, remove the files that rsync put on  /  when the storage isn't mounted before you mount it again. It would  be  a good idea to add a check for your mirror script (rsync really isn't sufficient for backups) that checks for this mount before pushing  data.

Yes. I learned this when the same thing happened to me.

BTW - there is NO \ on Unix. It is a forward /.  Computers are exacting machines. We need to be accurate as well, or they will do what we tell them, not what we meant to tell for them to do.

---

### Post by Quarkrad on 2015-10-13
I think my problem is actually 'seeing' what is in / and only / - or in my speak sda1.

---

### Post by TheFu on 2015-10-13
I only use shell commands. A few you might find helpful:
```
df -h 
du -sh /* |sort-h
```
Then work your way down the largest directories until you find the issue.

If you think there  are just a few huge files, **find** is made to find those.
```
find . -type f -size +3G -exec ls -lh {} \; 

```

---


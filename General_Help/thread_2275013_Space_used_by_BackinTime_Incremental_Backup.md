---
title: "Space used by BackinTime Incremental Backup"
date: 2015-04-23
forum: General Help
---

### Post by gus_zernial on 2015-04-23
I've recently started using backintime on Kubuntu 14.10 and I've done one full backip 4/19 and one incremental (?) backup on 4/23
When I do du -hd1 I get this ...

$ du -hd1 /BACKUPS/Snapshots/backintime/$HOSTNAME/$USER/1

346G    ./20150419-110948-459
175G    ./20150423-093001-255
521G    .

The size of the incremental looks way too big, and also the space useage on the backup disk as reported by df went way up after the incremental. But, I read somewhere that the actual space usage reported using these commands does not correctly account for hard links in the incremental ... is that true? If so how do I check actual space used by the incremental backup (I vaguely recall this involves comparing inode numbers between the full and the incremental backups, but I can't find the reference).   Thx, Gus

---

### Post by TheFu on 2015-04-23
B-I-T uses hardlinks. 
[http://backintime.le-web.org/documentation/](http://backintime.le-web.org/documentation/) may be helpful.

I don't have an answer to determine the difference in sizes today. Need to sleep on it.

---


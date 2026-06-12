---
title: "How do I remove zfs dedup tables (expand data)?"
date: 2013-09-12
forum: General Help
---

### Post by namewithhe1d on 2013-09-12
So I was experiencing pitiful zfs performance on my mounted pool after a long while.  Write speeds never passed 10 mb/s and it only got worse.  I turned deduplication off, and my write speed shot up to 75 mb/s.  Clearly the issue here... Now I want to remove the dedup table, or "expand" the data back out so I no longer have to keep the table in memory.  How can I achieve this without killing the pool and starting a new one?  Is it possible?

Result of sudo zpool status -D storage:

```
errors: No known data errors

 dedup: DDT entries 40516427, size 763 on disk, 154 in core


bucket              allocated                       referenced          
______   ______________________________   ______________________________
refcnt   blocks   LSIZE   PSIZE   DSIZE   blocks   LSIZE   PSIZE   DSIZE
------   ------   -----   -----   -----   ------   -----   -----   -----
     1    38.2M   4.78T   4.77T   4.77T    38.2M   4.78T   4.77T   4.77T
     2     386K   48.1G   47.7G   47.7G     785K   97.8G   97.0G   96.9G
     4    21.1K   2.62G   2.61G   2.61G    84.4K   10.5G   10.5G   10.5G
     8       51   5.21M   3.72M   3.87M      510   51.5M   37.7M   39.1M
    16       16   1.78M   1.06M   1.11M      303   32.6M   20.9M   21.8M
    32        5    640K   22.5K   63.9K      215   26.9M    968K   2.68M
   128        1    128K   4.50K   12.8K      202   25.2M    909K   2.52M
   16K        1    128K   4.50K   12.8K    29.6K   3.70G    133M    378M
 Total    38.6M   4.83T   4.82T   4.82T    39.1M   4.89T   4.88T   4.87T



```

I'm a relative newcomer to linux, so go easy on me.  Clearly the 39.1M is troubling, considering I've seen others with 2M on average. 

Thanks

---

### Post by stephanvaningen on 2013-10-22
It is quite doubtful that dedup in-sé is the cause for performance-issue. Couldn't it be that other system settings, being more intensively used because dedup is enabled, are the root cause of it? Specific  read/write cache which is too small?

I also had performace issues if I had the "ashift=12" not set for big disks... you are aware of that?

---

### Post by stephanvaningen on 2013-10-22
If indeed the dedup-table is on 'old iron', performance is down all the way: references: On [the Oracle-site]("https://blogs.oracle.com/bonwick/entry/zfs_dedup"), read section named "Scalability and performance". Also, [this source]("http://www.c0t0d0s0.org/archives/7271-ZFS-Dedup-Internals.html") says "Performance will be best, when the complete DDT fits in memory".

---


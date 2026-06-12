---
title: "Recovering data from Mac Time Machine"
date: 2019-09-01
forum: General Help
---

### Post by mboyns on 2019-09-01
Been following the instructions in [https://ubuntuforums.org/showthread.php?t=2193764](https://ubuntuforums.org/showthread.php?t=2193764) to recover the backup for my now dead Mac - I used the backup drive path as the source and the files were extracting OK until the target drive ran out of space.  The backup I was trying to recover was of a 240GB drive and the target drive had 425GB of space so I thought it would be OK.  However after it filled up it occurred to me that was it trying to recover all 8 of the rolling backups on the drive (so would actually have needed more like 2TB) ?  Would this be correct and so using the path to the "Latest" backup would only extract that backup and only need 240GB ?

---

### Post by mboyns on 2019-09-01
Answered my own question by doing it.

---

### Post by TheFu on 2019-09-01
Did I read that correctly?  The Mac backup tool for 8 backups of 240G takes 425G?  I suspect a better backup tool could be useful?  Obviously, the required storage would be dependent on the amount of changes made, but that growth seems hugely excessive.

Systems around here generally get 60 days of daily, versioned, backups to fit in 1.2x the original storage. So ...
240G x 1.2 = **288G**  For high risk systems, we'll have 180 days of versioned backups, but those tend to be for gateway systems which don't actually have any local data, so their backups are relatively tiny. For example:```

        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Sep  1 02:11:03 2019          138 MB            138 MB   (current mirror)
Sat Aug 31 02:11:03 2019         3.17 KB            138 MB
Fri Aug 30 02:11:03 2019      1002 bytes            138 MB
Thu Aug 29 09:36:08 2019         2.37 KB            138 MB
...
Tue May  7 02:11:03 2019         1.06 KB            140 MB
Mon May  6 02:11:02 2019         2.38 KB            140 MB
Sun May  5 02:11:02 2019       946 bytes            140 MB

```
That is everything needed to put the system back up in about 30 min.  Also, last week, I migrated that system between 2 major releases.  Rebuilding the system would start with the newer release now.

---

### Post by Skaperen on 2019-09-01
even with good tools like rdiff (i use a tool i wrote that is similar) the backup used space will grow over time reflecting the degree of change happening to the source.  a database updating a single row could cause a dozen very large files to be copied again in the 2nd backup.  files that are regularly changed would be copied every time.  the solution is to trim the backup to not include so many repetitions.  i don't know what management tools rdiff or the like actually have.  but you would not want to restore all 8 backup increments.

---

### Post by TheFu on 2019-09-01
I don't use rdiff, use rdiff-backup.  Different tools.

There is an option to ignore huge files, --max-file-size , but I find it easier to just keep media files in different areas and back them up using a simple rsync/mirror, not rdiff-backup.  Media files need a backup too.

If you build programs, your DVCS is really what needs to be backed up, not the build directories.
 
> Obviously, the required storage would be dependent on the amount of changes made, but that growth seems hugely excessive.

---


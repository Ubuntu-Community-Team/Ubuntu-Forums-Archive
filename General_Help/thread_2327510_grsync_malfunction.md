---
title: "grsync malfunction"
date: 2016-06-11
forum: General Help
---

### Post by cmcanulty on 2016-06-11
I have been running backups of 
/home and /etc 
to an external hard drive but now I suspect grsync is actually dumping multiple backups into
 / 
somewhere I can't find as now my
 / 
has suddenly jumped to 38GB which is at least 3x too much. But I have gone through the various
 /
folders and can't find the extra junk anywhere, please help. I wasted 2 hours resizing my / today from the live usb and already the contents have jumped another 3 GB I have the / now  as 50GB which is way too much but it was so full I couldn't boot or anything. I have nowhere near that many installs using up 38GB in /. My /home is a separate partition and not messed up t all by this.I always make sure the ext HD is mounted and browse to it in grsync so can't understand what is going on. I have attached a screenshot of the duplicate mount points in media and they both seem to back up rather than just to ext4 as I would like. I have found that grsync put files in media/cmcanulty/ext4 even after I unmount the ext HD and has many GB there so I deleted that and my / is back to a near normal 1GB now but how can I prevent this issue. It screwed up 2 computers so far.

---

### Post by leunam12 on 2016-06-11
have you tried the Disk usage Analyzer?

---

### Post by cmcanulty on 2016-06-11
I figured it out, grsync was backing up to /media/cmcanulty/ext4 but not actually to the drive so it actually was going into /media and filling up / why I can't figure out as I always check that it is mounted and then browse to it in grsync

---


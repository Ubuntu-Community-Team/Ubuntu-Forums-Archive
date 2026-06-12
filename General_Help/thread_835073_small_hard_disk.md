---
title: "small hard disk"
date: 2008-06-20
forum: General Help
---

### Post by akadruid on 2008-06-20
Hi all,

I am running Feisty on a very old PC with a 3.75GB hard drive.

On startup, 2.9GB space is in use, but over time the disk usage slowly grows, until around 10-12 days after starting, it runs out of space, and errors start appearing.  If you then restart the machine it goes back to 2.9GB in use, and everything is fine again for another 10 days.

I would love to know where all that space goes?  When the disk is full, df -h shows 3.75GB in use, but gdmap shows 2.9GB in use. top shows only 109120k swap in use.  Doing a find across the whole disk for files updated in the last couple of days does not reveal any runaway log files.  There is nothing large in /tmp.  Any ideas?

I know I could upgrade or reinstall but I've been fiddling with this box for years and got it just the way I like it, so I reckon its worth trying.

Thanks

aka

---

### Post by justleen on 2008-06-20
how about running a small cron job that checks the directory sizes, so you can monitor it?

somthing like
```
 for dirs in `ls -1 /`; do du -hs $dirs ; done 
```
or 
```
 find . -type d -exec du -hs {} \; 
```

---

### Post by akadruid on 2008-06-20
good thinking.  I have added the following to my crontab, and will now wait with feigned patience.

```
*/30 * * * * for dirs in `ls -1 /`; do du -hs /$dirs ; done 1>>/home/colin/dirsizes.log 2>/dev/null
```

(Must remember to remove it again eventually, or I will have a different disk space problem...)

---


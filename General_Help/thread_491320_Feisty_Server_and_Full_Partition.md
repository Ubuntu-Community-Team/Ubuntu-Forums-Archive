---
title: "Feisty Server and Full Partition"
date: 2007-07-03
forum: General Help
---

### Post by bbjonz on 2007-07-03
Hi Everyone,

I've installed Feisty server on a PC.  The partition I've installed it on is about 27G in size.  For some reason, the partition is full.  I've tried every means of deleted unused files (e.g., *deb and apt-get autoclean) but the df command  shows that the partition is still full.  Should a Feisty server take up that much space?  I don't have many programs installed (e.g. Firefox, Firefly Server) and the usual server stuff (e.g., MySql).  So, does the installed server size look right or are the files hiding somewhere in the root that I can't find?  (I should note that the /home directory is on another partition, so files in those directories don't count against root.)

Thanks in advance.

Joe

---

### Post by bodhi.zazen on 2007-07-03
Look in /root/.Trash

Also look at your log files.

If all else fails try du ...

[http://www.linux.com/articles/51600](http://www.linux.com/articles/51600)

[http://www.linfo.org/du.html](http://www.linfo.org/du.html)

---

### Post by bbjonz on 2007-07-03
Thanks for your reply and for providing the links.  There is no .Trash directory under root and I deleted all log files before posting.  The df command (which I use regularly) shows that the partition size is 27G and that 25G is used, but it says 0% is available.  Strange.  Using the commands in the links, I don't see anything terribly out of line--maybe the server installation is supposed to be that large?

Joe

---

### Post by bodhi.zazen on 2007-07-03
Seems odd to me ...

If there are on odd, large files, is your server full of data then ?

---

### Post by bbjonz on 2007-07-04
Not that I can tell, and I did a fair amount snooping.  Doesn't seem right to me, too.  All of my music is on a different drive, and I've got the home directories on a different partition.  Strange...

---

### Post by bbjonz on 2007-07-05
I think I know what it did, and it's pretty funny/interesting.  I had an external USB drive mounted on it for backups.  But I just bought an Airport Extreme, so I moved the drive to it, and reformatted to HSF before doing so.  So it's completely irrelevant to my server.  But I have a cron script that would backup (via rsync) my music and pictures on a second internal drive to the USB drive--and I forgot to deactivate it.  So, the cron script worked as it should, writing to a directory off of root that has the same name and path as the USB drive used to have.  So it was the backup that choked root...

Joe

---


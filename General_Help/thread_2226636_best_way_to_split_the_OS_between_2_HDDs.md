---
title: "best way to split the OS between 2 HDDs"
date: 2014-05-28
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-05-28
RAID is not a option, drives are a different size
so i have a couple HDDs in a system what is the best way to split the OS up between the two for the best performance
by split up i mean
Put /home on drive A
Put /var on drive B
Put /boot on drive A
...

i would like to take advantage of the combined I/O as much as possible

---

### Post by TheFu on 2014-05-28
Put / on a drive different from swap (if you swap).
Put your HOME somewhere else.
Turn off atime for mounted partitions.

Really, this stuff isn't gonna help in a perceivable way. Sorry.

There are ways to get more I/O from 2 disks, but those vastly reduce safety and more than double the chance of data loss on both disks.

So ... how are your backups? Excellent, I hope.

---

### Post by pqwoerituytrueiwoq on 2014-05-28
backups: non existent (yea yea, i know is should backup but i am lazy and i know i will pay for it eventually)
critical data is on multiple devices so unless about 3 or 4 systems fail at the same time...

i know it wont help much unless swapping

---

### Post by TheFu on 2014-05-28
Backing up Linux systems doesn't really require much storage. It is just the large media files that aren't nearly as important (for me) that have to be manually backed up. Everything else is handled in automatic, daily, backups.

I sleep really, really, really well.  For 30 systems here, versioned backups with 60-120 days require less than 500G of storage (about $45 these days).  A mirror backup just isn't enough in these days of file corruption, viruses, rootkits, worms, etc. ... Having a mirror of a corrupted file system isn't very useful, but if the backup is versioned, that corruption, if found quickly, isn't a big deal.

Now .... backups of media files are a different story completely. Those get a mirror, as needed, and some don't get backed up at all, but that is my choice, not a failure. I use 10% par2 files for those to ensure lazy bits and other corruption doesn't completely destroy an otherwise ok mirror.

Plus, I don't backup anything large that a fresh OS install will restore.  /usr is an example.  I do grab /etc and /usr/local, plus any settings put in odd places like /var .... and /data and /home  ... of course.   /media is ignored.

So - I've left your question. Sorry.  I've been upgrading a 12.04 VM server to 14.04 over ssh this morning (it is a headless system). Scary, but I knew my backups were 100% of everything I needed to get back to the same place even with a new OS. Just rebooted into the new OS.  All seems fine - even the VMs are up cleanly with relatively complex bridge settings.

My work here is done ... er ... after I force a backup!
```
INFO: Backup Start: Wed May 28 10:02:31 EDT 2014
INFO: Backup End: Wed May 28 10:03:41 EDT 2014

```
Nice, quick, done.  Just how backups should be!

---


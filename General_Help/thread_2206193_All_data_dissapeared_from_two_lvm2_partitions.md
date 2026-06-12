---
title: "All data dissapeared from two lvm2 partitions"
date: 2014-02-17
forum: General Help
---

### Post by magomar on 2014-02-17
I had two 3TB disks using lvm2, no raid. No backup. 
Computer running Ubuntu Server 12.04
After having some problems booting, I let the system try to automatically fix those problems. Then I could boot again normally, but my two lvm2 partitions appear empty. I've been trying to find out information by searching the web, but I don't know that to do next. Most of the posts I have read in my search talk about losing the volume or volume group entirely and having to recreate it. My problem is different because I still have the logical volumes there, everything looks right to me, but still all my files are gone.
I am inclined to think that the data is still there but I don't know how to proceed 
Any help or insight on the path to follow to recover the files is welcome. I already have a SystemRescueCD and I could take any of the disks of this computer and plug it into another computer runing linux.

---

### Post by TheFu on 2014-02-17
I'll be watching this thread closely, however about 10 yrs ago I had a 3 disk LVM setup and 1 of the disks failed in some way.  All the data on all the disks was gone. I got backup religion after that.  I should try to recover that old HDD (somewhere on a shelf here still) using the utilities from **testdisk**.

I suspect there was a hardware issue with one of the drives - controller, cable or the disk.  2 weeks ago, a 14 month old Seagate HDD died here. Had a good backup this time.

I wish you luck.

---

### Post by magomar on 2014-02-18
I have taken one of the two disks in my server and pluged it into my desktop computer, I have had no problems at all mounting the lvm2 partition and surprise ! all the files were there, untouched. I didn't even have to apply any undelete tools. So the problem should be in my server configuration. I guess I should change something in my server to be able to access those files, but I do not know what to do.I guess a clean reinstall of the server would fix things, and I really do not mind doing this. But still I would like to know what happended and how could I fix this withouth reinstalling the server. 
Any ideas?

---

### Post by TheFu on 2014-02-18
What changed?  To determine this, I have a bunch of ways ... but almost all of them are dependent on daily backups.

Retaining the log file from the last "update/upgrade" cycle across all servers is a help too. Did any config files get changed, merged, overwritten?

**System Config Backups**
Storage of system configs in daily backups doesn't take much space at all.  One of the systems has has 30 days of that stuff and it takes only 20MB of backup storage.
```
/Backups# du -sh spamcache
20M     spamcache
```
Been meaning to bump that up to 90 days. There is enough storage to store the entire OS, but there isn't any need. Just the config data is enough to rebuild the system in about 30 minutes.

Backups of this sort don't take much storage, really:
```
/Backups# df -h .
Filesystem            Size  Used Avail Use% Mounted on
/dev/sde3             577G  417G  131G  77% /Backups
```
That is for 38 systems. We are a tiny company. Backups for the corporate email and file server ARE included in that amount.

What is different between the desktop that works and the server that doesn't?  That's another way to attack this. Different kernels, lvm versions, things like that.

---


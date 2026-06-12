---
title: "LUKS &amp; recovery files. Please help."
date: 2016-09-20
forum: General Help
---

### Post by forestman2 on 2016-09-20
I have tree disc in my computer:
first - HDD 250 GB with ubuntu
second - HDD 320 GB with Windows 7
third - USB 60 GB - empty
My idea install ubuntu 15.10 in disk USB. I ran the installer, choose encryprion partition + LVM, and entered passwords. Showed a window with information how the disk is used. I do not know how it happened, it was selected for installation disk with Windows instead disk USB. Installation was interrupted by switching off. I know, it was a mistake...
Now, ubuntu from my first disk sees the drive as encrypted. Entering the password ends access denied to disk. Partition LUKS is closed.     
What is the chance to recovery files from disc HDD?
Please help.

---

### Post by TheFu on 2016-09-20
100% if you have good backups.
Can't say if you don't. Probably very low, but it isn't clear to me what was actually done.  
Boot off a live CD/Flash drive running Ubuntu 16.04 and look at all the drives. What is still good?  What doesn't seem to be working?  You can manually decrypt a partition, then manually mount LVs, if you like (and if that is really the issue).

If you overwrote Windows with encryption ... well ... if it were me, I wouldn't bother trying to get that back unless I had backups.

In the future, if you choose to use encryption, you 100% need
a) excellent backups - trying to get data back from corrupt, encrypted, partitions is next to impossible.
b) know what you are telling it to do - which drive and which partitions are being touched. Best to unplug the cables for those you don't want touched.
c) be prepared for the install to take 1-4 hrs.  I've never seen that, but I've heard about this taking a long time if folks choose certain options.  In the times I've used dm-crypt with LVM, the install was 15 minutes, just like any other install.

If you post back here, please label each drive and partition as A1, A2, B1, B2, .... and describe what is working and what isn't working clearly vs what you intended.  There is also a **boot-info** script you can run - that would provide much useful data for us. Links in my signature.

I suspect you don't have any backups.  Get thy "backup religion" going forward, please.  It isn't hard these days and it isn't like people can't afford $50 for a huge backup HDD. It isn't 1991 anymore.

---


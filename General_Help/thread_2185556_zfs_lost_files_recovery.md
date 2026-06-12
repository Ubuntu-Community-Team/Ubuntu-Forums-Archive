---
title: "zfs lost files recovery"
date: 2013-11-03
forum: General Help
---

### Post by alex.fedotov on 2013-11-03
After zpool export/import and upgrading OS I lost three Vbox files. their size now  ~1.5MB instead of 50-100GB. All snapshots are size 0. My secondary server - same picture.
And that's a DC with Exchange and user files. 

Export/import went smooth. 
Zpool status - healthy. Two other Vbox VMs  work absolutely no problem. Looks like everything is in place but I keep them off for now. 
Need to recover those files somehow. They there still there before the upgrading...

Tried to follow the following:
[http://www.solarisinternals.com/wiki/index.php/ZFS_forensics_scrollback_script](http://www.solarisinternals.com/wiki/index.php/ZFS_forensics_scrollback_script)

it's been almost 24 hours...

Any ideas?

Thanks!

---

### Post by tgalati4 on 2013-11-03
ZFS requires significant RAM to perform operations.  It's possible that the zfs process ran out of RAM with those rather large files and just dumped them.  Check the log files and see if you can pinpoint what happened.  The fact that it happened to 2 servers is consistent with this theory.

Rollback may not work in this case, because the zpool process failed rather than deleted the files in question.  The key to recovery is to figure out exactly what happened first.

---

### Post by alex.fedotov on 2013-11-03
Not sure if I can check the logs now... I have different OS now
More details:

I have three VirtualBox VMs. They all have two or three HDDs attached.
And all HDDs reside in the their own zfs systems.
E.g. 
Domain controller VM.

Disk C - /tank/vm/dc/system/system.vdi
Disk E - /tank/vm/dc/exchange/exchange.vdi
Disk F - /tank/vm/dc/exchange/data.vdi

I'm doing separate snapshots of those ZFS systems.
Normal size of the exchange.vdi is about 60-70GB, don't remember exactly. Now its size only 1.5MB and I can't
even attach it the VM.
Same story for the data.vdi.
system.vdi is actually 15GB instead of 55GB. I was able to start a server but that's about it....
Other two VMs have similar structure but size looks fine and I was able to recreate a VMs and start and stop
them. 

It's a DC that screwed... All my snapshots are 0 in size for the /tank/vm/dc/exchange /tank/vm/dc/data. I'm
keeping only a couple months of snapshots. 
DC was running just fine Saturday morning.
The original system was opensolaris 134b. I've replaced with fresh openindiana. and after with Ubuntu 12.04 with
ZFS. Openiniana was throwing an error message (assertion) when I've tried zdb. that's why I switched to Ubuntu.

i also did one, hmm... not good thing while installation yesterday. Didn't realize there is a dedicate drive for the logs I actually install new OS to that drive.and when import zpool back (it was degraded) I made a drive with previous OS as a new log drive. and zpool became healthy.

---

### Post by tgalati4 on 2013-11-03
Without log files, it's difficult to troubleshoot.  The log file at least keeps a timesline so you can see what was working and when so you can narrow down what failed first.

So it is your impression that the Domain Controller failed and overwrote or deleted the vm images (which happen to be zfs images)?  And you want a procedure to recover these zfs images?

Go through this guide starting on Page 267 and post what procedures you can perform:  [http://docs.oracle.com/cd/E19253-01/819-5461/819-5461.pdf](http://docs.oracle.com/cd/E19253-01/819-5461/819-5461.pdf)

---


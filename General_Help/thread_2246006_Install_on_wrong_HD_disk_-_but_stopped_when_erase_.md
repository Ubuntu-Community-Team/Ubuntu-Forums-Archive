---
title: "Install on wrong HD disk - but stopped when erase was click couple seconds"
date: 2014-09-27
forum: General Help
---

### Post by Bob_Ross on 2014-09-27
Ubuntu 14.04

Install was suppose to be started fresh on 1Tb drive, ubuntu was already on 500gb drive.

Clean Install was started on 500gb drive, as soon as erase all continue was clicked system was shut down. Did boot repair but no booting. Not able to mount etc..

Installed 14.04 on 1Tb drive, prefer to recover home directory on 500gb drive or at least a couple directoies.

 Tried Foremost but 0 files recovered. Could just have been command that didn't work "foremost all /dev/sdb1" without quotes.

Have not tried to do anything else with hopes of recovery. 

Last backup two weeks ago. But important update work was done in virtual box.

Need help to find way to recover that and the linux directory used for the data files.

Thanks
Bob

---

### Post by oldfred on 2014-09-27
Many have suggested testdisk, have you tried that?

       gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

If testdisk does not work, then you may have to use photorec. I have used it, it is slow, requires lots of room to copy files, recovers only by extension and will also recover the deleted files, so I had to compare many old versions, to last backup to try to find most recent data.

---

### Post by Bob_Ross on 2014-09-27
I only tried the two I mentioned. I'll take a look at these.

Thanks


> **oldfred said:**
> Many have suggested testdisk, have you tried that?

       gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

If testdisk does not work, then you may have to use photorec. I have used it, it is slow, requires lots of room to copy files, recovers only by extension and will also recover the deleted files, so I had to compare many old versions, to last backup to try to find most recent data.

---

### Post by Bob_Ross on 2014-09-27
So far TestDisk didn't see any partitions and is finding 100% error read on every cylinder. I can imagine not erasing the drive with a format or any more than a few seconds of a click these programs are not finding anything. The Disks application in ubuntu sees the 4 partitions just doesn't know their names.

I'll work through all of them one at a time, but looks like it's all lost. At least it's only a couple weeks, but really needed that couple weeks.

> **oldfred said:**
> Many have suggested testdisk, have you tried that?

       gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

If testdisk does not work, then you may have to use photorec. I have used it, it is slow, requires lots of room to copy files, recovers only by extension and will also recover the deleted files, so I had to compare many old versions, to last backup to try to find most recent data.

---

### Post by oldfred on 2014-09-27
Did you start testdisk in correct mode either MBR(msdos) or gpt(GUID) I think testdisk says UEFI for gpt.
If your drive was in different partition mode then testdisk will not correctly find partitions.

---

### Post by Bob_Ross on 2014-09-27
It was a standard 14.04 install. Nothing special. I always let the install do all the settings.

Oh well, at least it was only a couple weeks I lost and not the last 6 month's on an online application. It's release
will have to wait until I rebuild some of the web pages.

> **oldfred said:**
> Did you start testdisk in correct mode either MBR(msdos) or gpt(GUID) I think testdisk says UEFI for gpt.
If your drive was in different partition mode then testdisk will not correctly find partitions.

---

### Post by Bob_Ross on 2014-09-27
It never got that far. After I selected Intell/PC it did not show any partitions and even an analise 100% error read. The diskdrives shows it but unknow type, etc.., and
 all 4 partitions but it doesn't allow mounting. Only Ubuntu live will mount it.

> **Bob_Ross said:**
> It was a standard 14.04 install. Nothing special. I always let the install do all the settings.

Oh well, at least it was only a couple weeks I lost and not the last 6 month's on an online application. It's release
will have to wait until I rebuild some of the web pages.

---

### Post by Bob_Ross on 2014-09-27
Since it's a good bet it's gone, I might just install ubuntu 14.04 on the drive and if then they can be pulled off.

> **oldfred said:**
> Did you start testdisk in correct mode either MBR(msdos) or gpt(GUID) I think testdisk says UEFI for gpt.
If your drive was in different partition mode then testdisk will not correctly find partitions.

---


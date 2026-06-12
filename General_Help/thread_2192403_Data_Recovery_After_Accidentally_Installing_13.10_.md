---
title: "Data Recovery After Accidentally Installing 13.10 Over Windows 7?"
date: 2013-12-07
forum: General Help
---

### Post by ejl389 on 2013-12-07
The short version is that Ubuntu 13.10 was installed over top of my Windows 7 install. I won't speculate as to why this is the case, because this is just the latest in a very long series of very confusing events.

So, more to the point, the NTFS partition has been overwritten with Ext4. Ubuntu seems to have used the first 20 GB or so of space on the drive, but there was previously about 700 GB of data, so a large portion should still be on there in one form or another.

I suspect the sticking point will be the change in file system. Is there a tool that will allow for recovery of data from a disk that was written in NTFS, when the partition is now Ext4?

---

### Post by oldfred on 2013-12-07
You will obviously not be able to recover everything as the sectors Ubuntu wrote into are overwritten.

I would try testdisk first just to see what it shows with a deeper search. It should show previous NTFS partition, and may find enough info for files.
I have used photorec, which just scans drive for anything looking like a file, but it only recovers extensions, not file names, so it can be a long slow process.
Some have said for NTFS using Windows tools work better.

 For NTFS - Getdataback often recommended
[http://www.runtime.org/data-recovery-products.htm](http://www.runtime.org/data-recovery-products.htm)

      
 repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

      
 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by dragonfly41 on 2013-12-07
Here are some suggestions based on my similar experience ...

(1) Purchase/acquire an external (USB) hard drive of equal or greater capacity of your overwritten drive.

(2) Use a Live CD (e.g. live clonezilla) to clone your entire messed up windows+ubuntu into this external drive so you can work on recovering this clone (which will take a long time).

(3) Look to windows recovery tools to try to recover your overwritten NTFS partitions.   You will need to use another working windows PC as the host for running data recovery via windows. I have used [http://www.recovermyfiles.com/](http://www.recovermyfiles.com/) with some success on windows but you can also try testdisk which is free.   Run an evaluation version first to see if you can recover any files.

(4) Try various recovery tools (initially in free evaluation mode before purchasing a licence) since some work better than others.

(5) Be prepared to leave your recovery tools running continuously for several days in trying to analyse your 700 GB.

---

### Post by gene7 on 2014-06-05
Another suggestion is this service [http://www.cimaware.com](http://www.cimaware.com) that I always use when I lose data in MS Office

---


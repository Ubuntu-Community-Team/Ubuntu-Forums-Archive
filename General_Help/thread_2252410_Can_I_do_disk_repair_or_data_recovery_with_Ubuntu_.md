---
title: "Can I do disk repair or data recovery with Ubuntu? External drive hacked in XP"
date: 2014-11-11
forum: General Help
---

### Post by robert137 on 2014-11-11
Someone told me that Linux was excellent for recovering data on a hard disk.  I am new to Ubuntu and Linux, so I have no idea.  Here's the situation:

I've got a 500 G Buffalo Drive Station; NTSF Fromat,  that was hacked or otherwise made unrecognizable by Windows XP.  All of the sudden the disk showed up as a CD drive on in My Computer.   In Disk Management, I could see the drive, but there was no drive letter and it showed to be 100% free space, which was not correct.  So I could not access the data.

I found a software called Stellar Phoenix and it took days to scan the disk and then I was able to see all my folders, so I know they are still there.  But I was not connected to the Internet, when I suppose the software was going to take me to purchase the software and then recover my data.  The next time I tried the same thing, it said "not a valid volume or critical data structure badly damaged".  

Well, I know the data is still there from the first attempt with the recovery software, and I may try it some more.  But I have wanted to get as far away from Windows as I possibly could for a long time, so I thought I would check with some of you to see if maybe I can try recovery with Ubuntu, which I am in the process of installing and exploring now.  

If Ubuntu can be used to recover otherwise lost data, please refer me to where I can learn how to go about it.

Thanks!

---

### Post by oldfred on 2014-11-11
Often with NTFS it is better to use Windows tools.

But the Linux recovery tools are testdisk & photorec. 
Testdisk looks for old partition(s) and recreates them. It also has a deeper search that may find files. That is preferable as photorec is a drive scanner. It just scans drive for anything that looks like a file. It only recovers files extensions by type of file not full file name. It is very slow and you have to have another drive with lots of room to copy recovered files to.

There are other Linux recover tools also:
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

    An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

      [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by leclerc65 on 2014-11-11
I just repaired my b.i.l's PC using Partition Magic CD (successfully accessed the drive and copied the data).
You might also have luck with Puppy Linux (on CD or USB). Puppy is very NTFS friendly.

---


---
title: "NTFS signature missing..."
date: 2013-03-25
forum: General Help
---

### Post by ccw127 on 2013-03-25
I had a 1.5 TB drive that I rescued using ddrescue. My first attempt was to an image file... and it worked well enough, but I ran out of room (but that image file would mount and I could copy some files off).

I then went back and rescued again, this time from drive to drive so I would have enough room and be able to do all the ddrescue passes. ddrescue ran great and completed without any issues (other than the bad sectors of course).

I can't mount the physical drive. It complains that the NTFS signature is missing. ntfsfix can't fix the problem (it complains about no signature and some other errors, basically says the drive is corrupt). But if I use testdisk, I can see the files on there....

Is there a way to fix the NTFS?

SUMMARY:
You can try testdisk, but you will likely have to use microsoft's chkdsk..... Or perhaps a combination of the two.

---

### Post by oldfred on 2013-03-25
Another external with similar issue.
[http://ubuntuforums.org/showthread.php?t=2129275](http://ubuntuforums.org/showthread.php?t=2129275)

Are you sure you partitioned drive before writing data to it?

The NTFS signature is the PBR or partition boot sector. All NTFS partitions have to have a valid NTFS boot signature even if not used for booting. It also has the same info on start & size of partition as the partition table.

What does testdisk show?
       repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

   repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by ccw127 on 2013-03-25
Using testdisk to fix the PBR fixed the issue. The main record was fine, but it said the backup with corrupt. I restored the backup from the main, and all (mostly) was well. I had seen options to repair the boot info, but ignored it because I didn't realize the NTFS info would be there as well.

Now the last problem (I hope)...

I am now finding all the files that were at least parially residing in the bad areas of the old drive. While searching I am coming across files that throw and I/O error upon reading (or me trying to manually delete). I checked, and the new drive throws no errors in dmesg, and smartctl shows the health as fine (as far as a seagate drive ever looks 'fine' in smartctl.... I will never buy another seagate.... ).

Should I just run some ntfs checks on the drive? What could cause this as the drive is phsically fine (new/ refurb, just imaged from a bad drive).

Thanks for all the help so far.

---

### Post by oldfred on 2013-03-26
If you copied bad data, I am not sure anything can fix it. Normally chkdsk will not hurt anything, but if it sees errors it cannot fix it writes files to its chkdsk temp folder and once in a while it goes bersek and trys to copy a lot. But chkdsk is the only way to repair a Windows NTFS drive with corruption, usually after every power failure.

---

### Post by ccw127 on 2013-03-26
No, I'm sure the files are garbage... They were partially or wholely in bad sectors.... My current issue is I can't delete them from the new disk (i get I/o error messages )


UPDATE (Solved):

So I tried to play around with testdisk a couple more times and used about every option available to me in there... Nothing. Finally broke down and used a Windows 7 repair cd to run chkdsk from. It fixed some issues it found and exited normally. Drive seems to be working correctly now. I can access and delete files that before were throwing the I/O errors before. Now I get to sift the recovered files and slowly migrate over to a ext3 fs.

---


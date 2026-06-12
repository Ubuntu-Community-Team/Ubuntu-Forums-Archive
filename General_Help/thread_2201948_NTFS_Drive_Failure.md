---
title: "NTFS Drive Failure"
date: 2014-01-26
forum: General Help
---

### Post by Harp on 2014-01-26
I have a WD 3TB External HD, formatted to NTFS, that has recently failed. The drive contains very important data that I must recover. Ordinarily, I keep a backup of this data but, long story short, at the moment, this is not the case.

When I try to mount the drive in Ubuntu, it tells me:
```
Failed to open $MFTMirr/$DATA: No such file or directory
Failed to load $MFTMIRR: No such file or directory
Failed to mount '/dev/sdb2': No such file or directory
```

So I ran:
```
sudo ntfsfix /dev/sdb2

Mounting volume... Failed to open $MFTMirr/$DATA: No such file or directory
Failed to load $MFTMIRR: No such file or directory
FAILED
Attempting to correct errors... Failed to open $MFTMirr/$DATA: No such file or directory
Failed to load $MFTMIRR: No such file or directory
FAILED
Failed to startup volume: No such file or directory
Checking for self-located MFT segment... OK
Failed to open $MFTMirr/$DATA: No such file or directory
Failed to load $MFTMIRR: No such file or directory
Volume is corrupt. You should run chkdsk.
```

When I attach the drive to Windows, it lists it in File Explorer as the generic "Local Disk G:" and when I try to mount it, it says:
```
G:\ is not accessible. The parameter is incorrect.
```

Then, I opened a cmd prompt and ran:
```
chkdsk g:

The type of the file system is NTFS.
Unable to determine volume version and state. CHKDSK aborted.
```

So, I then ran Testdisk and told it to analyse the physical drive. It finds the following Partitions:
```
1 P EFI System 	[EFI System Partition]
2 P MS Data 	[3TB]
```

This looked slightly promising to me, as it lists the MS Data partition by the actual name I designated, "3TB." So I pressed P to list the files of this partition and it came back with: 
```
Can't open filesystem. Filesystem seems damaged.
```

At this point, I started to run PhotoRec but quickly realized it would take approximately 9,000 hours to complete and all of the information would be recovered sans filenames & directories (my ultimate nightmare). Instead, I decided to boot back into Linux and run ddrescue in the hopes that, perhaps, only the EFI partition was damaged and I could recover the data by making an image of the Data partition (?). 

Ddrescue took about 5 days to complete and logged no errors,  but when I tried to mount the .img file:
```
sudo mkdir /media/img
sudo mount -o loop /[path to]/3TB.img /media/img

Failed to open $MFTMirr/$DATA: No such file or directory
Failed to load $MFTMIRR: No such file or directory
Failed to mount '/dev/loop0': No such file or directory
```

So, this is where I am right now. Is there anything I've missed or anything else I can do to try to fix the filesystem of this drive, or am I doomed to PhotoRec Hell?

---

### Post by zteam2 on 2014-01-26
You can try with GetData Back for NTFS, if you want to, but that's not a freeware tool.
You can also try Recuva, but I think this task maybe too complicated for it.

It should also be noted that recent versions of photorec, is able to name documents and ZIP / RAR files automatically these days, Songs and movies can be named by filebot for example.

---

### Post by oldfred on 2014-01-26
Have you tried testdisk? Deeper search may also take a long time.

 Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://ubuntuforums.org/showthread.php?t=1443110](http://ubuntuforums.org/showthread.php?t=1443110)

---

### Post by Harp on 2014-01-26
> **oldfred said:**
> Have you tried testdisk? Deeper search may also take a long time.

Yes, I have tried TestDisk, as stated above. I have also tried other options which, for the sake of time, I have not listed here. I have done a deeper search with TestDisk. I have also done TestDisk > Advanced > Boot > Repair MFT, which compares the MFT with the MFT mirror. Both are bad, which essentially means that, sadly, TestDisk cannot help me.

I'm wondering what could have caused this. The drive was not physically moved/damaged at all and it sounds fine when it starts up (no clicking or anything). I've heard of people having problems with Internal 3.5" WD 3TB drives, something about two drives placed too closely to one-another that causes them to overheat. I'm not sure about the physical structure of this drive, if that is the case or not.

> **zteam2 said:**
> You can try with GetData Back for NTFS, if you want to, but that's not a freeware tool.

$80? Yikes, that's not cheap. But I would maybe rather pay that than to have to rename/reorganize the thousands of different files that PhotoRec would recover. I have the newest version of PhotoRec and haven't seen an option to name files but I will check again.

GetDataBack seems like it would do the job alright, keeping the subdirectories intact. But I wonder how long it would take. Do you know if it has an option to exclude certain file types? For example, I have thousands of .dng files on this drive that I DO NOT need to recover. PhotoRec won't allow me to exclude those, which is a sticking point for me.

---

### Post by d4m1r on 2014-01-27
Do you think it is a mechanical failure or only filesystem? Does the harddrive make a clicking noise?

If it does, try putting it in the freezer over night (in a ziplock bag) and try to boot it the next day....I've had similar issues in the past (drive not recognized) and had success using this method just long enough so I could copy my files off the mechanically compromised drive.

---

### Post by mastablasta on 2014-01-27
is it possible only partition table is damaged?


the freezer trick as silly as it sounds does work - but only in some cases.

---

### Post by Harp on 2014-01-27
> **d4m1r said:**
> Do you think it is a mechanical failure or only filesystem? Does the harddrive make a clicking noise?

The HD, as I said above, sounds fine. I even put a stethoscope to it. It hasn't even been moved for months, so it wasn't dropped/bumped or anything but possibly it could have overheated? I don't know, it was seeing a lot of use up until the end.

If all else fails, maybe I'll put it in the freezer but I'm hoping it's just a filesystem problem. 

**UPDATE**: I had a backup of this drive that I reformatted about a month ago and loaned to a friend for some project he was working on. I just talked to him and it turns out he hasn't used the drive yet. So I got it back from him and am now running **Recuva** to get the deleted data back. It's an older backup but it looks like I will be able to recover about 98% of the data from this reformatted backup. Basically, I got lucky as sh*t. However, I would still like to attempt recovery on the failed drive in order to recover the remaining 2% of the data. 

I'm wondering: **if I build a new partition table in gparted, basically re-format the drive, might I then be able to mount the drive and run data recovery?**

Thanks for the help.

---

### Post by oldfred on 2014-01-27
Gparted will be in effect reformat. Only resetting partitions if not shown may work, but you show two partitions. If that is what you had then resetting not required.

I am seeing too many users with similar issues posting. Not sure if a good idea to put all eggs in one very large basket. Or maybe several smaller partitions unless you have to have one large one for media. 

Did you look at drive from Disks or Disk Utility and  see Smart Status? All I know is passed. But it can run many tests.

---

### Post by Harp on 2014-01-27
Also, in case anyone is interested, I tried [GetDataBack]("http://www.runtime.org/data-recovery-software.htm"), as zteam2 suggested. It seems to restore subdirectories well and is fairly easy to use but, at the time of writing this, it has a price tag of $80. It also nearly requires you to download a separate program called DiskExplorer ($70) in order to browse the data you are trying to recover.

I also tried [Kvisoft Data Recovery]("http://www.kvisoft.com/data-recovery/"), which has a great interface is very user-friendly. It's priced at $70.

Then, I settled on [Recuva]("https://www.piriform.com/recuva"), which isn't as pretty as the others, but it does the job well and is completely free. 

With regards to my original problem, Recuva is what I recommend for data recovery. Now, if you'll excuse me, I'm off to the store to buy a new hard drive and set up a RAID-1.

---

### Post by Harp on 2014-01-27
> Not sure if a good idea to put all eggs in one very large basket. Or maybe several smaller partitions unless you have to have one large one for media. 

That's a good question. Would it be better to separate offline storage into individual partitions for say, Movies vs Documents? I had assumed that having them all on a single partition would be less complicated for the drive to access everything, lessening the risk of failure. But perhaps separating things into partitions would be better in the event of some kind of filesystem corruption. Or, at the least, it might help to keep different types of documents separated in the event of a data recovery.

I now have two 4TB drives that I'm planning to mirror and use to store all of my offline data. Should I partition them as well? I'm not sure about the logistics of partitioning a RAID-1 setup.

---

### Post by oldfred on 2014-01-28
The disadvantage of partitions is that then you may fill one and have lots of room on another. 

Some suggest LVM as you can move partitions. It is full drive and you cannot use gparted, but have to use LVM tools. I do not use it, it is a bit more complicated and may make recovery even more difficult.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

Note that RAID is not backup. Once you delete or corrupt a file is just is gone in both copies.

 Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

---

### Post by Harp on 2014-01-28
Since I was able to recover most of the information from an old backup, I went ahead and reformatted the drive to see whether it was a filesystem or a physical corruption. The drive reformatted fine and then mounted with no trouble whatsoever. So, physically, the drive is fine. I am now running a deep scan in recuva to see what it comes up with.

---


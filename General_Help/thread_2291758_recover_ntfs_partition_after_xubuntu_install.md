---
title: "recover ntfs partition after xubuntu install"
date: 2015-08-22
forum: General Help
---

### Post by stas7 on 2015-08-22
Hi guys,
I had several partitions on hdd, with the first partition with xubuntu and 2nd with linux swap, next where 2 ntfs partitionns.
I booted from xubuntu 14.04.1 livecd and chosen 'erase xubuntu' installation option, which deleted all partitions.
Since the first 2 portions contained xubuntu and were in the beginning of the disk I believe all the ntfs partitions should be untached. What is the simplest way to recover them?

According to mount command the new partition has type ext4. There is another one of size 255mb, not sure what is it for.
Please advise, thank you!

My primart os is win7, I can put HDD into USB box and connect to win7 computer if it needed

---

### Post by ajgreeny on 2015-08-22
Are you totally sure that the NTFS partitions are deleted?  Run a live xubuntu system and from that let's see the output of terminal command ```
sudo parted -l
```
Do not use the newly installed xubuntu system any more until we know what has happened, as any disk activity will reduce the chance of getting your files back, if they really are gone.

---

### Post by yancek on 2015-08-22
> I booted from xubuntu 14.04.1 livecd and chosen 'erase xubuntu' installation option, which deleted all partitions.

Interesting.  I haven't used Xubuntu lately but I've never seen an option like that on any Linux system.  Usually, it is Erase disk and install ??
Since you knew which partitions Xubuntu was on, it would have been a better choice to select the Manual or Something Else option and format and install to the same partition(s).  Too late now though.  Posting the output of the command suggested above should tell us whether you actually have any windows partitions.  If you need to recover data, you could try using TestDisk.

---

### Post by oldfred on 2015-08-22
You should have used the newer Ubuntu. 14.04.1 still has the erase drive bug.
       Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else. And fix is not in current versions. Perhaps in 15.04.
this bug was fixed in the package ubiquity - 2.18.8.3 jan 2015.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

You may be able to use testdisk to see old partitions, but Ubuntu normal install writes parts of files everywhere in partition, so some data will be overwritten. If it was a bootable install, only your backup will restore it to bootable again as files will be missing.

---

### Post by stas7 on 2015-08-22
I think all partitions are destroyed. Sorry for such format, I am writing from a phone. I used xubuntu 14 because the computer is over 10 years old, and I have VM of same version from which I would like to transfer data. 
Should I use testdisk from windows or from xubuntu livecd? 
Can it recover ntfs partitions in mbr or only files? I just don't have enough space to copy all the data.

> If it was a bootable install, only your backup will restore it to bootable again as files will be missing. 
I dont understand this sentence.
==========================
xubuntu@xubuntu:~$ sudo parted -l
Model: ATA SAMSUNG HM641JI (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   640GB  640GB  extended
 5      257MB   640GB  640GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/xubuntu--vg-swap_1: 1007MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  1007MB  1007MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/xubuntu--vg-root: 639GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  639GB  639GB  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

---

### Post by oldfred on 2015-08-22
That was not the bug, but the selection you made on install.
LVM is always a full drive install, unless you force it into something less. One of the advantages is that it has logical partition that can be easier to change, but then you want it on a full drive.
Also if you choose full drive encryption then you also use LVM.  
Full drive means the entire hard drive not just a partition.

The comment was that if the NTFS partition was a bootable partition for Windows, it only takes a file to be overwritten to prevent it from being bootable. For data you may be able to copy from testdisk many but not all files.
And if testdisk does not show files, you will have to use Photorec, which is slow.

You will have to have another drive or larger flash drives with enough space to copy recovered data into. You obviously cannot copy back to drive you are attempting to recover data from.

---

### Post by stas7 on 2015-08-23
Testdisk is said to be able to "Fix partition table, recover deleted partition" here [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Can I use this function?
I did choose LVM option during install.  I am trying to determine whether I should use testdisk or better try some windows specialised utility before its too late?
Does testdisk make any writes to HDD during work (if not than I could try first testdisk then some windows utility)?
If anybody had such case please share your expirience.
Don't want to argue whether it is a bug, I believe it should have shown some warning at least.

Also not sure which liveCD to use for testdisk. Many old threads recommend Ubuntu Rescue Remix, which seems to be not supported since 2012. The place where the computer located doesn't have internet, therefore I cannot install most recent version of testdisk from internet using xubuntu liveCD. Therefore would like to use some livecd that comes with testdisk already. Though if really recommended, I could move the computer to a place with internet.

---

### Post by yancek on 2015-08-23
You might be able to recover deleted partitions and repair the mbr, that is one of the claims and others have reported success.  Fortunately, I've never had to use it myself.

I don't know if some windows software would be better.  Not sure how you would do that in your circumstances, put the drive in another computer?

Knoppix or SystemRescueCD would probably be the best choices.  You can download either and put either on a CD (SystemRescueCD) or DVD (Knoppix) or a flash drive.  The link below has a list of other Linux Rescue CDs.

  [http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

---

### Post by oldfred on 2015-08-23
I think if you can boot a flash drive and have the Ubuntu installer with persistence enabled, you can install testdisk from a system with Inernet. 
Then when you reboot only your damaged system,you have to reinstall testdisk again, but it can be from persistence.

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[URL="http://ubuntuforums.org/showthread.php?t=1655412"]http://ubuntuforums.org/showthread.php?t=1655412
[/URL]
 [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Some that post here regularly and use Windows suggest using Windows tools to recover NTFS partition data. But I think you have to move drive to a Windows system that is working.

Shows some screen shots of testdisk.
[https://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu](https://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu)

 [URL="http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"]http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step
[/URL]
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)[URL="http://ubuntuforums.org/showthread.php?t=1655412"]
[/URL]

---

### Post by stas7 on 2015-08-24
> **yancek said:**
> I don't know if some windows software would be better.  Not sure how you would do that in your circumstances, put the drive in another computer?


I have USB HDD box and a computer with Windows, so can easily do this. But USB box may make it harder to analyse the HDD. Anybody can comment on this?

> **oldfred said:**
> An alternative Windows data recovery program is Recuva -- and it is free


If I try Recuva will write something to HDD?
In case it doesn't find my partions so that I could still try testdisk then

---

### Post by oldfred on 2015-08-24
Just about all these recovery tools are try them and see if they can find anything worthwhile. Most do not write anything until you tell them to copy files to another drive, not drive you are recovering from.

But the LVM does complicate it a lot and if that data was encrypted the old un-encrypted NTFS data may be harder to get to.

---

### Post by stas7 on 2015-08-25
I did not choose encyption option during installation.

So I finally recovered ntfs partitions using Testdisk.  Testdisk seems to be very good tool. I had to do deep search, which took about 4 hours. Some directory structure was lost, so I ran checkdisk from windows which restored some files and directories.
  Recuva don't seem to have functionality to restore deleted partition or I could not find it (I tried it first).
Thank a lot to everybody who replied!

---


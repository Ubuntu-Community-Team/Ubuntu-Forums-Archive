---
title: "External HDD mounts in linux, wont mount in windows. Worked before."
date: 2018-05-11
forum: General Help
---

### Post by greyfaux01 on 2018-05-11
Its fat32, 1 terabyte, toshiba USB external HDD. Was working fine in windows and linux, didnt use it for awhile, and now windows sees it as 'unrecognized or unsupported filesystem'. And i think it shows it as unallocated, although i'll have to put it back in windows to verify that if it matters. Struggling with horrible microsoft updates, so cant plug it in at the moment. It not only mounts in ubuntu fine, gparted seems to show it as good. I did the 'check' function and will add the results from that. Maybe a clue for one of you wizards.

Thanks for your help.

---

### Post by greyfaux01 on 2018-05-11
gparted info from the 'check' function

```

GParted 0.25.0 --enable-libparted-dmraid --enable-online-resize
Libparted 3.2
Check and repair file system (fat32) on /dev/sdb1  00:03:05    ( SUCCESS )     calibrate /dev/sdb1  00:00:00    ( SUCCESS )     path: /dev/sdb1 (partition)
start: 2048
end: 1953523711
size: 1953521664 (931.51 GiB) 

check file system on /dev/sdb1 for errors and (if possible) fix them  00:00:25    ( SUCCESS )     fsck.fat -a -w -v /dev/sdb1  00:00:25    ( SUCCESS )     fsck.fat 3.0.28 (2015-05-16)
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "MSWIN4.1"
Media byte 0xf8 (hard disk)
512 bytes per logical sector
16384 bytes per cluster
92 reserved sectors
First FAT starts at byte 47104 (sector 92)
2 FATs, 32 bit entries
244130816 bytes per FAT (= 476818 sectors)
Root directory start at cluster 3 (arbitrary size)
Data area starts at byte 488308736 (sector 953728)
61017748 data clusters (999714783232 bytes)
63 sectors/track, 255 heads
2048 hidden sectors
1953521664 sectors total
Reclaiming unconnected clusters.
Checking free cluster summary.
/dev/sdb1: 39526 files, 46144672/61017748 clusters




grow file system to fill the partition  00:02:40    ( SUCCESS )     using libparted 


========================================


```

---

### Post by yancek on 2018-05-11
Although there are a number of Linux tools to repair or at least try to repair windows filesystems, you would be better off using windows tools since it is a windows filesystem  When you boot windows, go into Disk Management to check if the partition is seen and if it has a drive letter.  It should since it is a proprietary windows filesystem.  Probably try the repair options discussed at the microsoft site at the link below.

[https://technet.microsoft.com/en-us/library/ee872425.aspx](https://technet.microsoft.com/en-us/library/ee872425.aspx)

---

### Post by greyfaux01 on 2018-05-11
Doesn't windows have to be able to mount it? I tried chkdsk but it didn't do it, iirc correctly I think that's the problem, no drive letter. When I get a chance I will double check. What I do know for sure it keeps wanting me to format, thats the only thing that pops up. 

Would it make any difference if I originally formatted it in Linux using gparted? Cuz I'm almost positive that's what I did 

I'll get back to you about drive letter and why the chkdsk failed. Thanks

---

### Post by yancek on 2018-05-11
I'm sure if you had a Linux filesystem on it, your windows would telling you to format it.  Not sure if it matters that you created the filesystem with GParted, might be possible.  I'd use a windows system to create windows partitions/filesystems.

---

### Post by greyfaux01 on 2018-05-12
And to be clear its def fat32, windows doesn't know that, under properties of the drive it comes up as 0gb used, like a blank disc, and it asks to format each time. 

Still gonna get exact steps and if there's a drive letter, will do chkdsk again just to see what comes up (again could be 'format now'), but will let you know for sure. 

Main thing is its my only terabyte in the house, no where to xfer the data to to reformat. I got the real important **** backed up but it's still hours of downloading so it would be great if I can figure out the root cause. 

In Ubuntu 'disks' the smart option is greyed out. Ubuntu Seen something about a problem with 16.04 in that regard, but don't want to go changing stuff I'm not sure about. I'd rather get it to mount in widows anyway and do chkdsk since its a windows file system, even if it was formatted with gparted.

---

### Post by greyfaux01 on 2018-05-12
-Ok it does get a drive letter, when i run chkdsk in gui it says it 'couldn't complete because disk not formatted, would you like to format?'
-In disk management it shows up as F:, but shows up as RAW, and under properties it shows up as 0mb free/0mb used.
-chkdsk in cmd says 'chkdsk not available for raw drives'.

Most stuff online has to do with getting the data off and reformatting, which im trying to avoid (even though i have the most important data backed up, im too poor to buy another terabyte at the moment and i have no other drive to hold 700gb of data).

So with some more searching i rediscovered the 'testdisk' program. It used to be part of partedmagic, but apparently testdisk itself is a standalone program and has been updated since partedmagic.. So i think im gonna follow these instructions from this link below and install testdisk on windows, and try to rebuild the partition table. If its just a corrupted partition table, testdisk may be able to rebuild it..

ive added the general steps in code tags that im gonna follow, but the one thing that worries me, it asks if the drive was created on win7/etc., this im not sure about. its been so many years since i had this HDD i cant remember if i originally formatted to fat32 in windows or gparted. im not sure how important that question is, so if anyone has any insight on this, it would be appreciated.

I also think i figured out what happened, im in school for IT, my teacher knows next to nothing about computers, im always showing him stuff and fixing the computers in class (he's not even certified in the entry level certifications he's 'teaching' us).. well we have this vipre AV scanning software that scans all removable media, no way to stop the scan, and you cant unmount safely the external drive. I constantly tell him i would rather wait for the scan to get done and 'safely remove' my drive instead of just ripping the cord out, but he's so sure it can never cause a problem, because 'he does it all the time'. Well from reading, i think thats exactly what happened. Vipre was scanning and my horrible teacher ripped out my HDD without 'removing safely' even after i told him i would rather let it finish the scan. So im thinking my partition table got corrupted, and im HOPING testdisk can fix it, and then it will magically work in windows again. I'll be sure to have a talk with my teacher about this if it does work, indicating the partition table indeed got corrupted (since thats all testdisk is fixing AFAIK).

So these are my steps, i'll post back results. If anyone has any info about testdisk that could help, or anything, feel free to add it, im flying kind of blind here. Nervous testdisk will ruin the drive, or i may pick the wrong option and ruin it myself.

[https://html5.litten.com/updated-how-to-fix-external-disk-drive-suddenly-became-raw/](https://html5.litten.com/updated-how-to-fix-external-disk-drive-suddenly-became-raw/)

```

run testdisk_win.exe

TestDisk is a console application so you have to use your keyboard to interact with it instead of your mouse.

Choose CREATE and hit enter

Make sure that your external disk is highlighted
Choose Proceed and hit enter

Select Analyse and hit enter

The partition data looks incorrect (an explanation of why is beyond the scope of this article)
Select Quick Search and hit enter

Say &#8216;Y&#8216; if it asks if the disk was made in Vista/Win7 (even if it was made in XP say &#8216;yes&#8217;)

Now the Quick Search will run

Lets look at the data on that partition press
P
and you should see a list of files/folders in the partition.

Hmmm&#8230; This looks like a bunch of diagnostic tools but not our missing data. We&#8217;ll need to look further. Press
Q
to go back a screen and then press
enter

IF YOU SEE ALL YOUR FILES THEN SKIP THE DEEPER SEARCH AND GO TO THE STEP DESCRIBING SELECTING WRITE

To get to this screen, select DEEPER SEARCH and press enter.

Naturally, the Deeper Search takes longer than the Quick Search

When the Deeper Search completes we now see two partitions. The one we saw after the quick search and another one.

Select the new partition and press
P
to see the files/folders and now we see the data we want to make visible again.

Press
Q
to go back a screen and then press enter to get to this screen.
Select WRITE and press enter in order to write our new partition table to the drive.
DO NOT WRITE A NEW PARTITION TABLE IF YOU DID NOT SEE YOUR FILES/FOLDERS

```

---

### Post by greyfaux01 on 2018-05-18
well testdisk didnt automatically fix it. it at first seen it with the  normal fat32 1000-931gb partition, but when i do 'quick search' and  'deep search' with the tool, it ends up showing the partition table as  HFS+ and has a different number of gigs. Its weird because the linux  sees everything perfectly fine, readable and writable to this terabyte.

If  i could afford another terabyte i would simply copy everything over to  the blank one, reformat the original, and just keep the same data on  both. one as a reduntant backup i guess. But that sucks because i still  wont have any more storage space, its almost like i would have to buy 2  more terabytes, for a total of 3, just to have extra space and have it  reduntant. where does it end? Besides atm i cant afford even one so im  still on a mission to fix this one. If its not the hardware, and linux  can read/write, its got to be fixable imo.

So for now im going to  make an account at the testdisk forums, the dev of the tool seems  pretty active there so maybe with the logfile that testdisk printed out  he can see the light, or tell me for sure its a bad HDD.. 

I  remember reading about long term stable HDDs and IIRC WD drives were all  mostly really good, would last for decades, but then their main factory  in Thailand got flooded or shut down or something, so all the  new/current WD drives are all more crapily made, not lasting nearly as  long.

I wish there was an affordable solution for archiving/using  1-2 terabytes of data, that was long term. I mean backup tapes come to  mind, but that doesnt seem like a good solution for a home user.  Blueray, even at 50g for double side (or dual layer) still is many many  discs, and in the future blueray players may not be very prevalent.  Theres got to be some long term solution multi-terabyte solution for  home users. If not its a niche that could use filling imo.. Well i  remember now seeing special HDDs that are made for long term use, but  their probably well out of my price range.

---


---
title: "Gparted not working to format/partition a 3TB drive that had been attempted in Win XP"
date: 2014-06-02
forum: General Help
---

### Post by 777funk on 2014-06-02
I've got a predicament with a WD 3TB drive that was working well enough in Linux. I partitioned it as 2TB EXT2 and 1TB NFTS (for XP).

Both partitions worked well in Linux but the 1TB NFTS partition wasn't showing up as a Windows format in XP (XP was saying I needed to format the drive letter)...

So I did this (in XP) in hopes that now it'd be recognizable. It tried for a second and failed to format. Then the drive was no longer mounting in Ubuntu. So... hmmm bummer because I would like to have it work in XP. 

But it gets worse! I went to reformat and partition the drive in GParted and I'm getting an error and can't get it to do anything.

Where do I start?

---

### Post by oldfred on 2014-06-02
XP is so old it does not know about gpt partitioning only MBR. 
And 3TB drives have to be gpt partitioned.
       
MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

If you used XP on the drive it may have forced conversion back to MBR corrupting gpt?
Better to use gdisk and see what it says. gpt does have a backup partition table which may salvage original partitions.

sudo apt-get install gdisk
      
 sudo gdisk -l /dev/sda

      
 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by 777funk on 2014-06-02
Thanks Fred. I don't mind loosing the data on that disk by the way (it's backed up other places). Is there a quick easy fix to get it to where I can at least format and re-partition the 3GB

---

### Post by oldfred on 2014-06-02
What does gdisk show?
If corrupted data or corrupted partition table gparted will not work.

---

### Post by 777funk on 2014-06-02
Thanks again Fred. Just installed gdisk and typed gdisk sdb (the device name). What exactly am I asking Gdisk to do?

---

### Post by oldfred on 2014-06-02
Gdisk should say if it sees gpt or only MBR or a mismatch between primary gpt table and backup gpt table.

You should get something like this:

```
Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3645 sectors (1.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    8300  Precise
   4        58925056       117229743   27.8 GiB    0700  TrustySSD

```

---

### Post by 777funk on 2014-06-03
Just did this:

sudo gdisk /dev/sdb 
GPT fdisk (gdisk) version 0.8.1


Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present


Creating new GPT entries.


Command (? for help):

---

### Post by 777funk on 2014-06-03
I'd like to reserve about 500GB to 1TB of this drive for XP (NFTS format) if it's possible. That was the original plan but it didn't seem to work. I'd really like to just wipe the drive and start over on it but I'm not familiar enough with terminal to do this. I tried dd write zeros and it took an entire day and was still running. I don't know if maybe I did something wrong. Just unfamiliar here.

---

### Post by oldfred on 2014-06-03
If you have used dd then there is no way to recover anything. Testdisk may have found old partitions.
If erasing partition table, you only have to use dd to zero out the MBR if MBR(msdos) partitioning. gpt has partition tables at both beginning & end of drive.

If just reformatting a drive, use gparted create your NTFS at the beginning of the drive. Then you can add Linux partitions but have to use Something Else or manual install to choose/change partitions to format & mount them. You could create the Linux partitions with Something Else but not the NTFS partition.

---

### Post by 777funk on 2014-06-03
Thanks Fred. As mentioned, I don't need to recover anything (since there wasn't anything important that isn't backed up) so much as to wipe the disk. Seems like the dd zeroing took a long time and I closed the terminal after about 24 hours unsure if it was working. But is there a quick and easy way to wipe the disk? Gparted, isn't allowing me to do anything since Windows touched the disk.

---

### Post by 777funk on 2014-06-03
**OH NO!** Now I've really got problems :( I got searching and found [this page]("http://fintastical.blogspot.com/2013/02/quick-wipe-of-hard-drive-using-linux.html") with the command:

```

sudo shred -v -z -n 1 /dev/sda

```

And I pasted it and hit enter (in a hurry to get to my work for the day), then quickly realized I didn't think enough to change 'sda' to the proper drive I was trying to wipe which is 'sdb'. 

The problem here is that sda is my linux installation. I caught it as it was working (maybe the first 5GB into the shred). But awe man... this is getting bigger than it should have been! It's a good thing I have my data backed up. At least my haste isn't killing the non recoverable.

Is there a way to repair the Ubuntu data I just destroyed? I'm running this install as we speak but only the programs I had open are still working.

---

### Post by sudodus on 2014-06-03
The very idea with ***shred*** is to make it impossible or at least extremely hard to recover (or steal) data. So what is overwritten is lost. You have a fair backup, so I doubt it is worth the effort to try to rescue data from the content (for example using ***PhotoRec***).

However, there are better and faster methods to wipe a drive; ***hdparm*** and ***DBAN***. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2124829"]
best way to wipe a drive[/URL]

-o-

1. Always ***backup*** your data before risky operations like editing partitions, wiping drives and installing new systems.

2. Always ***disconnect*** drives that should not be involved in risky operations (for example wiping drives). Boot from CD/DVD/USB.

---

### Post by 777funk on 2014-06-03
Thanks sudodus! Sorry I was a little unclear on the last post (#11). I *wanted *to wipe a drive (sd[COLOR=#0000ff]**[SIZE=5]b[/SIZE]**[/COLOR]), so that data is not something I have a problem with loosing (it's backed up and the data on the drive was damaged in Windows). 

What I am concerned about is that I accidentally left it as it was in the blog where I found it "**/dev/sd[SIZE=6][COLOR=#ff0000]a[/COLOR][/SIZE]**" after pasting and hastily hit Enter.
So now the first few Gigabytes of data on my Ubuntu partition are gone. No more Ubuntu for now. After the damage, it semi-worked for about 30 more minutes then eventually just folded up and crashed.

Is there a way to repair the OS I just damaged?

---

### Post by sudodus on 2014-06-03
If the operating system is overwritten by shred, I don't think so. Reinstall and put back your private files from your backup.

If there are files that you have not backup up, and they resided on the disk within what was overwritten, they are gone. The partition table is gone because it is in the very beginning of the drive. If there are files that you have not backup up, and they resided on the disk behind what was overwritten, the data are still there on the disk, and might be possible to recover with PhotoRec. But it is hard work.

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by 777funk on 2014-06-03
Thanks a lot for the help there! I'll see what I can find looking at the disk in a System Rescue. I didn't have much personal data on the Ubuntu OS partition fortunately. So that's good. Bummer on the reinstall but that's life! Thanks for the suggestions on HDPARM and DBAN. I'll check those out.

---

### Post by sudodus on 2014-06-03
Good luck :-)

---


---
title: "Recovering reformated partition"
date: 2008-04-17
forum: General Help
---

### Post by simoncifer on 2008-04-17
I have a Secure Digital card which was originally formated with FAT32 using Windows XP.  I put that SD card into a Palm PDA and mistakenly allowed it to reformat (to FAT16).  Now I am trying to recover the original FAT32 partition, and I am running into problem.

I have tried to use testdisk, in fact, following the procedure of [this wiki "Recovery of reformatted partition"]("http://www.cgsecurity.org/wiki/Data_Recovery_Examples#Recovery_of_reformated_partition").

Every step proceeds as written in the wiki, until the last step:
```
In Analyse, choose to rewrite the partition with the correct partition type.
```

When I am in "Analyse", it couldn't find any partition even after searching.  So I add a FAT32 partition.  The procedure continues and everything seems to be okay.  But I cannot mount the SD card to get the files.  When I plug the SD card into the reader, and try to mount it in KDE, a message pop up and says
```
mount: /dev/sdb1 can't read superblock
``` 
and when I check dmesg, it says the file system is set to read-only.  Here is the relevant part from dmesg:
```
[  292.162217] usb 5-1: new high speed USB device using ehci_hcd and address 3
[  292.300167] usb 5-1: configuration #1 chosen from 1 choice
[  292.426325] usbcore: registered new interface driver libusual
[  292.474242] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  292.474599] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  292.480749] Initializing USB Mass Storage driver...
[  292.481015] scsi4 : SCSI emulation for USB Mass Storage devices
[  292.481267] usb-storage: device found at 3
[  292.481272] usb-storage: waiting for device to settle before scanning
[  292.481623] usbcore: registered new interface driver usb-storage
[  292.481860] USB Mass Storage support registered.
[  297.470243] usb-storage: device scan complete
[  297.472476] scsi 4:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9407 PQ: 0 ANSI: 0
[  297.904871] sd 4:0:0:0: [sdb] 2012160 512-byte hardware sectors (1030 MB)
[  297.906126] sd 4:0:0:0: [sdb] Write Protect is off
[  297.906133] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  297.906138] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  297.908236] sd 4:0:0:0: [sdb] 2012160 512-byte hardware sectors (1030 MB)
[  297.909489] sd 4:0:0:0: [sdb] Write Protect is off
[  297.909495] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  297.909501] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  297.909507]  sdb: sdb1
[  297.910985] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  297.911062] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  301.362373] FAT: Filesystem panic (dev sdb1)
[  301.362383]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  301.362390]     File system has been set read-only

```

What can I do now to recover the files?  I mean I could see the list of files and directory when I was using the "Rebuild BS" function of testdisk.  And photorec doesn't recover any arbitrary files, only certain files with specific extension.

Any help will be much appreciated.  Thanks in advance.

- Simon

---

### Post by ryanhaigh on 2008-04-17
double post

---

### Post by ryanhaigh on 2008-04-17
Firstly I think you should use something like dd to make a copy of the disk in its current state. Then maybe try using xp to fix the fat partition (assuming its recognised by xp).

I used ADRC recovery tools to get some stuff back from a formatted memory stick once perhaps it will work for you, its for windows but is free.

---

### Post by Zorael on 2008-04-17
After losing the partition table on my main disk (stupid l0sedows malicious code), I used [Testdisk](http://en.wikipedia.org/wiki/Testdisk) from the official repositories, running off a Live CD. I'm not sure it's what you're looking for since you consciously reformatted, but it might just help.

[quote=Wikipedia]TestDisk queries the BIOS or the operating system in order to find the hard disks and their characteristics (LBA size and CHS geometry). TestDisk does a quick check of your disk's structure and compares it with the partition table for entry errors. If the table has entry errors, TestDisk can repair them.

However, it's up to the user to look over the list of possible partitions found by TestDisk and to select the one(s) which were being used just before the drive failed to boot or the partition(s) were lost. In some cases, especially after initiating a detailed search for lost partitions, TestDisk may show partition data which is simply from the remnants of a partition that had been deleted and overwritten long ago.

TestDisk has features for both novices and experts:
[list]
    [*] Recover deleted partition
    [*] Rebuild partition table
    [*] Rewrite Master boot record (MBR)
    [*] File Allocation Table, FAT[list]
          [*] FAT12 and FAT16 [list]
                [*] Find filesystem parameters to rewrite a valid boot sector
                [*] Use the two copies of the FAT to rewrite a coherent version[/list]
          [*] FAT32 [list]
                [*] Find filesystem parameters to rewrite a valid boot sector
                [*] Restore the boot sector using its backup
                [*] Use the two copies of the FAT to rewrite a coherent version[/list][/list]
    [*] NTFS [list]
          [*] Find filesystem parameters to rewrite a valid boot sector
          [*] Restore the boot sector using its backup
          [*] Restore the Master File Table (MFT) from its backup[/list]
    [*] Extended file systems, ext2 and ext3 [list]
          [*] Find backup superblock location to assist fsck[/list]
    [*] HFS+ [list]
          [*] Restore the boot sector using its backup[/list][/list]

For those who know little or nothing about data recovery techniques, TestDisk can be used to collect detailed information about a non-booting drive which can then be sent to a tech for further analysis. Those more familiar with such procedures should find TestDisk a handy tool in performing onsite recovery.[/quote]

---

### Post by simoncifer on 2008-04-17
> **ryanhaigh said:**
> Firstly I think you should use something like dd to make a copy of the disk in its current state. Then maybe try using xp to fix the fat partition (assuming its recognised by xp).

I used ADRC recovery tools to get some stuff back from a formatted memory stick once perhaps it will work for you, its for windows but is free.

Thanks for the suggestion, but I tried ADRC, and it did not work.  Basically, Windows XP is having problem with the memory card.  It assigned it a drive letter, but couldn't open it  (Windows Explorer stalled for a long time and then gave an error message).  The sad thing is that when I go to "Computer Management" under the "Administrative Tools", it said the partition on my memory card is "healthy".

I think last night when I was trying to fix it with testdisk, I screw up the partition table, with the wrong value of "head", "cylinder", etc.

- Simon

---

### Post by simoncifer on 2008-04-17
> **Zorael said:**
> After losing the partition table on my main disk (stupid l0sedows malicious code), I used [Testdisk](http://en.wikipedia.org/wiki/Testdisk) from the official repositories, running off a Live CD. I'm not sure it's what you're looking for since you consciously reformatted, but it might just help.

Thanks for your suggestion, but as I mentioned in my first post, I have tried to use testdisk last night, installed from the repositories.  

Sorry, I think my first post is too longer, so here is the summary of it:

1). Memory card with data on FAT32 partition.
2). Memory card was mistakenly formatted FAT16
3). Ran TestDisk (installed from repositiories)
4). With "RepairBS" under TestDisk, I can see the list of all my files.
5). "Analyse" under TestDisk could not find the old FAT32 partition.
6). Added a FAT32 partition under TestDisk to try to rebuild the partition.
7). Computer could not recognize this "rebuild" partition.

I think I have the wrong values for "sector", "head", and "cylinder" when I try to rebuild the partition.  Because I tried to use TestDisk 6.9 for Windows today (on my work computer) and the values for "sector", "head", and "cylinder" are all different than last night.

- Simon

---

### Post by bodhi.zazen on 2008-04-17
You may want to try photorec

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by simoncifer on 2008-04-17
> **bodhi.zazen said:**
> You may want to try photorec

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

Thanks.  I tried PhotoRec last night, installed from repositories.  It copied a bunch of files over to my hard drive.  But I couldn't find the files I want, just a bunch of random text files, picture files, etc.

I remembered I looked into the option for PhotoRec, to set the type of files I want to copy, but I couldn't find the type that I want.

I will try the newest version from the website, to see if there is anything changed.

- Simon

---

### Post by bodhi.zazen on 2008-04-17
Well, if that failed you are talking professional data recovery.

---

### Post by simoncifer on 2008-04-17
> **simoncifer said:**
> I will try the newest version from the website, to see if there is anything changed.

I just tried PhotoRec, and once again it copied a bunch of random files, not any specific files I want.

I also just tried TestDisk again, and I notice that with TestDisk version 6.9 for Windows, under the list of files it shows after repairing the boot sector ("RepairBS"), I can copy the files to some other place.

TestDisk from repositiories (version 6.6 I think) didn't have this function.

But the sad part is that a lot of the files didn't get copy in full.  What I mean is that some of the copies are only 4KB in size, but they are supposed to be MB in size. 

But not all the copies are only 4KB in size, the 3 files that I want seem to be copied to my hard drive in full (they are all ~50KB).

I will have to wait until I get home to check to see if the copy of those 3 files are okay.

Does anyone knows how to find out the correct values for "sector", "head" and "cylinder" for a partition (and basically the geometry of the disk)?  I think TestDisk could not detect the correct values.

- Simon

---

### Post by simoncifer on 2008-04-17
> **bodhi.zazen said:**
> Well, if that failed you are talking professional data recovery.

Ouch, I was under the impression that it was an easy fix: all I have to do is change the partition table back to its state as FAT32.

Of course, I am having a hard time right now because I don't know the correct values for "Sector", "Head", and "Cylinder".  Moreover TestDisk seems to be detecting the wrong values, but it did repair the boot sector and able to see the files.

---

### Post by simoncifer on 2008-04-18
> **simoncifer said:**
> But not all the copies are only 4KB in size, the 3 files that I want seem to be copied to my hard drive in full (they are all ~50KB).

Turns out I need 4 files, not 3, and those files should be 512KB instead.  So the copies generated by TestDisk version 6.9 did not work.

I tried Beta version of TestDisk, version 6.10, and it copied 512KB for all 4 files, but all 4 are corrupted, and had to be replaced.  So it didn't work neither. :(

I've made dd image of memory card, even before I ran TestDisk for the first time.  Right now I am trying all these different version of TestDisk on the dd image, but all result with 4 corrupted files.

Help.

- Simon

---


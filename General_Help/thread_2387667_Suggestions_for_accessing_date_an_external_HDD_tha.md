---
title: "Suggestions for accessing date an external HDD that won't mount?"
date: 2018-03-22
forum: General Help
---

### Post by drtombrown on 2018-03-22
Hi Everyone, I have an external WD Passport 1Tb that will not mount in Ubuntu. I am getting an i/o error and it appears that the file system has been corrupted. The drive still spins and there are no "death rattles" coming from the drive. Fortunately, I was able to successfully recover many of the files using testdisk. There are however many files that failed to copy over that I am hoping to recover perhaps through an alternative to testdisk. Anyone have suggestions on other apps or methods you could use to access the contents of a drive that won't mount (but still "works")??

Suggested so far:

GetDataBack = $79usd 

Anything a bit more economical?

---

### Post by rsteinmetz70112 on 2018-03-22
How did you copy the files you already recovered?

You might want to try:

[LIST]
[*]gddrescue - but it requires a drive of at least the same size as the original. It also might copy the problem you are having.
[*]rsync - may also work and is more flexible.
[/LIST]

Why won't the drive mount?
What errors are you getting when you try mounting for the command line?
Can you run fsck on the external drive?

---

### Post by drtombrown on 2018-03-22
> **rsteinmetz70112 said:**
> How did you copy the files you already recovered?

You might want to try:

[LIST]
[*]gddrescue - but it requires a drive of at least the same size as the original. It also might copy the problem you are having. 
[*]rsync - may also work and is more flexible. 
[/LIST]

Why won't the drive mount?
What errors are you getting when you try mounting for the command line?
Can you run fsck on the external drive?


Hi rsteinmetz70112,

Thanks for replying. Answers to your questions:
> 
Why won't the drive mount?

My pc lost power probably while the hdd was busy reading/writing. It appears the file system is corrupted? I am using 16.04. Here's the original error:
> 
Error mounting /dev/sdb1 at /media/[redacted]/My Passport1: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/[redacted]/My Passport1"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details

Note: I [redacted] my username in the message above. This is the original error message. Note that this message does not appear anymore after attempting to rebuild the bootsector and MFT in testdisk. The drive simply does not mount when plugged in (however is detected by testdisk).

I attempted to run chkdsk /f in a Windows environment but this fails simply b/c Windows cannot access the drive or detect/mount it (however it does show up in hardware manager).  

> How did you copy the files you already recovered?

I used testdisk to copy the files over to my pc. I believe the drill-down in testdisk is as follows:


[LIST=1]
[*] Select the drive 
[*]Select "Intel/PC partition" 
[*]Select "Analyse" 
[*]This report shows up in the next window:

> Disk /dev/sdd - 1000 GB / 931 GiB - CHS 121597 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

> 1 * Sys=72               13577 238 11 119521 238 60 1701990410                

 Bad relative sector.
  2 * Sys=74               45381  70  3 79242  34 29  543974724

 Bad relative sector.
  3 * NetWare 3.11+        10498  56 41 10498  56 40          0

 Bad relative sector.
 Only one partition must be bootable
 Space conflict between the following two partitions
  1 * Sys=72               13577 238 11 119521 238 60 1701990410 
[*]Select "Quick Search" 
[*]The partition is highlighted in green and  press "P" to list the files. 
[*]Copy & Paste selected to finals to destination 
[/LIST]

> What errors are you getting when you try mounting for the command line?

I have not attempted to 'force' mount the drive in command line. I lack the the proper knowledge depth to this without further instruction. 

> Can you run fsck on the external drive?

Here's the result of fsck on the external drive:

> Disk /dev/sdd: 931.5 GiB, 1000170586112 bytes, 1953458176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x69205244

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdd1        218129509 1920119918 1701990410 811.6G 72 unknown
/dev/sdd2        729050177 1273024900  543974724 259.4G 74 unknown
/dev/sdd3        168653938  168653938          0     0B 65 Novell Netware 386
/dev/sdd4       2692939776 2692991410      51635  25.2M  0 Empty

Partition table entries are not in disk order.

Note: I redacted the rest of the log report on the remaining drives.  Thanks for your help!

---

### Post by rsteinmetz70112 on 2018-03-27
Sorry for the late response.

I think your best bet is to repair the drive.

My suggestion is to boot into Windows using a Windows Install DVD and go to the Repair Console and fix the MBR ( if there is one) and then run chkdsk /f at least twice. 

Since it is "My Passport" you could also try the Western Digital tools. They may already be on the drive or you can download them from WD.

---

### Post by HermanAB on 2018-03-27
It is a NTFS file system?  Then you got to repair it with a Windows system, not Linux.

---


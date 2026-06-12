---
title: "GParted stuck on real resize"
date: 2012-11-02
forum: General Help
---

### Post by FleaBR on 2012-11-02
I am using the liveCD to shrink and resize my NTFS partition but it`s stuck on the real resize step for about 12 hours now, is it normal to take so long ?

It`s a 1TB hard-drive, it`s almost full, around 800GB used and 100GB free, I defragmented(with the MyDefrag tool) and ran a chckdsk before doing the resize. And the resize is being made at the beggining of the disk.

The disk seems to be completely idle, is there a way to check if something has gone wrong ?

I don`t know if I should bite the bullet and try to cancel it.

---

### Post by Cheesemill on 2012-11-02
If you click on 'Show Details' on the gparted progress windows you should see if the operation is still taking place, 12 hours sounds reasonable to me, especially with a resize operation on a partition of that size.

I really wouldn't cancel it, you're likely to end up with a corrupt partition if you do.

For future reference for operations like this I usually just delete the partition and create a new one, and then restore all the data from backup, it tends to be a lot quicker.

---

### Post by FleaBR on 2012-11-02
I clicked on the details but the only thing it shows is the commands it used for the resizing and shrinking.

---

### Post by oldfred on 2012-11-02
If you have 800MB in a 1TB drive your NTFS partition is full.

Windows wants about 30% free to work well. Starts to slow at 20% free and at 10% becomes about unusable.

Linux needs space also, and it hides 5% in the system partition just so you do not crash system. Generally 75 to 80% is full in Linux.

---

### Post by FleaBR on 2012-11-02
> **oldfred said:**
> If you have 800MB in a 1TB drive your NTFS partition is full.

Windows wants about 30% free to work well. Starts to slow at 20% free and at 10% becomes about unusable.

Linux needs space also, and it hides 5% in the system partition just so you do not crash system. Generally 75 to 80% is full in Linux.

I`m actually going to uninstall my current Windows installation, hence the resize for the new partition heh

---

### Post by FleaBR on 2012-11-02
Ok, so it finally ended but unfortunately it didn`t managed to resize it and showed this error, anyone knows what this is ?

> 

GParted 0.11.0 --enable-libparted-dmraid

Libparted 2.3
Move /dev/sda1 to the right and shrink it from 931.51 GiB to 881.21 GiB  15:24:31    ( ERROR )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 2,048
end: 1,953,523,711
size: 1,953,521,664 (931.51 GiB)
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:14    ( SUCCESS )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2012.1.15AR.1 (libntfs-3g)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 1000203088384 bytes (1000204 MB)
Current device size: 1000203091968 bytes (1000204 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 891169 MB (89.1%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 260707 MB 0
Multi-Record : 1000120 MB 171431
$MFTMirr : 500102 MB 1
Compressed : 329039 MB 31680
Sparse : 408753 MB 556463
Ordinary : 1000191 MB 130731
You might resize at 891168600064 bytes or 891169 MB (freeing 109035 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink file system  15:24:16    ( ERROR )
     	
run simulation  00:00:32    ( SUCCESS )
     	
ntfsresize -P --force --force /dev/sda1 -s 946191990783 --no-action
     	
ntfsresize v2012.1.15AR.1 (libntfs-3g)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 1000203088384 bytes (1000204 MB)
Current device size: 1000203091968 bytes (1000204 MB)
New volume size : 946191983104 bytes (946192 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 891169 MB (89.1%)
Collecting resizing constraints ...
Needed relocations : 7661053 (31380 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
real resize  15:23:44    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda1 -s 946191990783
     	
ntfsresize v2012.1.15AR.1 (libntfs-3g)
Failed to sync device /dev/sda1: Input/output error
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 1000203088384 bytes (1000204 MB)
Current device size: 1000203091968 bytes (1000204 MB)
New volume size : 946191983104 bytes (946192 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 891169 MB (89.1%)
Collecting resizing constraints ...
Needed relocations : 7661053 (31380 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
**ERROR(5): fsync: Input/output error**

========================================
Create Primary Partition #1 (ntfs, 50.30 GiB) on /dev/sda

========================================


---

### Post by oldfred on 2012-11-02
Have not seen that error. 

We normally suggest resizing Window from inside Windows using its MMC. Other partition tools may work, but better to use Windows tools for Windows.

You will need to run chkdsk from a Windows repairCD or USB.

---

### Post by FleaBR on 2012-11-03
> **oldfred said:**
> Have not seen that error. 

We normally suggest resizing Window from inside Windows using its MMC. Other partition tools may work, but better to use Windows tools for Windows.

You will need to run chkdsk from a Windows repairCD or USB.

Even though the issue is not even related to Ubuntu anymore you are helping me out, just wanted to thank you.

---


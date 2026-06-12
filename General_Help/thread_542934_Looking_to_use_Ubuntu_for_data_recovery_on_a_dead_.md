---
title: "Looking to use Ubuntu for data recovery on a dead XP NTFS hard drive"
date: 2007-09-04
forum: General Help
---

### Post by wattage on 2007-09-04
Hello everyone,

My friend recently came to me hopelessly upset because her XP machine crashed, taking all her family photos and other important files with it. I'm trying to rescue her stuff. I've done successful data recoveries before, but this one has me stumped. I hope you can lend a hand.

For all the details on what I've already tried, please skip down to 'THE DETAILS' below. Then come back. _I know this is a long post, but I want to be as detailed as I can._

I've tinkered around with Linux for a while, but I'm still an amateur at best. I'd like to use Linux (Ubuntu or Knoppix) to try mounting the NTFS image file or the damaged drive itself (if I have no other choice). Perhaps the files would then be immediately readable. Then I could copy the files to CD or a USB key. But I do not know how to properly use the MOUNT command for either purpose. Linux gurus, please help.

I'd like to exhaust all possible software methods of data recovery before surrendering her drive to an expensive professional data recovery center. I just feel like I'm so close to getting to her data. My gut says that the drive is still working and that the data should be recoverable. I've Googled, Wikipedia'ed, and searched this fine forum looking for answers.

I welcome your thoughts and instructions.

Thank you very much!!


**THE DETAILS**

Here's what I've done so far:
[LIST]
[*]I've disconnected the drive from her PC and connected it to a clean PC (with a powered IDE-to-USB adapter) that I use for data recovery. The recovery PC has two hard drives. Knoppix is loaded on the first one, and the second one is an empty drive with a single NTFS partition (used to catch the recovered data).
[*]Her damaged HD is correctly recognized by BIOS when I slaved it directly to my recovery PC for the initial diagnostic. And it is also recognized by XP, which I have loaded on a separate machine. So I'm confident that her data can be rescued.
[*]Next, with the damaged drive connected to the Knoppix PC, I ran GNU ddrescue to create an image of the entire damaged drive. After a few hours, ddrescue successfully finished creating the disk image.
[*]Then I removed the damaged drive and set it safely aside and connected the drive with the ddrescue image file to my XP machine. On that machine, I have the program Get Data Back for NTFS. The software is able to read the image file, but it only lists about 80 MB of the 70+ GB. And the files it lists are garbage or unreadable when I try to view them.
[*]Confused, I started over and created a new image file. This time I used ddr_help (which uses dd_rescue). It faithfully created an image, too. I got the same results as before from Get Data Back with this new image file. Only a small percentage of the files shows up.
[*]Tried running SpinRite 6.0 on the damaged drive. Failed. Received 'SpinRite Critical Error'. See SpinRite results at the end.
[*]Tried running TestDisk & PhotoRec 6.8 on the damaged drive. Failed. See TestDisk results at the end.
[*]I'm hesitant to run Get Data Back directly on the damaged drive. Everything I've read about data recovery says that doing so is a bad idea. The damaged drive should be used as little as possible. That brings me to where I am now. Back at square-one.
[/LIST]


**SpinRite 6.0 Results (DynaStat set to 1; Level set to 2 for Recover unreadable data)**
At the 'Select Drives and Partitions' screen, the damaged drive shows up as:
```
Drive 0  Add-On Controller
  Empty  <empty drive>    [this text on this line is in pink]

```
When I select 'Drive 0  Add-On Controller' line, the following message (in red) pops-up:
```
Some of this drive's items will be troublesome.
One or more of the partition items contained on this drive have some trouble which will prevent SpinRite from operating correctly. Rather than attempting to select every item at once, please individually highlight the specific items you wish to use so SpinRite may verify each one.
Press ESC to remove this message.

```
When I highlight the 'Empty  <empty drive>' line, the following message is displayed in the 'Partition / Item Details' section of the screen:
```
Unable to access this region
SpinRite is unable to access the entire range of sectors occupied by this region of the drive. The system's BIOS may be deliberately blocking access to this region if it is a "gap" at the end of the drive. In this case, SpinRite's inability to access is normal.

```
When I select the 'Empty  <empty drive>' line, the following message (in red) pops-up:
```
The item you are selecting may be troublesome
SpinRite has identified an unusual problem with the item you are selecting for operation. This drive may be offline or not ready. If possible, please make it ready before proceeding further. Press Enter to select this item for SpinRite to use, or press ESC if you prefer to cancel.
Press Enter to select or ESC to cancel.

```
Finally, when I try to start SpinRite, the following error appears:
```
SpinRite Critical Error
SpinRite's final verification of its ability to safely read and write to this drive has failed! Due to some hardware or firmware (BIOS) trouble, SpinRite's access to this drive could result in serious data corruption. Please see our web site for possible causes and cures. Update your BIOS?
Press ESC to abort further use of SpinRite.

```
Pressing ESC, exits SpinRite.



[B]TestDisk & PhotoRec 6.8 Results
[/B]At the TestDisk 'Select a media' screen, the damaged drive is correctly identified as:
Disk 80 - 82 GB / 76 GiB
I then select the following:
- Proceed
- [Intel] as the partition type
- [Analyse], receive 'Partition: Read error' message immediately.
- [Proceed]
- 'N' for 'search for partition created under Vista' question. Friend's PC was running XP.
- TestDisk begins searching for partitions. The 'Analyse cylinder' and 'Read error' counters are in unison, one-for-one.
- When finished, 'No partition found or selected for recovery'
- [Enter] to continue.
- 'No partitions found or selected for recovery'
- [Search!] to go deeper
- Still no partitions listed
- 'L' to load backup
- [Load] to load partition structure from backup...
- 'No partitions found or selected for recovery'
- [Quit]

---

### Post by zagloba on 2007-09-04
get live cd knoppix 
pop it in restart the comp. and u ready to save data

---

### Post by bigolyt on 2008-06-17
Ive booted to knoppix (which is AWESOME BTW) but I get an error when it tries to access the "BAD" HD.

Error - Konqueror

Could not mount device.

The reported error was:

mount: I could not determine the filesystem type, and none was specified.

The HD Spins and is recognized in the BIOS but nothing will allow me access to the files on it.

SOMEONE HELP PLEASE!! :)

---

### Post by Aearenda on 2008-06-17
On Ubuntu, if the drive had a readable partition table, I would expect to see it automounted. I suspect you are not going to be able to get the data, and that all ddrescue is doing is copying corrupt data.

To mount an NTFS partition the command is ```
sudo mount -t ntfs /dev/sdxy /mnt/folder
```Here 'sdxy' refers to the hardware name of the drive and the partition number (such as /dev/sdb1), and '/mnt/folder' is the name of a folder where you want to mount the drive, which must exist and be empty.

To discover whether Ubuntu can see a partition table do ```
sudo fdisk -l
```This will also tell you 'sdxy' for the mount, if it finds anything.

A thought - are you remembering to match the geometry and LBA settings from the original computer?

---

### Post by bigolyt on 2008-06-17
> **Aearenda said:**
> On Ubuntu, if the drive had a readable partition table, I would expect to see it automounted. I suspect you are not going to be able to get the data, and that all ddrescue is doing is copying corrupt data.

To mount an NTFS partition the command is ```
sudo mount -t ntfs /dev/sdxy /mnt/folder
```Here 'sdxy' refers to the hardware name of the drive and the partition number (such as /dev/sdb1), and '/mnt/folder' is the name of a folder where you want to mount the drive, which must exist and be empty.

To discover whether Ubuntu can see a partition table do ```
sudo fdisk -l
```This will also tell you 'sdxy' for the mount, if it finds anything.

A thought - are you remembering to match the geometry and LBA settings from the original computer?


When I run the sudo mount -t ntfs /dev/hdd /mnt/folder I get: 

Error reading bootsector: Input/output error
Failed to startup volume: Input/output error
Failed to mount '/dev/hdd': Input/output error
NTFS is inconsisten. Run chkdsk /f on Windows then reboot TWICE

When I run the sudo fdisk -l command it pulls the information from the primary HDD that I have hooked up.

The secondary HDD is the one I'm trying to get data off of. 

Primary is HDA1
Secondary is HDD

---

### Post by Aearenda on 2008-06-17
It should be /dev/hdd1.

Unless you have the drive geometry wrong, I think you need to give up on this one unless you can find someone with a detailed understanding of filesystems to help you reconstruct the drive layout. Ubuntu cannot find the partition table.

---

### Post by greco8523 on 2008-06-18
Sounds more like a hard drive problem than a software problem. TestDisk should be able to scan the disk without any problems, only if it's a physical problem with the disk that the errors you describe would come up. Does the drive make any strange noises? If there is important data on there then I would say you need a data recovery company. 

This might help you if you want to do any more tests: 
[http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html](http://www.datarecoveryadvice.org/data_recovery_linux_recover_utilities_tools.html)  

But if it seems like a physical problem maybe you should stop before it gets worst.

---


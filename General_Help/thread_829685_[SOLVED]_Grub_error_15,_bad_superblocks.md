---
title: "[SOLVED] Grub error 15, bad superblocks"
date: 2008-06-15
forum: General Help
---

### Post by nicom on 2008-06-15
My test machine runs a number of distros plus windows xp. I have recently been experimenting using my test machine to load Mythbuntu onto a usb harddrive to use on my PVR machine (currently Knoppmyth). After a recent install to the usb drive I am unable to start the test machine. I get an error
```
GRUB Loading stage1.5
GRUB loading, please wait...

Error 15
```
I have subsequently booted using the Ubuntu 7.10 live CD. I am unable to open the /boot/grub directory on sda3. If I look at the Nautilus file manager it marks the partitions as unreadable. GParted says the same. The problem looks somewhat similar to cedge's a couple of month's ago so I have been trying some of the diagnostics mentioned in his [thread]("http://ubuntuforums.org/showthread.php?t=752588").

fdisk -l gives the following: Note, hda1 does not have an os on it.
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ec118

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1027     8249346   83  Linux

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b357b35

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?           1        3188    25607578+   7  HPFS/NTFS
/dev/sda2            3189        5987    22482967+  83  Linux
/dev/sda3            8965        9729     6144862+  83  Linux
/dev/sda4            5988        8964    23912752+   5  Extended
/dev/sda5            8900        8964      522081   82  Linux swap / Solaris
/dev/sda6            5988        8899    23390577   83  Linux

Partition table entries are not in disk order
```
I am unable to correct with e2fsck as it gives:
```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -v -f /dev/sda2
e2fsck: No such file or directory while trying to open /dev/sda2
/dev/sda2: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```
dumpe2fs also did not work
```
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda3 | grep -i superblock
dumpe2fs 1.40.2 (12-Jul-2007)
dumpe2fs: No such file or directory while trying to open /dev/sda3
Couldn't find valid filesystem superblock.
```
I also tried smartmontools but the results do not mean much to me.
```
ubuntu@ubuntu:~$ sudo smartctl -H /dev/sda
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
```
and
```
ubuntu@ubuntu:~$ sudo smartctl --all /dev/sda
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST380817AS
Serial Number:    4MR0Q874
Firmware Version: 3.42
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Sun Jun 15 07:03:01 2008 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 ( 430) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  47) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   058   051   006    Pre-fail  Always       -       222726377
  3 Spin_Up_Time            0x0003   098   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       858
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   083   060   030    Pre-fail  Always       -       229915680
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3634
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1077
194 Temperature_Celsius     0x0022   031   042   000    Old_age   Always       -       31 (Lifetime Min/Max 0/13)
195 Hardware_ECC_Recovered  0x001a   058   051   000    Old_age   Always       -       222726377
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```
I also tried testdisk but it was not found with apt-get so no results there.
It looks to me like the disk is OK but that the file structure is corrupted in some way. Is someone able to help me so that I don't have to reinstall all the operating systems? Fortunately no important data (except daughter's game files -help!!).

---

### Post by nicom on 2008-06-16
I tried Super Grub Disk. When I select the "!LINUX! (>2) MANUAL" option it detects the grub menu as it used to appear. If I try to boot one of the operating systems (say Ubuntu) firstly I get an error because it can't find root at hda0,1. If I edit the grub command to the correct partition (hda1,1) the boot starts but freezes part way through. I loose video before I can see how far through it gets. If I try the Puppy os again I have to change the root location but again the boot process freezes and gives a message ```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(8,3)
``` 

Can anyone help me?

---

### Post by Herman on 2008-06-18
Which  partition has Ubuntu in it?
What's in the other Linux partitions?

---

### Post by nicom on 2008-06-18
The set up is like this

sda1   Windows XP
sda2   Ubuntu 7.10
sda3   Puppy 2.14
sda5   swap
sda6   Mythbuntu

The Puppy partition has Grub configured for the boot. The system worked fine until the second time I installed Mythbuntu onto an external drive.

Also I managed to get testdisk working last night by using SPM after switching on Universal repository. It was able to scan the disks and was able to locate backup copies of the superblocks. I tried restoring a backup copy using ```
/sbin/fsck.ext3 -b 24577 -B 1024 /dev/sda3
``` but with correct block numbers and blocksize. I got a similar error to e2fsck about unable to read superblock (not at my machine right now).

---

### Post by Herman on 2008-06-19
Well, I don't know...

Anything I can think of for a problem like this will be just guesswork. It seems very strange to me that  all of your file systems would be corrupted at once from installing an operating system on another hard disk. Maybe it's some kind of a disk geometry/partition table problem.

Try taking a look in your BIOS and check that your hard disks are properly set up and detected in your BIOS.
Have you made any hardware changes recently? (Added/removed a CD/DVD drive or a hard disk drive?)
Are your IDE hard drive cables and jumper settings all correct?

Do you have the Ubuntu Hardy Heron Desktop Live CD or Alternate CD? 
Maybe try resizing (shrinking) each of your partitions just a little bit with the partitioner in either of those CDs if you can and see if that helps.

You could try again with Super GRUB Disk, but press your 'c' key for [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and try to do this: [Direct (kernel) Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.")

Did you try detecting all your operating systems with TestDisk and writing a new partition table? [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html").

Regards, Herman :)

---

### Post by nicom on 2008-06-21
Herman,

Thanks for the advice, I have made some progress. After running Testdisk and rewriting the partition page I am now able to boot most of my systems (Ubuntu, Puppy and Windows) via super GRUB disk. Ubuntu and Windows worked from the menu but I need to edit the locations for Puppy. If I try to boot from the hard disk I now get a stage 2 error 22 which possibly indicates grub is pointing to the wrong partition. It doesn't seem to matter what I do the the menu.lst I still get the same mesasge. I even tried recreating a menu.lst using a utility provided with Puppy which came up with a very simple one, but I still get the same error message. 

It seems like it's reading a different menu.lst. Am I missing a step here to tell it which file to read?

By the way, the info on your website was incredibly helpful and has increased my understanding enormously, but obviously not quite enough.

---

### Post by Herman on 2008-06-21
:)  You probably have GRUB in Ubuntu and in Mythbuntu as well as Puppy Linux, so if you think you're getting the wrong GRUB menu you should be able to fix that by re-installing GRUB from whichever operating system you want.

If you want to boot with Ubuntu's GRUB, (using Ubuntu's GRUB menu, then install GRUB from Ubuntu to MBR.
```
sudo grub
``````
find /vmlinuz
```Assuming your Sata disk is your first hard disk, if it isn't then change 'root (hd0,1) to (hd1,1),```
root (hd0,1)
``````
setup (hd0)
``````
quit
```If you want to boot with Puppy's GRUB, (using Puppy's GRUB menu, then install GRUB from Puppy to MBR.
```
sudo grub
``````
find /vmlinuz
```Assuming your Sata disk is your first hard disk, if it isn't then change 'root (hd0,2) to (hd1,2),```
root (hd0,2)
``````
setup (hd0)
```
```
quit
```Or if you want your MBR to point to Mythbuntu and use Mythbuntu's GRUB and menu.lst, install Mythbuntu's GRUB to MBR, in much the same way, but replace 'root (hd0,2)', with 'root (hd0,5).

You will need to edit the /boot/grub/menu.lst from whichever operating system you installed GRUB to MBR from if you want to get rid of the GRUB Error 22 message.
Here is a link to my notes on GRUB Error 22 added after a copy of what it says in the GNU/GRUB manual about that error, [Grub error 22]("http://users.bigpond.net.au/hermanzone/p15.htm#22").

You'll soon get to know GRUB if you keep on trying. 

Regards, Herman :)

---

### Post by nicom on 2008-06-21
Success!!

I switched over to using the Ubuntu grub for the boot but I copied over the menu.lst from Puppy. I still had to modify the partition allocations in the file. It appears that the original cause of my problem was that Puppy and Mythbuntu exchanged partition numbers (Puppy went from sda3 to sda4 and Mythbuntu vice versa).

I did try resurrecting the grub on Puppy but kept running into problems. I could select root (hda1,4) but when I tried setup it said it could not find menu.lst. The method worked fine with the Ubuntu setup so I will leave it there.

Anyway Herman, thanks very much for your assistance and being so patient with me. As I said before I have learnt a lot.

---

### Post by Herman on 2008-06-22
:) Okay, good.

Just one more thing though,  
> I could select root [COLOR=Red]**(hda1,4)**[/COLOR] but when I tried setup it said it could not find menu.lst. It will help you to be aware that there are two ways we use for denominating partitions. 

In Linux terms, we might call a partition '/dev/hda4' or '/dev/sda3' or some thing like that.
The letter 's' is supposed to be for 'scsi', or 'sata'. 'h', if used, was for an IDE hard disk, but a lot of the time now, all hard drives ens up with the 's' letter regardless of what kind of hard disk they are. 
The first hard drive is 'a', the second will be 'b', third hard disk will be 'c', and so on.

In GRUB terms, a partition can be described as (hd1,4), that would mean the second hard disk (1), fifth partition (4), (because GRUB begins counting at the number 0).

As soon as you realize there are two differnet numbering systems going on here, you'll probably find things a lot easier for yourself. 
'(hda1.4)' doesn't mean anything to either GRUB or in Linux. 
I hope I'm being helpful, I mean to tell you this in a freindly way. :)

Here's a link that you might find handy for converting, [Quick Guide to GRUB's Numbering System]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")

Regards, Herman :)

---


---
title: "Recovering lost ext4 partition"
date: 2019-09-14
forum: General Help
---

### Post by Marco_Ros on 2019-09-14
Hello,
I have lost a Linux ext4 partition
I have not writen any data to the space in HDD left by it, so I'm sure that DATA can be recovered completely.

** I have tried TestDisk with the following results:**
```
 TestDisk 7.1, Data Recovery Utility, July 2019
Christophe GRENIER <grenier@cgsecurity.org>
https://www.cgsecurity.org

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121601 255 63
     Partition               Start        End    Size in sectors
 D Linux                14928 104 25 35945 125 20  337639424
 D Linux                14929 206 62 35946 227 57  337639424
 D Linux                14931  87  5 35948 107 63  337639424
 D Linux                14934 134 49 35951 155 44  337639424
 D Linux                14934 167 18 35951 188 13  337639424
 D Linux                14935  74 52 35952  95 47  337639424
 D Linux                14936  79 56 35953 100 51  337639424
------------- THIS IS THE LOST PARTITION -------------------
>D Linux                14937   1  1 35954 254 63  337654107
------------------------------------------------------------
 D Linux Swap           25479  53 47 25989 197 48    8202224
 D HPFS - NTFS          25989 198  1 47517 140 63  345843729
 D HPFS - NTFS          25989 198  2 121601  57 56 1535997952
 D Linux                25989 198  2 121601  57 56 1535997952 [U16]
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext4 blocksize=4096 Large_file Sparse_SB Recover, 172 GB / 161 Gi
```
LOST PARTITION DETAILS ACCORDING TO TestdDisk```

------------- THIS IS THE LOST PARTITION -------------------
>D Linux                14937   1  1 35954 254 63  337654107
------------------------------------------------------------
```
then, after executing comand fdisk:
```
sudo fdisk -lu
Disk /dev/loop0: 184.5 MiB, 193413120 bytes, 377760 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop1: 54.4 MiB, 57065472 bytes, 111456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop2: 42.8 MiB, 44879872 bytes, 87656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop3: 80.2 MiB, 84094976 bytes, 164248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop4: 54.4 MiB, 57069568 bytes, 111464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop5: 132 KiB, 135168 bytes, 264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop6: 89 MiB, 93327360 bytes, 182280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x000c597c

Disposit.  Inicio     Start      Final   Sectors   Size Id Tipo
/dev/sda1              2048     206847     204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2            206848   71682047   71475200  34.1G  7 HPFS/NTFS/exFAT
/dev/sda3         409323518  417525759    8202242   3.9G  5 Extendida
/dev/sda4  *      417525760 1953523711 1535997952 732.4G 83 Linux
/dev/sda5         409323520  417525759    8202240   3.9G 82 Linux swap / Solaris

Partition 3 does not start on physical sector boundary.
Partition table entries are not in disk order.
```
As can be seen, lost partition (161GB) does not appear in fdisk.

I tried to recover data using **PhotoRec**, stopping just passing the begining of next partition
[COLOR=#0000cd]/dev/sda3         409323518...[/COLOR]

but apparently most of the data (camera videos) cannot recovered correctly.

Knowing the initial al final sectors of my partition, how can I recover it?

Please, any advice will be of great help

---

### Post by TheFu on 2019-09-14
> **Marco_Ros said:**
> Hello,
I have lost a Linux ext4 partition
I have not writen any data to the space in HDD left by it, so I'm sure that DATA can be recovered completely.
...
Please, any advice will be of great help

Why did the corruption happen?  Does SMART show anything - perhaps failed sectors?  Getting data off failed sectors is very hard.  There is an **ubuntu data recovery** wiki google finds it.

If it was me, I'd get a new HDD and use ddrescue to mirror everything over to that new disk ASAP. Then I'd try to do all data recovery on that new HDD.

It won't help now, but having backups would make this problem a minor inconvenience.  Storage fails all the time and it never happens at a convenient time.

---

### Post by Marco_Ros on 2019-09-14
I had a windows 7 partition and sudenly, I was unable to boot using it, so, i tried to install it again, but after installing, It never booted, I even used Boot Repair, after all that, I destroyed the partition and created again, without succes, and after 2 essais, i was nos able to boot Linux.
the next day, I prepared an USB Ubuntu disk, only to discover my Linux partition passed away.

Lost partition was only 161GB and I have a partition that was just released that has a free space of >500GB, so, I don't think it is necessary to have a new disk, not have now the opportunity to do that

---

### Post by TheFu on 2019-09-14
What does the SMART data show?  Until that data is seen, it isn't possible to know if the disk issue is trivial or that disk is about to totally fail.

Boot Repair really shouldn't be used for about the last 3 yrs.  The complexities of all the different partition types and boot options are things it just cannot handle.  That reminds me, I need to update my boot-issues Visitor Message.  

Update: it didn't need updating. Here it is:

> Booting Issues
* Gather HDD Data with **Boot Repair**; don't actually run boot-repair, just gather data and post the URL.

---

### Post by Marco_Ros on 2019-09-14
Sorry, how can do accomplish SMART data show?

---

### Post by oldfred on 2019-09-14
Windows is known to rewrite MBR partition tables and "forget" to write  a Linux partition. It usually is sda5, the first logical partition and often leaves swap as only partition inside the extended & renumbers itswap to sda5.

In your case the space after sda2 and before start of extended partition is not shown as a partition. 
But is just cannot be added as you have used all 4 primary partitions. Was current sda4 really a logical partition before and perhaps extended partition started just after sda2?
Also boot flag must be on sda1. Grub does not use it, and Windows needs it on the Windows partition with boot files.

First backup current configuration, in case fixes make it worse. You can least can start over.
       backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 

Post PT_sda.txt in code tags.
Old versions of fdisk & sfdisk did not support gpt and had a simple structure. That could easier be edited. 
New version support newer gpt also, but then have a more complicated file structure to include GUIDs and extra info.

you may be able to use testdisk, but have to change some partitions from primary to logical to have it work. Test disk shows all the old structures, so if changed multiple times you may see several versions.
You need to make sure you only have 3 primary partitions ( or 2) as testdisk will put all the logical in one extended. And all logical partition must be adjacent, no primary partitions in the middle. So sda1 & sda2 are primary. Missing partition and current sda4 & sda5 can be logical. Missing could have been primary, but not sure it matters.

If testdisk does not work then we can look into restoring &  manually editing the backup partition table file.

I have not edited a sfdisk output & restored it. This is very old info where those very knowledgeable did that but it was with the old version of sfdisk.
      
 Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by TheFu on 2019-09-15
Instead of using sfdisk, parted will create "machine readable" output too, which can be imported later. Looks like there is nothing wrong sfdisk now (it didn't handle GPT disks correctly for a while), so that's fine too.

```
$ sudo parted -ml
```

As for SMART data, there are a few ways, but **smartctl** is the main tool.  Tell it to run the tests and wait for that to finish, then have it run the report. The two commands are:
```
sudo smartctl -t short /dev/sda
sudo smartctl -a  /dev/sda
```
Those are examples. Check the manpage for all the other options, for how to run longer tests, and how to do man other things.

---

### Post by Marco_Ros on 2019-09-19
Here are parted results:
```

sudo parted -ml
BYT;
/dev/sda:1000GB:scsi:512:4096:msdos:ATA TOSHIBA MQ01ABD1:;
1:1049kB:106MB:105MB:ntfs::;
2:106MB:36.7GB:36.6GB:ntfs::;
3:210GB:214GB:4200MB:::;
5:210GB:214GB:4200MB:linux-swap(v1)::;
4:214GB:1000GB:786GB:ext4::arranque;

```
comment: I cannot see lost partition

about smartctl response is:
```
command not found
```
mybe I need to install some package to accomplish this.
I've tried to install it using apt-get, but package is not available directly.

---

### Post by TheFu on 2019-09-19
Teaching to fish .... "*smartctl package name*" any search engine should provide the name.

---

### Post by Marco_Ros on 2019-09-19
you are right "mea culpa"
I submitted command, but don't see any results:
```
sudo smartctl -t short /dev/sda
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.15.0-62-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Thu Sep 19 16:52:22 2019

Use smartctl -X to abort test.
```
after 2 or more minutes, there is no display of results, does it save them in a log?
How will this test help me recover my lost partition?

---

### Post by TheFu on 2019-09-19
Re-read post #7 above. Please.

---

### Post by Marco_Ros on 2019-09-19
Result from [B]sudo smartctl -a  /dev/sda
[/B]
```
sudo smartctl -a  /dev/sda
[sudo] password for marcoa: 
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.15.0-62-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MQ01ABD...
Device Model:     TOSHIBA MQ01ABD100
Serial Number:    2361P302T
LU WWN Device Id: 5 000039 49218185d
Firmware Version: AX001A
User Capacity:    1 000 204 886 016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Thu Sep 19 21:06:13 2019 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  120) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 244) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1664
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       5185
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   054   054   000    Old_age   Always       -       18634
 10 Spin_Retry_Count        0x0033   203   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       4735
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       2199
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       258
193 Load_Cycle_Count        0x0032   096   096   000    Old_age   Always       -       49440
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       49 (Min/Max 12/75)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       1
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       0
222 Loaded_Hours            0x0032   057   057   000    Old_age   Always       -       17363
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       1
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       188
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 2
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 2 occurred at disk power-on lifetime: 18315 hours (763 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 30 b0 9e 61 e6  Error: UNC 48 sectors at LBA = 0x06619eb0 = 107060912

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 e0 9d 61 e0 00      00:15:27.848  READ DMA EXT
  25 00 00 e0 9c 61 e0 00      00:15:27.847  READ DMA EXT
  25 00 00 e0 9b 61 e0 00      00:15:27.756  READ DMA EXT
  25 00 00 e0 9a 61 e0 00      00:15:27.755  READ DMA EXT
  25 00 00 e0 99 61 e0 00      00:15:27.754  READ DMA EXT

Error 1 occurred at disk power-on lifetime: 17623 hours (734 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 41 b8 c7 c3 64 40  Error: ICRC, ABRT at LBA = 0x0064c3c7 = 6603719

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 18 c0 98 ba ca 40 00      00:03:09.518  READ FPDMA QUEUED
  60 00 b8 c8 c2 64 40 00      00:03:09.514  READ FPDMA QUEUED
  60 08 b0 70 94 0b 40 00      00:03:09.514  READ FPDMA QUEUED
  60 08 a8 a0 1f 1d 40 00      00:03:09.514  READ FPDMA QUEUED
  60 08 a0 50 c1 cb 40 00      00:03:09.514  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     18629         -
# 2  Short offline       Completed without error       00%     18624         -

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

---

### Post by TheFu on 2019-09-20
[https://kb.acronis.com/content/9181](https://kb.acronis.com/content/9181)
G-Sense_Error_Rate - vibration or dropping the HDD. That's a huge number. I've never seen one that high, but none of my HDDs even report that parameter.  Google will find explanations for the other values.

Old_Age and Pre-Fail seem to be the default for all storage.  10 yrs old or 1 month old, it doesn't matter.  I just checked about 20 HDDs here, they all say Old_Age and Pre-Fail. Some have been in use over 10 yrs.  I have excellent backups, so when they fail, it will be a minor inconvenience.  One have more than 10 relocated sectors. Any value over 10 means I need to replace it.  It is a 300GB HDD with almost 9 yrs of service.  I have 3-4 replacement disks of that age, but not active, around here. They were in a disk array
```
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       17
```

[https://en.wikipedia.org/wiki/S.M.A.R.T#Known_ATA_S.M.A.R.T._attributes](https://en.wikipedia.org/wiki/S.M.A.R.T#Known_ATA_S.M.A.R.T._attributes) has info on the different attributes.

---

### Post by oldfred on 2019-09-20
Did you back up partition table with sfdisk & with testdisk restore missing partition as L logical? 
As in post # 6?

---


---
title: "Partition has ceased to mount"
date: 2014-11-03
forum: General Help
---

### Post by Fsirett on 2014-11-03
I suspect the answer has already passed before my eyes, but I am not knowledgable enough to see it, therefore I bring this problem to you to keep me from doing something stupid...again!


I have a number of disks and this one has two partitions, one that is working just fine and this one that was fine this morning, but after a quick reboot, decided that it would not play. It has no programmes on it (that I know of!) but is used to store files. The files have not been added to for about a week or possibly a month. from other posts, I ran some diagnostics for you to have a look at .
First, the original error message:[INDENT]Error mounting /dev/sdb1 at /media/frank/Two: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/frank/Two"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/INDENT]

Next, I ran "dmesg | tail
```
$ dmesg | tail
[ 1471.972068]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1471.972077]         55 39 98 00 
[ 1471.972081] sd 4:0:0:0: [sdb]  
[ 1471.972085] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1471.972087] sd 4:0:0:0: [sdb] CDB: 
[ 1471.972089] Read(10): 28 00 55 39 98 00 00 00 08 00
[ 1471.972097] end_request: I/O error, dev sdb, sector 1429837824
[ 1471.972120] ata5: EH complete
[ 1471.972124] JBD2: IO error reading journal superblock
[ 1471.972130] EXT4-fs (sdb1): error loading journal

```

I am afraid that still means nothing to me.

I then ran over here and looked up all of the possible answers and I am not certain if any of them apply, but they did have loads of neat code for me to run and post here! 

Next I ran "$ sudo fdisk -l /dev/sdb"

```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0000bb53

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *   922064896  1945333759   511634432   83  Linux
/dev/sdb2            2048   922064895   461031424   83  Linux
/dev/sdb3      1945333760  1953523711     4094976   82  Linux swap / Solaris

Partition table entries are not in disk order

```

This has one thing that looks odd to me. Both partitions on this disk are for storing files only. There does not seem to me to be any reason for it to have anything to do with "boot." I first noticed that with GParted when I first began to look, but I am not certain that it should not be there, so leave the opinion to those who have reason to be believed.

I then ran "$ sudo fsck.ext4 -v /dev/sdb1":

```
e2fsck 1.42.9 (4-Feb-2014)
Error reading block 63471616 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? yes
Force rewrite<y>? no
Superblock has an invalid journal (inode 8).
Clear<y>? no
fsck.ext4: Illegal inode number while checking ext3 journal for Two

Two: ********** WARNING: Filesystem still has errors **********

```

I said yes to the first question, then I got cold feet. I am not certain what it was doing or if it was something that should be done, so I juat allowed it all to run as is.

Most of the information is probably useless, but I had fun seeing what the code came up with. Made me feel, for a few moments, like I really knew what I was doing!

In any case, what is the problem and how do I fix it?

If it is of any help, lately Firefox has been deciding to take frequent naps in the middle of things. Probably has nothing to do with this, but I just thought I might mention it in case it was something of interest.

Cheers

Frank Sirett

---

### Post by Bashing-om on 2014-11-03
Fsirett; Un Good !

1st suspect is the hard drive has died:
> 
Add. Sense: Unrecovered read error - auto reallocate failed

JBD2: IO error reading journal superblock
[ 1471.972130] EXT4-fs (sdb1): error loading journal

Superblock has an invalid journal (inode 8).

What results when a SMART test from the system disk utility is run ?

IF the over all assessment is "passed" then one might consider sparring off the superblock to a back up superblock ( the partition table !).
[http://ubuntuforums.org/showthread.php?t=2177756](http://ubuntuforums.org/showthread.php?t=2177756) (slickymaster)

Firefox indicator ? -> never hurts to run a file system check/repair on the operating system from a liveDVD environment, as the partition MUST not be mounted when these checks/repairs are conducted.
----------------
You can ignore the fact that there is a boot flag on sdb1 . It just means at some point a boot loader was installed to the 0th sector of the hard drive. As there is nothing in the system attempting to boot sdb1 it will have no effect.

just if it were me
[INDENT][INDENT][INDENT][INDENT]what I would do
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Fsirett on 2014-11-03
I shall try the SMART test and see what comes up. The drive is reasonably new, but well used, hence loads of drives. 

I shall post the results and adventures I now have. Never hurts to leave up more than enough. Folks like me need it.

---

### Post by Fsirett on 2014-11-03
I installed Gsmart and ran the smSMART tests for all of my drives. They all passed. For this particular drive, it gave me this:

```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-34-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Red (AF)
Device Model:     WDC WD10EFRX-68JCSN0
Serial Number:    WD-WCC1U2336454
LU WWN Device Id: 5 0014ee 25da69758
Firmware Version: 01.01A01
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Tue Nov  4 00:24:23 2014 CET
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
data collection:         (12960) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 148) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x30bd)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   168   167   051    Pre-fail  Always       -       95226
  3 Spin_Up_Time            0x0027   136   133   021    Pre-fail  Always       -       4158
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       100
  5 Reallocated_Sector_Ct   0x0033   165   165   140    Pre-fail  Always       -       1479
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   088   088   000    Old_age   Always       -       9174
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       99
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       45
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       54
194 Temperature_Celsius     0x0022   097   088   000    Old_age   Always       -       46
196 Reallocated_Event_Count 0x0032   001   001   000    Old_age   Always       -       1106
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       53
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
Warning: ATA error count 20692 inconsistent with error log pointer 3

ATA Error Count: 20692 (device log contains only the most recent five errors)
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

Error 20692 occurred at disk power-on lifetime: 9167 hours (381 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 00 09 80 e4  Error: UNC 8 sectors at LBA = 0x04800900 = 75499776

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 09 80 e4 0a  12d+16:17:26.326  READ DMA
  ca 00 08 00 08 00 e0 0a  12d+16:17:26.326  WRITE DMA
  ec 00 00 00 00 00 a0 0a  12d+16:17:26.029  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 0a  12d+16:17:25.719  SET FEATURES [Set transfer mode]

Error 20691 occurred at disk power-on lifetime: 9167 hours (381 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 00 09 40 e3  Error: UNC 8 sectors at LBA = 0x03400900 = 54528256

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 09 40 e3 0a  12d+16:17:22.561  READ DMA
  ec 00 00 00 00 00 a0 0a  12d+16:17:22.189  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 0a  12d+16:17:21.879  SET FEATURES [Set transfer mode]

Error 20690 occurred at disk power-on lifetime: 9167 hours (381 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 18 09 40 e3  Error: UNC 8 sectors at LBA = 0x03400918 = 54528280

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 18 09 40 e3 0a  12d+16:17:18.644  READ DMA
  ec 00 00 00 00 00 a0 0a  12d+16:17:18.273  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 0a  12d+16:17:18.156  SET FEATURES [Set transfer mode]

Error 20689 occurred at disk power-on lifetime: 9167 hours (381 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 10 09 40 e3  Error: UNC 8 sectors at LBA = 0x03400910 = 54528272

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 10 09 40 e3 0a  12d+16:17:15.016  READ DMA
  ec 00 00 00 00 00 a0 0a  12d+16:17:14.636  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 0a  12d+16:17:14.334  SET FEATURES [Set transfer mode]

Error 20688 occurred at disk power-on lifetime: 9167 hours (381 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 08 09 40 e3  Error: UNC 8 sectors at LBA = 0x03400908 = 54528264

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 09 40 e3 0a  12d+16:17:11.201  READ DMA
  ca 00 08 00 08 00 e0 0a  12d+16:17:11.200  WRITE DMA
  ec 00 00 00 00 00 a0 0a  12d+16:17:10.824  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 0a  12d+16:17:10.514  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       118         -

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

As I say, I am not absolutely certain what all this means. I do not like the "old age notes there, since the drive is only a year or two old, but it has been used as the system workhorse previously.This was the short test, I will be doing the longer test tonight and see what is happening with that. 

Axtually I see there was another item for the quick test. It might be the same information, but I submit it in any case:

```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-34-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Red (AF)
Device Model:     WDC WD10EFRX-68JCSN0
Serial Number:    WD-WCC1U2336454
LU WWN Device Id: 5 0014ee 25da69758
Firmware Version: 01.01A01
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Tue Nov  4 00:33:59 2014 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 113)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (12960) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 148) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x30bd)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   168   167   051    Pre-fail  Always       -       95226
  3 Spin_Up_Time            0x0027   136   133   021    Pre-fail  Always       -       4158
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       100
  5 Reallocated_Sector_Ct   0x0033   165   165   140    Pre-fail  Always       -       1480
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   088   088   000    Old_age   Always       -       9175
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       99
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       45
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       54
194 Temperature_Celsius     0x0022   097   088   000    Old_age   Always       -       46
196 Reallocated_Event_Count 0x0032   001   001   000    Old_age   Always       -       1107
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       53
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
Warning: ATA error count 20692 inconsistent with error log pointer 3

ATA Error Count: 20692 (device log contains only the most recent five errors)
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

Error 20692 occurred at disk power-on lifetime: 9167 hours (381 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 00 09 80 e4  Error: UNC 8 sectors at LBA = 0x04800900 = 75499776

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 09 80 e4 0a  12d+16:17:26.326  READ DMA
  ca 00 08 00 08 00 e0 0a  12d+16:17:26.326  WRITE DMA
  ec 00 00 00 00 00 a0 0a  12d+16:17:26.029  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 0a  12d+16:17:25.719  SET FEATURES [Set transfer mode]

Error 20691 occurred at disk power-on lifetime: 9167 hours (381 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 00 09 40 e3  Error: UNC 8 sectors at LBA = 0x03400900 = 54528256

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 00 09 40 e3 0a  12d+16:17:22.561  READ DMA
  ec 00 00 00 00 00 a0 0a  12d+16:17:22.189  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 0a  12d+16:17:21.879  SET FEATURES [Set transfer mode]

Error 20690 occurred at disk power-on lifetime: 9167 hours (381 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 18 09 40 e3  Error: UNC 8 sectors at LBA = 0x03400918 = 54528280

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 18 09 40 e3 0a  12d+16:17:18.644  READ DMA
  ec 00 00 00 00 00 a0 0a  12d+16:17:18.273  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 0a  12d+16:17:18.156  SET FEATURES [Set transfer mode]

Error 20689 occurred at disk power-on lifetime: 9167 hours (381 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 10 09 40 e3  Error: UNC 8 sectors at LBA = 0x03400910 = 54528272

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 10 09 40 e3 0a  12d+16:17:15.016  READ DMA
  ec 00 00 00 00 00 a0 0a  12d+16:17:14.636  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 0a  12d+16:17:14.334  SET FEATURES [Set transfer mode]

Error 20688 occurred at disk power-on lifetime: 9167 hours (381 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 08 09 40 e3  Error: UNC 8 sectors at LBA = 0x03400908 = 54528264

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 09 40 e3 0a  12d+16:17:11.201  READ DMA
  ca 00 08 00 08 00 e0 0a  12d+16:17:11.200  WRITE DMA
  ec 00 00 00 00 00 a0 0a  12d+16:17:10.824  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 0a  12d+16:17:10.514  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       10%      9175         432672
# 2  Short offline       Completed without error       00%       118         -

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

It looks a bit different to me, but then again, I know nearly nothing.

---

### Post by Bashing-om on 2014-11-04
Fsirett; Well, 

To be honest, I see it that the disk has failed:
> 
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       [color=red]53[/color]

In that all sectors that could be re-allocated as bad have been, and there are still 53 sectors that can not longer be re-allocated.
I could be wrong, others perhaps can advise better.

Can you access the partition from the liveDVD, pull your data off it ?(unlikely with a bad partition table ) -  Any time one messes about with partitions there is the chance of data loss.

Then see what results sparring off the super block and running another SMART test ? Maybe run the manufacture's tests on the hard drive ?

just does not look good
[INDENT][INDENT][INDENT][INDENT]for the home team
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by rbmorse on 2014-11-04
I agree with Bashing for the reason he stated. The drive is probably dead. 

You might be able to use Testdisk to recover the partition table for long enough to get data off that drive and onto another, but there's no guarantee of success.

---

### Post by Fsirett on 2014-11-05
I have been away for a bit so sorry for the delay. 

On reflection, I think this drive might have been active a few months ago when I was getting frequent mini blackouts. The power would disappear for a few microseconds some two or three times in five minutes or so. It fried an older drive and I installed a battery power helper, but if that was an active drive, it could be fried. A bad result, but it could have been much worse. 

Also on reflection, I tend to put my oldest drives to work hollding temporary data, as these are, so it might be my oldest drive. I am looking forward to using one of the high capacity drives (3T) that are said to be reliable and are now within striking distance of a reasonable price. I can also use a new computer, this one being about ten years or so old now and certainly showing its age. The USBs are beginning to go, the video has had to be supplemented and who knows what else. I think I am going to turn this one into an HTPC for my wife. I asume that with processor carrrying sound and video cards all the heavy lifting will be taken off of the aging processor.

In any case, I will try the Test disk first and then the Live Disk and I shall report the results here in order to help others who pass this way. I always find what is suggested, amd quite straightforward for those who know is sometimes best explained by a (near)  first time user in order to see tha problems from that perspective. 

On a completely other topic, I am assuming to do a system check repair from a live cd, I just boot up and then use the "fsck" command. Is that correct? I am going to upgrade to 14.10 in a few days in any case, but I would like this in my toolbox in any case

---

### Post by Fsirett on 2014-11-05
Nothing like going for broke with questions. I am just looking at the Testdisk downloads and I see three files. 

...dsc
...orig.tar.bz2
...debian.tar.gz

I looked at the .dsc file with Geany and I see it is a checksum file. Now I am confused. I assume the tar.b2 is a Bazaar file and I am familiar with .tar.gz, but not debian.tar.gz.

Burning this file to a disk does not look to be as straightforward as I might have hoped

Cheers again for all the help, I think I might have neglected to thank you guys for your kind offices before. A little rushed these days.

F.S.

---

### Post by coffeecat on 2014-11-05
> **Fsirett said:**
> Nothing like going for broke with questions. I am just looking at the Testdisk downloads and I see three files. 

...dsc
...orig.tar.bz2
...debian.tar.gz

Why are you doing that? Testdisk is an application that you can install in the live session. Simply boot up an Ubuntu live CD, make sure you are connected to the internet, open a terminal, and:

```
sudo apt-get update
sudo apt-get install testdisk
```

Or you can use the Software Centre.

You will lose testdisk when you shut down from the live session, but that doesn't matter because, hopefully, you will have already used it.

---

### Post by Fsirett on 2014-11-05
Cheers again! 

I had no idea, I just assumed it was a new disk. I shall install that in all my live disks from now on!

Cheers again!

FS

---

### Post by coffeecat on 2014-11-05
> **Fsirett said:**
> I shall install that in all my live disks from now on!

:?:

I really hope you won't have to be using testdisk that often! As I said, anything you install to a live session is lost when you power down, unless you have prepared a live USB with persistence. But that doesn't matter since the download for testdisk is only just over 300 kB and, hopefully, you will need it very infrequently.

---

### Post by Bashing-om on 2014-11-05
Fsirett; Hi !

Pleased you are taking to this like a duck to water. It is a learning process, after all.

As to 'fsck' you have the right of it; must be done with the file system (UN-)mounted - generally accomplished from a liveDVD(USB).

If in the event the partition table can not be rectified, what I have done several times is to zero out  that disk with the 'dd' tool . Then reformat the disk and place it back in service as a 'data' disk. I would never have full confidence in the integrity of that  disk again but it does serve the purpose of temporary usage.

Maybe this:
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/) <- written in a user-friendly way and introduces you to testdisk in a gentle way:

will prove of value to recover the partition(s).
[INDENT][INDENT]good luck
[INDENT][INDENT][INDENT]hard work yields greater dividends 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Fsirett on 2014-11-06
For my latest report:

From a live disk; I tried to load in Testdisk from the command line but it told me it did not exist. Fortunately you told me I could load from software centre so I went there and looked up testdisk which did not show up so I used another testing package that I do not see on the system now. I cannot remember the name of it. In any case, it seemed to do the trick. My poartition did come back, although it changed the owner and would not give me access. I decided to go ahead with the delayed upgrade to 14.10 and everything came back with that. Including changing ownership back to me. That was a happy result, but I am now looking at getting another remote drive to hold the data that I find most worthy. I doubt if many more drives will fail in the near future ( having a battery power supply backing me up) but I have learned my lesson (AGAIN!)

As for the system check to relieve my Firefox problem: under the live disk, I ran fsck and had a one line response, taking me a bit by surprise, but it seems to have done its job as things have improved on the Firefox front. The browser still takes "naps" (freezing and greying of the screen just for Firefox) but they tend to be shorter and rarer. I have no idea why this is happening, but the system is quite old ( about ten years) and I suppose parts are beginning to break down. the motherboard was never a first line player in any case.

Cheers again.

Frank Sirett

---

### Post by coffeecat on 2014-11-06
For future reference, because it seems you don't need testdisk now...

> **Fsirett said:**
> From a live disk; I tried to load in Testdisk from the command line but it told me it did not exist.

That's because you have to install it first. This has already been explained.

> **Fsirett said:**
>  Fortunately you told me I could load from software centre so I went there and looked up testdisk which did not show up

Most probably, Ubuntu Software Centre had not yet had a chance to update the package metadata, or rather the package index files, or perhaps you weren't connected to the internet. Software Centre needs to update the metadata before it can tell you about things that are in the repositories. You could have used the two apt-get commands I posted earlier instead. "apt-get update" loads the index files; "apt-get install" installs the specified package(s).

---

### Post by Fsirett on 2014-11-06
Cheers for all the help!

I once had some experience with fsck but it was not clear as to what it was doing and I was not going to risk jumping to conclusions (contusions?) with the mnemonics. Now I have a good idea of what it really is

As for using the disk as a data disk, I was already doing that. It is a policy of mine to move the operating systema nd the Home folders onto the newest disk (and on separate partitions) because I have all too much history with Windows and its tender mercies.

I have to say that Ubuntu has never let me down and, due to forums like this one, I can fix nearly everything that goes wrong. Something that I could not say about Windows and none of those I know who work with Apple can claim either; although the Apple zealots all claim that even their disasters are a part of the Apple goodness. 

For me, I want something that works most of the time and when it does not work can be made to work fairly quickly. I do not use whiz-bang computers because I do not make movies or play games. I also do not see why twenty year old software should cost more today than it did twenty years ago. Windows taught me all about the power of marketing there as well. The "New Improved Office" is often the same as the old Office with a bigger price tag on it, at least for my uses it was. 

I think Ubuntu is home now and I do not see me changing any time soon. Especially since my wife uses a Windows system and I get to monitor all of thelatest ads and popups there.

Cheers aain,

Frank Sirett

---


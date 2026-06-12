---
title: "How to fix a corrupt ext4 file system?"
date: 2013-03-02
forum: General Help
---

### Post by fljmayer on 2013-03-02
I have a RAID5 with 3 disks under Ubuntu 12.04. I created and maintain it with the Disk Utility, which seems to use mdadm underneath. Recently I ran out of space, so I  added another disk of the same size and grew the array. The additional disk is connected to a separate SATA controller (a JMB363 according to Disk Utility). Everything seemed fine for a while. Then the contents of one directory disappeared and files in other directories became inaccessible. When I list one of the corrupted directories, it shows nothing but the file names correctly; size, permissions, owner and modification date are missing. They all look like this when I do 'ls -l':

```
-????????? ? ? ? ?            ? THE_KILLER(1989).ISO
```

I did 'Check Array' with Disk Utility and also ran fsck, both reported no problems. I also ran extundelete, but it always crashed, seemingly before it could recover anything. There are now hundreds of files which I cannot even access because of permissions. Is there any way to repair the file system? What could have caused this?

Thanks, Felix

---

### Post by SaturnusDJ on 2013-03-04
I think this kind of behavior happens when somehow a disk isn't participation (correctly) in the array, while mdadm thinks it does.

We need more information. Post the output of the following.
If your array is still running (not a good idea):
```
cat /proc/mdstat
```
And:
```
mdadm --detail /dev/md0
```
(Or whatever you md device is.)


Disk information (array doesn't have to be running):
```
mdadm --examine /dev/sd*
```

Disk health:
```
smartctl -a /dev/sd[a-z]
```

---

### Post by fljmayer on 2013-03-09
Thanks for responding, I ran what you asked for (see below). This sounds like the addition of the 4th disk caused the problems and I need to rebuild the array.

```

$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md0 : active raid5 sdd1[0] sdc1[1] sdb1[3] sde[4]
      5860534272 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      bitmap: 0/15 pages [0KB], 65536KB chunk

unused devices: <none>

```

```

$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sun Aug  8 00:14:57 2010
     Raid Level : raid5
     Array Size : 5860534272 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 1953511424 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Sat Mar  9 22:24:50 2013
          State : active 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : :RAID
           UUID : 75a57ed9:795c3663:f15c1f90:3a2c26fd
         Events : 575667

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       1       8       33        1      active sync   /dev/sdc1
       3       8       17        2      active sync   /dev/sdb1
       4       8       64        3      active sync   /dev/sde

```

```

$ sudo mdadm --examine /dev/sd*
/dev/sda:
   MBR Magic : aa55
Partition[0] :    139212800 sectors at         2048 (type 83)
Partition[1] :      6008834 sectors at    139216894 (type 05)
mdadm: No md superblock detected on /dev/sda1.
/dev/sda2:
   MBR Magic : aa55
Partition[0] :      6008832 sectors at            2 (type 82)
mdadm: No md superblock detected on /dev/sda5.
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   3907024002 sectors at           63 (type fd)
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 75a57ed9:795c3663:f15c1f90:3a2c26fd
           Name : :RAID
  Creation Time : Sun Aug  8 00:14:57 2010
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907023730 (1863.01 GiB 2000.40 GB)
     Array Size : 5860534272 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907022848 (1863.01 GiB 2000.40 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 00010cf3:ce5ee599:feef2a7d:88a80bbe

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Mar  9 22:27:37 2013
       Checksum : add2bbfe - correct
         Events : 575667

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   3907024002 sectors at           63 (type fd)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 75a57ed9:795c3663:f15c1f90:3a2c26fd
           Name : :RAID
  Creation Time : Sun Aug  8 00:14:57 2010
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907023730 (1863.01 GiB 2000.40 GB)
     Array Size : 5860534272 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907022848 (1863.01 GiB 2000.40 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : eb03c7b3:a9b90cf0:90880a40:e775cdcf

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Mar  9 22:27:37 2013
       Checksum : 99567fb3 - correct
         Events : 575667

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   3907024002 sectors at           63 (type fd)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 75a57ed9:795c3663:f15c1f90:3a2c26fd
           Name : :RAID
  Creation Time : Sun Aug  8 00:14:57 2010
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907023730 (1863.01 GiB 2000.40 GB)
     Array Size : 5860534272 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907022848 (1863.01 GiB 2000.40 GB)
    Data Offset : 272 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fa954a9c:d5c12c8a:4536c4d6:be63adea

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Mar  9 22:27:37 2013
       Checksum : cd93b579 - correct
         Events : 575667

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 75a57ed9:795c3663:f15c1f90:3a2c26fd
           Name : :RAID
  Creation Time : Sun Aug  8 00:14:57 2010
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907023024 (1863.01 GiB 2000.40 GB)
     Array Size : 5860534272 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907022848 (1863.01 GiB 2000.40 GB)
    Data Offset : 6144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : bdc59f46:a51f641f:ff92eb06:decc1e21

Internal Bitmap : 8 sectors from superblock
    Update Time : Sat Mar  9 22:27:37 2013
       Checksum : 73b91d16 - correct
         Events : 575667

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing)

```

I am not adding disk health info because it would be a lot and the disks are fine according to Disk Utility.

---

### Post by SaturnusDJ on 2013-03-10
What can you say about the files. Are files, that you did not change after the grow, still normal?

I notice three things in outputs:
1. /dev/sde is added to the array as a complete drive, while the others are partitions of drives.
2. "Avail Dev Size" is 3907023730 for the first three, and 3907023024 for /dev/sde.
3. Data Offset also differs for /dev/sde.

Difference #2 comes from #1, both shouldn't be a problem. #3 I don't know for sure. I hope someone else know more about this.

---

### Post by fljmayer on 2013-03-10
Yes, I noticed the missing partition when everything was done. I had been following the instructions at [https://raid.wiki.kernel.org/index.php/Growing](https://raid.wiki.kernel.org/index.php/Growing) and everything seemed fine. Also I don't think I lost any more files on the RAID, not even new ones.

I am just wondering how this happened and if there are any other options but rebuilding the array from scratch.

---

### Post by SaturnusDJ on 2013-03-11
It would be wise if you do S.M.A.R.T. tests (smartctl -t), and post the relevant output here (smartctl -a).

---

### Post by fljmayer on 2013-03-11
Okay, here it is. You probably don't care about sda since it's the boot drive which is not part of the array.

```

$ sudo smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-38-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Raptor
Device Model:     WDC WD740GD-00FLA1
Serial Number:    WD-WMAKE1371343
Firmware Version: 27.08D27
User Capacity:    74,355,769,344 bytes [74.3 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Mar 11 23:03:07 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 1719) seconds.
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
                    No General Purpose Logging support.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  30) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x001f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   115   114   021    Pre-fail  Always       -       4791
  4 Start_Stop_Count        0x0032   100   100   040    Old_age   Always       -       505
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   044   044   000    Old_age   Always       -       41581
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0013   100   100   051    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       504
194 Temperature_Celsius     0x0022   123   112   000    Old_age   Always       -       27
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0012   200   200   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   200   179   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1024         -
# 2  Short offline       Completed without error       00%       393         -

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

```

$ sudo smartctl -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-38-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WMAZA0491473
LU WWN Device Id: 5 0014ee 0ad0d9e36
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Mar 11 23:06:57 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (38400) seconds.
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
recommended polling time:      ( 255) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   164   163   021    Pre-fail  Always       -       6758
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       127
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   072   072   000    Old_age   Always       -       20899
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       18
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       11
193 Load_Cycle_Count        0x0032   179   179   000    Old_age   Always       -       65747
194 Temperature_Celsius     0x0022   117   112   000    Old_age   Always       -       33
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       11
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   199   000    Old_age   Offline      -       59

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     17848         -

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

```

$ sudo smartctl -a /dev/sdc
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-38-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD20EARS-00S8B1
Serial Number:    WD-WCAVY2442056
LU WWN Device Id: 5 0014ee 259803335
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Mar 11 23:08:00 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (41580) seconds.
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
recommended polling time:      ( 255) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3031)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   145   144   021    Pre-fail  Always       -       9733
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       144
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   068   068   000    Old_age   Always       -       23509
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       32
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       18
193 Load_Cycle_Count        0x0032   166   166   000    Old_age   Always       -       102967
194 Temperature_Celsius     0x0022   117   110   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

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

```

$ sudo smartctl -a /dev/sdd
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-38-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD20EARS-00S8B1
Serial Number:    WD-WCAVY2875712
LU WWN Device Id: 5 0014ee 259803328
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Mar 11 23:08:45 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (40800) seconds.
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
recommended polling time:      ( 255) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3031)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   150   149   021    Pre-fail  Always       -       9491
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       157
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   068   068   000    Old_age   Always       -       23454
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       32
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       19
193 Load_Cycle_Count        0x0032   166   166   000    Old_age   Always       -       103230
194 Temperature_Celsius     0x0022   121   111   000    Old_age   Always       -       31
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

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

```

$ sudo smartctl -a /dev/sde
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-38-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARX-00PASB0
Serial Number:    WD-WMAZA5564029
LU WWN Device Id: 5 0014ee 05822d28a
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Mar 11 23:09:46 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (36600) seconds.
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
recommended polling time:      ( 255) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   167   166   021    Pre-fail  Always       -       6650
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       130
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   084   084   000    Old_age   Always       -       12402
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       14
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       8
193 Load_Cycle_Count        0x0032   192   192   000    Old_age   Always       -       24748
194 Temperature_Celsius     0x0022   123   115   000    Old_age   Always       -       27
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       30

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

---

### Post by SaturnusDJ on 2013-03-12
Okay, /dev/sdb has 11 Current Pending Sectors. That does mean 11 sectors are not readable at the time tried.
As soon as you will write to these sectors, they should be replaced with spares (or unlikely: found to be working again). When spares are being used, Reallocated Sector Count will increase, and Current Pending Sectors will lower.

Multi_Zone_Error_Rate for /dev/sdb and /dev/sde are non zero. It's a vague, generic attribute.

So maybe that's why data is gone missing.

But...it looks like the information is outdated, did you force tests?
If not, run this for the array drives:
```
smartctl -t short /dev/sdX
```
and
```
smartctl -t conveyance /dev/sdX
```
And report back with ```
smartctl -a /dev/sdX
``` again.

---

### Post by fljmayer on 2013-04-05
Sorry for the delay. How can you tell that data is outdated? How old is it? The failure happened in January.

I saw the pending sectors, but shouldn't a RAID5 protect me against that?

What bothers me also is that none of the file system tools find any problems, how can I fix the file system?

---

### Post by SaturnusDJ on 2013-04-05
'SMART Self-test log structure' should be filled with results from regular checks if you're serious about keeping your data safe.

That's why you need to run smartctl -t short/conveyance/long some times a week/month, or let smartd do that for you.


Currently I don't know very much about disk health vs raid. Fact is: if sectors from multiple disks are damaged, and your data is at those exact places, it's gone.

---


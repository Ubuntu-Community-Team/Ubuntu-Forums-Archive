---
title: "Bad magic number in super-block while opening filesystem"
date: 2014-10-09
forum: General Help
---

### Post by tobias6 on 2014-10-09
Hey guys,

A couple of days ago i had problems mounting the /sda5 partition of my harddrive on which ubuntu 13 is installed. As a result it wasnt possible to start ubuntu on my Laptop (DELL Vostro 3555).
Now im using an ubuntu live usb-stick (14.04.1 LTS) which  functions perfectly.
After reading some threads in this forum i tried
 
 [COLOR=#808080]sudo debugfs
 open /dev/sda5[/COLOR]

Using the cd command it was possible for me to navigate in the whole file system on /sda5 but not to open or to copy/move any of the data.
Now, some days later, using debugfs only delivers:
 
[COLOR=#808080]   /dev/sda5: Bad magic number in super-block while opening filesystem[/COLOR]

So it was not possible to navigate in the file system anymore. I have no idea of what could have caused this change. Also, when i try to open the /sda5 file system in the graphical interface it delivers an completely empty folder.Trying to boot without live stick delivers

 [COLOR=#808080]Error: unknown filesystem
 grub rescue>_[/COLOR]

Fourther investigation  suggested to try (via live stick):

  [COLOR=#808080]sudo apt-get install smartmontools
  sudo smartctl -t long /dev/sda5[/COLOR]

and after more than 150min of waiting:

[COLOR=#808080]  sudo smartctl -a /dev/sda5[/COLOR]

result:

```

smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 7200.5
Device Model:     ST9750420AS
Serial Number:    5WS1Z7M0
LU WWN Device Id: 5 000c50 03d1b6e9c
Firmware Version: 0001DEM1
User Capacity:    750,156,374,016 bytes [750 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Thu Oct  9 15:40:03 2014 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (    0) seconds.
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
recommended polling time:      ( 150) minutes.
Conveyance self-test routine
recommended polling time:      (   3) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   086   081   006    Pre-fail  Always       -       112597761
  3 Spin_Up_Time            0x0003   099   097   085    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   095   095   020    Old_age   Always       -       5647
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       4
  7 Seek_Error_Rate         0x000f   081   060   030    Pre-fail  Always       -       120245907
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       6318
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   020    Old_age   Always       -       2672
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       7509
188 Command_Timeout         0x0032   100   094   000    Old_age   Always       -       51540394046
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   045   032   045    Old_age   Always   FAILING_NOW 55 (16 172 55 49 0)
191 G-Sense_Error_Rate      0x0032   093   093   000    Old_age   Always       -       14066
192 Power-Off_Retract_Count 0x0032   098   098   000    Old_age   Always       -       4829
193 Load_Cycle_Count        0x0032   077   077   000    Old_age   Always       -       46157
194 Temperature_Celsius     0x0022   055   068   000    Old_age   Always       -       55 (0 8 0 0 0)
195 Hardware_ECC_Recovered  0x001a   116   099   000    Old_age   Always       -       112597761
197 Current_Pending_Sector  0x0012   095   092   000    Old_age   Always       -       120
198 Offline_Uncorrectable   0x0010   095   092   000    Old_age   Offline      -       120
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       151547921045326
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2672789226
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2027227678
254 Free_Fall_Sensor        0x0032   001   001   000    Old_age   Always       -       594

SMART Error Log Version: 1
ATA Error Count: 7578 (device log contains only the most recent five errors)
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

Error 7578 occurred at disk power-on lifetime: 6259 hours (260 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      02:21:40.555  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:40.538  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:40.537  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:40.537  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:40.537  READ FPDMA QUEUED

Error 7577 occurred at disk power-on lifetime: 6259 hours (260 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      02:21:37.724  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:37.724  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:37.724  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:37.724  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:37.724  READ FPDMA QUEUED

Error 7576 occurred at disk power-on lifetime: 6259 hours (260 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      02:21:35.107  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:35.107  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:35.107  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:35.106  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:35.106  READ FPDMA QUEUED

Error 7575 occurred at disk power-on lifetime: 6259 hours (260 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      02:21:32.489  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:32.488  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:32.488  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:32.488  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:32.488  READ FPDMA QUEUED

Error 7574 occurred at disk power-on lifetime: 6259 hours (260 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      02:21:29.872  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:29.871  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:29.871  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:29.871  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      02:21:29.870  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      6315         1179412200
# 2  Extended offline    Completed: read failure       90%      6311         1179412200
# 3  Extended offline    Completed: read failure       90%      6288         1179412200
# 4  Extended offline    Completed: read failure       90%      6287         1179412200
# 5  Short offline       Completed: read failure       90%      6237         1179412184
# 6  Short offline       Completed without error       00%      5607         -
# 7  Short offline       Completed without error       00%      4256         -
# 8  Short offline       Completed without error       00%      3264         -
# 9  Short offline       Completed without error       00%      3173         -
#10  Short offline       Completed without error       00%      2638         -
#11  Short offline       Completed without error       00%      2382         -
#12  Short offline       Completed without error       00%      1158         -
#13  Short offline       Completed without error       00%         5         -
#14  Short offline       Completed without error       00%         5         -
#15  Short offline       Completed without error       00%         0         -
#16  Short offline       Completed without error       00%         0         -

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

[COLOR=#808080]   sudo fdisk -l[/COLOR]
 delivered:
```

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x827ca83b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400   de  Dell Utility
/dev/sda2   *      206848    30926847    15360000    7  HPFS/NTFS/exFAT
/dev/sda3        30926848   906491914   437782533+   7  HPFS/NTFS/exFAT
/dev/sda4       906493950  1465147391   279326721    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       906493952  1453664255   273585152   83  Linux
/dev/sda6      1453666304  1465147391     5740544   82  Linux swap / Solaris

Disk /dev/sdb: 8021 MB, 8021606400 bytes
61 heads, 45 sectors/track, 5707 cylinders, total 15667200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9348aeba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2184    15667199     7832508    b  W95 FAT32

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1c4de958

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  1953520064   976760001    7  HPFS/NTFS/exFAT


```

This is the point on which the search function does not take me any fourther.
I hope you got any suggestions on how to go on and if it is possible to get anything of the data on /sda5 back.

Thanks for your help guys,

tobias6

---

### Post by tgalati4 on 2014-10-09
How much time did you spend playing round with the LiveUSB and snooping around the partition?

How much time did you spend copying important data to a blank USB stick?

You need to use the -w switch with *debug* to open the partition with write access.  But you need to first copy data onto another device for backup.

---


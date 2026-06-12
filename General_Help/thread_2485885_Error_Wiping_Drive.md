---
title: "Error Wiping Drive"
date: 2023-04-12
forum: General Help
---

### Post by zoomiest2 on 2023-04-12
I just bought a computer, second hand. It has a 3TB HDD. Is a slave drive at this point. I went to format it, but I get tons of errors. Is this HDD salvageable?

Here are a couple of outputs that I am getting. What does this mean?
[HTML]allan@OuterSpace:~$ sudo fsck /dev/sdc1
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
fsck.ext2: Input/output error while trying to open /dev/sdc1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
[/HTML]

[HTML]allan@OuterSpace:~$ sudo dd if=/dev/zero of=/dev/sdc1 bs=1M count=1
1+0 records in
1+0 records out
1048576 bytes (1.0 MB, 1.0 MiB) copied, 0.0028544 s, 367 MB/s
[/HTML]

While using Disks to wipe the drive: write zeros all over it:
[IMG]https://vulcanovo.com/errors/Hard-Drive-Formatting-Error.png[/IMG]

**When I open GParted, I get this error:**
[IMG]https://vulcanovo.com/errors/Hard-Drive-Formatting-Error2.png[/IMG]

It would be nice to save this 3TB drive. 
What else should I try?

Thank you in advance.

---

### Post by MAFoElffen on 2023-04-13
> **zoomiest2 said:**
> What else should I try?

```

lsblk
sudo apt-get update
sudo apt-get install -y smartmontools
sudo smartctl -t long /dev/sdX

```
Where "X" matches the drive found in the first command. Let it run. 

When finished, view the results with
```

smartctl -a /dev/sdX

```

---

### Post by zoomiest2 on 2023-04-14
Here is the output of that command... What do you think?

```
allan@OuterSpace:~$ sudo smartctl -a /dev/sdc1
[sudo] password for allan: 
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.19.0-38-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.14 (AF)
Device Model:     ST3000DM001-9YN166
Serial Number:    W1F0SR3J
LU WWN Device Id: 5 000c50 052a5aabd
Firmware Version: CC4B
User Capacity:    3,000,592,982,016 bytes [3.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Apr 14 08:38:53 2023 MDT

==> WARNING: A firmware update for this drive may be available,
see the following Seagate web pages:
http://knowledge.seagate.com/articles/en_US/FAQ/207931en
http://knowledge.seagate.com/articles/en_US/FAQ/223651en

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed without error or no self-test has ever been run.
Total time to complete Offline 
data collection:         (  575) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new command.
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
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 331) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x3085)    SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   084   084   006    Pre-fail  Always       -       211884001
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   097   097   020    Old_age   Always       -       3692
  5 Reallocated_Sector_Ct   0x0033   051   051   036    Pre-fail  Always       -       64736
  7 Seek_Error_Rate         0x000f   072   060   030    Pre-fail  Always       -       19851387
  9 Power_On_Hours          0x0032   062   062   000    Old_age   Always       -       33800
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   020    Old_age   Always       -       3631
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       2011
188 Command_Timeout         0x0032   100   028   000    Old_age   Always       -       88 146 154
189 High_Fly_Writes         0x003a   001   001   000    Old_age   Always       -       220
190 Airflow_Temperature_Cel 0x0022   074   066   045    Old_age   Always       -       26 (Min/Max 12/26)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       278
193 Load_Cycle_Count        0x0032   034   034   000    Old_age   Always       -       132878
194 Temperature_Celsius     0x0022   026   040   000    Old_age   Always       -       26 (0 3 0 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       15436h+14m+00.542s
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       115561117783992
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       46168589272763

SMART Error Log Version: 1
ATA Error Count: 463 (device log contains only the most recent five errors)
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

Error 463 occurred at disk power-on lifetime: 33783 hours (1407 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 91 00 32 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ea 00 00 00 00 00 a0 00      07:56:45.148  FLUSH CACHE EXT
  61 00 c0 ff ff ff 4f 00      07:56:45.142  WRITE FPDMA QUEUED
  61 00 40 ff ff ff 4f 00      07:56:45.141  WRITE FPDMA QUEUED
  ea 00 00 00 00 00 a0 00      07:56:44.549  FLUSH CACHE EXT
  61 00 c0 ff ff ff 4f 00      07:56:44.543  WRITE FPDMA QUEUED

Error 462 occurred at disk power-on lifetime: 33769 hours (1407 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 91 00 32 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ea 00 00 00 00 00 a0 00      11:18:46.941  FLUSH CACHE EXT
  61 00 c0 ff ff ff 4f 00      11:18:46.935  WRITE FPDMA QUEUED
  61 00 40 ff ff ff 4f 00      11:18:46.935  WRITE FPDMA QUEUED
  ea 00 00 00 00 00 a0 00      11:18:46.915  FLUSH CACHE EXT
  61 00 c0 ff ff ff 4f 00      11:18:46.909  WRITE FPDMA QUEUED

Error 461 occurred at disk power-on lifetime: 33759 hours (1406 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      00:22:20.744  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:22:20.554  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:22:20.546  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:22:20.537  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:22:20.534  READ FPDMA QUEUED

Error 460 occurred at disk power-on lifetime: 33759 hours (1406 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      00:22:12.517  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:22:12.509  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:22:11.077  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:22:11.073  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:22:11.069  READ FPDMA QUEUED

Error 459 occurred at disk power-on lifetime: 33759 hours (1406 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      00:22:08.119  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:22:08.112  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:22:08.109  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:22:08.103  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:22:08.096  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%     33785         4177528832

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

### Post by deadflowr on 2023-04-14
The drive is toast.
There are over 64,000 bad sectors.
That's a tell-tale sign of pending failure.

---


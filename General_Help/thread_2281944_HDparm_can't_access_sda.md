---
title: "HDparm can't access sda"
date: 2015-06-10
forum: General Help
---

### Post by ian83 on 2015-06-10
Trying to look at my HPA, forensics wiki says to type in HDparm -N /dev/sda and it spits out /dev/sda: Permission denied
this is on a boot USB of Lubuntu

---

### Post by bab1 on 2015-06-10
> **ian83 said:**
> Trying to look at my HPA, forensics wiki says to type in HDparm -N /dev/sda and it spits out /dev/sda: Permission denied
this is on a boot USB of Lubuntu

It has to be run by the root user.  In Ubuntu that would be ```
sudo hdparm -N /dev/sda
``` ... also the command is case sensitive.  HDparm is not the same as hdparm.

---

### Post by ian83 on 2015-06-11
That returns:
READ_NATIVE_MAX_ADDRESS_EXT failed: Input/output error

---

### Post by bab1 on 2015-06-11
> **ian83 said:**
> That returns:
READ_NATIVE_MAX_ADDRESS_EXT failed: Input/output error

So it appears that the hdparm command works correctly. You might just not like the output.  Is this disk a Windows partition; possibly  on a non hdparm aware disk?  Or maybe a disk in a RAID array?

The response just says that the disk did not respond to the hdparm command appropriately.   [**Here is an example**]("http://www.bleepingcomputer.com/forums/t/547270/cant-boot-from-windows-7-disk/page-2") of what I mean (not the subject heading).

[COLOR="#0000FF"]Edit:  Some examples.  What I get on a ssd [/COLOR]```
 max sectors   = 250069680/250069680, HPA is disabled
```

[COLOR="#0000FF"]What I get from a USB stick[/COLOR]```
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
SG_IO: bad/missing sense data, sb[]:  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 max sectors   = 0/1, HPA is enabled

```
[COLOR="#0000FF"]The point being that there are multiple responses that can be returned.

Sorry I only have non spinning disks on this host.  :-([/COLOR]

---

### Post by ian83 on 2015-06-11
This disc has windows 7 installed on its "640gb" (shows as 596gb in non binary) spinny disc hd installed in an HP laptop. From what I can tell my drive is locked by the bios, but all the passwords under security say clear. Do you think running DBAN and installing Ubuntu (I've  settled on xubuntu) would this have any effect, I would think likely not. I have a really old cracked copy of jetico total Wipeout that says my drive has "smart erase" enabled, not secure erase. I have found nothing about smart erase online, but lots about secure erase.
I mostly just want to erase the HPA.

---

### Post by bab1 on 2015-06-11
> **ian83 said:**
> This disc has windows 7 installed on its "640gb" (shows as 596gb in non binary) spinny disc hd installed in an HP laptop. From what I can tell my drive is locked by the bios, but all the passwords under security say clear. Do you think running DBAN and installing Ubuntu (I've  settled on xubuntu) would this have any effect, I would think likely not. I have a really old cracked copy of jetico total Wipeout that says my drive has "smart erase" enabled, not secure erase. I have found nothing about smart erase online, but lots about secure erase.
I mostly just want to erase the HPA.

I personally have no experience with that type of thing.  I run only Linux on my day to day hosts (servers, workstations and laptops).  I was answering your hdparm question.

I would post your installation and HDD problems in a new thread under the General forum or the  Installation & Upgrades forum of this site.

---

### Post by ian83 on 2015-06-14
I manage to come up with this, do you see any reason why I wouldnt be able to access HPA?

xubuntu@xubuntu:~$ sudo smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.16.0-30-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MK..65GSX
Device Model:     TOSHIBA MK6465GSX
Serial Number:    31UYB6TDB
LU WWN Device Id: 5 000039 32a208f60
Firmware Version: GJ002C
User Capacity:    640,135,028,736 bytes [640 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Sun Jun 14 12:34:30 2015 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

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
capabilities:              (0x51) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
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
recommended polling time:      ( 166) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0007   100   100   050    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   100   100   002    Pre-fail  Always       -       1951
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       2578
  5 Reallocated_Sector_Ct   0x0033   099   099   010    Pre-fail  Always       -       40
  7 Seek_Error_Rate         0x000f   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   035   035   000    Old_age   Always       -       26314
 10 Spin_Retry_Count        0x0013   151   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       2553
183 Runtime_Bad_Block       0x0022   100   100   001    Old_age   Always       -       6
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
185 Unknown_Attribute       0x0032   100   100   001    Old_age   Always       -       65535
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       1055
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       16
189 High_Fly_Writes         0x003a   100   100   001    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   064   033   045    Old_age   Always   In_the_past 36 (Min/Max 36/37)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       337
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       9175180
193 Load_Cycle_Count        0x0032   060   060   000    Old_age   Always       -       409284
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       13
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       1

SMART Error Log Version: 1
ATA Error Count: 1162 (device log contains only the most recent five errors)
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

Error 1162 occurred at disk power-on lifetime: 26146 hours (1089 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 12 66 37 0a 60  Error: UNC at LBA = 0x000a3766 = 669542

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 80 40 f0 b7 23 40 00      00:10:11.949  READ FPDMA QUEUED
  60 20 08 60 11 55 40 00      00:10:11.935  READ FPDMA QUEUED
  60 08 88 50 2a 57 40 00      00:10:11.871  READ FPDMA QUEUED
  61 08 50 88 dd b6 40 00      00:10:11.871  WRITE FPDMA QUEUED
  61 02 48 b0 42 cf 40 00      00:10:11.871  WRITE FPDMA QUEUED

Error 1161 occurred at disk power-on lifetime: 26146 hours (1089 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 42 66 37 0a 60  Error: UNC at LBA = 0x000a3766 = 669542

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 40 60 80 eb 08 40 00      00:10:07.821  READ FPDMA QUEUED
  60 80 60 f0 b6 23 40 00      00:10:07.815  READ FPDMA QUEUED
  60 80 60 70 b6 23 40 00      00:10:07.814  READ FPDMA QUEUED
  60 08 58 b0 0e 65 40 00      00:10:07.811  READ FPDMA QUEUED
  60 08 30 70 da 87 40 00      00:10:07.803  READ FPDMA QUEUED

Error 1160 occurred at disk power-on lifetime: 26146 hours (1089 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 42 66 37 0a 60  Error: WP at LBA = 0x000a3766 = 669542

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 28 b0 e0 6a 03 40 00      00:10:03.578  WRITE FPDMA QUEUED
  61 40 a8 f0 fd 2a 40 00      00:10:03.578  WRITE FPDMA QUEUED
  61 08 a0 f8 92 5e 40 00      00:10:03.578  WRITE FPDMA QUEUED
  61 38 98 10 6b 03 40 00      00:10:03.577  WRITE FPDMA QUEUED
  61 08 90 00 93 5e 40 00      00:10:03.577  WRITE FPDMA QUEUED

Error 1159 occurred at disk power-on lifetime: 26146 hours (1089 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 2a 66 37 0a 60  Error: UNC at LBA = 0x000a3766 = 669542

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 3e 10 10 b0 d0 40 00      00:09:59.416  READ FPDMA QUEUED
  61 08 10 40 e1 3e 40 00      00:09:59.406  WRITE FPDMA QUEUED
  61 08 78 38 e1 3e 40 00      00:09:59.360  WRITE FPDMA QUEUED
  60 08 38 50 2a 57 40 00      00:09:59.360  READ FPDMA QUEUED
  60 80 30 70 b5 23 40 00      00:09:59.360  READ FPDMA QUEUED

Error 1158 occurred at disk power-on lifetime: 26146 hours (1089 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 c2 66 37 0a 60  Error: WP at LBA = 0x000a3766 = 669542

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 08 58 30 e1 3e 40 00      00:09:55.226  WRITE FPDMA QUEUED
  61 08 50 28 e1 3e 40 00      00:09:55.194  WRITE FPDMA QUEUED
  61 08 48 f0 92 5e 40 00      00:09:55.166  WRITE FPDMA QUEUED
  61 00 40 60 85 5b 40 00      00:09:55.140  WRITE FPDMA QUEUED
  61 08 38 00 93 5e 40 00      00:09:55.139  WRITE FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        23         -
# 2  Short offline       Completed without error       00%        23         -
# 3  Short offline       Completed without error       00%        22         -
# 4  Short offline       Completed without error       00%        22         -
# 5  Short offline       Completed without error       00%        22         -
# 6  Short offline       Completed without error       00%        22         -
# 7  Short offline       Completed without error       00%        21         -
# 8  Short offline       Completed without error       00%        21         -

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

xubuntu@xubuntu:~$

---

### Post by bab1 on 2015-06-14
> **ian83 said:**
> I manage to come up with this, do you see any reason why I wouldnt be able to access HPA?

```
xubuntu@xubuntu:~$ sudo smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.16.0-30-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MK..65GSX
Device Model:     TOSHIBA MK6465GSX
Serial Number:    31UYB6TDB
LU WWN Device Id: 5 000039 32a208f60
Firmware Version: GJ002C
User Capacity:    640,135,028,736 bytes [640 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Sun Jun 14 12:34:30 2015 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

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
capabilities:              (0x51) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
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
recommended polling time:      ( 166) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0007   100   100   050    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   100   100   002    Pre-fail  Always       -       1951
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       2578
  5 Reallocated_Sector_Ct   0x0033   099   099   010    Pre-fail  Always       -       40
  7 Seek_Error_Rate         0x000f   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   035   035   000    Old_age   Always       -       26314
 10 Spin_Retry_Count        0x0013   151   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       2553
183 Runtime_Bad_Block       0x0022   100   100   001    Old_age   Always       -       6
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
185 Unknown_Attribute       0x0032   100   100   001    Old_age   Always       -       65535
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       1055
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       16
189 High_Fly_Writes         0x003a   100   100   001    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   064   033   045    Old_age   Always   In_the_past 36 (Min/Max 36/37)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       337
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       9175180
193 Load_Cycle_Count        0x0032   060   060   000    Old_age   Always       -       409284
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       13
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       1

SMART Error Log Version: 1
ATA Error Count: 1162 (device log contains only the most recent five errors)
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

Error 1162 occurred at disk power-on lifetime: 26146 hours (1089 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 12 66 37 0a 60  Error: UNC at LBA = 0x000a3766 = 669542

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 80 40 f0 b7 23 40 00      00:10:11.949  READ FPDMA QUEUED
  60 20 08 60 11 55 40 00      00:10:11.935  READ FPDMA QUEUED
  60 08 88 50 2a 57 40 00      00:10:11.871  READ FPDMA QUEUED
  61 08 50 88 dd b6 40 00      00:10:11.871  WRITE FPDMA QUEUED
  61 02 48 b0 42 cf 40 00      00:10:11.871  WRITE FPDMA QUEUED

Error 1161 occurred at disk power-on lifetime: 26146 hours (1089 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 42 66 37 0a 60  Error: UNC at LBA = 0x000a3766 = 669542

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 40 60 80 eb 08 40 00      00:10:07.821  READ FPDMA QUEUED
  60 80 60 f0 b6 23 40 00      00:10:07.815  READ FPDMA QUEUED
  60 80 60 70 b6 23 40 00      00:10:07.814  READ FPDMA QUEUED
  60 08 58 b0 0e 65 40 00      00:10:07.811  READ FPDMA QUEUED
  60 08 30 70 da 87 40 00      00:10:07.803  READ FPDMA QUEUED

Error 1160 occurred at disk power-on lifetime: 26146 hours (1089 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 42 66 37 0a 60  Error: WP at LBA = 0x000a3766 = 669542

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 28 b0 e0 6a 03 40 00      00:10:03.578  WRITE FPDMA QUEUED
  61 40 a8 f0 fd 2a 40 00      00:10:03.578  WRITE FPDMA QUEUED
  61 08 a0 f8 92 5e 40 00      00:10:03.578  WRITE FPDMA QUEUED
  61 38 98 10 6b 03 40 00      00:10:03.577  WRITE FPDMA QUEUED
  61 08 90 00 93 5e 40 00      00:10:03.577  WRITE FPDMA QUEUED

Error 1159 occurred at disk power-on lifetime: 26146 hours (1089 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 2a 66 37 0a 60  Error: UNC at LBA = 0x000a3766 = 669542

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 3e 10 10 b0 d0 40 00      00:09:59.416  READ FPDMA QUEUED
  61 08 10 40 e1 3e 40 00      00:09:59.406  WRITE FPDMA QUEUED
  61 08 78 38 e1 3e 40 00      00:09:59.360  WRITE FPDMA QUEUED
  60 08 38 50 2a 57 40 00      00:09:59.360  READ FPDMA QUEUED
  60 80 30 70 b5 23 40 00      00:09:59.360  READ FPDMA QUEUED

Error 1158 occurred at disk power-on lifetime: 26146 hours (1089 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 c2 66 37 0a 60  Error: WP at LBA = 0x000a3766 = 669542

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 08 58 30 e1 3e 40 00      00:09:55.226  WRITE FPDMA QUEUED
  61 08 50 28 e1 3e 40 00      00:09:55.194  WRITE FPDMA QUEUED
  61 08 48 f0 92 5e 40 00      00:09:55.166  WRITE FPDMA QUEUED
  61 00 40 60 85 5b 40 00      00:09:55.140  WRITE FPDMA QUEUED
  61 08 38 00 93 5e 40 00      00:09:55.139  WRITE FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%        23         -
# 2  Short offline       Completed without error       00%        23         -
# 3  Short offline       Completed without error       00%        22         -
# 4  Short offline       Completed without error       00%        22         -
# 5  Short offline       Completed without error       00%        22         -
# 6  Short offline       Completed without error       00%        22         -
# 7  Short offline       Completed without error       00%        21         -
# 8  Short offline       Completed without error       00%        21         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.h

xubuntu@xubuntu:~$
```

A couple of thoughts here.  Always wrap the text output in [noparse]```
 
```[/noparse] blocks.  Click on the [SIZE=6]**#**[/SIZE] icon and paste the text inside of the code blocks.  Nothing in the text above mentions HPA or DCO,   I wouldn't have any idea about working with HPA/DCO , but I can read and I know how to search using Google.  So here is [**what I have found**]("http://superuser.com/questions/642637/harddrive-wipe-out-hidden-areas-like-hpa-and-dco-also-after-malware-infectio").  Does it work?  I don't know if it does or not.

---


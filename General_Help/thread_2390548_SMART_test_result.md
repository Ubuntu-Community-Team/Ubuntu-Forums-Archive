---
title: "SMART test result"
date: 2018-04-30
forum: General Help
---

### Post by monkeybrain20122 on 2018-04-30
I ran SMART extended self test on my hd using the disks utility, it reported that overall assessment failed, but all the individual assessments are OK. See attached.

so I tried the command line 

```
sudo smartctl -d ata -a /dev/sda > ~/Downloads/smart-results.txt
```

```
The result is
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-20-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA THNSNS256GMCP
Serial Number:    X2HS11R4T2HY
LU WWN Device Id: 0 000000 000000000
Firmware Version: TA4ABBF0
User Capacity:    256,060,514,304 bytes [256 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      < 1.8 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS, ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Mon Apr 30 01:22:06 2018 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
**SMART overall-health self-assessment test result: PASSED**

General SMART Values:
Offline data collection status:  (0x06)    Offline data collection activity
                    was aborted by the device with a fatal error.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 113)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         ( 2097) seconds.
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
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  48) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x0001)    SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000a   100   100   000    Old_age   Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   100   100   050    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0012   100   100   000    Old_age   Always       -       0
  7 Unknown_SSD_Attribute   0x000b   100   100   050    Pre-fail  Always       -       0
  8 Unknown_SSD_Attribute   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       2449
 10 Unknown_SSD_Attribute   0x0013   100   100   050    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0012   093   093   000    Old_age   Always       -       7407
167 Unknown_Attribute       0x0022   100   100   000    Old_age   Always       -       0
168 Unknown_Attribute       0x0012   200   200   000    Old_age   Always       -       0
169 Unknown_Attribute       0x0013   120   120   010    Pre-fail  Always       -       328339038
170 Unknown_Attribute       0x0013   100   100   010    Pre-fail  Always       -       0
173 Unknown_Attribute       0x0013   184   184   100    Pre-fail  Always       -       661457797355
175 Program_Fail_Count_Chip 0x0012   100   100   000    Old_age   Always       -       0
177 Wear_Leveling_Count     0x0000   000   000   000    Old_age   Offline      -       14
181 Program_Fail_Cnt_Total  0x0032   000   000   000    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   000   000   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0012   000   000   000    Old_age   Always       -       3062
194 Temperature_Celsius     0x0022   100   009   000    Old_age   Always       -       0 (Min/Max 0/91)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x0022   200   200   000    Old_age   Always       -       0
233 Media_Wearout_Indicator 0x0000   000   000   000    Old_age   Offline      -       48384
240 Unknown_SSD_Attribute   0x0013   100   100   050    Pre-fail  Always       -       0
241 Total_LBAs_Written      0x0032   000   000   000    Old_age   Always       -       14831
242 Total_LBAs_Read         0x0032   000   000   000    Old_age   Always       -       24765

SMART Error Log not supported

SMART Self-test Log not supported

SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
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

So it seems that it passed the test (a different test?)

Can anyone explain what happened? Is the hd OK?

Thanks.

---

### Post by pqwoerituytrueiwoq on 2018-04-30
SMART is less than reliable that SSD is not that old i prefer [gsmartcontrol]("apt:gsmartcontrol") for doing a self test

rule of thumb is backup anything and everything

---

### Post by monkeybrain20122 on 2018-04-30
> **pqwoerituytrueiwoq said:**
> SMART is less than reliable that SSD is not that old i prefer [gsmartcontrol]("apt:gsmartcontrol") for doing a self test

rule of thumb is backup anything and everything

Isn't it just a gui for smartmontools with some options enabled? Because the output log look kind of the same. Does it look good or bad?  Thanks.

```
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-20-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA THNSNS256GMCP
Serial Number:    X2HS11R4T2HY
LU WWN Device Id: 0 000000 000000000
Firmware Version: TA4ABBF0
User Capacity:    256,060,514,304 bytes [256 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      < 1.8 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS, ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Mon Apr 30 04:49:51 2018 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
AAM feature is:   Unavailable
APM level is:     254 (maximum performance)
Rd look-ahead is: Disabled
Write cache is:   Enabled
ATA Security is:  Disabled, frozen [SEC2]

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x06)    Offline data collection activity
                    was aborted by the device with a fatal error.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 113)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         ( 2097) seconds.
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
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  48) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x0001)    SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     -O-R--   100   100   000    -    0
  2 Throughput_Performance  P-S---   100   100   050    -    0
  3 Spin_Up_Time            POS---   100   100   050    -    0
  5 Reallocated_Sector_Ct   -O--C-   100   100   000    -    0
  7 Unknown_SSD_Attribute   PO-R--   100   100   050    -    0
  8 Unknown_SSD_Attribute   P-S---   100   100   050    -    0
  9 Power_On_Hours          -O--C-   100   100   000    -    2449
 10 Unknown_SSD_Attribute   PO--C-   100   100   050    -    0
 12 Power_Cycle_Count       -O--C-   093   093   000    -    7407
167 Unknown_Attribute       -O---K   100   100   000    -    0
168 Unknown_Attribute       -O--C-   200   200   000    -    0
169 Unknown_Attribute       PO--C-   120   120   010    -    328339038
170 Unknown_Attribute       PO--C-   100   100   010    -    0
173 Unknown_Attribute       PO--C-   184   184   100    -    661457862891
175 Program_Fail_Count_Chip -O--C-   100   100   000    -    0
177 Wear_Leveling_Count     ------   000   000   000    -    14
181 Program_Fail_Cnt_Total  -O--CK   000   000   000    -    0
182 Erase_Fail_Count_Total  -O--CK   000   000   000    -    0
187 Reported_Uncorrect      -O--CK   100   100   000    -    0
192 Power-Off_Retract_Count -O--C-   000   000   000    -    3062
194 Temperature_Celsius     -O---K   057   009   000    -    43 (Min/Max 0/91)
197 Current_Pending_Sector  -O--C-   100   100   000    -    0
199 UDMA_CRC_Error_Count    -O---K   200   200   000    -    0
233 Media_Wearout_Indicator ------   000   000   000    -    48395
240 Unknown_SSD_Attribute   PO--C-   100   100   050    -    0
241 Total_LBAs_Written      -O--CK   000   000   000    -    14836
242 Total_LBAs_Read         -O--CK   000   000   000    -    24765
                            ||||||_ K auto-keep
                            |||||__ C event count
                            ||||___ R error rate
                            |||____ S speed/performance
                            ||_____ O updated online
                            |______ P prefailure warning

General Purpose Log Directory Version 1
SMART           Log Directory Version 1 [multi-sector log support]
Address    Access  R/W   Size  Description
0x00       GPL,SL  R/O      1  Log Directory
0x03       GPL     R/O     16  Ext. Comprehensive SMART error log
0x04       GPL,SL  R/O      1  Device Statistics log
0x07       GPL     R/O      1  Extended self-test log
0x09           SL  R/W      1  Selective self-test log
0x10       GPL     R/O      1  SATA NCQ Queued Error log
0x11       GPL,SL  R/O      1  SATA Phy Event Counters log
0x80-0x9f  GPL,SL  R/W     16  Host vendor specific log
0xb7       GPL,SL  VS      16  Device vendor specific log
0xe0       GPL,SL  R/W      1  SCT Command/Status
0xe1       GPL,SL  R/W      1  SCT Data Transfer

SMART Extended Comprehensive Error Log Version: 0 (16 sectors)
No Errors Logged

SMART Extended Self-test Log Version: 0 (1 sectors)
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      2533         0
# 2  Extended offline    Completed: read failure       90%      2533         0
# 3  Short offline       Completed: read failure       10%      2533         0
# 4  Short offline       Completed: read failure       20%      2532         0
# 5  Extended offline    Completed: read failure       90%      2532         0
# 6  Extended offline    Completed: read failure       90%      1317         0
# 7  Extended offline    Completed: read failure       90%      1316         0
# 8  Extended offline    Completed: read failure       90%      1316         0
# 9  Short offline       Completed: read failure       80%      1315         0
#10  Extended offline    Completed: read failure       90%      1315         0
#11  Extended offline    Completed: read failure       90%      2534         0

SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

SCT Status Version:                  3
SCT Version (vendor specific):       0 (0x0000)
SCT Support Level:                   1
Device State:                        Active (0)
Current Temperature:                 43 Celsius
Power Cycle Max Temperature:         91 Celsius
Lifetime    Max Temperature:         91 Celsius

SCT Data Table command not supported

SCT Error Recovery Control command not supported

Device Statistics (GP Log 0x04)
Page  Offset Size        Value Flags Description
0x01  =====  =               =  ===  == General Statistics (rev 2) ==
0x01  0x008  4            7409  ---  Lifetime Power-On Resets
0x01  0x010  4            2534  ---  Power-on Hours
0x01  0x018  6     31129476271  ---  Logical Sectors Written
0x01  0x028  6     51942369315  ---  Logical Sectors Read
0x04  =====  =               =  ===  == General Errors Statistics (rev 1) ==
0x04  0x008  4               0  ---  Number of Reported Uncorrectable Errors
0x04  0x010  4           78373  ---  Resets Between Cmd Acceptance and Completion
0x06  =====  =               =  ===  == Transport Statistics (rev 1) ==
0x06  0x008  4           78373  ---  Number of Hardware Resets
0x06  0x010  4        37165527  ---  Number of ASR Events
0x06  0x018  4               0  ---  Number of Interface CRC Errors
0x07  =====  =               =  ===  == Solid State Device Statistics (rev 1) ==
0x07  0x008  1             255  ---  Percentage Used Endurance Indicator
                                |||_ C monitored condition met
                                ||__ D supports DSN
                                |___ N normalized value

SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x0001  2            0  Command failed due to ICRC error
0x0003  2            0  R_ERR response for device-to-host data FIS
0x0004  2            0  R_ERR response for host-to-device data FIS
0x0006  2            0  R_ERR response for device-to-host non-data FIS
0x0007  2            0  R_ERR response for host-to-device non-data FIS
0x0008  2            0  Device-to-host non-data FIS retries
0x0009  2            7  Transition from drive PhyRdy to drive PhyNRdy
0x000a  2            9  Device-to-host register FISes sent due to a COMRESET
0x000f  2            0  R_ERR response for host-to-device data FIS, CRC
0x0010  2            0  R_ERR response for host-to-device data FIS, non-CRC
0x0012  2            0  R_ERR response for host-to-device non-data FIS, CRC
0x0013  2            0  R_ERR response for host-to-device non-data FIS, non-CRC
0x0002  2            0  R_ERR response for data FIS
0x0005  2            0  R_ERR response for non-data FIS
0x000b  2            0  CRC errors within host-to-device FIS

```

---

### Post by pqwoerituytrueiwoq on 2018-04-30
It looked like gnome-disk-utility in your screenshot, that was were you got the failed test result

---

### Post by monkeybrain20122 on 2018-04-30
> **pqwoerituytrueiwoq said:**
> It looked like gnome-disk-utility in your screenshot, that was were you got the failed test result

Yes, it was the disk utility in my screenshot. But I get passed in gsmartcontrol.

So do you think it looks ok?

---

### Post by pqwoerituytrueiwoq on 2018-04-30
are you sure you did the same test there are 3 types
It is probably fine, but backup anything you do not want to loose to be safe

---

### Post by monkeybrain20122 on 2018-04-30
> **pqwoerituytrueiwoq said:**
> are you sure you did the same test there are 3 types
It is probably fine, but backup anything you do not want to loose to be safe

I did the extended test in all cases. Yes, I do have backups.

---


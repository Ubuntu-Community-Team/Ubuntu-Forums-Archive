---
title: "harddrive will fail soon &amp; smartctl output"
date: 2019-06-27
forum: General Help
---

### Post by wile-e-coyote on 2019-06-27
Hi all,

Sort of a novice to ubuntu/linux. I have a dual boot setup and windows started only loading a blank screen. went into ubuntu to see if maybe grub needing fixing after a windows update. I was greeted with a message saying my hard drive will fail soon. If I understand this correctly, I should probably shut off my computer, stop using it, and restart it only after I get myself a new harddrive I can backup everything on. My question is, is smartctl reporting data on all of my harddrive or a particular partition? And is my course of action the correct interpretation of the data presented here? Thanks to all in advance.



```
smartctl 6.6 2017-11-05 r4594 [x86_64-linux-5.0.0-15-generic] (local build)
Copyright (C) 2002-17, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 7200.4
Device Model:     ST9320423AS
Serial Number:    5VH4EF34
LU WWN Device Id: 5 000c50 02a8340e6
Firmware Version: D005SDM1
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Thu Jun 27 19:15:56 2019 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
AAM level is:     254 (maximum performance), recommended: 208
APM level is:     254 (maximum performance)
Rd look-ahead is: Enabled
Write cache is:   Enabled
DSN feature is:   Unavailable
ATA Security is:  Disabled, frozen [SEC2]
Wt Cache Reorder: Unknown

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (  73)    The previous self-test completed having
                    a test element that failed and the test
                    element that failed is not known.
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
recommended polling time:      (  77) minutes.
Conveyance self-test routine
recommended polling time:      (   3) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     POSR--   086   079   006    -    69544150
  3 Spin_Up_Time            PO----   100   098   085    -    0
  4 Start_Stop_Count        -O--CK   095   095   020    -    5138
  5 Reallocated_Sector_Ct   PO--CK   035   035   036    NOW  1345
  7 Seek_Error_Rate         POSR--   076   060   030    -    112700648042
  9 Power_On_Hours          -O--CK   074   074   000    -    23079
 10 Spin_Retry_Count        PO--C-   100   100   097    -    0
 12 Power_Cycle_Count       -O--CK   097   037   020    -    3982
184 End-to-End_Error        -O--CK   100   100   099    -    0
187 Reported_Uncorrect      -O--CK   001   001   000    -    6648
188 Command_Timeout         -O--CK   100   099   000    -    4
189 High_Fly_Writes         -O-RCK   100   100   000    -    0
190 Airflow_Temperature_Cel -O---K   060   026   045    Past 40 (Min/Max 38/40 #197)
191 G-Sense_Error_Rate      -O--CK   100   100   000    -    584
192 Power-Off_Retract_Count -O--CK   100   100   000    -    3
193 Load_Cycle_Count        -O--CK   001   001   000    -    568672
194 Temperature_Celsius     -O---K   040   074   000    -    40 (0 3 0 0 0)
195 Hardware_ECC_Recovered  -O-RC-   057   048   000    -    69544150
197 Current_Pending_Sector  -O--C-   100   100   000    -    114
198 Offline_Uncorrectable   ----C-   100   100   000    -    114
199 UDMA_CRC_Error_Count    -OSRCK   200   200   000    -    0
240 Head_Flying_Hours       ------   100   253   000    -    22093 (37 28 0)
241 Total_LBAs_Written      ------   100   253   000    -    3870958543
242 Total_LBAs_Read         ------   100   253   000    -    1428863115
254 Free_Fall_Sensor        -O--CK   001   001   000    -    72
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
0x01       GPL,SL  R/O      1  Summary SMART error log
0x02       GPL,SL  R/O      5  Comprehensive SMART error log
0x03       GPL,SL  R/O      5  Ext. Comprehensive SMART error log
0x06       GPL,SL  R/O      1  SMART self-test log
0x07       GPL,SL  R/O      1  Extended self-test log
0x09       GPL,SL  R/W      1  Selective self-test log
0x10       GPL,SL  R/O      1  NCQ Command Error log
0x11       GPL,SL  R/O      1  SATA Phy Event Counters log
0x21       GPL,SL  R/O      1  Write stream error log
0x22       GPL,SL  R/O      1  Read stream error log
0x80-0x9f  GPL,SL  R/W     16  Host vendor specific log
0xa1       GPL,SL  VS      20  Device vendor specific log
0xa2       GPL     VS    2248  Device vendor specific log
0xa8       GPL,SL  VS      65  Device vendor specific log
0xa9       GPL,SL  VS       1  Device vendor specific log
0xb0       GPL     VS    2864  Device vendor specific log
0xbe-0xbf  GPL     VS   65535  Device vendor specific log
0xe0       GPL,SL  R/W      1  SCT Command/Status
0xe1       GPL,SL  R/W      1  SCT Data Transfer

SMART Extended Comprehensive Error Log Version: 1 (5 sectors)
Device Error Count: 3448 (device log contains only the most recent 20 errors)
    CR     = Command Register
    FEATR  = Features Register
    COUNT  = Count (was: Sector Count) Register
    LBA_48 = Upper bytes of LBA High/Mid/Low Registers ]  ATA-8
    LH     = LBA High (was: Cylinder High) Register    ]   LBA
    LM     = LBA Mid (was: Cylinder Low) Register      ] Register
    LL     = LBA Low (was: Sector Number) Register     ]
    DV     = Device (was: Device/Head) Register
    DC     = Device Control Register
    ER     = Error register
    ST     = Status register
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 3448 [7] occurred at disk power-on lifetime: 23078 hours (961 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 00 00 1f 40 00 73 8f 00 00  Error: UNC at LBA = 0x1f4000738f = 134217757583

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 00 00 01 00 1f 40 00 73 8f 40 00     00:00:38.994  READ FPDMA QUEUED
  60 00 00 00 01 00 1f 40 00 73 8e 40 00     00:00:38.993  READ FPDMA QUEUED
  60 00 00 00 01 00 1f 40 00 73 8d 40 00     00:00:38.992  READ FPDMA QUEUED
  60 00 00 00 01 00 1f 40 00 73 8c 40 00     00:00:38.989  READ FPDMA QUEUED
  60 00 00 00 01 00 1f 40 00 73 8b 40 00     00:00:38.988  READ FPDMA QUEUED

Error 3447 [6] occurred at disk power-on lifetime: 23078 hours (961 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 00 00 1f 40 00 73 8f 00 00  Error: WP at LBA = 0x1f4000738f = 134217757583

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  61 00 00 01 00 00 12 05 00 12 a0 40 00     00:00:36.212  WRITE FPDMA QUEUED
  60 00 00 00 20 00 1f 40 00 73 80 40 00     00:00:36.208  READ FPDMA QUEUED
  61 00 00 01 00 00 12 04 00 12 a0 40 00     00:00:36.207  WRITE FPDMA QUEUED
  61 00 00 01 00 00 12 03 00 12 a0 40 00     00:00:36.207  WRITE FPDMA QUEUED
  61 00 00 01 00 00 12 02 00 12 a0 40 00     00:00:36.206  WRITE FPDMA QUEUED

Error 3446 [5] occurred at disk power-on lifetime: 23078 hours (961 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 00 00 1f 40 00 73 8f 00 00  Error: UNC at LBA = 0x1f4000738f = 134217757583

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 00 00 01 00 1f 40 00 73 8f 40 00     00:13:32.392  READ FPDMA QUEUED
  60 00 00 00 01 00 1f 40 00 73 8e 40 00     00:13:32.389  READ FPDMA QUEUED
  60 00 00 00 01 00 1f 40 00 73 8d 40 00     00:13:32.389  READ FPDMA QUEUED
  60 00 00 00 01 00 1f 40 00 73 8c 40 00     00:13:32.388  READ FPDMA QUEUED
  60 00 00 00 01 00 1f 40 00 73 8b 40 00     00:13:32.388  READ FPDMA QUEUED

Error 3445 [4] occurred at disk power-on lifetime: 23078 hours (961 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 00 00 1f 40 00 73 8f 00 00  Error: UNC at LBA = 0x1f4000738f = 134217757583

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 00 00 20 00 1f 40 00 73 80 40 00     00:13:29.585  READ FPDMA QUEUED
  61 00 00 00 10 00 1f 40 00 73 50 40 00     00:13:29.585  WRITE FPDMA QUEUED
  61 00 00 00 08 00 1f 25 00 71 40 40 00     00:13:29.584  WRITE FPDMA QUEUED
  61 00 00 00 20 00 12 1f 00 31 c0 40 00     00:13:29.583  WRITE FPDMA QUEUED
  61 00 00 00 20 00 12 7b 00 38 20 40 00     00:13:29.583  WRITE FPDMA QUEUED

Error 3444 [3] occurred at disk power-on lifetime: 23078 hours (961 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 00 00 1f 16 00 73 d7 00 00  Error: UNC at LBA = 0x1f160073d7 = 133513114583

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 00 00 08 00 1f 17 00 73 48 40 00     00:12:25.441  READ FPDMA QUEUED
  60 00 00 00 08 00 1f 16 00 73 d0 40 00     00:12:25.439  READ FPDMA QUEUED
  60 00 00 00 08 00 1f 16 00 73 a8 40 00     00:12:25.438  READ FPDMA QUEUED
  60 00 00 00 08 00 1f 16 00 73 88 40 00     00:12:25.430  READ FPDMA QUEUED
  60 00 00 00 08 00 1f 16 00 73 38 40 00     00:12:25.429  READ FPDMA QUEUED

Error 3443 [2] occurred at disk power-on lifetime: 23078 hours (961 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 00 00 1f 89 00 6b a2 00 00  Error: UNC at LBA = 0x1f89006ba2 = 135442492322

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 00 00 08 00 1f 8b 00 6b 80 40 00     00:12:06.832  READ FPDMA QUEUED
  60 00 00 00 08 00 1f 89 00 6b a0 40 00     00:12:06.824  READ FPDMA QUEUED
  60 00 00 00 10 00 1f 89 00 6b 88 40 00     00:12:06.822  READ FPDMA QUEUED
  60 00 00 00 08 00 1f 89 00 6b 68 40 00     00:12:06.816  READ FPDMA QUEUED
  60 00 00 00 08 00 1f 89 00 6b 58 40 00     00:12:06.813  READ FPDMA QUEUED

Error 3442 [1] occurred at disk power-on lifetime: 23078 hours (961 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 00 00 1f 00 00 73 17 00 00  Error: UNC at LBA = 0x1f00007317 = 133144015639

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 00 00 08 00 1f 00 00 73 20 40 00     00:11:10.453  READ FPDMA QUEUED
  60 00 00 00 08 00 1f 00 00 73 10 40 00     00:11:10.425  READ FPDMA QUEUED
  60 00 00 00 08 00 1f ff 00 72 88 40 00     00:11:10.423  READ FPDMA QUEUED
  60 00 00 00 20 00 02 4c 00 05 40 40 00     00:11:10.422  READ FPDMA QUEUED
  60 00 00 00 08 00 02 4c 00 05 28 40 00     00:11:10.421  READ FPDMA QUEUED

Error 3441 [0] occurred at disk power-on lifetime: 23078 hours (961 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER -- ST COUNT  LBA_48  LH LM LL DV DC
  -- -- -- == -- == == == -- -- -- -- --
  40 -- 51 00 00 00 1f eb 00 6d f1 00 00  Error: UNC at LBA = 0x1feb006df1 = 137086660081

  Commands leading to the command that caused the error were:
  CR FEATR COUNT  LBA_48  LH LM LL DV DC  Powered_Up_Time  Command/Feature_Name
  -- == -- == -- == == == -- -- -- -- --  ---------------  --------------------
  60 00 00 01 00 00 00 9c 00 04 20 40 00     00:00:47.864  READ FPDMA QUEUED
  60 00 00 01 00 00 00 9b 00 04 20 40 00     00:00:47.864  READ FPDMA QUEUED
  60 00 00 01 00 00 00 9a 00 04 20 40 00     00:00:47.864  READ FPDMA QUEUED
  60 00 00 01 00 00 00 99 00 04 20 40 00     00:00:47.863  READ FPDMA QUEUED
  61 00 00 00 08 00 00 de 00 5e 00 40 00     00:00:47.862  WRITE FPDMA QUEUED

SMART Extended Self-test Log Version: 1 (1 sectors)
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: unknown failure    90%     23078         0
# 2  Short offline       Completed without error       00%     13762         -
# 3  Short offline       Completed without error       00%     12688         -
# 4  Short offline       Completed without error       00%      4937         -
# 5  Short offline       Completed without error       00%         1         -
# 6  Short offline       Completed without error       00%         1         -
# 7  Short offline       Completed without error       00%         1         -

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

SCT Status Version:                  3
SCT Version (vendor specific):       522 (0x020a)
SCT Support Level:                   1
Device State:                        Active (0)
Current Temperature:                    40 Celsius
Power Cycle Min/Max Temperature:     38/41 Celsius
Lifetime    Min/Max Temperature:      3/77 Celsius
Lifetime    Average Temperature:        38 Celsius
Under/Over Temperature Limit Count:   0/0

SCT Temperature History Version:     2
Temperature Sampling Period:         1 minute
Temperature Logging Interval:        1 minute
Min/Max recommended Temperature:     14/55 Celsius
Min/Max Temperature Limit:           10/60 Celsius
Temperature History Size (Index):    128 (43)

Index    Estimated Time   Temperature Celsius
  44    2019-06-27 17:08    38  *******************
 ...    ..(  3 skipped).    ..  *******************
  48    2019-06-27 17:12    38  *******************
  49    2019-06-27 17:13    37  ******************
  50    2019-06-27 17:14    37  ******************
  51    2019-06-27 17:15    38  *******************
 ...    ..(  3 skipped).    ..  *******************
  55    2019-06-27 17:19    38  *******************
  56    2019-06-27 17:20    37  ******************
 ...    ..(  6 skipped).    ..  ******************
  63    2019-06-27 17:27    37  ******************
  64    2019-06-27 17:28    38  *******************
 ...    ..(  4 skipped).    ..  *******************
  69    2019-06-27 17:33    38  *******************
  70    2019-06-27 17:34    37  ******************
 ...    ..(  4 skipped).    ..  ******************
  75    2019-06-27 17:39    37  ******************
  76    2019-06-27 17:40    38  *******************
 ...    ..(  5 skipped).    ..  *******************
  82    2019-06-27 17:46    38  *******************
  83    2019-06-27 17:47    37  ******************
 ...    ..(  2 skipped).    ..  ******************
  86    2019-06-27 17:50    37  ******************
  87    2019-06-27 17:51    38  *******************
 ...    ..(  3 skipped).    ..  *******************
  91    2019-06-27 17:55    38  *******************
  92    2019-06-27 17:56    39  ********************
  93    2019-06-27 17:57    39  ********************
  94    2019-06-27 17:58    38  *******************
  95    2019-06-27 17:59    37  ******************
  96    2019-06-27 18:00    37  ******************
  97    2019-06-27 18:01    38  *******************
 ...    ..(  8 skipped).    ..  *******************
 106    2019-06-27 18:10    38  *******************
 107    2019-06-27 18:11    37  ******************
 108    2019-06-27 18:12    38  *******************
 ...    ..(  6 skipped).    ..  *******************
 115    2019-06-27 18:19    38  *******************
 116    2019-06-27 18:20    39  ********************
 117    2019-06-27 18:21    39  ********************
 118    2019-06-27 18:22     ?  -
 119    2019-06-27 18:23    24  *****
 120    2019-06-27 18:24    25  ******
 121    2019-06-27 18:25    26  *******
 122    2019-06-27 18:26    28  *********
 123    2019-06-27 18:27    29  **********
 124    2019-06-27 18:28    30  ***********
 125    2019-06-27 18:29    31  ************
 126    2019-06-27 18:30    32  *************
 127    2019-06-27 18:31    33  **************
   0    2019-06-27 18:32     ?  -
   1    2019-06-27 18:33    34  ***************
   2    2019-06-27 18:34    34  ***************
   3    2019-06-27 18:35    34  ***************
   4    2019-06-27 18:36    35  ****************
   5    2019-06-27 18:37    36  *****************
   6    2019-06-27 18:38     ?  -
   7    2019-06-27 18:39    36  *****************
   8    2019-06-27 18:40     ?  -
   9    2019-06-27 18:41    37  ******************
  10    2019-06-27 18:42    35  ****************
  11    2019-06-27 18:43    36  *****************
  12    2019-06-27 18:44    37  ******************
  13    2019-06-27 18:45    37  ******************
  14    2019-06-27 18:46     ?  -
  15    2019-06-27 18:47    37  ******************
  16    2019-06-27 18:48     ?  -
  17    2019-06-27 18:49    38  *******************
  18    2019-06-27 18:50    38  *******************
  19    2019-06-27 18:51    38  *******************
  20    2019-06-27 18:52    39  ********************
 ...    ..( 11 skipped).    ..  ********************
  32    2019-06-27 19:04    39  ********************
  33    2019-06-27 19:05    40  *********************
  34    2019-06-27 19:06    39  ********************
  35    2019-06-27 19:07    39  ********************
  36    2019-06-27 19:08    40  *********************
  37    2019-06-27 19:09    40  *********************
  38    2019-06-27 19:10    41  **********************
  39    2019-06-27 19:11    40  *********************
 ...    ..(  3 skipped).    ..  *********************
  43    2019-06-27 19:15    40  *********************

SCT Error Recovery Control:
           Read: Disabled
          Write: Disabled

Device Statistics (GP/SMART Log 0x04) not supported

Pending Defects log (GP Log 0x0c) not supported

SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x000a  2            3  Device-to-host register FISes sent due to a COMRESET
0x0001  2            0  Command failed due to ICRC error
0x0003  2            0  R_ERR response for device-to-host data FIS
0x0004  2            0  R_ERR response for host-to-device data FIS
0x0006  2            0  R_ERR response for device-to-host non-data FIS
0x0007  2            0  R_ERR response for host-to-device non-data FIS

```

---

### Post by wildmanne39 on 2019-06-27
*Thread moved to **General Help a more appropriate sub-forum**.*

---

### Post by deadflowr on 2019-06-27
> My question is, is smartctl reporting data on all of my harddrive or a particular partition? 
The whole drive.
>  And is my course of action the correct interpretation of the data presented here? 
The best course of action is to already be backing up before issues ever arise.
But in lieu of that stopping using it is probably the next best thing.

---

### Post by Autodave on 2019-06-28
The next time that you power up, you had better have a means to copy everything that you are going to want to keep.  The next time could be the last time that HD functions: if it even functions then.

---

### Post by TheFu on 2019-06-29
> **Autodave said:**
> The next time that you power up, you had better have a means to copy everything that you are going to want to keep.  The next time could be the last time that HD functions: if it even functions then.

+1. Yep. That is the worst numbers I've seen from SMART on any disk that is still sorta working. * He's dead Jim.*

---


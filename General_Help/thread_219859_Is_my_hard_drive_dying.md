---
title: "Is my hard drive dying?"
date: 2006-07-20
forum: General Help
---

### Post by dangral on 2006-07-20
I installed smartmontools and did a smartctl -a /dev/hdc. The results were not encouraging. Should I expect that my hard drive will completely fail soon? I hae not noticed any performance issues with the hard drive, and I only ran smartctl because I was curious to see the output.

> smartctl -a /dev/hda
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST340014A
Serial Number:    3JX90G69
Firmware Version: 3.16
User Capacity:    40,000,000,000 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Thu Jul 20 16:02:50 2006 EDT
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
recommended polling time:        (  31) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   063   054   006    Pre-fail  Always       -       241074960
  3 Spin_Up_Time            0x0003   098   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1242
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   081   060   030    Pre-fail  Always       -       138987947
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       15330
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       109
194 Temperature_Celsius     0x0022   041   044   000    Old_age   Always       -       41
195 Hardware_ECC_Recovered  0x001a   063   054   000    Old_age   Always       -       241074960
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 4
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

Error 4 occurred at disk power-on lifetime: 6214 hours (258 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 29 43 09 e0  Error: UNC at LBA = 0x00094329 = 607017

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 27 43 09 e0 00      19:17:09.656  READ DMA
  c8 00 01 00 00 00 e0 00      19:17:09.656  READ DMA
  c8 00 08 87 53 d6 e3 00      19:17:13.724  READ DMA
  c8 00 08 5f e5 d5 e3 00      19:17:13.709  READ DMA
  c8 00 08 17 d6 cc e3 00      19:17:13.699  READ DMA

Error 3 occurred at disk power-on lifetime: 6214 hours (258 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 29 43 09 e0  Error: UNC at LBA = 0x00094329 = 607017

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 27 43 09 e0 00      19:17:09.656  READ DMA
  c8 00 01 00 00 00 e0 00      19:17:09.656  READ DMA
  c8 00 08 4f fc d5 e3 00      19:17:09.656  READ DMA
  c8 00 08 07 7f d5 e3 00      19:17:04.265  READ DMA
  ca 00 08 7f fd a4 e1 00      19:17:04.256  WRITE DMA

Error 2 occurred at disk power-on lifetime: 6214 hours (258 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 29 43 09 e0  Error: UNC at LBA = 0x00094329 = 607017

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 27 43 09 e0 00      19:17:04.196  READ DMA
  c8 00 08 4f c0 d5 e3 00      19:17:04.195  READ DMA
  c8 00 08 77 63 ca e3 00      19:17:04.184  READ DMA
  c8 00 08 1f 46 ca e3 00      19:17:04.265  READ DMA
  c8 00 40 69 e4 35 e3 00      19:17:04.256  READ DMA

Error 1 occurred at disk power-on lifetime: 6214 hours (258 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 29 43 09 e0  Error: UNC at LBA = 0x00094329 = 607017

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 27 43 09 e0 00      19:16:55.938  READ DMA
  c8 00 08 b7 0b a5 e1 00      19:16:55.925  READ DMA
  c8 00 08 cf 63 09 e0 00      19:16:55.907  READ DMA
  c8 00 08 af 63 09 e0 00      19:16:55.907  READ DMA
  c8 00 10 b7 63 09 e0 00      19:16:55.906  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         0         -

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



---

### Post by Jussi Kukkonen on 2006-07-20
> **dangral said:**
> I installed smartmontools and did a smartctl -a /dev/hdc. The results were not encouraging. Should I expect that my hard drive will completely fail soon? I hae not noticed any performance issues with the hard drive, and I only ran smartctl because I was curious to see the output.

Doesn't look that bad to me. If I read it correctly your drive has been on for 15330 hours (638 days), and SMART has noticed four errors during that time -- all on day 258. Your vendor-specific SMART attributes have never failed (you can see that from the dashes in the WHEN_FAILED column).

Now, don't take this as a promise, but I'd bet your drive is ok. I admit I can't read the actual error log, though.

---


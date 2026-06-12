---
title: "urgent problem Ubuntu dapper LTS mounting failed"
date: 2008-05-29
forum: General Help
---

### Post by weissnich on 2008-05-29
Hi,

my Ubuntu dapper LTS has been rock stable until now, no problem,
1 hour ago all worked properly, I did nothing unusual, now I boot again and booting fails, I am depply worried:(:

[HTML]mount: Mounting /dev/hda5 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such device or directory
mount: Mounting /sys on /root/sys failed: failed: No such device or directory
mount: Mounting /proc on /root/proc failed: No such device or directory
Target filesystem doesn't have /sbin/init
/bin/sh: can't access tty; job control turned off[/HTML]

What happened???

---

### Post by weissnich on 2008-05-29
Someone please??
This is urgent as I have to get access to some files until tomorrow.

---

### Post by weissnich on 2008-05-29
I can mount hda5 from a live cd linux, so no hardware error?
There were no dapper updates the last days, so I really have no clue what caused this error, mysterious:confused:

---

### Post by weissnich on 2008-05-30
now it works again, but how long????
has to be a hard disc error,
but is this error really bad, anyone knows?

smartctl output

```
=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA MK2018GAP
Serial Number:    32F40299T
Firmware Version: M1.42 A
User Capacity:    20.003.880.960 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri May 30 03:22:02 2008 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 112) The previous self-test completed having
                                        the read element of the test failed.
Total time to complete Offline
data collection:                 ( 212) seconds.
Offline data collection
capabilities:                    (0x1b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        No Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  24) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       870
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       3199
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       19
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   086   086   000    Old_age   Always       -       5681
 10 Spin_Retry_Count        0x0033   163   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       3137
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       63
193 Load_Cycle_Count        0x0032   084   084   000    Old_age   Always       -       166694
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       19
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       4
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       686
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       4202
222 Loaded_Hours            0x0032   089   089   000    Old_age   Always       -       4404
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       349
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       3

SMART Error Log Version: 1
ATA Error Count: 808 (device log contains only the most recent five errors)
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

Error 808 occurred at disk power-on lifetime: 5680 hours (236 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 87 d2 bf e1  Error: ICRC, ABRT 1 sectors at LBA = 0x01bfd287 = 29348487

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 90 f8 d1 bf e1 00      04:17:59.185  READ DMA
  c8 00 00 88 d2 bf e1 00      04:17:59.170  READ DMA
  c8 00 08 38 a3 be e1 00      04:17:59.169  READ DMA
  c8 00 40 d8 a2 be e1 00      04:17:59.159  READ DMA
  c8 00 08 78 c7 bb e1 00      04:17:59.153  READ DMA

Error 807 occurred at disk power-on lifetime: 5676 hours (236 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 bf 74 d8 e1  Error: ICRC, ABRT 1 sectors at LBA = 0x01d874bf = 30962879

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 c0 73 d8 e1 00      00:05:47.692  READ DMA
  c8 00 e8 b0 2b d1 e1 00      00:05:47.643  READ DMA
  c8 00 48 28 5d cc e1 00      00:05:47.006  READ DMA
  ca 00 08 a0 cf b5 e1 00      00:05:41.542  WRITE DMA
  ca 00 d8 c8 ce b5 e1 00      00:05:41.541  WRITE DMA

Error 806 occurred at disk power-on lifetime: 5676 hours (236 days + 12 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 cf d4 dc e1  Error: ICRC, ABRT 1 sectors at LBA = 0x01dcd4cf = 31249615

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 d0 d3 dc e1 00      00:01:40.172  READ DMA
  c8 00 18 98 dc c1 e1 00      00:01:40.172  READ DMA
  c8 00 08 80 90 c1 e1 00      00:01:40.149  READ DMA
  c8 00 08 08 eb b7 e1 00      00:01:40.147  READ DMA
  c8 00 08 48 b2 d7 e1 00      00:01:40.146  READ DMA

Error 805 occurred at disk power-on lifetime: 5641 hours (235 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 be 48 af e0  Error: ICRC, ABRT 1 sectors at LBA = 0x00af48be = 11487422

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 38 87 48 af e0 00      02:40:51.322  READ DMA
  c8 00 68 5f 46 af e0 00      02:40:51.319  READ DMA
  c8 00 50 0f 46 af e0 00      02:40:51.318  READ DMA
  c8 00 50 0f 46 af e0 00      02:40:51.294  READ DMA
  c8 00 0e ff e0 73 e1 00      02:40:51.262  READ DMA

Error 804 occurred at disk power-on lifetime: 5641 hours (235 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 de 79 8a e1  Error: ICRC, ABRT 1 sectors at LBA = 0x018a79de = 25852382

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 80 5f 79 8a e1 00      02:27:48.313  READ DMA
  c8 00 68 27 19 3f e0 00      02:27:48.312  READ DMA
  c8 00 08 27 e4 60 e0 00      02:27:48.289  READ DMA
  c8 00 80 df 78 8a e1 00      02:27:48.263  READ DMA
  c8 00 68 27 19 3f e0 00      02:27:48.238  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       00%      5681         4126375
# 2  Short offline       Completed without error       00%      5680         -
# 3  Short offline       Completed without error       00%      5680         -


```

---

### Post by drao on 2008-05-30
Ur hd is about to fail. take backup of ur imp files.

---

### Post by drao on 2008-05-30
You can't do anything, since its a mechanical error inside ur hard disk. I had similar kind of error with my samsung harddisk....and its even bad compare to ur hd. it has around 22k errors.

---


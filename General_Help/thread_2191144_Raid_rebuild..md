---
title: "Raid rebuild."
date: 2013-12-01
forum: General Help
---

### Post by NertSkull on 2013-12-01
So over the past year or so, I've had my raid setup to email me on status changes.  During that year, twice I've received messages like this.

```
MD Device: /dev/md0Event: Rebuild45

/proc/mdstat:
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[2] sdc1[3]
      625129336 blocks super 1.2 [2/2] [UU]
      [=========>...........]  check = 45.4% (283829632/625129336) finish=81.9min speed=69431K/sec
       unused devices: <none>
```

I get an email every hour.  So I get 4 or 5 emails showing the progress of the "rebuild".  Then once its rebuilt, everything seems to be back to normal.  I'm not aware of doing anything different around this time to cause it to do this.

Is this a problem?  Does this mean one of my drives is starting to fail?  

Or is this just a normal thing raid/mdadm does from time to time to maintain the health of the system?  It would seem to me that during the rebuild time my data is not as safe as I would like it, that if one of the drives failed during the rebuild I could lose data.  Is that correct?

Do I need to be worried about this?

---

### Post by SaturnusDJ on 2013-12-02
Every first sunday of the month around 1:15 (I think) mdadm raid arrays are being checked. I never received mail of that check. So this is not normal. It's hard to tell how dangerous this is. Start with smart checks for all members.
Like:
```

smartctl -a /dev/sdb1
```

---

### Post by NertSkull on 2013-12-02
So I ran 

```
smartctl -a /dev/sdb1
```

And it told me that the overall health of the test result was 'PASSED'

But I read a bit more into smartctl as I've never used it.  And it looks like I should try to actually run a test on the drive.  So I did the following command

```
smartctl --test=short /dev/sdb
```

Then I reran the smartctl -a command.  I still get that it 'PASSED' but there is more information.  I don't know exactly how to read it, but it looks like maybe there was an error??? Maybe not?? 

But I thought I'd post results to see if anyone can give my guidance.  Thanks.
```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-32-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda ES
Device Model:     ST3750640NS
Serial Number:    5QD0HGZG
Firmware Version: 3CNR
User Capacity:    750,156,374,016 bytes [750 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Dec  2 18:58:59 2013 EST
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
data collection:                (  430) seconds.
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
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 202) minutes.
SCT capabilities:              (0x003d) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   097   093   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       84
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   083   060   030    Pre-fail  Always       -       215870791
  9 Power_On_Hours          0x0032   067   067   000    Old_age   Always       -       28952
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       83
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   080   080   000    Old_age   Always       -       20
190 Airflow_Temperature_Cel 0x0022   069   052   045    Old_age   Always       -       31 (Min/Max 30/33)
194 Temperature_Celsius     0x0022   031   048   000    Old_age   Always       -       31 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   069   059   000    Old_age   Always       -       68872312
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 Data_Address_Mark_Errs  0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 1
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

Error 1 occurred at disk power-on lifetime: 14909 hours (621 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 00 4f 91 77 e0  Error: IDNF at LBA = 0x0077914f = 7835983

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 80 00 91 77 e0 00      03:18:52.160  READ DMA EXT
  25 00 80 80 90 77 e0 00      03:18:52.159  READ DMA EXT
  25 00 80 00 90 77 e0 00      03:18:52.156  READ DMA EXT
  25 00 80 80 8f 77 e0 00      03:18:52.155  READ DMA EXT
  25 00 80 00 8f 77 e0 00      03:18:52.153  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     28952         -
# 2  Short offline       Completed without error       00%     15744         -
# 3  Extended offline    Aborted by host               90%     15744         -
# 4  Short captive       Completed without error       00%     15740         -
# 5  Short offline       Completed without error       00%     15442         -
# 6  Short offline       Completed without error       00%     14902         -
# 7  Short offline       Completed without error       00%     14901         -
# 8  Short offline       Completed without error       00%     13322         -
# 9  Short offline       Completed without error       00%     12291         -
#10  Short offline       Aborted by host               50%     12285         -
#11  Short offline       Completed without error       00%     12265         -
#12  Short offline       Completed without error       00%     12222         -
#13  Short offline       Completed without error       00%     12201         -
#14  Short offline       Completed without error       00%     12200         -

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

I should say I also ran the short test on the other drive part of the raid (sdc) and it came back saying there were no errors.

So how do I interpret this.  Is my sdb drive failing?  Is it time to replace it?  Is it okay for longer?

I just don't know how to interpret what this means.

Thanks for pointing me in the right direction though.  That was a good thing to do, to check the SMART data.

---

### Post by SaturnusDJ on 2013-12-03
Post S.M.A.R.T. results for both disks.

I see a high Hardware_ECC_Recovered count.

---

### Post by NertSkull on 2013-12-03
Can do.  Above is from the sdb drive.

Here is from the sdc drive.

```


smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-32-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Device Model:     ST2000DM001-9YN164
Serial Number:    S1E06YV0
LU WWN Device Id: 5 000c50 04afcb49a
Firmware Version: CC4C
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Tue Dec  3 07:19:54 2013 EST
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
data collection:                (  575) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.


SMART capabilities:            (0x0003) Saves SMART data before entering                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 222) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x3085) SCT Status supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   111   099   006    Pre-fail  Always       -       38005184
  3 Spin_Up_Time            0x0003   096   095   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       52
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   057   052   030    Pre-fail  Always       -       73024392320
  9 Power_On_Hours          0x0032   085   085   000    Old_age   Always       -       13645
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       52
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   072   058   045    Old_age   Always       -       28 (Min/Max 27/30)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       46
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       68
194 Temperature_Celsius     0x0022   028   042   000    Old_age   Always       -       28 (0 21 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       269680996529460
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3984567550608
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       5043695038206


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     13633         -
# 2  Short offline       Completed without error       00%     13633         -


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

### Post by SaturnusDJ on 2013-12-07
Okay. The high counts here don't directly mean something is wrong.

You can run a S.M.A.R.T. in order to see if critical attributes change.
```
smartctl -t short /dev/sdb
smartctl -t short /dev/sdc

```
Then read S.M.A.R.T. again.

Note again that the example in your first posts shows a 'check' not a resync/rebuild. If the warning mail is during a check, it may be ignored.
If you are sure the mails were not about checks, then watch the syslog for clues.

---


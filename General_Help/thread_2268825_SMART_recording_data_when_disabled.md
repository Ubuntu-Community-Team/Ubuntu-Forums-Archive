---
title: "SMART recording data when disabled?"
date: 2015-03-11
forum: General Help
---

### Post by chris137 on 2015-03-11
Hi,
I just checked an old harddrive to see what was on it and how old it might be.
Since it was already formatted I went to check SMART which was disabled.
I then enabled it and got an ouput I would expect for a new drive.
Since I am planning to sell that drive it would be quite important to know if it is actually practiacally unused or if SMART simply does not record data while disabled.
I myself feel the question might be kind of dumb because disabled usally means nothing is happening.
I just don't really now how SMART works and if it really needs to be enabled to monitor the data.

Thanks

---

### Post by tgalati4 on 2015-03-11
Typically the power-on hours are recorded for warranty purposes.  The error logging and other parameters may or may not be recorded depending on how the manufacturer implemented SMART.

---

### Post by chris137 on 2015-03-12
So what you're saying is that if I see a zero there the drive actually was not used - no matter if SMART was enabled or not?

---

### Post by tgalati4 on 2015-03-12
Yes, however, every drive that I have ever bought new had a least 2 or 3 hours on it.  So I presume this was quality testing.  It's possible that a refurbished drive with new firmware installed would have all 0's for health monitoring.  I've also had used drives without SMART enabled show all the history when SMART was enabled.  So it really depends on the drive manufacturer and how they implement SMART.

Is this a refurbished or "open box" disk drive?

---

### Post by chris137 on 2015-03-12
I've honestly never heard of these terms.
Here is the smartctl-output if that helps:
```
~$ sudo smartctl -a /dev/sdd
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-46-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint M5
Device Model:     SAMSUNG HM160HC
Serial Number:    S12TJ1LB774197
LU WWN Device Id: 5 0f0000 0c2774197
Firmware Version: LQ100-10
User Capacity:    160.041.885.696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS, ATA/ATAPI-7 T13/1532D revision 0
Local Time is:    Thu Mar 12 15:49:46 2015 CET
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
data collection:         (   55) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
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
recommended polling time:      (  55) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   252   252   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   252   252   025    Pre-fail  Always       -       2125
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       7
  5 Reallocated_Sector_Ct   0x0033   070   070   010    Pre-fail  Always       -       282
  7 Seek_Error_Rate         0x000e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   252   252   000    Old_age   Always       -       1
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       6
191 G-Sense_Error_Rate      0x0032   252   252   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       4
194 Temperature_Celsius     0x0022   175   106   000    Old_age   Always       -       21 (Min/Max 21/44)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x0032   252   252   000    Old_age   Always       -       0
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       4

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

---

### Post by tgalati4 on 2015-03-12
You have one hour on your drive (power-on hours) and 282 relocated sectors--which seems like a lot for a new drive.  It estimates that you are at 70% capacity for this parameter.  When you get to 10%, warnings will go off.  A disk drive keeps reserved sectors for moving data when it detects a bad or failing sector.  You have 282 of them.  When you run out of room to relocate bad sectors, you start to lose data.  Run *badblocks* on the drive.

```
sudo badblocks /dev/sdd
```

The other parameters look OK.

---

### Post by DigiAngel on 2015-03-12
Run a short test:

sudo smartctl -t short /dev/sdd

wait a couple minutes then:

sudo smartctl -a /dev/sdd

Your last test will show you the time in hours:

```
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      4614         -

```

---

### Post by chris137 on 2015-03-12
Badblocks did not find anything yet. I stopped it at 15% since it really takes a very long time.
The selftest only logs the Power on hours at the time of the test.
I don't know why this should be a different value (tested it and is is not).

---

### Post by tgalati4 on 2015-03-13
Let *badblocks* finish.  It will scan the entire disk surface which can take a while.  If you have blocks (groups of adjacent sectors) that can't be read correctly, they will be listed.  You want to know this before you install a new system or store data on it.  It's also a good way to break in a drive by getting it warm and allowing it to spin for a while.

---

### Post by chris137 on 2015-03-13
Well I actually did not really want to know if the drive had corrupt blocks.
I just wanted to find out if that power-on-date was accurate.

---


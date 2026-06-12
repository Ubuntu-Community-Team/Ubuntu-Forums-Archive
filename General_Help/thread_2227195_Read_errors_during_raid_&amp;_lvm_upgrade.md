---
title: "Read errors during raid &amp; lvm upgrade"
date: 2014-05-31
forum: General Help
---

### Post by dave_b2 on 2014-05-31
I've got 4 drives in my system, configured as 2 Raid1 arrays(2tb sda,sdb = md0 & 3tb sdc,sdd = md1), and a single LVM volume sitting on top of md0 & md1. This is the OS drive as well as data.

I'm running out of disk space, so bought new drives to upgrade md0, following [http://christopher.murtagh.name/2011/12/07/upgrading-software-raid-drives-and-increase-capacity/](http://christopher.murtagh.name/2011/12/07/upgrading-software-raid-drives-and-increase-capacity/)

I have :
 - failed & removed sda from the array
 - removed sda and swapped for new drive
 - partitioned and added new sda into the array
 - waited for the array to synchronise
 - failed & removed sdb from the array
 - removed sdb and swapped for new drive
 - partitioned and added new sdb into the array

So far so good.  The array is happy on the new sda, in a "clean, degraded" state. The system boots, and everything seems to run as normal.

 However, when rebuilding the array onto the new sdb, I get read errors from sda:

```
[  135.147982] ata3.00: exception Emask 0x0 SAct 0x3f SErr 0x0 action 0x0
[  135.148122] ata3.00: irq_stat 0x40000008
[  135.148203] ata3.00: failed command: READ FPDMA QUEUED
[  135.148312] ata3.00: cmd 60/00:00:80:9e:49/04:00:01:00:00/40 tag 0 ncq 524288 in
[  135.148312]          res 41/40:00:98:9e:49/00:00:01:00:00/40 Emask 0x409 (media error) <F>
[  135.148590] ata3.00: status: { DRDY ERR }
[  135.148667] ata3.00: error: { UNC }
[  135.150184] ata3.00: configured for UDMA/133
[  135.150236] sd 2:0:0:0: [sda] Unhandled sense code
[  135.150242] sd 2:0:0:0: [sda]  
[  135.150246] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  135.150251] sd 2:0:0:0: [sda]  
[  135.150255] Sense Key : Medium Error [current] [descriptor]
[  135.150263] Descriptor sense data with sense descriptors (in hex):
[  135.150266]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  135.150288]         01 49 9e 98 
[  135.150297] sd 2:0:0:0: [sda]  
[  135.150303] Add. Sense: Unrecovered read error - auto reallocate failed
[  135.150309] sd 2:0:0:0: [sda] CDB: 
[  135.150312] Read(16): 88 00 00 00 00 00 01 49 9e 80 00 00 04 00 00 00
[  135.150337] end_request: I/O error, dev sda, sector 21601944
[  135.150511] ata3: EH complete
[  140.438299] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  140.438436] ata3.00: irq_stat 0x40000008
[  140.438518] ata3.00: failed command: READ FPDMA QUEUED
[  140.438642] ata3.00: cmd 60/08:08:98:9e:49/00:00:01:00:00/40 tag 1 ncq 4096 in
[  140.438642]          res 41/40:00:98:9e:49/00:00:01:00:00/40 Emask 0x409 (media error) <F>
[  140.438919] ata3.00: status: { DRDY ERR }
[  140.438997] ata3.00: error: { UNC }
[  140.440517] ata3.00: configured for UDMA/133
[  140.440568] sd 2:0:0:0: [sda] Unhandled sense code
[  140.440574] sd 2:0:0:0: [sda]  
[  140.440579] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  140.440584] sd 2:0:0:0: [sda]  
[  140.440588] Sense Key : Medium Error [current] [descriptor]
[  140.440597] Descriptor sense data with sense descriptors (in hex):
[  140.440600]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  140.440622]         01 49 9e 98 
[  140.440632] sd 2:0:0:0: [sda]  
[  140.440638] Add. Sense: Unrecovered read error - auto reallocate failed
[  140.440692] sd 2:0:0:0: [sda] CDB: 
[  140.440718] Read(16): 88 00 00 00 00 00 01 49 9e 98 00 00 00 08 00 00
[  140.440780] end_request: I/O error, dev sda, sector 21601944
[  140.440922] ata3: EH complete
[  140.440980] md/raid1:md0: sda: unrecoverable I/O read error for block 21319296
[  140.441630] md: md0: recovery interrupted.
[  140.784750] RAID1 conf printout:
[  140.784779]  --- wd:1 rd:2
[  140.784785]  disk 0, wo:0, o:1, dev:sda2
[  140.784790]  disk 1, wo:1, o:1, dev:sdb2
[  140.788882] RAID1 conf printout:
[  140.788893]  --- wd:1 rd:2
[  140.788898]  disk 0, wo:0, o:1, dev:sda2

```

and the array fails to rebuild:
```
~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sat Apr  7 18:03:13 2012
     Raid Level : raid1
     Array Size : 1953512312 (1863.01 GiB 2000.40 GB)
  Used Dev Size : 1953512312 (1863.01 GiB 2000.40 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Sat May 31 13:38:13 2014
          State : clean, degraded 
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

           Name : davesbox:0  (local to host davesbox)
           UUID : 9f00f1e6:f6c20318:c7e3f8ff:49d49467
         Events : 29923

    Number   Major   Minor   RaidDevice State
       2       8        2        0      active sync   /dev/sda2
       1       0        0        1      removed

       3       8       18        -      spare   /dev/sdb2

```

This drive is new, and I think doesn't report any smart errors: ```
~# smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-27-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD40EURX-64WRWY0
Serial Number:    WD-WCC4E1260378
LU WWN Device Id: 5 0014ee 2b4941ee3
Firmware Version: 80.00A80
User Capacity:    4,000,787,030,016 bytes [4.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Sat May 31 13:43:37 2014 BST
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
data collection:         (52380) seconds.
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
recommended polling time:      ( 524) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x703d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   171   164   051    Pre-fail  Always       -       159
  3 Spin_Up_Time            0x0027   178   178   021    Pre-fail  Always       -       8075
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       13
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       17
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       13
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       5
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       7
194 Temperature_Celsius     0x0022   120   113   000    Old_age   Always       -       32
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       11
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

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

I've still got the old disks, but as the array is in use I guess that data i now out of date?  I tried removing the new sdb drive, putting the old sdb back in place, but (probably not surprisingly) mdadm doesn't like that: ```
~# mdadm --re-add /dev/md0 /dev/sdb1
mdadm: --re-add for /dev/sdb1 to/dev/md0 is not possible
```

Help!

What's wrong with my new drive (sda)?  Is there really a media error?
How can I get back to a fully working array? (lets assume that I, errr, don't have backups - except the drives mentioned.)
Can I use one of the old drives to "repair" the data I currently can't read from the new sda drive?

For good measure, here's the smart report for the new hdb (which I'm trying to rebuild to)```
~# smartctl -a /dev/sdb
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-27-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD40EURX-64WRWY0
Serial Number:    WD-WCC4E1248468
LU WWN Device Id: 5 0014ee 209e958f8
Firmware Version: 80.00A80
User Capacity:    4,000,787,030,016 bytes [4.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Sat May 31 13:54:29 2014 BST
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
data collection:         (51360) seconds.
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
recommended polling time:      ( 513) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x703d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   253   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   177   176   021    Pre-fail  Always       -       8116
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       9
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       3
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       9
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       4
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       4
194 Temperature_Celsius     0x0022   120   114   000    Old_age   Always       -       32
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

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

Any help will be greatly appreciated!

---


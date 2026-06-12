---
title: "RAID5 MDADM Problems"
date: 2016-10-16
forum: General Help
---

### Post by gianni-muretto on 2016-10-16
I already tried plenty of things from different sources and finally completely lost the overview.

I am using a HP Proliant Microserver Gen8 with 4x 2TB Disks in RAID5 via MDADM (no spare disk, all disks in RAID5). Since I was moving to my new flat a few days ago, I found out that my RAID does not work anymore. Please advise.

```
sudo mdadm --examine /dev/sd[a,b,c,e]
```

gives me

```
/dev/sda: 
  MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
/dev/sde:
MBR Magic : aa55
Partition[0] :   3907029167 sectors at 1 (type ee)




```

```
sudo mdadm --examine /dev/sd[a,b,c,e]1
```

gives me

```
/dev/sda1: 
         Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : bde64026:64cd0693:ac9eaa09:248c1d9f
           Name : SPACEBALL1:0  (local to host SPACEBALL1)
  Creation Time : Tue Jul 22 20:56:20 2014
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=1024 sectors
          State : clean
    Device UUID : 487006ab:5ec4c2e8:52865188:8f41c365


    Update Time : Sun Oct 16 09:21:37 2016
       Checksum : ca2852f0 - correct
         Events : 34272


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : spare
   Array State : .AA. ('A' == active, '.' == missing, 'R' == replacing)

==================================


/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : bde64026:64cd0693:ac9eaa09:248c1d9f
           Name : SPACEBALL1:0  (local to host SPACEBALL1)
  Creation Time : Tue Jul 22 20:56:20 2014
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=1024 sectors
          State : clean
    Device UUID : 826ca966:c33e2409:86480ff8:59864858


    Update Time : Sun Oct 16 09:21:37 2016
       Checksum : 86fd089 - correct
         Events : 34272


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1

==================================


/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : bde64026:64cd0693:ac9eaa09:248c1d9f
           Name : SPACEBALL1:0  (local to host SPACEBALL1)
  Creation Time : Tue Jul 22 20:56:20 2014
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=1024 sectors
          State : clean
    Device UUID : e71aa0e4:b6a73a6c:c90b61d7:a059b612


    Update Time : Sun Oct 16 09:21:37 2016
       Checksum : 833c7e6c - correct
         Events : 34272


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2

==================================

/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : bde64026:64cd0693:ac9eaa09:248c1d9f
           Name : SPACEBALL1:0  (local to host SPACEBALL1)
  Creation Time : Tue Jul 22 20:56:20 2014
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
     Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262064 sectors, after=1024 sectors
          State : active
    Device UUID : 6945ec2b:b6a682b2:e6dea56f:01b08d13


    Update Time : Sun Oct 16 00:06:07 2016
       Checksum : a9ec4b41 - correct
         Events : 33250


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)



```

Sidemark: When entering this, I also get the message "mdadm: no md superblock detected on /dev/sdd1"

I also checked all drives with

```
sudo smartctl -Hc /dev/sdX1
```

All results are: "PASSED"

```
cat /etc/mdadm/mdadm.conf
```

says

```
# mdadm.conf#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=bde64026:64cd0693:ac9eaa09:248c1d9f name=SPACEBALL1:0



```

```
mdadm -D /dev/md0
```

gives me

```
/dev/md0:        Version : 1.2
     Raid Level : raid0
  Total Devices : 4
    Persistence : Superblock is persistent


          State : inactive


           Name : SPACEBALL1:0  (local to host SPACEBALL1)
           UUID : bde64026:64cd0693:ac9eaa09:248c1d9f
         Events : 34272


    Number   Major   Minor   RaidDevice


       -       8        1        -        /dev/sda1
       -       8       17        -        /dev/sdb1
       -       8       33        -        /dev/sdc1
       -       8       65        -        /dev/sde1



```

```
cat /proc/mdstat
```

gives me 

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] md0 : inactive sde1[4](S) sdb1[1](S) sda1[5](S) sdc1[2](S)
      7813529600 blocks super 1.2
       
unused devices: <none>



```

---

### Post by frostschutz on 2016-10-16
Please use ```
 tags for output instead of > [ quote] or whatever you used. It's not readable.

You have two failed drives. /dev/sde1 failed first ( Sun Oct 16 00:06:07 2016 ), the others failed nine hours later with some activity in between (+1000 Event Count). /dev/sda1 does not believe itself to be part of the array at all (spare), that's strange.

Don't check your drives with smartctl -H. That always says "passed" no matter how broken the drive is. Give the full output of smartctl -a (in code tags please) for each drive, run selftests with smartctl -t long. If you have any drives with bad sectors you will have to buy new drives, and copy with ddrescue, before making any further attempts at recovery.

If the drives are intact you can attempt recovery using an overlay like described here: [https://raid.wiki.kernel.org/index.php/Recovering_a_failed_software_RAID#Making_the_harddisks_read-only_using_an_overlay_file](https://raid.wiki.kernel.org/index.php/Recovering_a_failed_software_RAID#Making_the_harddisks_read-only_using_an_overlay_file)

And using said overlay, play with mdadm --create (doing --create wrong will lose you all data) and/or --assemble --force. **Do NOT try this without an overlay or full disk copy.**

[code]
# Experiment 1
mdadm --assemble --force /dev/md0 /dev/overlay/sdb1 /dev/overlay/sdc1 /dev/overlay/sde1
# Experiment 2
mdadm --create /dev/md0 --assume-clean --metadata=1.2 --level=5 --chunk=512 --layout=ls --data-offset=128M --raid-devices=4 /dev/overlay/sda1 /dev/overlay/sdb1 /dev/overlay/sdc1 missing

```

---

### Post by gianni-muretto on 2016-10-17
Hi Frostschutz and thanks for you reply.

Sorry, I will use code tags from now on :)

Funny thing: It seems that my server renamed one of the disks, sde1 is now sdd1... strange...

```
sudo smartctl -a /dev/sdbX
```

_**sda1:**_

```

=== START OF INFORMATION SECTION 
===Model Family:     Western Digital Caviar Green
Device Model:     WDC WD20EADS-00R6B0
Serial Number:    WD-WCAVY2279881
LU WWN Device Id: 5 0014ee 203fa907e
Firmware Version: 01.00A01
User Capacity:    2.000.398.934.016 bytes [2,00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Mon Oct 17 22:32:04 2016 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (40800) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 464) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   173   144   021    Pre-fail  Always       -       8325
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1005
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   066   066   000    Old_age   Always       -       25294
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       994
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       325
193 Load_Cycle_Count        0x0032   173   173   000    Old_age   Always       -       82473
194 Temperature_Celsius     0x0022   119   103   000    Old_age   Always       -       33
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       31
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       21
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      90%     25293         -
# 2  Short offline       Completed: read failure       90%     25273         2997435951
# 3  Conveyance offline  Completed: read failure       90%     25273         2997435951
# 4  Extended offline    Completed without error       00%     13101         -



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

_**sdb1:**_

```

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF)
Device Model:     WDC WD20EARS-07MVWB0
Serial Number:    WD-WCAZA4205101
LU WWN Device Id: 5 0014ee 25adaec87
Firmware Version: 51.0AB51
User Capacity:    2.000.398.934.016 bytes [2,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Mon Oct 17 22:33:30 2016 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (36660) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 354) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3035) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   253   253   021    Pre-fail  Always       -       1033
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       611
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   080   080   000    Old_age   Always       -       15230
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       609
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       242
193 Load_Cycle_Count        0x0032   193   193   000    Old_age   Always       -       21256
194 Temperature_Celsius     0x0022   120   106   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      90%     15229         -
# 2  Short offline       Completed without error       00%     15208         -
# 3  Conveyance offline  Completed without error       00%     15208         -
# 4  Short offline       Completed without error       00%      2942         -
# 5  Short offline       Completed without error       00%      2441         -
# 6  Short offline       Completed without error       00%      1664         -


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



_**sdc1:**_

```

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF)
Device Model:     WDC WD20EARS-07MVWB0
Serial Number:    WD-WCAZA4205101
LU WWN Device Id: 5 0014ee 25adaec87
Firmware Version: 51.0AB51
User Capacity:    2.000.398.934.016 bytes [2,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Mon Oct 17 22:33:30 2016 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (36660) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 354) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3035) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   253   253   021    Pre-fail  Always       -       1033
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       611
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   080   080   000    Old_age   Always       -       15230
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       609
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       242
193 Load_Cycle_Count        0x0032   193   193   000    Old_age   Always       -       21256
194 Temperature_Celsius     0x0022   120   106   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      90%     15229         -
# 2  Short offline       Completed without error       00%     15208         -
# 3  Conveyance offline  Completed without error       00%     15208         -
# 4  Short offline       Completed without error       00%      2942         -
# 5  Short offline       Completed without error       00%      2441         -
# 6  Short offline       Completed without error       00%      1664         -


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



_**sdd1:**_

```

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green
Device Model:     WDC WD20EADS-00R6B0
Serial Number:    WD-WCAVY0028670
LU WWN Device Id: 5 0014ee 202949363
Firmware Version: 01.00A01
User Capacity:    2.000.398.934.016 bytes [2,00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Mon Oct 17 22:35:01 2016 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (42360) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 482) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x303f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       1342
  3 Spin_Up_Time            0x0027   171   143   021    Pre-fail  Always       -       8441
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1085
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   056   056   000    Old_age   Always       -       32653
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1076
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       261
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       823
194 Temperature_Celsius     0x0022   120   101   000    Old_age   Always       -       32
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   197   197   000    Old_age   Always       -       1171
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       197
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   182   182   000    Old_age   Offline      -       3661


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Interrupted (host reset)      90%     32652         -
# 2  Short offline       Completed: read failure       90%     32632         3709938467
# 3  Conveyance offline  Completed: read failure       90%     32632         3709939805
# 4  Extended offline    Completed without error       00%     20537         -


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

I started ```
sudo [COLOR=#000000]smartctl -t long /dev/sdX1[/COLOR]
```[COLOR=#000000] on all drives. The last drive will have finished the tests tomorrow. Where can I review the long tests' outcomes then?

Thanks for your support :)[/COLOR]

---

### Post by frostschutz on 2016-10-17
smartctl is always on the disk itself (sda) as opposed to a partition (sda1).

your sda disk has serious issues (31 pending sectors, 21 uncorrectables), same for sdd (1171 pending, 197 uncorrectable). that's super bad. get replacements and hope that ddrescue will be able to get most of it.

your selftests were aborted for some reason (# 1  Extended offline    Interrupted (host reset)) perhaps you rebooted after starting them, or cancelled them somehow, or you had a bus reset (check dmesg).

---


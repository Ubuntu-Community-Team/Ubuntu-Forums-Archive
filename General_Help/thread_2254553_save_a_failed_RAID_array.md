---
title: "save a failed RAID array"
date: 2014-11-28
forum: General Help
---

### Post by buffchick on 2014-11-28
I have a machine where the sata card failed and caused me to lose my raid array. I tested the drives externally and they are in good shape. I have moved the drives to a new machine (with enough onboard sata ports) and am attempting to get the array back up but I've run into problems. It's a RAID 5 array with 4 drives. It appears one of the drives is not in the array. I'm running ubuntu 14.04 and the current mdadm.conf is still the default. I have the old mdadm.conf information. I'd really like to preserve the data on the drives. Suggestions?

Here's what mdadm has to say:

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : inactive sdd1[2] sde1[4] sdb1[5]
      5860537608 blocks super 1.2
```

```
sudo mdadm --examine /dev/sd[bcde]1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x2
     Array UUID : ef1b89aa:a2bbaab9:2ce4bdd0:47832afb
           Name : mediaserver:0
  Creation Time : Tue Aug  6 08:38:10 2013
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907025072 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
Recovery Offset : 1799197544 sectors
   Unused Space : before=1968 sectors, after=1200 sectors
          State : clean
    Device UUID : 968168e5:6c695c7b:66a78ba1:9bccdc80

    Update Time : Sun Sep 29 16:09:54 2013
       Checksum : dd82d9a - correct
         Events : 47568

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : .AAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : ef1b89aa:a2bbaab9:2ce4bdd0:47832afb
           Name : mediaserver:0
  Creation Time : Tue Aug  6 08:38:10 2013
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907025072 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=1200 sectors
          State : clean
    Device UUID : 1da9199e:cc6fc424:128e502c:881d890a

    Update Time : Sun Sep 29 14:46:26 2013
       Checksum : 1923ec18 - correct
         Events : 47565

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : ef1b89aa:a2bbaab9:2ce4bdd0:47832afb
           Name : mediaserver:0
  Creation Time : Tue Aug  6 08:38:10 2013
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907025072 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=1200 sectors
          State : clean
    Device UUID : 3688a662:e042319b:017fe47f:a73d04b2

    Update Time : Sun Sep 29 16:09:54 2013
       Checksum : 4f2dc2e7 - correct
         Events : 47568

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : .AAA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : ef1b89aa:a2bbaab9:2ce4bdd0:47832afb
           Name : mediaserver:0
  Creation Time : Tue Aug  6 08:38:10 2013
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907025072 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=1200 sectors
          State : clean
    Device UUID : 173cc321:8c8b416a:635388f7:3dd0bb3e

    Update Time : Sun Sep 29 16:09:54 2013
       Checksum : e1b6266d - correct
         Events : 47568

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : .AAA ('A' == active, '.' == missing, 'R' == replacing)
```

With array stopped
```
sudo mdadm --assemble --scan -v
mdadm: looking for devices for further assembly
mdadm: no RAID superblock on /dev/sde
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdc
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sda5
mdadm: no RAID superblock on /dev/sda2
mdadm: no RAID superblock on /dev/sda1
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sde1 is identified as a member of /dev/md/mediaserver:0, slot 3.
mdadm: /dev/sdd1 is identified as a member of /dev/md/mediaserver:0, slot 1.
mdadm: /dev/sdc1 is identified as a member of /dev/md/mediaserver:0, slot 0.
mdadm: /dev/sdb1 is identified as a member of /dev/md/mediaserver:0, slot 2.
mdadm: added /dev/sdc1 to /dev/md/mediaserver:0 as 0 (possibly out of date)
mdadm: added /dev/sdb1 to /dev/md/mediaserver:0 as 2
mdadm: added /dev/sde1 to /dev/md/mediaserver:0 as 3
mdadm: added /dev/sdd1 to /dev/md/mediaserver:0 as 1
mdadm: /dev/md/mediaserver:0 assembled from 2 drives and 1 rebuilding - not enough to start the array.
mdadm: looking for devices for further assembly
mdadm: No arrays found in config file or automatically
```

```
sudo mdadm --detail --scan
ARRAY /dev/md127 metadata=1.2 spares=1 name=mediaserver:0 UUID=ef1b89aa:a2bbaab9:2ce4bdd0:47832afb
```

I also tried:
```
sudo mdadm --assemble /dev/md127 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: /dev/md127 assembled from 2 drives and 1 rebuilding - not enough to start the array.
```

---

### Post by tgalati4 on 2014-11-28
What is the SMART status of the drive that is not included?

```
sudo smartctl -a /dev/sdc
```

It's possible that the drive enumeration has changed.  Try moving the cables around.  Keep track of which SATA port is plugged into what drive.  I would presume that you want a sequential order, not:

> 
mdadm: /dev/sde1 is identified as a member of /dev/md/mediaserver:0, slot 3.
mdadm: /dev/sdd1 is identified as a member of /dev/md/mediaserver:0, slot 1.
mdadm: /dev/sdc1 is identified as a member of /dev/md/mediaserver:0, slot 0.
mdadm: /dev/sdb1 is identified as a member of /dev/md/mediaserver:0, slot 2.


---

### Post by buffchick on 2014-11-29
Here you go. but I already did this for all drives and they passed.

```
sudo smartctl -a /dev/sdc
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.16.0-23-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda LP
Device Model:     ST32000542AS
Serial Number:    6XW1S5KT
LU WWN Device Id: 5 000c50 02b52710a
Firmware Version: CC34
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5900 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Sat Nov 29 00:47:17 2014 EST

==> WARNING: A firmware update for this drive may be available,
see the following Seagate web pages:
http://knowledge.seagate.com/articles/en_US/FAQ/207931en
http://knowledge.seagate.com/articles/en_US/FAQ/213915en

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (  633) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 437) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x103f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   108   099   006    Pre-fail  Always       -       19073554
  3 Spin_Up_Time            0x0003   100   100   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       342
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -       31216932
  9 Power_On_Hours          0x0032   078   078   000    Old_age   Always       -       20029
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       348
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   078   041   045    Old_age   Always   In_the_past 22 (0 23 22 21 0)
194 Temperature_Celsius     0x0022   022   059   000    Old_age   Always       -       22 (0 8 0 0 0)
195 Hardware_ECC_Recovered  0x001a   037   021   000    Old_age   Always       -       19073554
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       1
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       257698058238
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3194407957
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       534490404

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      6979         -
# 2  Short offline       Completed without error       00%      5954         -
# 3  Short offline       Completed without error       00%      4150         -

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

### Post by buffchick on 2014-12-09
I've tried some steps based on suggestions from other forums. it looks like the data is still there. Still looking for further help

```
sudo mdadm --manage /dev/md127 --re-add /dev/sdc1
mdadm: --re-add for /dev/sdc1 to /dev/md127 is not possible
```
```
sudo mdadm --assemble /dev/md127 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: /dev/md127 assembled from 2 drives and 1 rebuilding - not enough to start the array.
```
```
sudo mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Tue Aug  6 08:38:10 2013
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Sun Sep 29 16:09:54 2013
          State : active, FAILED, Not Started
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : mediaserver:0
           UUID : ef1b89aa:a2bbaab9:2ce4bdd0:47832afb
         Events : 47568

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       2       8       49        1      active sync   /dev/sdd1
       5       8       17        2      spare rebuilding   /dev/sdb1
       4       8       65        3      active sync   /dev/sde1
```
```
sudo mdadm --assemble --force -vv /dev/md127 /dev/sdb1 /dev/sdd1 /dev/sde1
mdadm: looking for devices for /dev/md127
mdadm: /dev/sdb1 is identified as a member of /dev/md127, slot 2.
mdadm: /dev/sdd1 is identified as a member of /dev/md127, slot 1.
mdadm: /dev/sde1 is identified as a member of /dev/md127, slot 3.
mdadm: no uptodate device for slot 0 of /dev/md127
mdadm: added /dev/sdb1 to /dev/md127 as 2
mdadm: added /dev/sde1 to /dev/md127 as 3
mdadm: added /dev/sdd1 to /dev/md127 as 1
mdadm: /dev/md127 assembled from 2 drives and 1 rebuilding - not enough to start the array.
```
original mdadm.conf
```
# mdadm.conf
#
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
#ARRAY /dev/md0  UUID=ef1b89aa:a2bbaab9:2ce4bdd0:47832afb

# This file was auto-generated on Mon, 11 Jun 2012 18:04:27 -0500
# by mkconf $Id$
```
Three different folks on three different sites suggested use --force so I  did. Not sure that was the best idea in retrospect. Here's what I  got...
```
sudo mdadm --assemble --force /dev/md127 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: forcing event count in /dev/sdc1(0) from 47565 upto 47568
mdadm: /dev/md127 assembled from 3 drives and 1 rebuilding - not enough to start the array. 
```
I think that was a bad idea... they're all marked spares now...
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : inactive sdd1[2](S) sdc1[0](S) sde1[4](S) sdb1[5](S)
      7814050144 blocks super 1.2
```

---

### Post by tgalati4 on 2014-12-09
Is it possible that the RAID was rebuilding during the -force command and you did not give it enough time to finish?  It can take a while.

---


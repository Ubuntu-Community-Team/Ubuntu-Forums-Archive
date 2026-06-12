---
title: "Issues with RAID"
date: 2014-01-01
forum: General Help
---

### Post by griztown on 2014-01-01
Hi all,

I'm seeing some strange issues with my Ubuntu machine. I have several raid arrays, two RAID 1s and one RAID 5. Recently it has been booting in degraded mode, why I'm not sure. Each time I use mdadm to add the partition back to the array. This seems to work until I reboot when it is degraded again. I'm wondering if there is some step I'm missing after I get the array back up and running? Perhaps my mdadm.conf file is corrupted?

But the scariest thing I've noticed is files go missing that are more recent. I don't understand why this would be. The files I'm missing are on the RAID 1 array so both disks should be an exact copy right? If I have one I should have all files right? But for some reason some are missing. I readd the missing disk to the array and it rebuilds it, I have a lost any chance of saving those files? 

Thanks in advance.

---

### Post by SaturnusDJ on 2014-01-01
After rebuild the disks should be almost identical, so you won't find your lost files based on raid level.

So you need to find out whats up here...
Begin with reading S.M.A.R.T. for each disk.

```
smartctl -a /dev/sda
```

Then post all examine's for the array members:
```
mdadm --examine /dev/sd*
```

---

### Post by griztown on 2014-01-01
Thanks for your reply. Attached is the output for the S.M.A.R.T. tool. Output is in the following order: sda, sdb, sdc. Appears to have found two errors with sdc.
 [ATTACH]249081[/ATTACH]

---

### Post by griztown on 2014-01-01
Here's the output for the examine commands. I ran it in this order: sda1, sda5, sda6, sdb1, sdb5, sdb6, sdc1, sdc5, sdc6.[ATTACH]249082[/ATTACH]

---

### Post by SaturnusDJ on 2014-01-01
Something went wrong with the SMART logs, please post again. You may post inline using the code-tag.

Concerning raid, definitely something strange going on.
Looking at the examine's, RAID5 is fine. The two raid1 arrays both exist from 2 drives, but there appears to be a not used third one for both arrays that may cause trouble.

Please provide the output of this commands:
```

cat /proc/mdstat
mdadm --detail /dev/md*

```

---

### Post by griztown on 2014-01-01
Here's the output for smartctl -a /dev/sdc

```

smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-57-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=======> INVALID ARGUMENT TO -t: /dev/sdc
=======> VALID ARGUMENTS ARE: offline, short, long, conveyance, vendor,N, select,M-N, pending,N, afterselect,[on|off], scttempint,N[,p] <=======

Use smartctl -h to get a usage summary

tbrenner@ubuntu-main:~$ 
tbrenner@ubuntu-main:~$ sudo smartctl -a /dev/sdc 
[sudo] password for tbrenner: 
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-57-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint F3
Device Model:     SAMSUNG HD103SJ
Serial Number:    S246J9BB106093
LU WWN Device Id: 5 0024e9 2043b2cd0
Firmware Version: 1AJ10001
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Wed Jan  1 16:53:27 2014 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		( 9300) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 155) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       8
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   071   070   025    Pre-fail  Always       -       8877
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       108
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       23645
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       133
191 G-Sense_Error_Rate      0x0022   252   252   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   058   000    Old_age   Always       -       32 (Min/Max 18/42)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       11
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       262
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       133

SMART Error Log Version: 1
ATA Error Count: 2
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

Error 2 occurred at disk power-on lifetime: 20781 hours (865 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 00      00:00:01.326  IDENTIFY DEVICE
  00 00 00 00 00 00 e0 08      00:00:01.325  NOP [Abort queued commands]
  00 00 01 08 f0 0e 40 08      00:00:01.325  NOP [Abort queued commands]
  00 00 a0 00 e3 5e 40 08      00:00:01.320  NOP [Abort queued commands]
  61 00 00 30 71 c2 40 08      00:00:01.274  WRITE FPDMA QUEUED

Error 1 occurred at disk power-on lifetime: 20781 hours (865 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 00 00 00 00 a0 00      00:00:01.303  IDENTIFY DEVICE
  00 00 00 00 00 00 00 08      00:00:01.303  NOP [Abort queued commands]
  00 00 00 00 00 00 00 08      00:00:01.303  NOP [Abort queued commands]
  00 00 10 20 71 c2 40 08      00:00:01.298  NOP [Abort queued commands]
  61 00 90 10 e3 5e 40 08      00:00:01.272  WRITE FPDMA QUEUED

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

for cat /proc/mdstat
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid5 sda6[1] sdc6[3] sdb5[2]
      1561656320 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
md1 : active raid1 sdc5[2] sda5[1]
      195180416 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sdb1[2] sda1[1]
      487104 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

```

for mdadm --detail /dev/md0
```

/dev/md0:
        Version : 1.2
  Creation Time : Sat Sep 22 08:34:01 2012
     Raid Level : raid1
     Array Size : 487104 (475.77 MiB 498.79 MB)
  Used Dev Size : 487104 (475.77 MiB 498.79 MB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Dec  9 17:36:03 2013
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : ubuntu-main:0  (local to host ubuntu-main)
           UUID : a04b3379:480ef690:b365aeb3:aacd93e7
         Events : 150

    Number   Major   Minor   RaidDevice State
       2       8       17        0      active sync   /dev/sdb1
       1       8        1        1      active sync   /dev/sda1

```

for mdadm --detail /dev/md1
```

/dev/md1:
        Version : 1.2
  Creation Time : Sat Sep 22 08:39:39 2012
     Raid Level : raid1
     Array Size : 195180416 (186.14 GiB 199.86 GB)
  Used Dev Size : 195180416 (186.14 GiB 199.86 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Wed Jan  1 16:57:32 2014
          State : active 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : ubuntu-main:1  (local to host ubuntu-main)
           UUID : c6662562:50dc0b26:8dfcf367:dad97b53
         Events : 5073515

    Number   Major   Minor   RaidDevice State
       2       8       37        0      active sync   /dev/sdc5
       1       8        5        1      active sync   /dev/sda5

```

for mdadm --detail /dev/md2
```

/dev/md2:
        Version : 1.2
  Creation Time : Sat Sep 22 08:45:56 2012
     Raid Level : raid5
     Array Size : 1561656320 (1489.31 GiB 1599.14 GB)
  Used Dev Size : 780828160 (744.66 GiB 799.57 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent

    Update Time : Wed Jan  1 16:58:00 2014
          State : clean 
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : ubuntu-main:2  (local to host ubuntu-main)
           UUID : be00c1db:43eba4f8:4eacb439:420f9fa5
         Events : 611373

    Number   Major   Minor   RaidDevice State
       3       8       38        0      active sync   /dev/sdc6
       1       8        6        1      active sync   /dev/sda6
       2       8       21        2      active sync   /dev/sdb5

```

Thanks for the help!

---

### Post by SaturnusDJ on 2014-01-02
/dev/sdc is okay. If UDMA_CRC_Error_Count is increasing, you need to replace the SATA data cable.
What about the others?

Concerning /dev/md0...
/dev/sdc1 believes it is an array member, while I don't think it is.

The same goes for array /dev/md1 versus 'member' /dev/sdb6.

Both these 'members' have an outdated event count AND the information says there should not be a third partition.
They might interfere the assemble process during boot.

My advise:
Mount these 'fake members' as normal devices (that's possible with raid1 members but strongly not recommended for working arrays) and see what's on them. If there are files that are not on the main arrays (md0, md1) you may safe those files to them. The files could be corrupted. That's up to you to find out.
After having analyzed these 'fake members,' destroy the raid layer.

First make sure these partitions are not mentioned in the output of
```
cat /proc/mdstat
```
if the case is that you have rebooted for example meanwhile.
Then:
```

mdadm --zero-superblock /dev/sdc1
mdadm --zero-superblock /dev/sdb6

```
Chances are booting goes fine now. To be sure, post your mdadm.conf.

Also, I'm missing some logic here:
[IMG]http://i40.tinypic.com/2efn8s1.png[/IMG]
Not a problem, but why did you build the arrays this way?

---

### Post by griztown on 2014-01-03
Thanks SaturnusDJ. Sadly, I'm not sure there was any logic when I created it. It was my first time doing so. I wanted a small RAID 1 for the boot partition. I also wanted a larger RAID 5 for my data. Then, for some reason, I chose RAID 1 for the root directory. Oh well.

So, just to be clear, are you suggesting I remove sdc1 and sdb6 from the RAID arrays and mount them like a normal drive? 

Here's the output from the S.M.A.R.T. command on the other drives.
```

$ sudo smartctl -a /dev/sda 
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-57-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint F3
Device Model:     SAMSUNG HD103SJ
Serial Number:    S246J90B142567
LU WWN Device Id: 5 0024e9 204540be2
Firmware Version: 1AJ10001
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Fri Jan  3 08:25:35 2014 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		( 9240) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 154) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   071   069   025    Pre-fail  Always       -       9053
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       84
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       22687
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       113
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       6
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   060   000    Old_age   Always       -       27 (Min/Max 17/40)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       60
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       113

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

```

$ sudo smartctl -a /dev/sdb
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-57-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint F3
Device Model:     SAMSUNG HD103SJ
Serial Number:    S246J9BB106095
LU WWN Device Id: 5 0024e9 2043b2cde
Firmware Version: 1AJ10001
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Fri Jan  3 08:26:29 2014 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		( 9240) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 154) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   071   070   025    Pre-fail  Always       -       8895
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       107
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       23685
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       131
191 G-Sense_Error_Rate      0x0022   252   252   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   060   000    Old_age   Always       -       28 (Min/Max 17/40)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       92
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       131

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

### Post by SaturnusDJ on 2014-01-03
You don't need to remove them because they are currently not in an array. They are like ghost members or so.

Yes mount them as they were non-raid drives, get missing stuff of them, then zero-superblock.

---

### Post by griztown on 2014-01-03
Thanks again SaturnusDJ. Not being a UNIX admin expert, what would be the simplest way to mount those and then zero-superblock them?

---

### Post by griztown on 2014-01-03
Thanks again SaturnusDJ. Not being a UNIX admin expert, what would be the simplest way to mount those and then zero-superblock them?

---

### Post by griztown on 2014-01-03
Is there a way around this?

```

$ sudo mount /dev/sdb6 /mnt
mount: unknown filesystem type 'linux_raid_member'

```

---

### Post by SaturnusDJ on 2014-01-03
Just with the normal mount command to a location inside the root (/).

Edit:
Ah page 2 and you've got the mount command. Good.

Try with the t flag.
Like
```
mount -t ext4 /dev/sdb6 /temporary
```

---

### Post by griztown on 2014-01-03
Hmmm, didn't like that.

```

$ sudo mount -t ext4 /dev/sdb6 /temporary
mount: wrong fs type, bad option, bad superblock on /dev/sdb6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I also tried ext3 and ext2

---

### Post by SaturnusDJ on 2014-01-03
Okay. I don't know why normal mount isn't working. Maybe the filesystem is corrupt already.

You may try this: [http://blog.sleeplessbeastie.eu/2012/05/08/how-to-mount-software-raid1-member-using-mdadm/](http://blog.sleeplessbeastie.eu/2012/05/08/how-to-mount-software-raid1-member-using-mdadm/)
Start an **new** array using the member. Then mount, pull stuff off, stop the array, destroy the superblock.

---

### Post by griztown on 2014-01-04
Thanks. I did that and then I got this error:

```

$ sudo mount /dev/md3 /temporary
mount: unknown filesystem type 'LVM2_member'

```

I typed sudo pvdisplay and it shows a conflict.
```

$ sudo pvdisplay
  Found duplicate PV xny33Ds5AmHaUCNkeJRt7NkD879l4kNV: using /dev/md3 not /dev/md1

```

Is it possible to rename it? So I could have separate versions? Looks like pvchange -u will do this. Just want to make sure I did this correctly. Would I use it like so?

```

sudo pvchange -u /dev/md3

```

---

### Post by griztown on 2014-01-04
Okay, I tried changing the pv ID but got an error:

```

$ sudo pvchange -u /dev/md3
  Found duplicate PV xny33Ds5AmHaUCNkeJRt7NkD879l4kNV: using /dev/md1 not /dev/md3
  Unable to find /dev/md3 in vgUbuntu
  0 physical volumes changed / 0 physical volumes not changed
  Internal error: Volume Group vgUbuntu was not unlocked
  Device '/dev/md3' has been left open.
  Device '/dev/md3' has been left open.
  Device '/dev/md1' has been left open.
  Device '/dev/md3' has been left open.
  Device '/dev/md3' has been left open.
  Device '/dev/md3' has been left open.
  Device '/dev/md1' has been left open.
  You have a memory leak (not released memory pool):
   [0xc2a460]
  You have a memory leak (not released memory pool):
   [0xc2a460]

```

I tried changing the volume group name but that told me I have active volumes. Since my root directory is in vgUbuntu, I'm a little nervous about doing more. Since you mentioned that the files are most likely corrupted, is it worth going further? I suppose I could create a live CD and try tinkering with it that way?

---

### Post by SaturnusDJ on 2014-01-05
LiveCD definitely is the way to go!

---


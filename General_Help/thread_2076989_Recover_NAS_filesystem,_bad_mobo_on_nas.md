---
title: "Recover NAS filesystem, bad mobo on nas"
date: 2012-10-27
forum: General Help
---

### Post by Mautobu on 2012-10-27
My NAS is an IOmega Storcenter Pro ix4-100. The drives (from what I can tell) are all good. The board is bad. I'm attempting to plug in the drives to a box to recover files from a live distro, but haven't had any luck yet. I've tried:

mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1

with no luck. It's a 4 drive array of 500 gb drives.

---

### Post by Mautobu on 2012-10-28
Shameless self bump. They're all linux raid members.

---

### Post by steeldriver on 2012-10-28
What does "with no luck" mean, exactly? what is the actual error message from mdadm?

You *may* have better luck letting it scan for the array rather than specifying everything explicitly

```
mdadm --assemble --scan
```

---

### Post by Mautobu on 2012-11-01
Well, this is what I get from that first command I tried:

```
mdadm: no recogniseable superblock on /dev/sde1
mdadm: /dev/sde1 has no superblock - assembly aborted
```

And from --assemble --scan I get:

```
mdadm: No arrays found in config file or automatically
```


Thoughts?


-EDIT-

I've run mdadm --examine /dev/sd*

```
/dev/sdb:
   MBR Magic : aa55
Partition[0] :      2040254 sectors at            1 (type 83)
Partition[1] :    974727810 sectors at      2040255 (type 83)
mdadm: No md superblock detected on /dev/sdb1.
mdadm: No md superblock detected on /dev/sdb2.
/dev/sdc:
   MBR Magic : aa55
Partition[0] :      2040254 sectors at            1 (type 83)
Partition[1] :    974727810 sectors at      2040255 (type 83)
mdadm: No md superblock detected on /dev/sdc1.
mdadm: No md superblock detected on /dev/sdc2.
/dev/sdd:
   MBR Magic : aa55
Partition[0] :      2040254 sectors at            1 (type 83)
Partition[1] :    974727810 sectors at      2040255 (type 83)
mdadm: No md superblock detected on /dev/sdd1.
mdadm: No md superblock detected on /dev/sdd2.
/dev/sde:
   MBR Magic : aa55
Partition[0] :      2040254 sectors at            1 (type 83)
Partition[1] :    974727810 sectors at      2040255 (type 83)
mdadm: No md superblock detected on /dev/sde1.
mdadm: No md superblock detected on /dev/sde2.
```


-EDIT- 
-AGAIN-

```
sudo mdadm --create /dev/md1 --assume-clean -l5 -n4 -c64 /dev/sd{b,c,d,e}1
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=1020032K  mtime=Wed Dec 31 19:02:42 1969
mdadm: /dev/sdc1 appears to contain an ext2fs file system
    size=1020032K  mtime=Wed Dec 31 19:02:42 1969
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=1020032K  mtime=Wed Dec 31 19:02:42 1969
mdadm: /dev/sde1 appears to contain an ext2fs file system
    size=1020032K  mtime=Wed Dec 31 19:02:42 1969
```

-EDIT-

So, I created a new array over top of the old one, it says there's a filesystem there (ext2fs), but I can't mount it.

```
sudo mount -t ext2 /dev/md1 /mnt/array/ -o ro
mount: wrong fs type, bad option, bad superblock on /dev/md1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by Mautobu on 2012-11-01
Some random info:

```
smartctl 5.42 2011-10-20 r3458 [x86_64-linux-2.6.32-279.el6.x86_64] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST3500820AS
Serial Number:    5QM3VGVK
LU WWN Device Id: 5 000c50 01234a8db
Firmware Version: SD25
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Nov  1 20:56:18 2012 EDT

==> WARNING: There are known problems with these drives,
see the following Seagate web pages:
http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207931
http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951
http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207957

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  642) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 118) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x103b)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   089   089   006    Pre-fail  Always       -       129799018
  3 Spin_Up_Time            0x0003   094   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       38
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       68
  7 Seek_Error_Rate         0x000f   070   060   030    Pre-fail  Always       -       12916773004
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       7291
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       38
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       441
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   001   001   000    Old_age   Always       -       106
190 Airflow_Temperature_Cel 0x0022   060   058   045    Old_age   Always       -       40 (Min/Max 34/40)
194 Temperature_Celsius     0x0022   040   042   000    Old_age   Always       -       40 (0 19 0 0 0)
195 Hardware_ECC_Recovered  0x001a   042   021   000    Old_age   Always       -       129799018
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       1979
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       1979
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 467 (device log contains only the most recent five errors)
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

Error 467 occurred at disk power-on lifetime: 7290 hours (303 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 01 01 00 00 a0 00      00:03:14.595  IDENTIFY DEVICE
  00 00 00 00 00 00 00 ff      00:03:14.287  NOP [Abort queued commands]
  ec 00 01 01 00 00 a0 00      00:03:09.268  IDENTIFY DEVICE
  00 00 00 00 00 00 00 04      00:03:09.112  NOP [Abort queued commands]
  ec 00 04 9d 00 32 a0 00      00:03:03.769  IDENTIFY DEVICE

Error 466 occurred at disk power-on lifetime: 7290 hours (303 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 01 01 00 00 a0 00      00:03:09.268  IDENTIFY DEVICE
  00 00 00 00 00 00 00 04      00:03:09.112  NOP [Abort queued commands]
  ec 00 04 9d 00 32 a0 00      00:03:03.769  IDENTIFY DEVICE
  25 00 00 01 04 04 e0 00      00:02:58.371  READ DMA EXT
  c8 00 00 01 02 04 e0 00      00:02:57.614  READ DMA

Error 465 occurred at disk power-on lifetime: 7290 hours (303 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 04 9d 00 32 a0 00      00:03:03.769  IDENTIFY DEVICE
  25 00 00 01 04 04 e0 00      00:02:58.371  READ DMA EXT
  c8 00 00 01 02 04 e0 00      00:02:57.614  READ DMA
  25 00 00 01 00 04 e0 00      00:02:57.604  READ DMA EXT
  c8 00 00 01 fe 03 e0 00      00:02:57.598  READ DMA

Error 464 occurred at disk power-on lifetime: 7290 hours (303 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0  Device Fault; Error: ABRT 4 sectors at LBA = 0x0032009d = 3276957

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 01 04 04 e0 00      00:02:58.371  READ DMA EXT
  c8 00 00 01 02 04 e0 00      00:02:57.614  READ DMA
  25 00 00 01 00 04 e0 00      00:02:57.604  READ DMA EXT
  c8 00 00 01 fe 03 e0 00      00:02:57.598  READ DMA
  25 00 00 01 fb 03 e0 00      00:02:57.590  READ DMA EXT

Error 463 occurred at disk power-on lifetime: 7290 hours (303 days + 18 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 e0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ec 00 01 01 00 00 a0 00      00:04:03.899  IDENTIFY DEVICE
  00 00 00 00 00 00 00 ff      00:04:03.591  NOP [Abort queued commands]
  ec 00 01 01 00 00 a0 00      00:03:58.572  IDENTIFY DEVICE
  00 00 00 00 00 00 00 04      00:03:58.416  NOP [Abort queued commands]
  ec 00 04 9d 00 32 a0 00      00:03:53.077  IDENTIFY DEVICE

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
```
smartctl 5.42 2011-10-20 r3458 [x86_64-linux-2.6.32-279.el6.x86_64] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST3500820AS
Serial Number:    5QM3V5MV
LU WWN Device Id: 5 000c50 01236f12a
Firmware Version: SD25
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Nov  1 20:56:24 2012 EDT

==> WARNING: There are known problems with these drives,
see the following Seagate web pages:
http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207931
http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951
http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207957

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  642) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 119) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x103b)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   108   099   006    Pre-fail  Always       -       20922341
  3 Spin_Up_Time            0x0003   094   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       37
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x000f   070   060   030    Pre-fail  Always       -       12926020233
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       7316
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       37
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   099   099   000    Old_age   Always       -       1
190 Airflow_Temperature_Cel 0x0022   059   053   045    Old_age   Always       -       41 (Min/Max 36/41)
194 Temperature_Celsius     0x0022   041   047   000    Old_age   Always       -       41 (0 19 0 0 0)
195 Hardware_ECC_Recovered  0x001a   024   020   000    Old_age   Always       -       20922341
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

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
```
smartctl 5.42 2011-10-20 r3458 [x86_64-linux-2.6.32-279.el6.x86_64] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST3500820AS
Serial Number:    5QM3V7CV
LU WWN Device Id: 5 000c50 01236f604
Firmware Version: SD25
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Nov  1 20:56:29 2012 EDT

==> WARNING: There are known problems with these drives,
see the following Seagate web pages:
http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207931
http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951
http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207957

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  642) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 116) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x103b)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   099   006    Pre-fail  Always       -       217045393
  3 Spin_Up_Time            0x0003   094   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       37
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   072   060   030    Pre-fail  Always       -       8631575404
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       7316
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       37
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   082   082   000    Old_age   Always       -       18
190 Airflow_Temperature_Cel 0x0022   059   057   045    Old_age   Always       -       41 (Min/Max 36/41)
194 Temperature_Celsius     0x0022   041   043   000    Old_age   Always       -       41 (0 20 0 0 0)
195 Hardware_ECC_Recovered  0x001a   039   026   000    Old_age   Always       -       217045393
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

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
```
smartctl 5.42 2011-10-20 r3458 [x86_64-linux-2.6.32-279.el6.x86_64] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST3500820AS
Serial Number:    5QM3V782
LU WWN Device Id: 5 000c50 01236ef17
Firmware Version: SD25
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Nov  1 20:56:34 2012 EDT

==> WARNING: There are known problems with these drives,
see the following Seagate web pages:
http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207931
http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207951
http://seagate.custkb.com/seagate/crm/selfservice/search.jsp?DocId=207957

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  642) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 119) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x103b)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       130600028
  3 Spin_Up_Time            0x0003   094   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       38
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -       4336280574
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       7316
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       38
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   088   088   000    Old_age   Always       -       12
190 Airflow_Temperature_Cel 0x0022   057   054   045    Old_age   Always       -       43 (Min/Max 36/43)
194 Temperature_Celsius     0x0022   043   046   000    Old_age   Always       -       43 (0 19 0 0 0)
195 Hardware_ECC_Recovered  0x001a   038   026   000    Old_age   Always       -       130600028
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

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

---

### Post by Mautobu on 2012-11-04
Wow, no love, eh?

---


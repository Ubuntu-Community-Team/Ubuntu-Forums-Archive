---
title: "my bootchart and long time"
date: 2013-03-20
forum: General Help
---

### Post by devjustly on 2013-03-20
hello

this is my bootchart

[https://docs.google.com/file/d/0BwS0_GGz-wuDdzBZUFplRXNXOGM/edit?usp=sharing](https://docs.google.com/file/d/0BwS0_GGz-wuDdzBZUFplRXNXOGM/edit?usp=sharing)

and i think is too much time to boot 01:15:55

what is the longest process in time? how reduce this time?

how i can read this bootchart?


[B]edit
[/B]PC running ubuntu 12.10, 
4gb ram
Intel® Core&#8482;2 Quad CPU Q9550 @ 2.83GHz × 4 
hard disk 228.3GiB
unity

---

### Post by devjustly on 2013-03-20
another time boot 01:12:30

---

### Post by gordintoronto on 2013-03-21
It's always helpful if you describe your computer when you ask this kind of question.

Is it a laptop? Laptops usually have slower hard drives than desktops. Are you running Kubuntu? Seventy-five seconds to boot Kubuntu on a computer which is a few years old, is pretty reasonable.

---

### Post by devjustly on 2013-03-21
> **gordintoronto said:**
> It's always helpful if you describe your computer when you ask this kind of question.

Is it a laptop? Laptops usually have slower hard drives than desktops. Are you running Kubuntu? Seventy-five seconds to boot Kubuntu on a computer which is a few years old, is pretty reasonable.
update my question 
i think powerful computer and [COLOR=#000000][FONT=arial]suitable for ubuntu[/FONT][/COLOR]

---

### Post by tgalati4 on 2013-03-21
Your bootchart shows IO Waits and disk utilization at 100%, so it looks like you have a slow disk.  How full is the disk?  Any SMART errors?

```
df -h
sudo smartctl -a /dev/sda
```

You are also running Landscape, which is a network monitor.  Do you need Landscape on this machine?

---

### Post by devjustly on 2013-03-21
> **tgalati4 said:**
> Your bootchart shows IO Waits and disk utilization at 100%, so it looks like you have a slow disk.  How full is the disk?  Any SMART errors?

```
df -h
sudo smartctl -a /dev/sda
```

You are also running Landscape, which is a network monitor.  Do you need Landscape on this machine?

for
```
df -h

```
result 
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       115G   11G   99G  10% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           2.0G  5.7M  2.0G   1% /tmp
tmpfs           791M  828K  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  1.4M  2.0G   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sda3       114G   68G   41G  63% /home



```

and for second line 

```
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.7.0-7-generic] (local build)Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.12
Device Model:     ST3250318AS
Serial Number:    9VY5GGHV
LU WWN Device Id: 5 000c50 01fbf822e
Firmware Version: CC38
User Capacity:    250,059,350,016 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Mar 21 18:08:09 2013 EET
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
data collection: 		(  592) seconds.
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
recommended polling time: 	 (  42) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x103f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   118   099   006    Pre-fail  Always       -       177788232
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   088   088   020    Old_age   Always       -       13218
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   066   060   030    Pre-fail  Always       -       4768551
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1450
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   094   094   020    Old_age   Always       -       6943
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   093   093   000    Old_age   Always       -       7
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       12885164351
189 High_Fly_Writes         0x003a   094   094   000    Old_age   Always       -       6
190 Airflow_Temperature_Cel 0x0022   062   058   045    Old_age   Always       -       38 (Min/Max 38/38)
194 Temperature_Celsius     0x0022   038   042   000    Old_age   Always       -       38 (0 16 0 0 0)
195 Hardware_ECC_Recovered  0x001a   048   028   000    Old_age   Always       -       177788232
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       2
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       2
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       2302102471619
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       2247075572
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       1429558020


SMART Error Log Version: 1
ATA Error Count: 7 (device log contains only the most recent five errors)
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


Error 7 occurred at disk power-on lifetime: 1126 hours (46 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00      01:17:54.500  READ DMA EXT
  ca 00 08 f8 f1 e0 ef 00      01:17:54.499  WRITE DMA
  2f 00 01 30 08 00 a0 00      01:17:54.498  READ LOG EXT
  27 00 00 00 00 00 e0 00      01:17:54.498  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      01:17:54.490  IDENTIFY DEVICE


Error 6 occurred at disk power-on lifetime: 1126 hours (46 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00      01:17:51.452  READ DMA EXT
  2f 00 01 30 08 00 a0 00      01:17:51.450  READ LOG EXT
  27 00 00 00 00 00 e0 00      01:17:51.450  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      01:17:51.442  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      01:17:51.437  SET FEATURES [Set transfer mode]


Error 5 occurred at disk power-on lifetime: 1126 hours (46 days + 22 hours)
  When the command that caused the error occurred, the device was in an unknown state.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00      01:17:48.402  READ DMA EXT
  25 00 08 ff ff ff ef 00      01:17:48.191  READ DMA EXT
  25 00 08 ff ff ff ef 00      01:17:48.164  READ DMA EXT
  25 00 08 ff ff ff ef 00      01:17:48.136  READ DMA EXT
  25 00 08 ff ff ff ef 00      01:17:48.111  READ DMA EXT


Error 4 occurred at disk power-on lifetime: 1126 hours (46 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00      01:17:44.591  READ DMA EXT
  c8 00 80 80 55 4b e1 00      01:17:44.589  READ DMA
  25 00 88 f8 51 4b e1 00      01:17:44.580  READ DMA EXT
  c8 00 28 18 b7 47 e1 00      01:17:44.551  READ DMA
  2f 00 01 30 08 00 a0 00      01:17:44.550  READ LOG EXT


Error 3 occurred at disk power-on lifetime: 1126 hours (46 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f  Error: UNC at LBA = 0x0fffffff = 268435455


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 ff ff ff ef 00      01:17:41.365  READ DMA EXT
  c8 00 18 20 46 50 e1 00      01:17:41.361  READ DMA
  c8 00 e0 88 76 51 e1 00      01:17:41.358  READ DMA
  c8 00 38 90 74 51 e1 00      01:17:41.335  READ DMA
  2f 00 01 30 08 00 a0 00      01:17:41.334  READ LOG EXT


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

### Post by tgalati4 on 2013-03-21
Your disk is not full.  You are running a Seagate 7200 rpm Barracuda, which is a speedy fish.

You have possibly a lot of corrected errors on this drive:

195 Hardware_ECC_Recovered  0x001a   048   028   000    Old_age   Always       -       177788232

If I read this correctly (and you will have to do some research on this particular drive), you are at 48% from 100% (brand new) of corrected errors.

You have some uncorrectable errors on the drive (UNC) and an ATA error (which is the SATA Input/output layer).  Change or reseat the cables.  Clean the dust out of the electronics of the drive, and start backing up your data.  It could be a simple as a loose cable, or a drive that is about to fail.

---


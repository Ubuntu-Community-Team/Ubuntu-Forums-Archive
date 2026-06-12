---
title: "Creating a logical volume on a specific physical volume gets me a input/output error"
date: 2016-04-07
forum: General Help
---

### Post by jerome1232 on 2016-04-07
In preparation for the Ubuntu 16.04 release I was going to backup many of my steam games to a drive that has sat unallocated. I use LVM so today I tried to create a logical volume that took up 100% of it's space, I also tried smaller sizes down to 50% but every attempt got me an Input/output error. The drive appears to pass all smart tests so I'm confused about what is going on.

To show I'm trying to create the volume on /dev/sdb1, it currently has not extents allocated

```
sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda3
  VG Name               ubuntu-vg
  PV Size               2.73 TiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              715335
  Free PE               79
  Allocated PE          715256
  PV UUID               4Kmieh-09uu-rS0n-yesw-WVNg-VeLZ-Qo6r1j
   
[COLOR="#0000CD"]  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               ubuntu-vg
  PV Size               298.09 GiB / not usable 1.31 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              76311
  Free PE               76311
  Allocated PE          0
  PV UUID               DYoPyD-JjZX-LTqS-JctZ-Gn6s-qZZu-w8pHJW[/COLOR]

```

When I try to create a volume on it (I want it to be only on this physical volume, I will split it into it's own volume group so I can restore the games into the new install) I get an input/output error.

```
sudo lvcreate -n steamBackup -l 50%PVS ubuntu-vg /dev/sdb1
  /dev/sdb1: write failed after 0 of 2048 at 15360: Input/output error

```

SMART data tells me the drive is OK and not failing
```
sudo smartctl -a /dev/sdb
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-63-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue (SATA)
Device Model:     WDC WD3200AAKS-00G3A0
Serial Number:    WD-WCAT16790251
LU WWN Device Id: 5 0014ee 1017bfd0f
Firmware Version: 40.00A40
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.5, 3.0 Gb/s
Local Time is:    Thu Apr  7 14:15:07 2016 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		( 5700) seconds.
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
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  69) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   165   157   021    Pre-fail  Always       -       2708
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1982
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   033   033   000    Old_age   Always       -       49212
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1897
192 Power-Off_Retract_Count 0x0032   199   199   000    Old_age   Always       -       968
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1992
194 Temperature_Celsius     0x0022   109   087   000    Old_age   Always       -       34
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       15
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     49212         -
# 2  Short offline       Completed without error       00%     35737         -
# 3  Short offline       Completed without error       00%     35638         -
# 4  Extended offline    Completed without error       00%     21247         -
# 5  Extended offline    Completed without error       00%      8992         -

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

I not sure at all what's going on with this drive...

---

### Post by jerome1232 on 2016-04-10
It seems a loose cable has gotten the better of me.

I fiddled with the wires and the drive works normally.

---


---
title: "Read Error at bootup"
date: 2013-11-10
forum: General Help
---

### Post by atblock on 2013-11-10
So my computer froze while it was in powersave mode, and I could not reboot it with REISUB, or access it over the network, forcing me to hard reboot. When I rebooted, I was greeted with the message "Read Error" in the top left corner.

I booted into a LiveCD, and tried ```
fdisk -l
``` which gave me the following output:
```
root@ubuntu:/home/ubuntu# fdisk -l
fdisk: unable to read /dev/sda: Inappropriate ioctl for device
```

I immediately imaged the drive with gddrescue, and then proceeded to run e2fsck. That seemed to complete successfully, and now when I run fsck, I get:
```
fsck from util-linux 2.20.1e2fsck 1.42.8 (20-Jun-2013)
/dev/sda1: clean, 1475560/18317312 files, 48594157/73242187 blocks
```

So all seems good over there. However, I still cannot get any output from fdisk, and when I reboot, I still get the same error.

---

### Post by fantab on 2013-11-10
Try to run 'fdisk -l' with sudo, '
```
sudo fdisk -l
```

You can also check with 
```
sudo parted -l
```

---

### Post by atblock on 2013-11-10
Hi, I'm running as root, so no need for sudo (I don't even think it will let me run without sudo).
As for parted, in gparted (which I imagine would show the same information as parted) it showed an ext4 partition at sda1 and an extended partition at sda1 which when expanded, opens up to show a swap partition at ext5.

---

### Post by fantab on 2013-11-10
You can then boot with Ubuntu Live DVD/USB and run fdisk and parted.

---

### Post by atblock on 2013-11-10
If you must know, here is the actually output from parted:

```

Model: ATA WDC WD10EZEX-00R (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size   Type      File system     Flags
 1      1049kB  300GB   300GB  primary   ext4            boot
 3      300GB   1000GB  700GB  primary
 2      1000GB  1000GB  677MB  extended
 5      1000GB  1000GB  677MB  logical   linux-swap(v1)

```

---

### Post by atblock on 2013-11-10
I've been running from a livecd this whole time.

---

### Post by fantab on 2013-11-10
It seems to me like a Hardware issue with the /dev/sda. Try to run SMART tests on the HDD with the utility 'Disks' from LiveDVD. Also check in the BIOS for SATA Mode, see if its set to AHCI.
One issue I notice is that your first partition starts at *1049kb*,  when it should be **1048kb**, not sure if it IS responsible for the error. You can use Gparted to set it right and see if it makes any difference.

Try to boot from an older kernel and see if it helps, you can boot into an older Kernel, if present, from Grub Menu-> Advanced Options.

Another thing: Have you changed the partition table of your HDD, esp, from GPT to 'msdos'?

Try the HDD manufacturer's disk utilities, if they have, and run them on  HDD to see if it reports any issues. If the utilities are Windows only  then connect the HDD to a Windows Machine and run the utilities.
If none of the above works, then perhaps we need to 'recreate the partition table'.

---

### Post by atblock on 2013-11-10
The extended offline test and short test seem to stop after 10% with LBA of first error 8. In the error log it says 

Here are the results

```

smartctl 6.2 2013-04-20 r3812 [i686-linux-3.10.0-2-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD10EZEX-00RKKA0
Serial Number:    WD-WCC1S4826458
LU WWN Device Id: 5 0014ee 208b6d829
Firmware Version: 80.00A80
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Mon Nov 11 04:35:01 2013 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		( 9780) seconds.
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
recommended polling time: 	 ( 113) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x30b5)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   198   198   051    Pre-fail  Always       -       7001
  3 Spin_Up_Time            0x0027   187   176   021    Pre-fail  Always       -       1616
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       36
  5 Reallocated_Sector_Ct   0x0033   180   180   140    Pre-fail  Always       -       874
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       1589
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       36
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       21
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       14
194 Temperature_Celsius     0x0022   101   091   000    Old_age   Always       -       42
196 Reallocated_Event_Count 0x0032   001   001   000    Old_age   Always       -       874
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       1


SMART Error Log Version: 1
ATA Error Count: 6999 (device log contains only the most recent five errors)
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


Error 6999 occurred at disk power-on lifetime: 1587 hours (66 days + 3 hours)
  When the command that caused the error occurred, the device was doing SMART Offline or Self-test.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 08 00 00 e0  Error: UNC 8 sectors at LBA = 0x00000008 = 8


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 00 00 e0 00   1d+11:00:17.366  READ DMA
  ec 00 00 00 00 00 a0 00   1d+11:00:17.304  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00   1d+11:00:17.299  SET FEATURES [Set transfer mode]


Error 6998 occurred at disk power-on lifetime: 1587 hours (66 days + 3 hours)
  When the command that caused the error occurred, the device was doing SMART Offline or Self-test.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 08 00 00 e0  Error: UNC 8 sectors at LBA = 0x00000008 = 8


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 00 00 e0 00   1d+11:00:15.343  READ DMA
  ec 00 00 00 00 00 a0 00   1d+11:00:15.282  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00   1d+11:00:15.276  SET FEATURES [Set transfer mode]


Error 6997 occurred at disk power-on lifetime: 1587 hours (66 days + 3 hours)
  When the command that caused the error occurred, the device was doing SMART Offline or Self-test.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 08 00 00 e0  Error: UNC 8 sectors at LBA = 0x00000008 = 8


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 00 00 e0 00   1d+11:00:13.328  READ DMA
  ec 00 00 00 00 00 a0 00   1d+11:00:13.268  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00   1d+11:00:13.261  SET FEATURES [Set transfer mode]


Error 6996 occurred at disk power-on lifetime: 1587 hours (66 days + 3 hours)
  When the command that caused the error occurred, the device was doing SMART Offline or Self-test.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 08 00 00 e0  Error: UNC 8 sectors at LBA = 0x00000008 = 8


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 00 00 e0 00   1d+11:00:11.314  READ DMA
  ec 00 00 00 00 00 a0 00   1d+11:00:11.254  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00   1d+11:00:11.247  SET FEATURES [Set transfer mode]


Error 6995 occurred at disk power-on lifetime: 1587 hours (66 days + 3 hours)
  When the command that caused the error occurred, the device was doing SMART Offline or Self-test.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 08 00 00 e0  Error: UNC 8 sectors at LBA = 0x00000008 = 8


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 08 00 00 e0 00   1d+11:00:09.282  READ DMA
  ec 00 00 00 00 00 a0 00   1d+11:00:09.221  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00   1d+11:00:09.215  SET FEATURES [Set transfer mode]


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%      1589         8
# 2  Extended offline    Completed: read failure       90%      1587         8
# 3  Short offline       Aborted by host               10%      1587         -


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

### Post by fantab on 2013-11-11
> Error: UNC 8 sectors at LBA = 0x00000008 = 8

Looks like bad sectors. UNC= UNCorrectable.

If the drive is in Warranty, Replace it. If Not then perhaps you can try any Disk Repair Utilities (I have no idea which ones are good). 
Generally newer HDD firmware is capable of sorting out the bad sectors to the end of the disk, so the disk becomes reusuable. 
If I were you I would, create a new Partition Table and the partitions all over again. Use Gparted -> Device -> 'Create new partition table', apply changes. Then go on to create newer partitions. Install Ubuntu and see how it fares.

If in doubt, consult a specialist.

Good Luck...
for reference:
[http://www.tomshardware.com/forum/295129-32-dropped-drive-linux](http://www.tomshardware.com/forum/295129-32-dropped-drive-linux)

---


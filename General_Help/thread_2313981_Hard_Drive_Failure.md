---
title: "Hard Drive Failure?"
date: 2016-02-17
forum: General Help
---

### Post by Elijah_Duffy on 2016-02-17
Recently, disks has been telling me that my hard drive is failing. I looked at the SMART status, but cannot understand anything there (I have attached a screenshot). The weird thing is, there are a couple of lines that say "Pre-Fail" under the "Type" field, and many fields that say "Old Age" under "Type." The weird thing about this however, is that my hard drive was replaced around a year and a half ago. The thing I find really weird about the SMART status is that from my understanding of the fields, it is saying my HDD has been powered up for 4 months and 27 days. This is not true though as I have had the HDD out of my laptop less than one month again to see if this error was from apparent physical damage.

Before this error started coming up, I had decided to install Windows on my computer again (which I learned was a bad idea). And of course, Windows removed the GRUB bootloader not allowing me to boot into Ubuntu at all. It was after that I reinstalled GRUB bootloader using an Ubuntu Live USB and Boot-Repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) that this problem appeared. 

Any help would be greatly appreciated.

My SMART status through the GNOME-Disks Application is attached.

---

### Post by sandyd on 2016-02-17
Hi, can you post the output of the following:

```

sudo smartctl --test=short /dev/sda
## Wait 1minute
sudo smartctl -a /dev/sda

```
If the disk that is failing is not /dev/sda, replace it with correct disk

---

### Post by Elijah_Duffy on 2016-02-18
> **sandyd said:**
> Hi, can you post the output of the following:

```

sudo smartctl --test=short /dev/sda
## Wait 1minute
sudo smartctl -a /dev/sda

```
If the disk that is failing is not /dev/sda, replace it with correct disk

Here is the output:
```
smartctl 6.4 2014-10-07 r4002 [x86_64-linux-4.2.0-27-generic] (local build)Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Black
Device Model:     WDC WD3200BEKT-08PVMT1
Serial Number:    WD-WXP1CC1K8735
LU WWN Device Id: 5 0014ee 6578910b7
Firmware Version: 02.01A02
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Thu Feb 18 18:30:30 2016 PST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.


General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (  73)	The previous self-test completed having
					a test element that failed and the test
					element that failed is not known.
Total time to complete Offline 
data collection: 		( 5880) seconds.
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
recommended polling time: 	 (  61) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x7037)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       991
  3 Spin_Up_Time            0x0027   163   140   021    Pre-fail  Always       -       816
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2188
  5 Reallocated_Sector_Ct   0x0033   139   139   140    Pre-fail  Always   FAILING_NOW 512
  7 Seek_Error_Rate         0x002f   100   253   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3614
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2059
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       276
193 Load_Cycle_Count        0x0032   190   190   000    Old_age   Always       -       30048
194 Temperature_Celsius     0x0022   105   091   000    Old_age   Always       -       38
196 Reallocated_Event_Count 0x0032   192   192   000    Old_age   Always       -       8
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   096   096   000    Old_age   Always       -       3429


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: unknown failure    90%      3614         -
# 2  Extended offline    Completed: unknown failure    90%      3422         -
# 3  Vendor (0x50)       Completed without error       00%        54         -
# 4  Short offline       Completed without error       00%        53         -
# 5  Short offline       Completed without error       00%         4         -


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

Thanks.

---

### Post by sandyd on 2016-02-18
The Power_On_Hours indicates how much time the HDD has spent running in total, not really the amount of time that it was last shutdown.

That being said, seeing as you have already have a Reallocated_Sector_Ct of 512, the HDD seems to be in danger of failing. Of course, you can continue using it and see if the number of reallocated sectors increases, but it is a general warning that something is not right with your drive and that there is a stronger posibility that the drive could fail compared to a drive without a high number of reallocated sectors. There is not much Ubuntu can do as this issue is physical not software.

---

### Post by montag dp on 2016-02-18
You should probably look at this thread:

[https://forum.manjaro.org/index.php?topic=17890.0](https://forum.manjaro.org/index.php?topic=17890.0)

It's not Ubuntu, but I believe it's the same problem. Western Digital hard drives seem to be problematic in Linux, but there's a fix at least for drives that haven't broken yet. You will need to install whichever package has idle3ctl. I'm not sure what package that is on Ubuntu, or if you might need a PPA.

Edit: although, your load cycle count doesn't look too bad, depending on how long you've had it. So it might not actually be the same problem. That thread is still probably worth a look, though. It might help you in the future even if this disk is toast.

---

### Post by gordintoronto on 2016-02-19
Let me be blunt: the hard drive has failed. You need to copy any files you want to an external media, or an online backup system such as Dropbox. Preferably both.

Then buy a new hard drive which is compatible with your computer, install it, and install your operating system of choice.

---


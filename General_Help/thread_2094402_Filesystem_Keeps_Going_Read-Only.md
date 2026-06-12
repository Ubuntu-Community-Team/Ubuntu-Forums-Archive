---
title: "Filesystem Keeps Going Read-Only"
date: 2012-12-13
forum: General Help
---

### Post by dniMretsaM on 2012-12-13
So recently my filesystem has started going RO on me; seemingly at random. Sometimes, I'll boot up my system and run happily all day. Sometimes, it will go read-only on boot. If that happens, I will be offered the option to fix it automatically, skip mounting the drive, or manually recover it. Selecting automatic recovery works fine. Other times, I'll boot up my machine, run for a while, and then it will go RO and I'll get errors all over the place. When this happens, I have to use manual recovery to get it to work. So my question is, how can I find out what is making this happen?

---

### Post by LiamOS on 2012-12-13
Can you post the contents of /proc/mounts and /etc/fstab, the output of 'df -h', and 'dmesg | grep -i mount'?


EDIT: I see Larry the Cow. Nice to see such taste. ;)

---

### Post by SeijiSensei on 2012-12-13
Make sure you always shut the system down cleanly using either the shutdown command from the menus or "shutdown -h now" at the command prompt.

You might also want to install [smartmontools]("https://help.ubuntu.com/community/Smartmontools") to check the health of the drive with smartctl.

If you have not run a backup recently, do so now.

---

### Post by dannyboy79 on 2012-12-13
> **SeijiSensei said:**
> Make sure you always shut the system down cleanly using either the shutdown command from the menus or "shutdown -h now" at the command prompt.

You might also want to install [smartmontools]("https://help.ubuntu.com/community/Smartmontools") to check the health of the drive with smartctl.

If you have not run a backup recently, do so now.
+1
the kernel changing the filesystem to read only is a bad sign that the hard disk is failing. check your kern.log or syslog for io errors and bad sectors and what not. BACK UP IMPORTANT STUFF NOW!

---

### Post by dniMretsaM on 2012-12-13
/proc/mounts:
```
rootfs / rootfs rw 0 0
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,relatime,size=4022844k,nr_inodes=1005711,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,relatime,size=1614288k,mode=755 0 0
/dev/disk/by-uuid/6c8b79ad-ad6e-41aa-a2e0-7e570bd9fd3f / ext4 rw,relatime,errors=remount-ro,commit=600,data=ordered 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
none /run/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /run/user tmpfs rw,nosuid,nodev,noexec,relatime,size=102400k,mode=755 0 0
/dev/sda4 /home ext4 ro,relatime,data=ordered 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
```

/etc/fstab:
```
# / was on /dev/sda1 during installation
UUID=6c8b79ad-ad6e-41aa-a2e0-7e570bd9fd3f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=da462159-6444-4785-bd61-4d4c096058ac /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=e206b01d-6cec-4b56-b469-25b106536f09 none            swap    sw              0       0
```
df -h:
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        33G   12G   20G  37% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  904K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G   80K  3.9G   1% /run/shm
none            100M   12K  100M   1% /run/user
/dev/sda4       570G   91G  450G  17% /home
```
dmesg | grep -i mount:
```
[    0.003553] Mount-cache hash table entries: 256
[    9.337978] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   22.544178] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   23.032732] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[  321.509302] EXT4-fs (sda4): Remounting filesystem read-only
[ 2956.779536] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[ 2956.807986] EXT4-fs error (device sda4): ext4_remount:4575: Abort forced by user
```

---

### Post by LiamOS on 2012-12-13
Well, you can simply edit your fstab and remove errors=remount-ro to have it not remount read only, I believe.
This isn't the ideal solution, though.

You should definitely check the filesystem integrity and hard disk integrity to get an idea of where the problem is originating.

---

### Post by dniMretsaM on 2012-12-13
> **SeijiSensei said:**
> Make sure you always shut the system down cleanly using either the shutdown command from the menus or "shutdown -h now" at the command prompt.

You might also want to install [smartmontools]("https://help.ubuntu.com/community/Smartmontools") to check the health of the drive with smartctl.

If you have not run a backup recently, do so now.

I usually use either the menu, "reboot," or "poweroff -n." I'll check out smartmontools. It's a pretty new drive (got the computer in late July/early August), so it should be covered by warranty if it is failing. Also, anything important that hasn't been backed up yet is being transfered to my ownCloud box.

> **LiamOS said:**
> Well, you can simply edit your fstab and remove errors=remount-ro to have it not remount read only, I believe.
This isn't the ideal solution, though.

You should definitely check the filesystem integrity and hard disk integrity to get an idea of where the problem is originating.

The reason I didn't do that is because I knew that wouldn't fix the actual problem (whatever that might be).

EDIT: The smartctl long test will complete just before 20:00 (about 2 and a half hours). I'll report back when it's done.

---

### Post by dniMretsaM on 2012-12-13
The test after a few minutes with a read failure. Here's the output:
```
smartctl version 5.38 [i486-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     ST9750420AS
Serial Number:    6WS2C7MH
Firmware Version: 0001SDM5
User Capacity:    750,156,374,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Thu Dec 13 23:33:26 2012 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		 (   0) seconds.
Offline data collection
capabilities: 			 (0x73) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
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
recommended polling time: 	 ( 148) minutes.
Conveyance self-test routine
recommended polling time: 	 (   3) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   092   086   006    Pre-fail  Always       -       11510708
  3 Spin_Up_Time            0x0003   098   098   085    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   094   094   020    Old_age   Always       -       6757
  5 Reallocated_Sector_Ct   0x0033   099   098   036    Pre-fail  Always       -       283
  7 Seek_Error_Rate         0x000f   075   060   030    Pre-fail  Always       -       33706040
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1181
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       828
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       1606
188 Unknown_Attribute       0x0032   100   099   000    Old_age   Always       -       4295032835
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   060   043   045    Old_age   Always   In_the_past 40 (0 21 41 38)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       56
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       2345
193 Load_Cycle_Count        0x0032   090   090   000    Old_age   Always       -       20122
194 Temperature_Celsius     0x0022   040   057   000    Old_age   Always       -       40 (0 15 0 0)
195 Hardware_ECC_Recovered  0x001a   106   099   000    Old_age   Always       -       11510708
197 Current_Pending_Sector  0x0012   099   083   000    Old_age   Always       -       40
198 Offline_Uncorrectable   0x0010   099   083   000    Old_age   Offline      -       40
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       266159123334051
241 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       3896156835
242 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       2525889655
254 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 578 (device log contains only the most recent five errors)
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

Error 578 occurred at disk power-on lifetime: 1180 hours (49 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      00:01:00.544  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:01:00.530  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:01:00.490  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:01:00.488  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:01:00.483  READ FPDMA QUEUED

Error 577 occurred at disk power-on lifetime: 1178 hours (49 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      00:05:28.081  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:05:28.081  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:05:28.080  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:05:28.080  READ FPDMA QUEUED
  60 00 08 ff ff ff 4f 00      00:05:28.080  READ FPDMA QUEUED

Error 576 occurred at disk power-on lifetime: 1178 hours (49 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 ff ff ff 4f 00      00:05:22.911  READ FPDMA QUEUED
  61 00 20 e8 21 04 42 00      00:05:22.910  WRITE FPDMA QUEUED
  61 00 08 00 77 9d 40 00      00:05:22.910  WRITE FPDMA QUEUED
  60 00 f0 ff ff ff 4f 00      00:05:22.909  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 00      00:05:22.908  READ NATIVE MAX ADDRESS EXT

Error 575 occurred at disk power-on lifetime: 1178 hours (49 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 f0 ff ff ff 4f 00      00:05:20.048  READ FPDMA QUEUED
  60 00 00 ff ff ff 4f 00      00:05:20.047  READ FPDMA QUEUED
  60 00 88 98 29 44 40 00      00:05:20.041  READ FPDMA QUEUED
  60 00 00 00 28 44 40 00      00:05:20.019  READ FPDMA QUEUED
  60 00 20 ff ff ff 4f 00      00:05:20.010  READ FPDMA QUEUED

Error 574 occurred at disk power-on lifetime: 1178 hours (49 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 ff ff ff 0f

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 ff ff ff 4f 00      00:46:25.628  READ FPDMA QUEUED
  b0 da 00 00 4f c2 00 00      00:46:25.334  SMART RETURN STATUS
  b0 d0 01 00 4f c2 00 00      00:46:25.279  SMART READ DATA
  b0 d1 01 00 4f c2 00 00      00:46:25.268  SMART READ ATTRIBUTE THRESHOLDS [OBS-4]
  e5 00 00 00 00 00 00 00      00:46:25.268  CHECK POWER MODE

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      1181         1426982048
# 2  Extended offline    Completed: read failure       90%      1180         1426982048
# 3  Short offline       Completed: read failure       90%      1180         788573400
# 4  Extended offline    Completed: read failure       90%      1180         1426982048
# 5  Extended offline    Completed: read failure       90%      1180         1423344680
# 6  Extended offline    Completed: read failure       90%      1180         788573400

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

### Post by dannyboy79 on 2012-12-13
as I suggested earlier check your kern.log and syslog for bad sector errors or IO errors.

---

### Post by dniMretsaM on 2012-12-13
> **dannyboy79 said:**
> as I suggested earlier check your kern.log and syslog for bad sector errors or IO errors.

These are the errors that I got. I assume that these are bad sectors:
kern.log:
```
Dec  9 18:56:08 panp9 kernel: [    1.744714] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 10 11:44:18 panp9 kernel: [    1.240964] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 11 12:38:20 panp9 kernel: [    1.740343] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 11 15:31:24 panp9 kernel: [    1.306551] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 12 10:38:28 panp9 kernel: [    1.244899] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 12 10:49:58 panp9 kernel: [  736.713587] end_request: I/O error, dev sda, sector 809300040
Dec 12 21:04:01 panp9 kernel: [    2.240576] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 12 21:14:46 panp9 kernel: [    1.240991] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 12 21:16:18 panp9 kernel: [  119.168546] end_request: I/O error, dev sda, sector 788573352
Dec 13 11:45:14 panp9 kernel: [    1.244959] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 13 14:13:30 panp9 kernel: [ 7152.556477] end_request: I/O error, dev sda, sector 1336472968
Dec 13 14:13:30 panp9 kernel: [ 7152.556546] end_request: I/O error, dev sda, sector 2056
Dec 13 14:13:30 panp9 kernel: [ 7152.556550] Buffer I/O error on device sda1, logical block 1
Dec 13 14:13:30 panp9 kernel: [ 7152.556551] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556555] Buffer I/O error on device sda1, logical block 2
Dec 13 14:13:30 panp9 kernel: [ 7152.556556] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556593] end_request: I/O error, dev sda, sector 10248
Dec 13 14:13:30 panp9 kernel: [ 7152.556595] Buffer I/O error on device sda1, logical block 1025
Dec 13 14:13:30 panp9 kernel: [ 7152.556596] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556653] end_request: I/O error, dev sda, sector 4196368
Dec 13 14:13:30 panp9 kernel: [ 7152.556655] Buffer I/O error on device sda1, logical block 524290
Dec 13 14:13:30 panp9 kernel: [ 7152.556657] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556705] end_request: I/O error, dev sda, sector 29365760
Dec 13 14:13:30 panp9 kernel: [ 7152.556707] Buffer I/O error on device sda1, logical block 3670464
Dec 13 14:13:30 panp9 kernel: [ 7152.556709] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556762] end_request: I/O error, dev sda, sector 29365816
Dec 13 14:13:30 panp9 kernel: [ 7152.556763] Buffer I/O error on device sda1, logical block 3670471
Dec 13 14:13:30 panp9 kernel: [ 7152.556764] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556796] end_request: I/O error, dev sda, sector 29757688
Dec 13 14:13:30 panp9 kernel: [ 7152.556798] Buffer I/O error on device sda1, logical block 3719455
Dec 13 14:13:30 panp9 kernel: [ 7152.556799] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556830] end_request: I/O error, dev sda, sector 29832704
Dec 13 14:13:30 panp9 kernel: [ 7152.556832] Buffer I/O error on device sda1, logical block 3728832
Dec 13 14:13:30 panp9 kernel: [ 7152.556833] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556864] end_request: I/O error, dev sda, sector 46139520
Dec 13 14:13:30 panp9 kernel: [ 7152.556866] Buffer I/O error on device sda1, logical block 5767184
Dec 13 14:13:30 panp9 kernel: [ 7152.556867] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556899] end_request: I/O error, dev sda, sector 46140496
Dec 13 14:13:30 panp9 kernel: [ 7152.556900] Buffer I/O error on device sda1, logical block 5767306
Dec 13 14:13:30 panp9 kernel: [ 7152.556902] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556933] end_request: I/O error, dev sda, sector 46141304
Dec 13 14:15:25 panp9 kernel: [ 7267.081805] end_request: I/O error, dev sda, sector 1336463640
Dec 13 14:15:25 panp9 kernel: [ 7267.081879] end_request: I/O error, dev sda, sector 1336463896
Dec 13 15:32:03 panp9 kernel: [    2.242831] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 13 15:36:45 panp9 kernel: [  308.124655] end_request: I/O error, dev sda, sector 788573400
Dec 13 15:36:49 panp9 kernel: [  311.904018] end_request: I/O error, dev sda, sector 788573536
Dec 13 15:36:59 panp9 kernel: [  321.474804] end_request: I/O error, dev sda, sector 788573400
Dec 13 15:36:59 panp9 kernel: [  321.474838] end_request: I/O error, dev sda, sector 146488728
Dec 13 19:09:57 panp9 kernel: [    1.308202] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 13 19:12:06 panp9 kernel: [    1.738108] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
```

syslog:
```
Dec 12 21:16:18 panp9 kernel: [  119.168546] end_request: I/O error, dev sda, sector 788573352
Dec 13 14:13:30 panp9 kernel: [ 7152.556477] end_request: I/O error, dev sda, sector 1336472968
Dec 13 14:13:30 panp9 kernel: [ 7152.556546] end_request: I/O error, dev sda, sector 2056
Dec 13 14:13:30 panp9 kernel: [ 7152.556550] Buffer I/O error on device sda1, logical block 1
Dec 13 14:13:30 panp9 kernel: [ 7152.556551] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556555] Buffer I/O error on device sda1, logical block 2
Dec 13 14:13:30 panp9 kernel: [ 7152.556556] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556593] end_request: I/O error, dev sda, sector 10248
Dec 13 14:13:30 panp9 kernel: [ 7152.556595] Buffer I/O error on device sda1, logical block 1025
Dec 13 14:13:30 panp9 kernel: [ 7152.556596] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556653] end_request: I/O error, dev sda, sector 4196368
Dec 13 14:13:30 panp9 kernel: [ 7152.556655] Buffer I/O error on device sda1, logical block 524290
Dec 13 14:13:30 panp9 kernel: [ 7152.556657] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556705] end_request: I/O error, dev sda, sector 29365760
Dec 13 14:13:30 panp9 kernel: [ 7152.556707] Buffer I/O error on device sda1, logical block 3670464
Dec 13 14:13:30 panp9 kernel: [ 7152.556709] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556762] end_request: I/O error, dev sda, sector 29365816
Dec 13 14:13:30 panp9 kernel: [ 7152.556763] Buffer I/O error on device sda1, logical block 3670471
Dec 13 14:13:30 panp9 kernel: [ 7152.556764] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556796] end_request: I/O error, dev sda, sector 29757688
Dec 13 14:13:30 panp9 kernel: [ 7152.556798] Buffer I/O error on device sda1, logical block 3719455
Dec 13 14:13:30 panp9 kernel: [ 7152.556799] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556830] end_request: I/O error, dev sda, sector 29832704
Dec 13 14:13:30 panp9 kernel: [ 7152.556832] Buffer I/O error on device sda1, logical block 3728832
Dec 13 14:13:30 panp9 kernel: [ 7152.556833] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556864] end_request: I/O error, dev sda, sector 46139520
Dec 13 14:13:30 panp9 kernel: [ 7152.556866] Buffer I/O error on device sda1, logical block 5767184
Dec 13 14:13:30 panp9 kernel: [ 7152.556867] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556899] end_request: I/O error, dev sda, sector 46140496
Dec 13 14:13:30 panp9 kernel: [ 7152.556900] Buffer I/O error on device sda1, logical block 5767306
Dec 13 14:13:30 panp9 kernel: [ 7152.556902] lost page write due to I/O error on sda1
Dec 13 14:13:30 panp9 kernel: [ 7152.556933] end_request: I/O error, dev sda, sector 46141304
Dec 13 14:15:25 panp9 kernel: [ 7267.081805] end_request: I/O error, dev sda, sector 1336463640
Dec 13 14:15:25 panp9 kernel: [ 7267.081879] end_request: I/O error, dev sda, sector 1336463896
Dec 13 15:36:45 panp9 kernel: [  308.124655] end_request: I/O error, dev sda, sector 788573400
Dec 13 15:36:49 panp9 kernel: [  311.904018] end_request: I/O error, dev sda, sector 788573536
Dec 13 15:36:59 panp9 kernel: [  321.474804] end_request: I/O error, dev sda, sector 788573400
Dec 13 15:36:59 panp9 kernel: [  321.474838] end_request: I/O error, dev sda, sector 146488728
```

---

### Post by dannyboy79 on 2012-12-13
yeah, your main partition /dev/sda1 has a ton of IO errors as you can see. If I were you Id run disk analyzer to see if your sectors are bad and reallocated or pending. Either way if it were me, I'd dump the disk and buy a new one. this one looks shot.

---

### Post by dniMretsaM on 2012-12-13
> **dannyboy79 said:**
> yeah, your main partition /dev/sda1 has a ton  of IO errors as you can see. If I were you Id run disk analyzer to see  if your sectors are bad and reallocated or pending. Either way if it  were me, I'd dump the disk and buy a new one. this one looks  shot.

Not sure what you mean by disk analyzer. I vaguely remember  something like that being installed by default in Ubuntu, but I'm not  sure what the program name is. Anyway, this computer is less than 4  months old so I believe it's still under warranty. I guess it was just a  bum drive... :(

---

### Post by Asmodai on 2012-12-13
When the reallocated sector count is higher than zero, a drive is generally close to failing completely. In your case, the corresponding SMART value is 283, so yeah...

---

### Post by dniMretsaM on 2012-12-14
I opened a support ticket on the System76 Web site and they said it would be no problem to replace, so I'll go ahead and mark this as solved. Thanks guys.

---


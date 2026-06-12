---
title: "Recover data from NAS HD"
date: 2015-12-02
forum: General Help
---

### Post by gilsonsjc on 2015-12-02
Hi everybody

  One of my NAS' 2TB HD failed. I have the NAS set up as raid 1. I removed both HDs (the bad one and the good one) and added new and bigger HDs. Now, I need to recover the data from the old-good HD so that I can upload to the NAS again.

  I have one external HD enclosure, one Macbok air and a Ubuntu VM on vmware fusion.

  One of the things I did in order to identify one of my old HDs was failing was to run the commands on the page [http://mybookworld.wikidot.com/mybook-live-debricking-guide-osx-and-windows]("http://mybookworld.wikidot.com/mybook-live-debricking-guide-osx-and-windows") against the good-old HD with the option to NOT to destroy the data

  Here I some information I could gather so far
  
```
$sudo fdisk -l

Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

```
$ sudo mdadm --examine /dev/sdb
mdadm: No md superblock detected on /dev/sdb.

```

  What should I do in order to recover the data?

Thanks
Gilson

---

### Post by tgalati4 on 2015-12-03
Welcome to the forums.  What was the model of the NAS?  If your NAS used a hardware RAID1 to control the disk drives, then you need to find an identical NAS enclosure, put in an identical-sized replacement drive, and rebuild the RAID1 pool on the NAS, then transfer the data.  If your original NAS enclosure is working with the larger drives, then take them out and put in your original 2TB drive, and find an identical replacement drive.  The NAS should automatically rebuild the pool.  Let that happen, and it will take time.

Once the pool has been recreated, start your backup process.  Don't try to backup and recreate the pool at the same time--too much risk of a 2nd hard drive failure.

---

### Post by gilsonsjc on 2015-12-03
The NAS is one Western Digital My Book World Edition II Whitelights. It is currently running 2 new HDs of 5 TB each. Since I have only thing enclosure, I will try to remove the current drives and insert the old one whit the data as you recommended to test.

I will let you know if that worked.

Thanks.

It turns out I was working on the drive that failed. Here is the drive I am trying to mount to recovery the data and what I have tried to far:

$ sudo fdisk -l
```

Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 45A11E44-7BEE-40FA-AF61-C0D4CA0654D0

Device       Start        End    Sectors   Size Type
/dev/sdc1    64320    3984191    3919872   1.9G Linux RAID
/dev/sdc2  3984192    4498175     513984   251M Linux RAID
/dev/sdc3  4498176    6474175    1976000 964.9M Linux RAID
/dev/sdc4  6474176 3907029134 3900554959   1.8T Linux RAID

```

$ sudo mount /dev/md0 /mnt
```
$ sudo mount /dev/md0 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```


$ dmesg | tail -n 100 
```

[   97.590495] sd 33:0:0:0: Attached scsi generic sg2 type 0
[   97.602615] sd 33:0:0:0: [sdb] Spinning up disk...
[  105.379014] .ready
[  105.381670] sd 33:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[  105.385490] sd 33:0:0:0: [sdb] Write Protect is off
[  105.385497] sd 33:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  105.387682] sd 33:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  105.415475] sd 33:0:0:0: [sdb] Attached SCSI disk
[  215.652022] EXT4-fs (loop0): mounting ext3 file system using the ext4 subsystem
[  215.652298] EXT4-fs (loop0): bad geometry: block count 499952 exceeds size of device (120452 blocks)
[  230.677236] usb 1-2: USB disconnect, device number 3
[  230.682887] sd 33:0:0:0: [sdb] Synchronizing SCSI cache
[  230.682906] sd 33:0:0:0: [sdb] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[  535.816999] usb 1-2: new high-speed USB device number 4 using ehci-pci
[  535.964892] usb 1-2: New USB device found, idVendor=0928, idProduct=000a
[  535.964897] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  535.964899] usb 1-2: Product: 1394A/USB2.0/eSATA combo drive
[  535.964901] usb 1-2: Manufacturer: PI-208
[  535.964903] usb 1-2: SerialNumber: 2009021200001475
[  536.018373] usb-storage 1-2:1.0: USB Mass Storage device detected
[  536.018559] scsi host34: usb-storage 1-2:1.0
[  537.018644] scsi 34:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
[  537.023146] sd 34:0:0:0: Attached scsi generic sg2 type 0
[  537.035945] sd 34:0:0:0: [sdb] Spinning up disk...
[  545.685119] .ready
[  545.687908] sd 34:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[  545.690574] sd 34:0:0:0: [sdb] Write Protect is off
[  545.690580] sd 34:0:0:0: [sdb] Mode Sense: 10 00 00 00
[  545.692502] sd 34:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  547.485277]  sdb: sdb1 sdb2 sdb3 sdb4
[  549.330208] sd 34:0:0:0: [sdb] Attached SCSI disk
[  587.500858] sd 34:0:0:0: [sdb] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  587.500865] sd 34:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  587.500877] sd 34:0:0:0: [sdb] Add. Sense: Data phase error
[  587.500881] sd 34:0:0:0: [sdb] CDB: Read(10) 28 00 00 3c ca c0 00 00 08 00
[  587.500884] blk_update_request: I/O error, dev sdb, sector 3984064
[  615.107154] sd 34:0:0:0: [sdb] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  615.107160] sd 34:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  615.107164] sd 34:0:0:0: [sdb] Add. Sense: Data phase error
[  615.107168] sd 34:0:0:0: [sdb] CDB: Read(10) 28 00 00 3c ca c0 00 00 08 00
[  615.107171] blk_update_request: I/O error, dev sdb, sector 3984064
[  615.107177] Buffer I/O error on dev sdb1, logical block 489968, async page read
[  638.996500] sd 34:0:0:0: [sdb] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  638.996508] sd 34:0:0:0: [sdb] Sense Key : Medium Error [current] 
[  638.996513] sd 34:0:0:0: [sdb] Add. Sense: Data phase error
[  638.996517] sd 34:0:0:0: [sdb] CDB: Read(10) 28 00 00 3c cb 40 00 00 08 00
[  638.996521] blk_update_request: I/O error, dev sdb, sector 3984192
[  671.403732] md: bind<sdb2>
[  671.417697] md: bind<sdb3>
[  671.429457] md: bind<sdb4>
[  916.145549] EXT4-fs (loop0): mounting ext3 file system using the ext4 subsystem
[  916.145572] EXT4-fs (loop0): bad geometry: block count 499952 exceeds size of device (120452 blocks)
[  938.701220] EXT4-fs (loop0): mounting ext3 file system using the ext4 subsystem
[  938.701254] EXT4-fs (loop0): bad geometry: block count 499952 exceeds size of device (120452 blocks)
[ 1027.971605] EXT4-fs (loop0): mounting ext3 file system using the ext4 subsystem
[ 1027.971617] EXT4-fs (loop0): bad geometry: block count 499952 exceeds size of device (120452 blocks)
[ 1090.355904] usb 1-2: USB disconnect, device number 4
[ 1090.363349] sd 34:0:0:0: [sdb] Synchronizing SCSI cache
[ 1090.363371] sd 34:0:0:0: [sdb] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 1463.518184] usb 1-2: new high-speed USB device number 5 using ehci-pci
[ 1463.667570] usb 1-2: New USB device found, idVendor=0928, idProduct=000a
[ 1463.667575] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1463.667578] usb 1-2: Product: 1394A/USB2.0/eSATA combo drive
[ 1463.667580] usb 1-2: Manufacturer: PI-208
[ 1463.667581] usb 1-2: SerialNumber: 2009021200001475
[ 1463.724790] usb-storage 1-2:1.0: USB Mass Storage device detected
[ 1463.724980] scsi host35: usb-storage 1-2:1.0
[ 1464.731309] scsi 35:0:0:0: Direct-Access     Ext Hard  Disk                 PQ: 0 ANSI: 4
[ 1464.733876] sd 35:0:0:0: Attached scsi generic sg2 type 0
[ 1464.745829] sd 35:0:0:0: [sdc] Spinning up disk...
[ 1469.083624] .ready
[ 1469.087834] sd 35:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[ 1469.089975] sd 35:0:0:0: [sdc] Write Protect is off
[ 1469.089984] sd 35:0:0:0: [sdc] Mode Sense: 10 00 00 00
[ 1469.093345] sd 35:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1469.119977]  sdc: sdc1 sdc2 sdc3 sdc4
[ 1469.131610] sd 35:0:0:0: [sdc] Attached SCSI disk
[ 1492.984081] sd 35:0:0:0: [sdc] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1492.984090] sd 35:0:0:0: [sdc] Sense Key : Medium Error [current] 
[ 1492.984094] sd 35:0:0:0: [sdc] Add. Sense: Data phase error
[ 1492.984097] sd 35:0:0:0: [sdc] CDB: Read(10) 28 00 00 3c ca c0 00 00 08 00
[ 1492.984100] blk_update_request: I/O error, dev sdc, sector 3984064
[ 1516.945163] sd 35:0:0:0: [sdc] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1516.945167] sd 35:0:0:0: [sdc] Sense Key : Medium Error [current] 
[ 1516.945169] sd 35:0:0:0: [sdc] Add. Sense: Data phase error
[ 1516.945172] sd 35:0:0:0: [sdc] CDB: Read(10) 28 00 00 3c ca c0 00 00 08 00
[ 1516.945173] blk_update_request: I/O error, dev sdc, sector 3984064
[ 1516.945177] Buffer I/O error on dev sdc1, logical block 489968, async page read
[ 1517.088615] md: export_rdev(sdc2)
[ 1517.093427] md: export_rdev(sdc2)
[ 1517.111599] md: export_rdev(sdc3)
[ 1517.116648] md: export_rdev(sdc3)
[ 1517.132338] md: export_rdev(sdc4)
[ 1517.134496] md: export_rdev(sdc4)
[ 1761.496542] EXT4-fs (loop0): mounting ext3 file system using the ext4 subsystem
[ 1761.496557] EXT4-fs (loop0): bad geometry: block count 499952 exceeds size of device (120452 blocks)
[ 4992.005590] EXT4-fs (loop0): mounting ext3 file system using the ext4 subsystem
[ 4992.006389] EXT4-fs (loop0): bad geometry: block count 499952 exceeds size of device (120452 blocks)
[ 5069.353129] EXT4-fs (loop0): mounting ext3 file system using the ext4 subsystem
[ 5069.353173] EXT4-fs (loop0): bad geometry: block count 499952 exceeds size of device (120452 blocks)

```


What else should I try?

Please remember this HD has data I must not loose!

Thanks
Gilson

---

### Post by tgalati4 on 2015-12-03
A RAID1 will typically work in a degraded fashion when 1 drive fails.  When the second drive fails, it will fail to mount.  So if your *dmesg* output is on the "good" drive, then you now have 2 failed drives and data recovery is not trivial.

---

### Post by gilsonsjc on 2015-12-03
I forgot to mention that the above commands I got running it on a Ubuntu virtual machine and having the good drive connected to the laptop with a Sata to USB cable - not sure it that changes anything.

---

### Post by tgalati4 on 2015-12-03
Check the SMART parameters of the disk drive:

```
sudo smartctl -a /dev/sdg
```

Your drive number will be different from /dev/sdg.

---

### Post by gilsonsjc on 2015-12-04
Here it goes

```

gsantos@ubuntu:~$ smartctl -a /dev/sdb
smartctl 6.4 2014-10-07 r4002 [x86_64-linux-4.2.0-19-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org

/dev/sdb: Unknown USB bridge [0x0928:0x000a (0x000)]
Please specify device type with the -d option.

Use smartctl -h to get a usage summary
```

---

### Post by tgalati4 on 2015-12-04
You can't get SMART parameters through a USB enclosure.  You need to connect it to a SATA port.

---

### Post by gilsonsjc on 2015-12-04
I am sorry. All I get is a Sata to USB and a laptop. Is there any way I can do it with what I have?

---

### Post by tgalati4 on 2015-12-04
Put the hard drive in a desktop computer with a LiveUSB of Ubuntu 14.04.  Connect the hard drive with a SATA cable and connect to the network with an ethernet cable.  Boot, install *smartmontools*, it will be in RAM only with a Live session, check the SMART status of the drive.

---

### Post by gilsonsjc on 2015-12-05
As I told you, I do not own a desktop. I will have to borrow that computer from someone to use it for a couple of hours. Having said that, what else I will need to run on the desktop? Thanks

---

### Post by tgalati4 on 2015-12-05
As long as you have a wired, ethernet connection to the computer, you should be able to boot the LiveUSB stick, install *smartmontools* run the command to get the SMART parameters.  You need to determine what is causing both hard drives to fail before you can start a recovery process.

Some reading:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

In theory, you should be able to find a near-matching 2TB drive, put it in your NAS, now with 2 matching disk drives, and let the NAS rebuild the RAID1 pool.  If this is successful, then you have access to your data, and a short-term backup, until you move your data to another medium.

---

### Post by gilsonsjc on 2015-12-07
Hi - I borrow a desktop pc from good friend of mine (thanks Cassio!!!) and was finally able to run the smartctl command as requested. Please find below the output

```
smartctl 6.4 2014-10-07 r4002 [x86_64-linux-4.2.0-16-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF)
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WCAZA6352649
LU WWN Device Id: 5 0014ee 25b100d33
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 1.5 Gb/s
Local Time is:    Tue Dec  8 01:39:40 2015 UTC
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
data collection: 		(35460) seconds.
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
recommended polling time: 	 ( 342) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   194   194   051    Pre-fail  Always       -       3201
  3 Spin_Up_Time            0x0027   253   164   021    Pre-fail  Always       -       941
  4 Start_Stop_Count        0x0032   091   091   000    Old_age   Always       -       9385
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   066   066   000    Old_age   Always       -       25107
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       332
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       175
193 Load_Cycle_Count        0x0032   009   009   000    Old_age   Always       -       574030
194 Temperature_Celsius     0x0022   113   075   000    Old_age   Always       -       37
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       19
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       1
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       4

SMART Error Log Version: 1
ATA Error Count: 483 (device log contains only the most recent five errors)
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

Error 483 occurred at disk power-on lifetime: 25103 hours (1045 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 c0 ca 3c e0  Error: UNC 8 sectors at LBA = 0x003ccac0 = 3984064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c0 ca 3c e0 00      00:49:10.711  READ DMA
  ec 00 00 00 00 00 e0 00      00:49:08.043  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:49:08.033  SET FEATURES [Set transfer mode]

Error 482 occurred at disk power-on lifetime: 25103 hours (1045 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 c0 ca 3c e0  Error: UNC 8 sectors at LBA = 0x003ccac0 = 3984064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c0 ca 3c e0 00      00:48:35.729  READ DMA
  ec 00 00 00 00 00 e0 00      00:48:32.975  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:48:32.962  SET FEATURES [Set transfer mode]

Error 481 occurred at disk power-on lifetime: 25103 hours (1045 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 c0 ca 3c e0  Error: UNC 8 sectors at LBA = 0x003ccac0 = 3984064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c0 ca 3c e0 00      00:47:59.800  READ DMA
  ec 00 00 00 00 00 e0 00      00:47:57.122  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:47:57.122  SET FEATURES [Set transfer mode]

Error 480 occurred at disk power-on lifetime: 25103 hours (1045 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 c0 ca 3c e0  Error: UNC 8 sectors at LBA = 0x003ccac0 = 3984064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 c0 ca 3c e0 00      00:47:24.553  READ DMA

Error 479 occurred at disk power-on lifetime: 25103 hours (1045 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 40 7b 39 e0  Error: UNC 8 sectors at LBA = 0x00397b40 = 3767104

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 40 7b 39 e0 00      00:46:19.839  READ DMA
  ec 00 00 00 00 00 e0 00      00:46:19.814  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:46:19.795  SET FEATURES [Set transfer mode]

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

I ran some additional commands too:
```
Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 45A11E44-7BEE-40FA-AF61-C0D4CA0654D0

Device       Start        End    Sectors   Size Type
/dev/sda1    64320    3984191    3919872   1.9G Linux RAID
/dev/sda2  3984192    4498175     513984   251M Linux RAID
/dev/sda3  4498176    6474175    1976000 964.9M Linux RAID
/dev/sda4  6474176 3907029134 3900554959   1.8T Linux RAID

ubuntu@ubuntu:~$ sudo mount /dev/md0 /mnt
mount: special device /dev/md0 does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sda /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
ubuntu@ubuntu:~$ dmesg | tail -n 100
[   60.699395] ata1.00: status: { DRDY ERR }
[   60.699397] ata1.00: error: { UNC }
[   60.708547] ata1.00: configured for UDMA/133
[   60.708563] sd 0:0:0:0: [sda] tag#25 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   60.708568] sd 0:0:0:0: [sda] tag#25 Sense Key : Medium Error [current] [descriptor] 
[   60.708571] sd 0:0:0:0: [sda] tag#25 Add. Sense: Unrecovered read error - auto reallocate failed
[   60.708576] sd 0:0:0:0: [sda] tag#25 CDB: Read(10) 28 00 00 3c cb 40 00 01 00 00
[   60.708578] blk_update_request: I/O error, dev sda, sector 3984200
[   60.708597] ata1: EH complete
[   63.496075] ata1.00: exception Emask 0x0 SAct 0x83 SErr 0x0 action 0x0
[   63.496080] ata1.00: irq_stat 0x40000008
[   63.496083] ata1.00: failed command: READ FPDMA QUEUED
[   63.496089] ata1.00: cmd 60/08:38:40:cb:3c/00:00:00:00:00/40 tag 7 ncq 4096 in
                        res 41/40:00:40:cb:3c/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[   63.496092] ata1.00: status: { DRDY ERR }
[   63.496094] ata1.00: error: { UNC }
[   63.506084] ata1.00: configured for UDMA/133
[   63.506101] sd 0:0:0:0: [sda] tag#7 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   63.506105] sd 0:0:0:0: [sda] tag#7 Sense Key : Medium Error [current] [descriptor] 
[   63.506109] sd 0:0:0:0: [sda] tag#7 Add. Sense: Unrecovered read error - auto reallocate failed
[   63.506113] sd 0:0:0:0: [sda] tag#7 CDB: Read(10) 28 00 00 3c cb 40 00 00 08 00
[   63.506115] blk_update_request: I/O error, dev sda, sector 3984192
[   63.506119] Buffer I/O error on dev sda2, logical block 0, async page read
[   63.506130] ata1: EH complete
[   63.746160] cgroup: new mount options do not match the existing superblock, will be ignored
[   64.961224] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[   65.160352] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready
[   66.709432] e1000e: enp0s25 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   66.709541] e1000e 0000:00:19.0 enp0s25: 10/100 speed: disabling TSO
[   66.709576] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready
[  181.370324] ata1.00: exception Emask 0x0 SAct 0x20 SErr 0x0 action 0x0
[  181.370330] ata1.00: irq_stat 0x40000008
[  181.370334] ata1.00: failed command: READ FPDMA QUEUED
[  181.370340] ata1.00: cmd 60/08:28:40:cb:3c/00:00:00:00:00/40 tag 5 ncq 4096 in
                        res 41/40:00:40:cb:3c/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  181.370343] ata1.00: status: { DRDY ERR }
[  181.370346] ata1.00: error: { UNC }
[  181.378726] ata1.00: configured for UDMA/133
[  181.378740] sd 0:0:0:0: [sda] tag#5 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  181.378745] sd 0:0:0:0: [sda] tag#5 Sense Key : Medium Error [current] [descriptor] 
[  181.378749] sd 0:0:0:0: [sda] tag#5 Add. Sense: Unrecovered read error - auto reallocate failed
[  181.378753] sd 0:0:0:0: [sda] tag#5 CDB: Read(10) 28 00 00 3c cb 40 00 00 08 00
[  181.378756] blk_update_request: I/O error, dev sda, sector 3984192
[  181.378769] ata1: EH complete
[  184.875317] ata1.00: exception Emask 0x0 SAct 0x2000000 SErr 0x0 action 0x0
[  184.875321] ata1.00: irq_stat 0x40000008
[  184.875325] ata1.00: failed command: READ FPDMA QUEUED
[  184.875331] ata1.00: cmd 60/08:c8:30:cb:3c/00:00:00:00:00/40 tag 25 ncq 4096 in
                        res 41/40:00:30:cb:3c/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  184.875334] ata1.00: status: { DRDY ERR }
[  184.875337] ata1.00: error: { UNC }
[  184.884796] ata1.00: configured for UDMA/133
[  184.884808] sd 0:0:0:0: [sda] tag#25 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  184.884812] sd 0:0:0:0: [sda] tag#25 Sense Key : Medium Error [current] [descriptor] 
[  184.884816] sd 0:0:0:0: [sda] tag#25 Add. Sense: Unrecovered read error - auto reallocate failed
[  184.884820] sd 0:0:0:0: [sda] tag#25 CDB: Read(10) 28 00 00 3c cb 30 00 00 08 00
[  184.884822] blk_update_request: I/O error, dev sda, sector 3984176
[  184.884834] ata1: EH complete
[  187.660008] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[  187.660013] ata1.00: irq_stat 0x40000008
[  187.660016] ata1.00: failed command: READ FPDMA QUEUED
[  187.660022] ata1.00: cmd 60/01:00:3f:cb:3c/00:00:00:00:00/40 tag 0 ncq 512 in
                        res 41/40:00:3f:cb:3c/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  187.660025] ata1.00: status: { DRDY ERR }
[  187.660027] ata1.00: error: { UNC }
[  187.669404] ata1.00: configured for UDMA/133
[  187.669416] sd 0:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  187.669421] sd 0:0:0:0: [sda] tag#0 Sense Key : Medium Error [current] [descriptor] 
[  187.669424] sd 0:0:0:0: [sda] tag#0 Add. Sense: Unrecovered read error - auto reallocate failed
[  187.669428] sd 0:0:0:0: [sda] tag#0 CDB: Read(10) 28 00 00 3c cb 3f 00 00 01 00
[  187.669431] blk_update_request: I/O error, dev sda, sector 3984191
[  187.669444] ata1: EH complete
[  190.444774] ata1.00: exception Emask 0x0 SAct 0x40000 SErr 0x0 action 0x0
[  190.444779] ata1.00: irq_stat 0x40000008
[  190.444782] ata1.00: failed command: READ FPDMA QUEUED
[  190.444789] ata1.00: cmd 60/01:90:3e:cb:3c/00:00:00:00:00/40 tag 18 ncq 512 in
                        res 41/40:00:3e:cb:3c/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  190.444792] ata1.00: status: { DRDY ERR }
[  190.444794] ata1.00: error: { UNC }
[  190.454920] ata1.00: configured for UDMA/133
[  190.454932] sd 0:0:0:0: [sda] tag#18 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  190.454937] sd 0:0:0:0: [sda] tag#18 Sense Key : Medium Error [current] [descriptor] 
[  190.454940] sd 0:0:0:0: [sda] tag#18 Add. Sense: Unrecovered read error - auto reallocate failed
[  190.454944] sd 0:0:0:0: [sda] tag#18 CDB: Read(10) 28 00 00 3c cb 3e 00 00 01 00
[  190.454947] blk_update_request: I/O error, dev sda, sector 3984190
[  190.454959] ata1: EH complete
[  193.217853] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
[  193.217857] ata1.00: irq_stat 0x40000008
[  193.217861] ata1.00: failed command: READ FPDMA QUEUED
[  193.217867] ata1.00: cmd 60/08:08:c0:ca:3c/00:00:00:00:00/40 tag 1 ncq 4096 in
                        res 41/40:00:c0:ca:3c/00:00:00:00:00/40 Emask 0x409 (media error) <F>
[  193.217870] ata1.00: status: { DRDY ERR }
[  193.217872] ata1.00: error: { UNC }
[  193.227425] ata1.00: configured for UDMA/133
[  193.227437] sd 0:0:0:0: [sda] tag#1 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  193.227442] sd 0:0:0:0: [sda] tag#1 Sense Key : Medium Error [current] [descriptor] 
[  193.227445] sd 0:0:0:0: [sda] tag#1 Add. Sense: Unrecovered read error - auto reallocate failed
[  193.227449] sd 0:0:0:0: [sda] tag#1 CDB: Read(10) 28 00 00 3c ca c0 00 00 08 00
[  193.227452] blk_update_request: I/O error, dev sda, sector 3984064
[  193.227465] ata1: EH complete


```




What shall I do next?

---

### Post by steeldriver on 2015-12-07
Just FYI, the WD Greens are not recommended for RAID because the 'Idle 3' Intellipark feature can cause excessive load cycle counts. Just something to be aware of when you're shopping for the replacement drives.

---

### Post by tgalati4 on 2015-12-07
Yes, and I assume that you bought the NAS enclosure without disks and put your own disks in it.  Green disks generally are not suitable for RAID service.

So you have 25K hours on this drive.  Most consumer drives are rated to 30k hours.  You have 547K load cycles.  Most consumer drives are rated to 600K.  So your drive is nearing the end of its life from a design standpoint.  You have 8 uncorrectable sectors.  This is not bad for the drive's age, and if this number increases linearly with time, then it's time to replace the drive.  You have had 19 relocation events, meaning the drive's firmware has attempted to move data from the bad sectors to reserve sectors 19 times.  So your drive has passed, but it is starting to have issues.

What are the SMART parameters for the second 2TB disk drive?

The *dmesg* output is troubling.  The kernel really wants to read those bad sectors.

---

### Post by gilsonsjc on 2015-12-08
> **steeldriver said:**
> Just FYI, the WD Greens are not recommended for RAID because the 'Idle 3' Intellipark feature can cause excessive load cycle counts. Just something to be aware of when you're shopping for the replacement drives.

I wish I knew that sooner. I bought 2x5TB WD Green HDs which are currently running in the same NAS in RAID 1. :(

> **tgalati4 said:**
> Yes, and I assume that you bought the NAS enclosure without disks and put your own disks in it.  Green disks generally are not suitable for RAID service.

So you have 25K hours on this drive.  Most consumer drives are rated to 30k hours.  You have 547K load cycles.  Most consumer drives are rated to 600K.  So your drive is nearing the end of its life from a design standpoint.  You have 8 uncorrectable sectors.  This is not bad for the drive's age, and if this number increases linearly with time, then it's time to replace the drive.  You have had 19 relocation events, meaning the drive's firmware has attempted to move data from the bad sectors to reserve sectors 19 times.  So your drive has passed, but it is starting to have issues.

What are the SMART parameters for the second 2TB disk drive?

The *dmesg* output is troubling.  The kernel really wants to read those bad sectors.

I actually bought the NAS with the disks on it already. Weeks ago I bought the replacement disk myself. Following WD's recommendation, I got 2x5tb green disks WD to run in raid 1 in the same NAS (MBWE II Whitelights). I wish I had known they were not good for RAID 1 before.

I connected the other drive to the computer (the one that failed) as you recommended. Please find below the information about it:


```
Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdb
smartctl 6.4 2014-10-07 r4002 [x86_64-linux-4.2.0-16-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (AF)
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WCAZA6328687
LU WWN Device Id: 5 0014ee 25b0ffdec
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 1.5 Gb/s
Local Time is:    Tue Dec  8 08:42:49 2015 UTC
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
data collection: 		(35760) seconds.
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
recommended polling time: 	 ( 345) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   239   166   021    Pre-fail  Always       -       3016
  4 Start_Stop_Count        0x0032   091   091   000    Old_age   Always       -       9331
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   066   066   000    Old_age   Always       -       25103
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       306
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       140
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       625927
194 Temperature_Celsius     0x0022   121   075   000    Old_age   Always       -       29
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

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

What should I do next?

Thank you!

---

### Post by steeldriver on 2015-12-08
> **gilsonsjc said:**
> I wish I knew that sooner. I bought 2x5TB WD Green HDs which are currently running in the same NAS in RAID 1. :(

Well FWIW I run a RAID1 setup with a pair of WD20EARX Greens, however I used idle3-tools to disable the IntelliPark feature on them (there may be better ways now. I haven't checked recently)

[http://idle3-tools.sourceforge.net/](http://idle3-tools.sourceforge.net/)

They are currently showing LCCs of 22587 and 28833 respectively after a little over 30,000 power-on hrs  (the asymmetry is due to having a small /var partition on one I think: the RAID arrays don't use the whole disk)

---

### Post by tgalati4 on 2015-12-08
The disk that failed, actually looks in better shape than the working disk.  So take a Sharpie and mark the drives as Drive 0 and Drive 1 and assume that they are both mechanically working.  Take another two 2 TB drives and use *dd* to copy the data from Drive 0 to a fresh disk and Drive 1 to a fresh disk.  Mark them as Drive 0 New and Drive 1 New.  Put those in your NAS and try to mount.  After copying, put Drive 0 and Drive 1 in a safe place.  Do no further operations with them.  Do no further operations with them.

You will now attempt to recover data from the copies that you have made, Drive 0 New and Drive 1 New.

Since it is a Western Digital MyBook NAS, it makes sense that it would have WD drives.  Green drives are consumer-grade drives.  After going through the Agony Units of data recovery, your opinion of Green drives may change.

Are you running the latest [firmware]("http://http://support.wdc.com/KnowledgeBase/answer.aspx?ID=3304") on the NAS?

Some reading:  [http://mybookworld.wikidot.com/forum/t-90514/how-to-recover-data-from-wd-my-book-world-edition-nas-device](http://mybookworld.wikidot.com/forum/t-90514/how-to-recover-data-from-wd-my-book-world-edition-nas-device)

The most important step is working on copies of your original drives.  Any further operations on your original drives puts your data at risk.

I don't have a MyBook, but my quick web search confirms that recovery is automatic as long as you one good RAID1 drive and one good, matching blank drive.  I would assume that you should be able to mount the NAS to at least access your data with one good RAID1.  So, now I have to assume that you have other problems, like both drives are scrambled, or the NAS power supply is weak, or the NAS hardware is failing.

---

### Post by gilsonsjc on 2015-12-08
so it looks like I just need to run the following command in order to disable it?
 ```
idle3ctl -d /dev/sda
```

Does it void the warranty?

> **tgalati4 said:**
> The disk that failed, actually looks in better shape than the working disk.  So take a Sharpie and mark the drives as Drive 0 and Drive 1 and assume that they are both mechanically working.  Take another two 2 TB drives and use *dd* to copy the data from Drive 0 to a fresh disk and Drive 1 to a fresh disk.  Mark them as Drive 0 New and Drive 1 New.  Put those in your NAS and try to mount.  After copying, put Drive 0 and Drive 1 in a safe place.  Do no further operations with them.  Do no further operations with them.

You will now attempt to recover data from the copies that you have made, Drive 0 New and Drive 1 New.

Since it is a Western Digital MyBook NAS, it makes sense that it would have WD drives.  Green drives are consumer-grade drives.  After going through the Agony Units of data recovery, your opinion of Green drives may change.

Are you running the latest [firmware]("http://http://support.wdc.com/KnowledgeBase/answer.aspx?ID=3304") on the NAS?

Some reading:  [http://mybookworld.wikidot.com/forum/t-90514/how-to-recover-data-from-wd-my-book-world-edition-nas-device](http://mybookworld.wikidot.com/forum/t-90514/how-to-recover-data-from-wd-my-book-world-edition-nas-device)

The most important step is working on copies of your original drives.  Any further operations on your original drives puts your data at risk.

I don't have a MyBook, but my quick web search confirms that recovery is automatic as long as you one good RAID1 drive and one good, matching blank drive.  I would assume that you should be able to mount the NAS to at least access your data with one good RAID1.  So, now I have to assume that you have other problems, like both drives are scrambled, or the NAS power supply is weak, or the NAS hardware is failing.

Hey tgalati4, here is what I have here:
1) NAS with brand new 2x5TB disks running on RAID 1 - since it is brand new without any data on it I can remove them from the NAS and use it them if needed.
2) 2x2TB disks (Drive 0 and/or Drive 1) that used to run on the same NAS in #1 on RAID 1. I tried to clean the disks that have failed (lets brand it as "Drive 0") using the clean disk option in the NAS Web GUI, I guess that option has formatted the disk. However it continued failing.
3) 1 Sata to USB enclosure
4) 1 PC with 2 SATA ports running Ubuntu from USB, temporarily borrowed from a good friend.

I can't get another disks due to budget issues. Is there any way to work only what I have here do recovery the data from Drive 1 and/or Drive 0?

I am running the latest firmware from WD and it is working just fine with the new 2x5tb disks.

I also have a thread opened on that forum, let me read that link to see what if I can get anything.

My NAS does not work with neither Disk 0 or Disk 1 mounted, either together or separately one at a time.

---

### Post by tgalati4 on 2015-12-08
Some more tips:  [http://iknowsomething.com/how-to-fix-bricked-wd-my-book-world-edition-or-install-brand-new-disk/](http://iknowsomething.com/how-to-fix-bricked-wd-my-book-world-edition-or-install-brand-new-disk/)

Sometimes disks with 30K hours get sticky spindles, run hotter, and take more power.  So, purchase a new power supply, and see if the disks spin up properly.  It's possible the new 5TB disks spin easier (they are new after all).

One way to copy two disks:

```
sudo cp /dev/sda /dev/sdb
```

So you could simply copy the 2 TB drive to the 5 TB drive and then use *parted* to fix the partitions.  You could simply mark the remaining 3 TB space as a separate, blank partition.  Mark the unit Drive 0 New.  Put that in the NAS, by itself, and see if it mounts and if you can see your data.  Don't put the second disk in it.  Set the NAS to JBOD mode.

I don't know what the "Clean Disk Option" mode does from the web panel.  If you did wipe the disk, then data recovery is difficult.  Use *testdisk* and *photorec* to attempt to recover data.  You can use your second 5 TB drive to receive the recovered files.

---

### Post by gilsonsjc on 2015-12-08
> **gilsonsjc said:**
> Hey tgalati4, here is what I have here:
1) NAS with brand new 2x5TB disks running on RAID 1 - since it is brand new without any data on it I can remove them from the NAS and use it them if needed.
2) 2x2TB disks (Drive 0 and/or Drive 1) that used to run on the same NAS in #1 on RAID 1. I tried to clean the disks that have failed (lets brand it as "Drive 0") using the clean disk option in the NAS Web GUI, I guess that option has formatted the disk. However it continued failing.
3) 1 Sata to USB enclosure
4) 1 PC with 2 SATA ports running Ubuntu from USB, temporarily borrowed from a good friend.

I can't get another disks due to budget issues. Is there any way to work only what I have here do recovery the data from Drive 1 and/or Drive 0?

I am running the latest firmware from WD and it is working just fine with the new 2x5tb disks.

I also have a thread opened on that forum, let me read that link to see what if I can get anything.

My NAS does not work with neither Disk 0 or Disk 1 mounted, either together or separately one at a time.

I've tried the commands on the linked page and it did not work out:

```

Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 45A11E44-7BEE-40FA-AF61-C0D4CA0654D0

Device       Start        End    Sectors   Size Type
/dev/sda1    64320    3984191    3919872   1.9G Linux RAID
/dev/sda2  3984192    4498175     513984   251M Linux RAID
/dev/sda3  4498176    6474175    1976000 964.9M Linux RAID
/dev/sda4  6474176 3907029134 3900554959   1.8T Linux RAID


ubuntu@ubuntu:~/Desktop$ sudo modprobe md
modprobe: FATAL: Module md not found.
ubuntu@ubuntu:~/Desktop$ sudo mknod /dev/md4 b 9 4
ubuntu@ubuntu:~/Desktop$ sudo mdadm --assemble /dev/md4 /dev/sda4
mdadm: /dev/sda4 is busy - skipping
ubuntu@ubuntu:~/Desktop$ sudo mkdir /media/xyz
ubuntu@ubuntu:~/Desktop$ sudo mount /dev/md4 /media/xyz
mount: /dev/md4: can't read superblock
ubuntu@ubuntu:~/Desktop$ sudo chmod -R 777 /media/xyz

```

> **tgalati4 said:**
> Some more tips:  [http://iknowsomething.com/how-to-fix-bricked-wd-my-book-world-edition-or-install-brand-new-disk/](http://iknowsomething.com/how-to-fix-bricked-wd-my-book-world-edition-or-install-brand-new-disk/)

I ran that process to install the new 2x5TB disks and it worked. Let me try that with the Disk 1 and it does not work with Disk 0 using the option to NOT to destroy the data.

> **gilsonsjc said:**
> I ran that process to install the new 2x5TB disks and it worked. Let me try that with the Disk 1 and it does not work with Disk 0 using the option to NOT to destroy the data.

I have just realized that I can not run that process on the Disk 0 nor Disk 1 since it will destroy all data!

Since you told me the Disk 0 (the bad one) is better than the good one, would you provide me with the steps to recover the older partition so that I can try to recover the data from there instead from the good disk Disk 1?

> **gilsonsjc said:**
> I have just realized that I can not run that process on the Disk 0 nor Disk 1 since it will destroy all data!

Since you told me the Disk 0 (the bad one) is better than the good one, would you provide me with the steps to recover the older partition so that I can try to recover the data from there instead from the good disk Disk 1?

I gave the testdisk a shot and ran against the drive that failed. Here are some screenshots:

[ATTACH=CONFIG]266051[/ATTACH]
[ATTACH=CONFIG]266052[/ATTACH]

 I am stuck in this step here. What should I do next?

---

### Post by tgalati4 on 2015-12-08
I can't recommend any operation on Disk 0 or Disk 1 as that puts your data at risk.  The only recommendation I can make is to *cp*, *dd*, *ddrescue*, or use *clonezilla* to make a copy of one of your disks (either Disk 0 or Disk 1).  Then, and only then, perform the data rescue from the copy.

There are several flavors of RAID1.  I do not know what the MyBook uses for its RAID1.  Obviously, *[testdisk]("http://www.cgsecurity.org/wiki/TestDisk")* does not support it.  It supports standard, Linux, software raid (md).  Don't assume that your disk has an *md* RAID1 on it.

---

### Post by gilsonsjc on 2015-12-10
> **tgalati4 said:**
> Some more tips:
[http://iknowsomething.com/how-to-fix-bricked-wd-my-book-world-edition-or-install-brand-new-disk/](http://iknowsomething.com/how-to-fix-bricked-wd-my-book-world-edition-or-install-brand-new-disk/)

Sometimes disks with 30K hours get sticky spindles, run hotter, and
take more power.  So, purchase a new power supply, and see if the
disks spin up properly.  It's possible the new 5TB disks spin easier
(they are new after all).

One way to copy two disks:

```
sudo cp /dev/sda /dev/sdb
```

So you could simply copy the 2 TB drive to the 5 TB drive and then use
*parted* to fix the partitions.  You could simply mark the
remaining 3 TB space as a separate, blank partition.  Mark the unit
Drive 0 New.  Put that in the NAS, by itself, and see if it mounts and
if you can see your data.  Don't put the second disk in it.  Set the
NAS to JBOD mode.

I don't know what the "Clean Disk Option" mode does from the web
panel.  If you did wipe the disk, then data recovery is difficult.
Use *testdisk* and *photorec* to attempt to recover data.
You can use your second 5 TB drive to receive the recovered
files.

So I created a copy of the Drive 1 to the Drive 1 new. I picked the
Drive 1 first because you said before it was in better conditions that
the disk that did not failed.

Here are the steps I followed:
```
ubuntu@ubuntu:~$ sudo cp /dev/sdb /dev/sda
ubuntu@ubuntu:~$ sudo fdisk -l
GPT PMBR size mismatch (3907029167 != 1177606575) will be corrected by w(rite).
Disk /dev/sda: 4.6 TiB, 5000981078016 bytes, 9767541168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: B138D12E-0A18-4727-BBB4-B2C151A4DFCD

```

The first line (GPT PMBR etc...) was written in red

Then I tried parted to recover the lost partitions. Not sure if I am
entering bad start and end parameters (that was a guess, I don't even
have a clue of values to use) and it did not return anything, output
below
```

ubuntu@ubuntu:~$ sudo parted /dev/sda
GNU Parted 3.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) rescue
Warning: Not all of the space available to /dev/sda appears to be used, you can
fix the GPT to use all of the space (an extra 5860512000 blocks) or continue
with the current setting?
Fix/Ignore? Ignore
Start? 0
End? 60000000000

(parted)

```

Then I tried testdisk, and wrote the last Linux raid partition (the
biggest one in green below)

[ATTACH=CONFIG]266071[/ATTACH]

THis is how it looks like after testdisk
```

Disk /dev/sda: 4.6 TiB, 5000981078016 bytes, 9767541168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: F59CA53A-56AF-0244-A5FB-A23CA28484D4

Device       Start        End    Sectors  Size Type
/dev/sda1  6474176 3907028869 3900554694  1.8T Linux RAID

```

Then I tried the following
```

root@ubuntu:/home/ubuntu# modprobe mdmodprobe: FATAL: Module md not found.

root@ubuntu:/home/ubuntu# find /lib/modules/ -name "md*"
/lib/modules/4.2.0-16-generic/kernel/crypto/md4.ko
/lib/modules/4.2.0-16-generic/kernel/drivers/md
/lib/modules/4.2.0-16-generic/kernel/drivers/md/md-cluster.ko
/lib/modules/4.2.0-16-generic/kernel/drivers/net/mdio.ko
/lib/modules/4.2.0-16-generic/kernel/drivers/net/phy/mdio-bcm-unimac.ko
/lib/modules/4.2.0-16-generic/kernel/drivers/net/phy/mdio-bitbang.ko
/lib/modules/4.2.0-16-generic/kernel/drivers/net/phy/mdio-gpio.ko
/lib/modules/4.2.0-16-generic/kernel/drivers/net/phy/mdio-octeon.ko
/lib/modules/4.2.0-16-generic/kernel/drivers/staging/lustre/lustre/mdc
/lib/modules/4.2.0-16-generic/kernel/drivers/staging/lustre/lustre/mdc/mdc.ko
/lib/modules/4.2.0-16-generic/kernel/drivers/usb/image/mdc800.ko

root@ubuntu:/home/ubuntu# ls -alh /lib/modules/4.2.0-16-generic/kernel/drivers/md
total 1.2M
drwxr-xr-x  4 root root  749 Oct 21 15:53 .
drwxr-xr-x 86 root root 1.3K Oct 21 15:57 ..
drwxr-xr-x  2 root root   32 Oct 21 15:53 bcache
-rw-r--r--  1 root root  18K Oct  8 17:24 dm-bio-prison.ko
-rw-r--r--  1 root root  49K Oct  8 17:24 dm-bufio.ko
-rw-r--r--  1 root root  13K Oct  8 17:24 dm-cache-cleaner.ko
-rw-r--r--  1 root root  95K Oct  8 17:24 dm-cache.ko
-rw-r--r--  1 root root  21K Oct  8 17:24 dm-cache-mq.ko
-rw-r--r--  1 root root  25K Oct  8 17:24 dm-cache-smq.ko
-rw-r--r--  1 root root  44K Oct  8 17:24 dm-crypt.ko
-rw-r--r--  1 root root  14K Oct  8 17:24 dm-delay.ko
-rw-r--r--  1 root root  38K Oct  8 17:24 dm-era.ko
-rw-r--r--  1 root root  14K Oct  8 17:24 dm-flakey.ko
-rw-r--r--  1 root root  24K Oct  8 17:24 dm-log.ko
-rw-r--r--  1 root root  29K Oct  8 17:24 dm-log-userspace.ko
-rw-r--r--  1 root root  25K Oct  8 17:24 dm-log-writes.ko
-rw-r--r--  1 root root  34K Oct  8 17:24 dm-mirror.ko
-rw-r--r--  1 root root  43K Oct  8 17:24 dm-multipath.ko
-rw-r--r--  1 root root 9.5K Oct  8 17:24 dm-queue-length.ko
-rw-r--r--  1 root root  37K Oct  8 17:24 dm-raid.ko
-rw-r--r--  1 root root  24K Oct  8 17:24 dm-region-hash.ko
-rw-r--r--  1 root root 8.8K Oct  8 17:24 dm-round-robin.ko
-rw-r--r--  1 root root 9.8K Oct  8 17:24 dm-service-time.ko
-rw-r--r--  1 root root  68K Oct  8 17:24 dm-snapshot.ko
-rw-r--r--  1 root root  15K Oct  8 17:24 dm-switch.ko
-rw-r--r--  1 root root 107K Oct  8 17:24 dm-thin-pool.ko
-rw-r--r--  1 root root  26K Oct  8 17:24 dm-verity.ko
-rw-r--r--  1 root root 6.4K Oct  8 17:24 dm-zero.ko
-rw-r--r--  1 root root  12K Oct  8 17:24 faulty.ko
-rw-r--r--  1 root root  13K Oct  8 17:24 linear.ko
-rw-r--r--  1 root root  28K Oct  8 17:24 md-cluster.ko
-rw-r--r--  1 root root  19K Oct  8 17:24 multipath.ko
drwxr-xr-x  2 root root   44 Oct 21 15:53 persistent-data
-rw-r--r--  1 root root  25K Oct  8 17:24 raid0.ko
-rw-r--r--  1 root root  75K Oct  8 17:24 raid10.ko
-rw-r--r--  1 root root  59K Oct  8 17:24 raid1.ko
-rw-r--r--  1 root root 162K Oct  8 17:24 raid456.ko

root@ubuntu:/home/ubuntu# cat /proc/mdstat
Personalities : 
unused devices: <none>

root@ubuntu:/home/ubuntu# modprobe -l | grep md
modprobe: invalid option -- 'l'

root@ubuntu:/home/ubuntu# fgrep CONFIG_MD /boot/config-$(uname -r)CONFIG_MD=y
CONFIG_MD_AUTODETECT=y
CONFIG_MD_LINEAR=m
CONFIG_MD_RAID0=m
CONFIG_MD_RAID1=m
CONFIG_MD_RAID10=m
CONFIG_MD_RAID456=m
CONFIG_MD_MULTIPATH=m
CONFIG_MD_FAULTY=m
CONFIG_MD_CLUSTER=m
CONFIG_MDIO=m
CONFIG_MDIO_BITBANG=m
CONFIG_MDIO_GPIO=m
CONFIG_MDIO_OCTEON=m
CONFIG_MDIO_BCM_UNIMAC=m

```

Now I am stuck on mouting the "Disk 1 new" - what shall I do? Thanks

---

### Post by tgalati4 on 2015-12-10
You were supposed to answer "Why yes, please fix the partition size for me automatically."  You answered ignore.

You are following an old tutorial.  *md* is not a module anymore.  It is now part of the kernel.  With old tutorials, you need to follow and understand the basic steps.  These steps may need to be changed with a newer system.

You are trying to mount the drive as part of a software RAID1, and it is probably not an *md* software RAID member.  My guess is it is a hardware RAID1 device.

Since this is a copy, use *testdisk* and tell it to make it an ext4 partition.  Then reboot and see if you can see it in Nautilus.

How long did it take to perform the copy?  Was it a few minutes, or did it take hours?

---

### Post by gilsonsjc on 2015-12-10
> **tgalati4 said:**
> You were supposed to answer "Why yes, please fix the partition size for me automatically."  You answered ignore.

You are following an old tutorial.  *md* is not a module anymore.  It is now part of the kernel.  With old tutorials, you need to follow and understand the basic steps.  These steps may need to be changed with a newer system.

You are trying to mount the drive as part of a software RAID1, and it is probably not an *md* software RAID member.  My guess is it is a hardware RAID1 device.

Since this is a copy, use *testdisk* and tell it to make it an ext4 partition.  Then reboot and see if you can see it in Nautilus.

I was afraid I was doing something wrong so I choose ignore. Should I take a step back and try parted again even when testdisk has already recovered the partition?
How can I confirm whether it is a hardware rather than a software RAID?
If I understood, I should use testdisk to change the /dev/sda1 partition type from Linux Raid to ext4 - is that correct?
If I am to change the partition type, which option from the list below is the ext4 one?
[ATTACH=CONFIG]266076[/ATTACH]

Thanks again

---

### Post by gilsonsjc on 2015-12-11
I started copying the Disk 0 to the other 5TB diisk using ddrescue. I am not sure if it is stuck or not, but the image sizing has not been growing for about 11 hours now. 

```
root@ubuntu:/media/ubuntu/bckp# ddrescue -d -r1  /dev/sdb /media/ubuntu/bckp/image-disk-0.raw /media/ubuntu/bckp/image-disk-0.log
GNU ddrescue 1.19
Press Ctrl-C to interrupt
rescued:   137046 MB,    errsize:   1863 GB,  current rate:          0 B/s
     ipos:       1232 GB,     errors:    1439,    average rate:     1763 kB/s
     opos:      1232 GB,  run time:   21.58 h,  successful read:   11.05 h ago
Scraping failed blocks... (forwards)

```

Should I let it continue or stop it? 

Thanks

---

### Post by tgalati4 on 2015-12-11
You have a lot going on.  Forum support works best with a one-at-time process.  First, put the Drive 1 New (that *testdisk* supposedly fixed) back into the NAS.  If it is really hardware RAID1, and *testdisk* really did fix it, then your NAS should  boot up and you should be able to see your data.

If that is the case, put the second, blank drive and see if the NAS will image it to get the full RAID1 working.

How long did the first copy take?  11 hours seems excessive.  It's possible that the drive mechanism is bad or a controller issue, or something else.  You can try to stop it, but since this is a RAID1, both disk drives should have the same data on it.  You only need to recover 1 to get most of your data back.

---

### Post by gilsonsjc on 2015-12-12
I agree with you, this post is really a mess. And it is my fault. I am going to ask the admins to close it and open a new one. Thanks for the help

---


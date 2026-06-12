---
title: "Disk write speed reduced by half over night"
date: 2013-03-10
forum: General Help
---

### Post by SaturnusDJ on 2013-03-10
After a night of sleep the write speed of my mdadm array is around 110MB/s, while before going to bed it was arround 220MB/s.

The used disks don't enter stand-by or a power saving state, nor do the s-ata links as far as I know.

What could have done this?

[SIZE=3]**Found the cause here: [http://ubuntuforums.org/showthread.php?t=2124231&page=3&p=12580567#post12580567](http://ubuntuforums.org/showthread.php?t=2124231&page=3&p=12580567#post12580567)**[/SIZE]

---

### Post by SaturnusDJ on 2013-03-11
Details:

1. Rebooting doesn't fix this problem. Powering off and on again does!
2. Sending the drives to stand-by/sleep (hdparm -y /-Y) doesn't fix or cause this problem.

Who has an idea please??

---

### Post by rnerwein on 2013-03-11
hi
it's just a feeling. for me it looks like a fully filled cache. you can try: creat a file (smaller than your cache) --> it's very, very fast. but then type: time sync  :-) ups !
ciao

---

### Post by SaturnusDJ on 2013-03-11
Thanks for the reply.
I don't understand how this will debug or solve the problem, could you explain in more detail?

This is the script I use to test:
```
dd if=/dev/zero of=/md/testfile2 bs=1M count=10000
dd if=/md/testfile2 of=/dev/null bs=1M
hdparm -t /dev/md0

```
So, three small tests: 1. Write 10GB to array. 2. Read 10GB from array. 3. Test read speed of array.

Output when used with time sync:
```
# time ./bench 
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 89.592 s, 117 MB/s
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 37.5878 s, 279 MB/s

/dev/md0:
 Timing buffered disk reads: 758 MB in  3.00 seconds = 252.39 MB/sec

real	2m15.037s
user	0m0.144s
sys	0m43.979s

```

---

### Post by SaturnusDJ on 2013-03-12
Found out something new:

I stopped the array and tested the disks individually.
/dev/sdd had a write of around 70MB/s. Other two have around 140MB/s. This combined in the array gives ~120MB/s. (See above.) The array normally has ~220MB/s.

I unplugged /dev/sdd data, and plugged back in, still slow speed.
Then I unplugged /dev/sdd data and power, and plugged back in, speeds where normal again!


How is this possible, I don't understand.

---

### Post by tgalati4 on 2013-03-12
Try moving cables around.  If the problem moves with the cable, then you might get a new cable to see if that fixes the problem. If /dev/sdd remains slow, regardless of cable used, then it's possible that the on-board SATA controller is failing and it resorts to a slower speed to maintain connectivity.

```
smartctl -a /dev/sdd
``` might show what data mode it is using.

---

### Post by SaturnusDJ on 2013-03-13
Thanks, good idea. I'll use a different cable at a different port.

After booting, kernel always reports "SATA link up 3.0 Gbps." During the night, nothing is added to the logs, so I assume link speed is still the same.

S.M.A.R.T. is clean. Nothing weird or different between the drives when looking at hdparm/smartctl information. Cron disabled, no fix.


After lots of google searched, I tried one more time and found this: [http://forums.overclockers.co.uk/showthread.php?p=22512444](http://forums.overclockers.co.uk/showthread.php?p=22512444)
Sound like my problem. I'll continue debugging first.

---

### Post by sdowney717 on 2013-03-13
Cosmic radiation killed your chips.
Reading the other forum thread indicates the drive is faulty.
Electromagnetic radiation permeates everything.
[http://www.newscientist.com/blog/technology/2008/03/do-we-need-cosmic-ray-alerts-for.html](http://www.newscientist.com/blog/technology/2008/03/do-we-need-cosmic-ray-alerts-for.html)
Drives have firmware memory.

---

### Post by SaturnusDJ on 2013-03-13
Thanks for the reply. The problem with that is a power off (not reboot) fixes the problem temporary. 

To my surprise I just found out today all drives are slow when tested individually. Search 1-2 hours for clues...nothing. 
So I created a partition in the middle of the disk and the speeds scaled down with this (as normally with a hdd). At the moment I can't think how to conclude something out of that information, but maybe someone else can.

Power off -> power on -> fixed. But of course, after the next night the writes will be slow again. So I guess changing cables/ports isn't going to do anything.

It's so hard to debug this...

---

### Post by sdowney717 on 2013-03-13
I am not convinced it is not a firmware corruption issue. the drive is mechanically ok and also somewhat electronically ok as smart data shows no errors.
The input output chips and internal memory buffers, the data is perhaps being corrupted and then has to be internally corrected on the fly as it reads and writes.
Or some IO pipeline process is being throttled. 
Sometimes you can upload new firmware to drives.
Firmware software tells the drive how to function. Bad firmware means it wont run or the drive will run poorly.
If the drives are put into another PC and have the same behavior, it is the drives problem.
Any chance you can do that or boot another OS to further test them?

---

### Post by SaturnusDJ on 2013-03-13
Okay. The easiest thing is to try a different OS, maybe 12.10 live usb instead of 12.04 minimal at ssd.
A different pc would be a lot more work, but possible.

---

### Post by tgalati4 on 2013-03-13
After reading the other post that you linked, it takes some time to narrow down both the issue and the cause.  At this point, all you can do is try different configurations to identify if the performance issue is with the disk drive itself, or a combination of SATA port, cable, machine, OS, that is causing the problem.  If you have an NTFS partition on the drive and it is slow in Windows and Linux, then you can be reasonably sure that it's the drive--after swapping cables, ports, etc, and your other drives are running much faster.

---

### Post by SaturnusDJ on 2013-03-13
I just tried BIOS F2 and F4B for my [GA-MA74GM-S2H (rev. 1.x)]("http://www.gigabyte.com/products/product-page.aspx?pid=2775#bios").
The reason is, because 'SB700 spread spectrum' won't stay disabled. I've read spread spectrum might give performance degradation, but this would be noticeable instantly, and not after a night of sleep, right?
I think normally the hard drives, WD20EFRX, don't have spread spectrum enabled. But I can enable it by placing a jumper.
Just saying.



Okay. Tonight's setup:
- Ubuntu 12.10 live usb.
- Replace 1 or more S-ATA data cables.
- One 20GB raid5 array created without --assume-clean.
- Three 10GB no raid partitions, to be able to test single disks.
- One raid5 array taking all remaining space, created with --assume-clean.
- All arrays and drives with tuned parameters.
- Verifying read/write before going to bed.

---

### Post by SaturnusDJ on 2013-03-13
Already one (third) drive dropped to low write speeds even before getting to bed...it's the one with different cable.
No logs between high and low speeds...
This makes me sick... :mad:

Edit:
Only one fast left now.

---

### Post by SaturnusDJ on 2013-03-14
So this morning all three drives were slow again. Also no clue why.

I switched back to non live environment. I'm starting to think the problem is time related. After leaving the computer idle for some hours, the write speeds are still normal.
It's like something happens around 1:30 (am).

At this moment I'm collecting a bit of iotop/free information and behavior. I'm running with 2GB RAM at this time.
```
# free -m
             total       used       free     shared    buffers     cached
Mem:          1936       1860         76          0         11       1473
-/+ buffers/cache:        375       1561
Swap:            0          0          0
```

---

### Post by tgalati4 on 2013-03-14
Some drives have a self-test routine that runs automatically every XX hours.  Perhaps when that happens your drive speed slows down.  Powering down causes the self-test clock to reset.  Your SMART parameters should show some logs about self-tests.  If there is testing data that was not run manually (*sudo smartctl -t short /dev/sda*) then maybe that is the issue.

---

### Post by SaturnusDJ on 2013-03-14
Nice idea. However the longest test takes around 4.5 hours, so when I woke up this morning they should be done already.
But here is a full S.M.A.R.T. log of one of the drivers so you can have a look yourself. :)
```
# smartctl -x /dev/sdb
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.2.0-38-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EFRX-68AX9N0
Serial Number:    WD-WMC301187959
LU WWN Device Id: 5 0014ee 603308271
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ACS-2 (revision not indicated)
Local Time is:    Thu Mar 14 19:04:50 2013 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
AAM feature is:   Unavailable
APM feature is:   Unavailable
Rd look-ahead is: Enabled
Write cache is:   Enabled
ATA Security is:  Disabled, NOT FROZEN [SEC1]

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
data collection: 		(26160) seconds.
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
recommended polling time: 	 ( 265) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x70bd)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     POSR-K   200   200   051    -    0
  3 Spin_Up_Time            POS--K   195   171   021    -    3216
  4 Start_Stop_Count        -O--CK   100   100   000    -    40
  5 Reallocated_Sector_Ct   PO--CK   200   200   140    -    0
  7 Seek_Error_Rate         -OSR-K   200   200   000    -    0
  9 Power_On_Hours          -O--CK   100   100   000    -    226
 10 Spin_Retry_Count        -O--CK   100   253   000    -    0
 11 Calibration_Retry_Count -O--CK   100   253   000    -    0
 12 Power_Cycle_Count       -O--CK   100   100   000    -    26
192 Power-Off_Retract_Count -O--CK   200   200   000    -    10
193 Load_Cycle_Count        -O--CK   200   200   000    -    30
194 Temperature_Celsius     -O---K   127   118   000    -    20
196 Reallocated_Event_Count -O--CK   200   200   000    -    0
197 Current_Pending_Sector  -O--CK   200   200   000    -    0
198 Offline_Uncorrectable   ----CK   100   253   000    -    0
199 UDMA_CRC_Error_Count    -O--CK   200   200   000    -    0
200 Multi_Zone_Error_Rate   ---R--   200   200   000    -    0
                            ||||||_ K auto-keep
                            |||||__ C event count
                            ||||___ R error rate
                            |||____ S speed/performance
                            ||_____ O updated online
                            |______ P prefailure warning

General Purpose Log Directory Version 1
SMART           Log Directory Version 1 [multi-sector log support]
GP/S  Log at address 0x00 has    1 sectors [Log Directory]
SMART Log at address 0x01 has    1 sectors [Summary SMART error log]
SMART Log at address 0x02 has    5 sectors [Comprehensive SMART error log]
GP    Log at address 0x03 has    6 sectors [Ext. Comprehensive SMART error log]
SMART Log at address 0x06 has    1 sectors [SMART self-test log]
GP    Log at address 0x07 has    1 sectors [Extended self-test log]
SMART Log at address 0x09 has    1 sectors [Selective self-test log]
GP    Log at address 0x10 has    1 sectors [NCQ Command Error log]
GP    Log at address 0x11 has    1 sectors [SATA Phy Event Counters]
GP    Log at address 0x21 has    1 sectors [Write stream error log]
GP    Log at address 0x22 has    1 sectors [Read stream error log]
GP/S  Log at address 0x80 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x81 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x82 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x83 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x84 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x85 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x86 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x87 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x88 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x89 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8a has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8b has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8c has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8d has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8e has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x8f has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x90 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x91 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x92 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x93 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x94 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x95 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x96 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x97 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x98 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x99 has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9a has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9b has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9c has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9d has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9e has   16 sectors [Host vendor specific log]
GP/S  Log at address 0x9f has   16 sectors [Host vendor specific log]
GP/S  Log at address 0xa0 has   16 sectors [Device vendor specific log]
GP/S  Log at address 0xa1 has   16 sectors [Device vendor specific log]
GP/S  Log at address 0xa2 has   16 sectors [Device vendor specific log]
GP/S  Log at address 0xa3 has   16 sectors [Device vendor specific log]
GP/S  Log at address 0xa4 has   16 sectors [Device vendor specific log]
GP/S  Log at address 0xa5 has   16 sectors [Device vendor specific log]
GP/S  Log at address 0xa6 has   16 sectors [Device vendor specific log]
GP/S  Log at address 0xa7 has   16 sectors [Device vendor specific log]
GP/S  Log at address 0xa8 has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xa9 has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xaa has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xab has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xac has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xad has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xae has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xaf has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xb0 has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xb1 has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xb2 has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xb3 has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xb4 has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xb5 has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xb6 has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xb7 has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xbd has    1 sectors [Device vendor specific log]
GP/S  Log at address 0xc0 has    1 sectors [Device vendor specific log]
GP    Log at address 0xc1 has   93 sectors [Device vendor specific log]
GP/S  Log at address 0xe0 has    1 sectors [SCT Command/Status]
GP/S  Log at address 0xe1 has    1 sectors [SCT Data Transfer]

SMART Extended Comprehensive Error Log Version: 1 (6 sectors)
No Errors Logged

SMART Extended Self-test Log Version: 1 (1 sectors)
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       179         -
# 2  Conveyance offline  Completed without error       00%       178         -
# 3  Short offline       Completed without error       00%       178         -
# 4  Short offline       Completed without error       00%        83         -
# 5  Short offline       Completed without error       00%        72         -
# 6  Extended offline    Completed without error       00%        51         -
# 7  Conveyance offline  Completed without error       00%        46         -
# 8  Short offline       Completed without error       00%        46         -
# 9  Conveyance offline  Completed without error       00%         1         -
#10  Short offline       Completed without error       00%         1         -
#11  Conveyance offline  Completed without error       00%         0         -
#12  Short offline       Completed without error       00%         0         -

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

SCT Status Version:                  3
SCT Version (vendor specific):       258 (0x0102)
SCT Support Level:                   1
Device State:                        Active (0)
Current Temperature:                    20 Celsius
Power Cycle Min/Max Temperature:     18/21 Celsius
Lifetime    Min/Max Temperature:     14/21 Celsius
Under/Over Temperature Limit Count:   0/0
SCT Temperature History Version:     2
Temperature Sampling Period:         1 minute
Temperature Logging Interval:        1 minute
Min/Max recommended Temperature:      0/60 Celsius
Min/Max Temperature Limit:           -41/85 Celsius
Temperature History Size (Index):    478 (175)

Index    Estimated Time   Temperature Celsius
 176    2013-03-14 11:07    17  -
 ...    ..( 18 skipped).    ..  -
 195    2013-03-14 11:26    17  -
 196    2013-03-14 11:27    18  -
 ...    ..( 10 skipped).    ..  -
 207    2013-03-14 11:38    18  -
 208    2013-03-14 11:39     ?  -
 209    2013-03-14 11:40    18  -
 ...    ..( 25 skipped).    ..  -
 235    2013-03-14 12:06    18  -
 236    2013-03-14 12:07    19  -
 ...    ..(  5 skipped).    ..  -
 242    2013-03-14 12:13    19  -
 243    2013-03-14 12:14    18  -
 ...    ..( 94 skipped).    ..  -
 338    2013-03-14 13:49    18  -
 339    2013-03-14 13:50    19  -
 ...    ..( 21 skipped).    ..  -
 361    2013-03-14 14:12    19  -
 362    2013-03-14 14:13    20  *
 ...    ..( 12 skipped).    ..  *
 375    2013-03-14 14:26    20  *
 376    2013-03-14 14:27    19  -
 377    2013-03-14 14:28    20  *
 ...    ..( 12 skipped).    ..  *
 390    2013-03-14 14:41    20  *
 391    2013-03-14 14:42    19  -
 ...    ..( 12 skipped).    ..  -
 404    2013-03-14 14:55    19  -
 405    2013-03-14 14:56    20  *
 ...    ..( 11 skipped).    ..  *
 417    2013-03-14 15:08    20  *
 418    2013-03-14 15:09    19  -
 ...    ..( 46 skipped).    ..  -
 465    2013-03-14 15:56    19  -
 466    2013-03-14 15:57    20  *
 ...    ..(  8 skipped).    ..  *
 475    2013-03-14 16:06    20  *
 476    2013-03-14 16:07    19  -
 477    2013-03-14 16:08    20  *
 ...    ..( 37 skipped).    ..  *
  37    2013-03-14 16:46    20  *
  38    2013-03-14 16:47    19  -
 ...    ..(  8 skipped).    ..  -
  47    2013-03-14 16:56    19  -
  48    2013-03-14 16:57    20  *
  49    2013-03-14 16:58    20  *
  50    2013-03-14 16:59    20  *
  51    2013-03-14 17:00    19  -
 ...    ..(  8 skipped).    ..  -
  60    2013-03-14 17:09    19  -
  61    2013-03-14 17:10    20  *
 ...    ..(  5 skipped).    ..  *
  67    2013-03-14 17:16    20  *
  68    2013-03-14 17:17    21  **
 ...    ..(  2 skipped).    ..  **
  71    2013-03-14 17:20    21  **
  72    2013-03-14 17:21    20  *
 ...    ..( 54 skipped).    ..  *
 127    2013-03-14 18:16    20  *
 128    2013-03-14 18:17    19  -
 129    2013-03-14 18:18    20  *
 ...    ..( 36 skipped).    ..  *
 166    2013-03-14 18:55    20  *
 167    2013-03-14 18:56    19  -
 168    2013-03-14 18:57    19  -
 169    2013-03-14 18:58    19  -
 170    2013-03-14 18:59    20  *
 ...    ..(  4 skipped).    ..  *
 175    2013-03-14 19:04    20  *

SCT Error Recovery Control:
           Read:     70 (7.0 seconds)
          Write:     70 (7.0 seconds)

SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x0001  2            0  Command failed due to ICRC error
0x0002  2            0  R_ERR response for data FIS
0x0003  2            0  R_ERR response for device-to-host data FIS
0x0004  2            0  R_ERR response for host-to-device data FIS
0x0005  2            0  R_ERR response for non-data FIS
0x0006  2            0  R_ERR response for device-to-host non-data FIS
0x0007  2            0  R_ERR response for host-to-device non-data FIS
0x0008  2            0  Device-to-host non-data FIS retries
0x0009  2            1  Transition from drive PhyRdy to drive PhyNRdy
0x000a  2            1  Device-to-host register FISes sent due to a COMRESET
0x000b  2            0  CRC errors within host-to-device FIS
0x000f  2            0  R_ERR response for host-to-device data FIS, CRC
0x0012  2            0  R_ERR response for host-to-device non-data FIS, CRC
0x8000  4        26657  Vendor specific

```

HDParm:
```
# hdparm -I /dev/sdb

/dev/sdb:

ATA device, with non-removable media
powers-up in standby; SET FEATURES subcmd spins-up.
	Model Number:       WDC WD20EFRX-68AX9N0                    
	Serial Number:      WD-WMC301187959
	Firmware Revision:  80.00A80
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
	Supported: 9 8 7 6 5 
	Likely used: 9
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors: 3907029168
	Logical  Sector size:                   512 bytes
	Physical Sector size:                  4096 bytes
	Logical Sector-0 offset:                  0 bytes
	device size with M = 1024*1024:     1907729 MBytes
	device size with M = 1000*1000:     2000398 MBytes (2000 GB)
	cache/buffer size  = unknown
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	   *	Power-Up In Standby feature set
	   *	SET_FEATURES required to spinup after power up
	    	SET_MAX security extension
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	    	Media Card Pass-Through
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	URG for READ_STREAM[_DMA]_EXT
	   *	URG for WRITE_STREAM[_DMA]_EXT
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Gen3 signaling speed (6.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	Idle-Unload when NCQ is active
	   *	NCQ priority information
	   *	unknown 76[15]
	   *	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[7]
	    	unknown 206[12] (vendor specific)
	    	unknown 206[13] (vendor specific)
	    	unknown 206[14] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
		supported: enhanced erase
	278min for SECURITY ERASE UNIT. 278min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee603308271
	NAA		: 5
	IEEE OUI	: 0014ee
	Unique ID	: 603308271
Checksum: correct

```

---

### Post by SaturnusDJ on 2013-03-15
Unless someone knows another test to perform, I'll try with another PC tonight.

After waking up this morning, the third drive (/dev/sdd) was slow. Yesterday and today the machine has been idle (deliberately) for longer periods, but nothing happened. Thus suspicion for a problem related to time increased.

---

### Post by tgalati4 on 2013-03-15
This message is troubling:  0x8000  4        26657  Vendor specific

There were 26,000 events with a "Vendor Specific" label.  That means proprietary to the hard drive manufacturer.  Who knows what these events are or if they are related to the speed problems?

The self-test tables look OK, and the tests seem to happen every ~45 hours plus some other factors.  So I don't think the self-test is responsible for your slow data rates.  A quick google search on your drive pulls up similar issues and RMA actions by users who are not happy with the write performance.

According to the Capabilities:

Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	**R/W multiple sector transfer: Max = 16	Current = 0**
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 ***udma6 **
	     **Cycle time: min=120ns recommended=120ns**
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=**120ns**  IORDY flow control=**120ns**

The drive seems to be running at its highest rated IO speed.  I'm not sure what IORDY is--perhap IO READY--some sort of handshaking, and it can be disabled.  Research that and turn it off if possible and see if there is a performance difference.

Also, your multiple sector transfer is set to 0.  Normally that would be set to 2, 4, 8, 16.  Maximum is 16 in your case.  Perhaps with small files it is better to be 0.  Something else to research and try tuning.

I just looked at my laptop drive (Western Digital Scorpio Blue) and it has the following:

0x8000  4        12610  Vendor specific

So, perhaps 26K vendor specific events is OK.

---

### Post by SaturnusDJ on 2013-03-15
Thanks for continuing to reply.

I found out myself that 0x8000 Vendor Specific is the drive uptime in seconds. :)
Because I'm still in the setup phase of this server, I run S.M.A.R.T. tests manually.

Do you have some of these google links? The only thing I found was about another WD drive with the same issue as me but worse. The guy replaced it via RMA. Three bad performing drives would be really bad luck.

I spend some time looking at IORDY, but apparently not enough, or otherwise there isn't much to find. I'll search more.

R/W multiple sector transfer is a bit strange. Most drives have a higher number here but for WD drives it's ok that this is very low or zero I read. I already tried some values, but this didn't change the slow write speeds at the time being.

At this moment the other pc is up and running. Strange thing: When the WD20EFRX sata data cables were attached, the computer wouldn't get past the BIOS screen. So I attached them afterwards. This might have been because I enabled PM2...but still a bit strange.

---

### Post by tgalati4 on 2013-03-15
If you bought your 3 drives at the same time and the serial numbers are close, then it could be a production problem.  The fact that you have run many throughput tests seems to indicate that these drives are not performing as you expect.  Where these new, retail disk drives, or were they refurbished, special-deal from Fry's Electronics?

---

### Post by SaturnusDJ on 2013-03-16
They are bought at the same time, however the serialnumbers are not from the same range.
As far as I know the disks were new. That's how they were sold. S.M.A.R.T. attributes were all zero.

I just benched the other pc after a night of sleep, and the speeds are fine!
I don't want to make a wrong conclusion, so debugging doesn't stop here. A big difference with the normal pc is that this one has 8GB RAM, the normal had 2GB.

---

### Post by SaturnusDJ on 2013-03-17
Yesterday I changed back to the server pc.

I changed a lot of things and this morning the speeds were normal. But I'm not convinced yet, it could be coincidence.

Changes:
- Pulled the energy meter from between the socket pdu and computer.
- Pulled 1GB RAM, leaving 1GB there, resulting in 50% less RAM, and less speed because of switching from dual channel to single channel. [**No fix.**]
- Change some IRQ things in BIOS. From auto to manual, and then per IRQ from auto to reserved for pci/other.
- Changed some other things in the BIOS from auto to manual, however I know the outcome is the same.
- Didn't start the big raid5 array (that's build with --assume-clean for testing), only the small one of 3*10GB. [**No fix.**]
- Hard disk's outside the tower. Resulting in a ~6-10 degrees Celsius higher temperature, because there's no fan. [**No fix.**]
- Different cables. Because the internal ones are only 20cm.
- Left 'free -m' commands running over night. [**No fix.**]
- Computer time/date was set a little bit ahead so it doesn't run behind over night because cron ntp stuff is disabled. [**No fix.**]

- Much less storage tweaking:
Now:
```

md2 stripe_cache_size: 4096
md3 stripe_cache_size: -

read ahead sdb: 256
read ahead sdc: 256
read ahead sdd: 256
read ahead md2: 4096
read ahead md3: -

sda scheduler: noop deadline [cfq]
sdb scheduler: noop deadline [cfq]
sdc scheduler: noop deadline [cfq]
sdd scheduler: noop deadline [cfq]

```
(All stock except scs.)

Normally (tuned):
```

md2 stripe_cache_size: 4096
md3 stripe_cache_size: 4096

read ahead sdb: 64
read ahead sdc: 64
read ahead sdd: 64
read ahead md2: 4096
read ahead md3: 4096

sda scheduler: [noop] deadline cfq
sdb scheduler: noop [deadline] cfq
sdc scheduler: noop [deadline] cfq
sdd scheduler: noop [deadline] cfq

```

The raid write speeds are not very high, I think because of a lack of (dual channel) memory.
Normally: 220MB/s write, 280MB/s read.
Now: 200MB/s write, 280MB/s read.

Non-raid speeds are fine.

I think I'll leave it this way one more night to be sure, before turning back the disadvantages of this config.

---

### Post by SaturnusDJ on 2013-03-21
After changing back to 3x 20cm data sata cables, the third (/dev/sdd) dropped speeds. It's a little strange because I remember the same happening with longer cables. Only not in the last few days.

Changing to long tonight.

---

### Post by SaturnusDJ on 2013-03-23
Okay speed drop (all three) with long cables. This makes me sick......

---

### Post by SaturnusDJ on 2013-03-23
In some way it has to do something with the cables.
Because:
- Earlier the long cables survived quite some nights.
- Directly after I replaced the short cable of a drive (that wouldn't speed up after a power off and on) with a long cable the speed was fine.

But tonight all drives had the longer cables and still dropped speed. So there is something else.

---

### Post by SaturnusDJ on 2013-03-30
I consider the problem solved.

After thinking everything over, without any assumptions, a combination of symptoms led to the cause.

What I forgot to mention was the room temperature. At night around 14 degrees Celsius. During the day not more than 20 degrees Celsius.

That's perfect right?? Apparently not. **The cold temperature at night causes the write speed to drop.**

After turning off all four 120mm fans, the problem is solved.

---

### Post by tgalati4 on 2013-03-30
That is the strangest thing I have ever heard.  It's possible that the drive controller firmware has a routine to check temperature and reduce speed if it is cold.  Perhaps it's a bearing wear issue.  You can use *hddtemp* or *smartctl* or the panel monitor to log temperatures.  Use another routine to log write speeds and see at what temperature the drives slow down.  That would be helpful for setting your temperature controller.

---

### Post by Jay_E on 2013-03-30
Greetings.
  I'm from Florida.  I have an irrational fear of turning off the fans.
I ran "sar -m TEMP 60 360"  - my system is running at 50 and 67C.
(And there are 3 fans running on the case.  72F inside the house.)


I tend to think of problems that I have encountered in the past - which may not have much to your specific set up.

The problem is very interesting. especially the cables.
Try a magnifying glass and look at the connectors.
I have had past bad experience of fan vibration and connectors.
Probably not in these times - but worth a look.

Some straw targets:
  PowerSupply - maybe your house power is better at night than in the day and your PS may be overloaded (marginally) so, maybe the DC power fluctuates in the daytime.
Maybe taking out the fans reduces DC load?
Got a DC voltmeter and some exposed test point? Be careful.. :-)

 Vibration - Are the fans jiggling the drives?

Here a cache, there a cache, every where....
Maybe the benchmark program runs faster with clean caches in CPU?
Would like to know more about the benchmark program.
Maybe it reaches a delay working with directories?
I'm thinking of writing a simple python program  to fill up your disk  with 100k files -
see if files in the beginning write faster than later.
If you want to try this, I can post some code...
Hmm... another favorite ghost in the closet is garbage collection.  I know nothing about it - so it is easy for me to blame... 

About the disks.
There is an old, but thorough diagnostic made by Gibson Research Company that boots off a cd and does extensive diagnostics on each sector. It saves your data, writes patterns, reads patterns and restores your data.  It was called spin-rite.
?? Does any else think this might be worthwhile??

Best Wishes,
Jay

---

### Post by dcstar on 2013-03-31
> **SaturnusDJ said:**
> I consider the problem solved.

After thinking everything over, without any assumptions, a combination of symptoms led to the cause.

What I forgot to mention was the room temperature. At night around 14 degrees Celsius. During the day not more than 20 degrees Celsius.

That's perfect right?? Apparently not. **The cold temperature at night causes the write speed to drop.**

After turning of all four 120mm fans, the problem is solved. With summer coming, a fan controller with temperature sensors is not a bad idea.

It is possible that you have a hardware issue like a bad solder joint or component on the MB around the disk controller, when the MB cools down overnight something no longer makes good contact to run at normal data rates and the hardware throttles down to do the best it can.

You can usually identify this sort of thing with a can of Spray Freeze that electronics technicians used to use back in the day, you essentially freeze various bits of a running system to see if you can trigger the problem and that lets you narrow down the physical location of the issue.

As well, any contamination on the MB can cause all sorts of issues - I once had a server go unreliable because the customer had it sitting on carpet in an office that was steam-cleaned twice a year and all the steam was sucked into it (along with the dirt in the air) creating a slimy coating all over the MB and a server that started rebooting itself enough to be replaced. It was only when the MB was properly cleaned that it behaved correctly again (and the customer learnt an expensive lesson about putting servers in appropriate environments). Dust in IT equipment is one thing, dust + moisture/humidity is just asking for trouble.

If you do have these sort of hardware problems then eventually it will cause bigger issues, like loss of data.

---

### Post by SaturnusDJ on 2013-04-03
@tgalati4
I must admit that I'm a bit tired of the problem. Therefor no more testing, and finally enjoying my new server. The problem triggering temperature is around 18 degrees Celsius. Above 22 is safe.


@Jay_E
I guarantee it's a temperature related problem.
Google tests show it's better for a HDD to have a temperature in the 30 degrees Celsius than much lower than that.


@dcstar
I'm pretty sure the problem is HDD related. The HDD in the bottom of the case suffered the most write speed drops, it's 2 degrees colder than the HDD above it, which is 1-2 degrees colder than the top HDD.

---

### Post by WinRiddance on 2013-04-12
I really don't understand why this thread is marked as solved? Did anyone here aside from myself notice that the temp related answers were neither actual permanent solutions, nor were they backed by anything specific to hard drives from hard disk manufacturers, hard disk forums, and so on. I'm mentionming this because I have almost identical 2 TB drives by WD and my transfer speeds from disk to disk never got above 12 mbps which, for Sata2 is pretty darn slow. I get better speeds with my USB 2 on this system. We're in Florida, the wife loves/needs the heat, so our house temeprature is never below 78 degrees F. Furthermore, I've got the setup with the 2 TB drives sitting in a partial enclosure which keeps things just a tad bit warmer yet. It simply makes no sense to me at all that the difference of 2 - 4 degrees F. would make such a huge difference or that it can be accepted as a viable explanation. Oh, and last but not least, after the first 90 minutes of file transferring (moving, not copying) the transfer speed has slowed down from the above mentioned 12 mbps to only 5.6 mbps where it seems to have stabilized. Aside from the browser and Deluge I have nothing else running. CPU is an AMD Phenom Quad Core.

Same computer, same system, but different drives in my eSata Drobo and I'm gettting consistent transfer speeds of 80 - 110 mbps. Different port though since the eSata isn't the same as the Sata2 hard disk connectors. The only thing that makes sense to me is that the slow transfer speeds have something specific to do with the mainboard connectors ... which then gets shot down when the same setup under Windoze offers much greater speeds ... or that it has something specific to do with Nautilus as posts relative to this issue have been around for years. Oldest transfer speed problem that I could find for Linux was from 2007.
I don't use NTFS though. I experienced problems like this with Ext3 as well as my current Ext4 drives.

I would be very interested to know if anyone has tried large transfers with either PacmanFM or Thunar? If speeds in those file managers are substantially different then the problem would appear to be more specifically related to Nautilus ... especially considering that some of the answers here implied considerably faster speeds when using the terminal only ... ??? Why would Nautilus make the drives behave so much more sluggish? If I had anticipated this slowness I would have tried Thunar myself. Now I'm stuck waiting for the next 15 hours. :(

Whoooops, just noticed that my transfer speed is down to only 4.4 mbps now. Both 2 TB disks are less than 30 days old too, bought at different times from 2 different vendors. They're both 2 TB _**WD**_ disks though ... :confused:
PEACE.

[COLOR=#800000]**EDIT: **[/COLOR]Just removed the side panel. I can place my hand on top of both drives as they're working and neither one of them feels hot or cool. Just pleasantly warm. I have noticed though that the transfer speeds seems to fluctuate, possibly based on the type of files that are being transferred? I'll keep an eye on those speeds and report back if I find out anything more specific.

.

---

### Post by SaturnusDJ on 2013-04-13
I know how annoying this is. I tried many many things. Because you talk about Nautilus, I first suggest to try dd.

---

### Post by WinRiddance on 2013-04-13
**Alright, some more information and possibly even a real solution for many of us ...**

Still thinking that Nautilus is part of the problem because within a 2 - 3 hour period the mbps transfer speed went back up to 7.8 for quite awhile, only to be followed by dropping way down to only 3.3 mbps and staying there until I had enough and closed everything down. Remember what I said about file handling and file sizes earlier. Since the date that I was transferring had every type of file ranging in size from 10 KB to 1.5 GB it does make sense in a way that a GUI based file manager (Nautilus) handles different file sizes at different speeds. After all, there's only so much that an app can do so fast, right?

[B]I'm a bit surprised that nobody else came up with the following ...
[/B]
Notoriously rsync, even in GUI mode, is very fast. Well, since most *buntu flavored GUI backup apps are based on rsync I went ahead and installed LuckyBackup from the software repository. LuckyBackup is super easy to use after you figure out the initial buttons. It has a superuser mode, the ability to preserve permssions, synchronization to keep only changed/newer files, and so on. When I stopped the initial file transfer from one disk to the other my speed was down to 3.3 mbps. The fastest that I had was 12 mbps, and that's it. If you look at the screenshots below you can see that my average transfer speed with LuckyBackup was almost 25 mbps ... [COLOR=#800000]**twice the speed of what I started out with!**[/COLOR] Didn't have to wait 17 hours for everything to complete either ... :P

Granted, I now had a duplicate of the files that I initially wanted to move, but it only takes seconds to reformat a disk, thereby wiping everything out. No sweat off my back. And if you want to wipe the drive totally clean you'll have to use DD anyway in order to totally wipe out every bit of data that you had on your old disk. Anyway, LuckyBackup did the trick for me. **Bottom line,** if you're making large data tranfers ... take a few seconds to start this with a GUI based backup app. and not your file manager.

I also found this link to be pretty useful, concernig IDE/Sata and other Bios settings:
[Ultimate BIOS Guide: Every Setting Decrypted and Explained! - Page 1 | Maximum PC]("http://www.maximumpc.com/article/features/ultimate_bios_guide_every_bios_setting_revealed?page=0,0")

Last but not least ... A word of warning to all of you who are still using Windows. If you plan on using the enhanced AHCI setting for your installed SATA drives, be sure to make that adjustment in your mainboard Bios BEFORE you install Windows. Read the information at the above link for more details on that.

.

---

### Post by WinRiddance on 2013-04-13
> **SaturnusDJ said:**
> I know how annoying this is. I tried many many things. Because you talk about Nautilus, I first suggest to try dd.

The "problem" with DD is that most Windows users, especially ones who are intimidated by the terminal, would prefer a solution with an easy, pretty, gui based app. Granted, for wiping a drive clean there's nothing better but for large file transfers there are alternatives that don't involve the use of a file manager that has dozens of different functions, as opposed to strictly the functions of moving/copying files ...
Just trying to be mindful of those Windows users who are just now diving into Linux. :)

.

---

### Post by SaturnusDJ on 2013-04-13
Ofcourse. But using dd for benching would be more accurate and stable.

If you run these commands, you'll at least know if your drive(s) is/are alright.
```

dd if=/dev/zero of=/YOUR_HDD_MOUNTPOINT/testfile bs=1M count=2000
echo 3 > /proc/sys/vm/drop_caches
sync
dd if=/YOUR_HDD_MOUNTPOINT/testfile of=/dev/null bs=1M
echo 3 > /proc/sys/vm/drop_caches
sync

```
This generates a 2GB file and reads it afterwards.
Drop caches and sync make sure everything is written to disk and not only cached. (Mostly usefull between the writing and reading of the file.)

---

### Post by WinRiddance on 2013-04-18
Last but not least ... One final thing to consider ...

As indicated earlier, my file transfer speed increased by more than double when I used the LuckyBackup backup program for the transfers as opposed to just the Nautilus (in my case Caja) file manager. I tested this repeatedly during the past few days and the result was always the same on my SATA drives ... the backup application always achieved faster, much more consistent transfers. BUT ... [B]then I took this one step further ...
[/B]
I noticed that my SATA drive cables were older, red, basic generic SATA cables while my drives were actually SATA2's. Well, I'd read in another forum that the correct cables can make a big difference too. So I purchased SATA3 cables which are downward compatible with SATA and SATA2, only to find that now the same drives were transferring files, _even with the file manager,_ substantially faster than before. My average transfer speed for close to 10 GB of file transfers via the file manager was now almost 70 mbps.
So we have several possible culprits for slow transfer speed, all of which can be addressed:

**1.** Consider AHCI settings if you're a Windoze user, before installing the Windoze OS.
**2.** Consider using an rsync based backup application for large volume file transfers.
**3.** Make sure that you're using a good quality, high speed SATA3 cable on newer SATA drives.

.

---


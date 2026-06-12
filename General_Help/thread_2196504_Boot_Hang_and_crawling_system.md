---
title: "Boot Hang and crawling system"
date: 2013-12-29
forum: General Help
---

### Post by JWLER on 2013-12-29
_**Problem**_: Boot hangs for 5 minutes or so, then I get splashscreen. I log in, wait another 10 minutes or so then I am at desktop. Any action I attempt takes at least 30 seconds to 3 minutes to complete. Prior to this system had been great.

_**System**_: 12.04 dual boot windows vista. Dual core desktop 2 HDD partitioned as follows: 
 Hard drive 1 - Windows 
/dev/sda1 * 63 204796619 102398278+ 7 HPFS/NTFS/exFAT
/dev/sda2 204796620 488375999 141789690 f W95 Ext'd (LBA)
/dev/sda5 204796683 409593239 102398278+ 7 HPFS/NTFS/exFAT
/dev/sda6 409593303 488375999 39391348+ 7 HPFS/NTFS/exFAT

Hard drive 2 Linux and data storage
/dev/sdb1 * 2048 2048002047 1024000000 7 HPFS/NTFS/exFAT
/dev/sdb2 2048002048 3064408307 508203130 7 HPFS/NTFS/exFAT
/dev/sdb3 3064410110 3907028991 421309441 5 Extended
/dev/sdb5 3064410112 3894448127 415019008 83 Linux
/dev/sdb6 3894450176 3907028991 6289408 82 Linux swap / Solaris

_**Actions attempted:**_
fsck on /dev/sdb5 from liveCD gave following results
```

ubuntu@ubuntu:/$ sudo fsck -f -y /dev/sdb5
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb5: 558427/25944064 files (0.3% non-contiguous), 22886097/103754752 blocks

```

Queried SMART drive info:
```
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdb5
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-29-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WMAZA2034403
LU WWN Device Id: 5 0014ee 6ab4436ae
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Mon Dec 30 03:55:43 2013 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (38460) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 255) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   092   092   051    Pre-fail  Always       -       45901
  3 Spin_Up_Time            0x0027   253   165   021    Pre-fail  Always       -       1258
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2953
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       12515
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1487
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       336
193 Load_Cycle_Count        0x0032   064   064   000    Old_age   Always       -       409304
194 Temperature_Celsius     0x0022   121   109   000    Old_age   Always       -       29
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   198   198   000    Old_age   Always       -       689
198 Offline_Uncorrectable   0x0030   199   199   000    Old_age   Offline      -       463
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   198   197   000    Old_age   Offline      -       616

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       702         -
# 2  Short captive       Interrupted (host reset)      80%         0         -

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


looking at dmesg with the livecd boot I notice some long pauses, and then some of the same "ta3.00: failed command: READ FPDMA QUEUED" errors

```

.728813] sd 8:0:0:2: Attached scsi generic sg6 type 0
[    7.728971] sd 7:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    7.728999] sd 8:0:0:3: Attached scsi generic sg7 type 0
[    7.729487] sd 7:0:0:0: [sdd] Write Protect is off
[    7.729490] sd 7:0:0:0: [sdd] Mode Sense: 33 00 00 08
[    7.730090] sd 7:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    7.738315]  sdd: sdd1
[    7.740734] sd 7:0:0:0: [sdd] Attached SCSI disk
[    7.744616] sd 8:0:0:1: [sdf] Attached SCSI removable disk
[    7.749606] sd 8:0:0:0: [sde] Attached SCSI removable disk
[    7.753607] sd 8:0:0:2: [sdg] Attached SCSI removable disk
[    7.757611] sd 8:0:0:3: [sdh] Attached SCSI removable disk
[   69.714570] EXT4-fs (sdb5): INFO: recovery required on readonly filesystem
[   69.714573] EXT4-fs (sdb5): write access will be enabled during recovery
[   72.987276] EXT4-fs (sdb5): recovery complete
[   74.781885] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[   82.610229] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   91.912830] kjournald starting.  Commit interval 5 seconds
[   91.912891] EXT3-fs (loop1): using internal journal
[   91.912894] EXT3-fs (loop1): recovery complete
[   91.912906] EXT3-fs (loop1): mounted filesystem with ordered data mode
[  114.076489] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  114.141070] udevd[3085]: starting version 175
[  114.462323] device-mapper: multipath: version 1.3.0 loaded
[  114.480123] Bluetooth: Core ver 2.16
[  114.480160] NET: Registered protocol family 31
[  114.480162] Bluetooth: HCI device and connection manager initialized
[  114.480164] Bluetooth: HCI socket layer initialized
[  114.480166] Bluetooth: L2CAP socket layer initialized
[  114.480172] Bluetooth: SCO socket layer initialized

and then 

  117.892180] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  118.728362] tda829x 5-0042: type set to tda8295+18271
[  119.848469] cx23885[0]: registered device video0 [v4l2]
[  119.848530] cx23885[0]: registered device vbi0
[  119.848533] cx23885_audio_register(): Missing SRAM channel configuration for analog TV Audio
[  120.934330] cx23885[0]: registered device video1 [mpeg]
[  120.934333] cx23885_dvb_register() allocating 1 frontend(s)
[  120.934337] cx23885[0]: cx23885 based dvb card
[  121.011177] MT2131: successfully identified at address 0x61
[  121.012803] DVB: registering new adapter (cx23885[0])
[  121.012807] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[  121.013209] cx23885_dev_checkrevision() Hardware revision = 0xb1
[  121.013215] cx23885[0]/0: found at 0000:03:00.0, rev: 15, irq: 17, latency: 0, mmio: 0xf9c00000
[  121.013224] cx23885 0000:03:00.0: setting latency timer to 64
[  128.032018] eth0: no IPv6 routers present
[13166.264444] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[14777.469837] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[14777.469843] ata3.00: irq_stat 0x40000008
[14777.469848] ata3.00: failed command: READ FPDMA QUEUED
[14777.469856] ata3.00: cmd 60/00:00:c0:34:a7/01:00:e2:00:00/40 tag 0 ncq 131072 in
[14777.469858]          res 41/40:00:40:35:a7/00:00:e2:00:00/40 Emask 0x409 (media error) <F>
[14777.469862] ata3.00: status: { DRDY ERR }
[14777.469865] ata3.00: error: { UNC }
[14777.479333] ata3.00: configured for UDMA/133
[14777.479344] ata3: EH complete
[14780.613657] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[14780.613663] ata3.00: irq_stat 0x40000008
[14780.613668] ata3.00: failed command: READ FPDMA QUEUED
[14780.613676] ata3.00: cmd 60/00:08:c0:34:a7/01:00:e2:00:00/40 tag 1 ncq 131072 in
[14780.613678]          res 41/40:00:40:35:a7/00:00:e2:00:00/40 Emask 0x409 (media error) <F>
[14780.613682] ata3.00: status: { DRDY ERR }
[14780.613685] ata3.00: error: { UNC }
[14780.623299] ata3.00: configured for UDMA/133
[14780.623310] ata3: EH complete
[14783.721492] ata3.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[14783.721497] ata3.00: irq_stat 0x40000008
[14783.721502] ata3.00: failed command: READ FPDMA QUEUED
[14783.721511] ata3.00: cmd 60/00:00:c0:34:a7/01:00:e2:00:00/40 tag 0 ncq 131072 in
[14783.721512]          res 41/40:00:40:35:a7/00:00:e2:00:00/40 Emask 0x409 (media

```


I'm in way over my head at this point and would be super appreciative of any guidance on how to proceed. Im working currently on trying to back up the linux partition, (which will also be a first for me)

Thanks in advance
Jess

---


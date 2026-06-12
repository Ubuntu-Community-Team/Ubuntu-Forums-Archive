---
title: "SSD Crucial M4 I/O error"
date: 2016-08-24
forum: General Help
---

### Post by zook2 on 2016-08-24
[COLOR=#141414][FONT=&amp]Hello[/FONT][/COLOR][COLOR=#141414][FONT=&amp], i tried to install W10 on my laptop using my SSD but it doesn't show on devices list. To check it i connected to my laptop (w8) and look that isn't initialized, when i try to initialize it shows ""the request could not be completed because of an i/o device error"[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]The drive is fully recognized on IDE mode but not on AHCI.

[/FONT][/COLOR][COLOR=#141414][FONT=&amp]Looking for a fix i tried to secure erase but is the same problem on Linux.
[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]Also attached a log file from Parted Magic - Secure Erase tool
[/FONT][/COLOR]
> ```

Parted Magic 2013_11_11 (hdparm v9.43) Secure Erase Log


Started: Tue Aug 23 17:48:01 UTC 2016
Finished: Tue Aug 23 17:48:07 UTC 2016


M4-CT256M4SSD2 (/dev/sda) SERIAL NUMBER: 00000000121709094A41 SIZE:238.5G RESULTS:Erase Failed
Secure Erase Method: Normal Secure Erase


==================================================
M4-CT256M4SSD2 (/dev/sda)
==================================================


hdparm v9.43


/dev/sda:


ATA device, with non-removable media
Model Number: M4-CT256M4SSD2 
Serial Number: 00000000121709094A41
Firmware Revision: 070H 
Transport: Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0
Standards:
Used: unknown (minor revision code 0x0028)
Supported: 9 8 7 6 5
Likely used: 9
Configuration:
Logical max current
cylinders 16383 16383
heads 16 16
sectors/track 63 63
--
CHS current addressable sectors: 16514064
LBA user addressable sectors: 268435455
LBA48 user addressable sectors: 500118192
Logical Sector size: 512 bytes
Physical Sector size: 512 bytes
Logical Sector-0 offset: 0 bytes
device size with M = 1024*1024: 244198 MBytes
device size with M = 1000*1000: 256060 MBytes (256 GB)
cache/buffer size = unknown
Form Factor: 2.5 inch
Nominal Media Rotation Rate: Solid State Device
Capabilities:
LBA, IORDY(can be disabled)
Queue depth: 32
Standby timer values: spec'd by Standard, with device specific minimum
R/W multiple sector transfer: Max = 16 Current = 16
Advanced power management level: 254
DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 (?)
Cycle time: min=120ns recommended=120ns
PIO: pio0 pio1 pio2 pio3 pio4
Cycle time: no flow control=120ns IORDY flow control=120ns
Commands/features:
Enabled Supported:
* SMART feature set
Security Mode feature set
* Power Management feature set
* Write cache
* Look-ahead
* Host Protected Area feature set
* WRITE_BUFFER command
* READ_BUFFER command
* NOP cmd
* DOWNLOAD_MICROCODE
* Advanced Power Management feature set
SET_MAX security extension
* 48-bit Address feature set
* Device Configuration Overlay feature set
* Mandatory FLUSH_CACHE
* FLUSH_CACHE_EXT
* SMART error logging
* SMART self-test
* General Purpose Logging feature set
* WRITE_{DMA|MULTIPLE}_FUA_EXT
* 64-bit World wide name
* IDLE_IMMEDIATE with UNLOAD
Write-Read-Verify feature set
* WRITE_UNCORRECTABLE_EXT command
* {READ,WRITE}_DMA_EXT_GPL commands
* Segmented DOWNLOAD_MICROCODE
* Gen1 signaling speed (1.5Gb/s)
* Gen2 signaling speed (3.0Gb/s)
* Gen3 signaling speed (6.0Gb/s)
* Native Command Queueing (NCQ)
* Phy event counters
* NCQ priority information
DMA Setup Auto-Activate optimization
Device-initiated interface power management
* Software settings preservation
* SMART Command Transport (SCT) feature set
* SCT Write Same (AC2)
* SCT Error Recovery Control (AC3)
* SCT Features Control (AC4)
* SCT Data Tables (AC5)
* Data Set Management TRIM supported (limit 8 blocks)
* Deterministic read data after TRIM
Security:
Master password revision code = 65534
supported
not enabled
not locked
not frozen
not expired: security count
supported: enhanced erase
2min for SECURITY ERASE UNIT. 2min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 500a075109094a41
NAA : 5
IEEE OUI : 00a075
Unique ID : 109094a41
Checksum: correct


smartctl 5.43 2012-06-30 r3573 [i686-linux-3.10.18-pmagic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net


=== START OF INFORMATION SECTION ===
Model Family: Crucial/Micron RealSSD C300/C400/m4
Device Model: M4-CT256M4SSD2
Serial Number: 00000000121709094A41
LU WWN Device Id: 5 00a075 109094a41
Firmware Version: 070H
User Capacity: 256,060,514,304 bytes [256 GB]
Sector Size: 512 bytes logical/physical
Device is: In smartctl database [for details use: -P show]
ATA Version is: 8
ATA Standard is: ATA-8-ACS revision 6
Local Time is: Tue Aug 23 17:48:07 2016 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status: (0x80) Offline data collection activity
was never started.
Auto Offline Data Collection: Enabled.
Self-test execution status: ( 0) The previous self-test routine completed
without error or no self-test has ever
been run.
Total time to complete Offline
data collection: ( 1190) seconds.
Offline data collection
capabilities: (0x7b) SMART execute Offline immediate.
Auto Offline data collection on/off support.
Suspend Offline collection upon new
command.
Offline surface scan supported.
Self-test supported.
Conveyance Self-test supported.
Selective Self-test supported.
SMART capabilities: (0x0003) Saves SMART data before entering
power-saving mode.
Supports SMART auto save timer.
Error logging capability: (0x01) Error logging supported.
General Purpose Logging supported.
Short self-test routine
recommended polling time: ( 2) minutes.
Extended self-test routine
recommended polling time: ( 19) minutes.
Conveyance self-test routine
recommended polling time: ( 3) minutes.
SCT capabilities: (0x003d) SCT Status supported.
SCT Error Recovery Control supported.
SCT Feature Control supported.
SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME FLAG VALUE WORST THRESH TYPE UPDATED WHEN_FAILED RAW_VALUE
1 Raw_Read_Error_Rate 0x002f 100 100 050 Pre-fail Always - 51
5 Reallocated_Sector_Ct 0x0033 100 100 010 Pre-fail Always - 0
9 Power_On_Hours 0x0032 100 100 001 Old_age Always - 19839
12 Power_Cycle_Count 0x0032 100 100 001 Old_age Always - 2045
170 Grown_Failing_Block_Ct 0x0033 100 100 010 Pre-fail Always - 0
171 Program_Fail_Count 0x0032 100 100 001 Old_age Always - 0
172 Erase_Fail_Count 0x0032 100 100 001 Old_age Always - 66
173 Wear_Levelling_Count 0x0033 099 099 010 Pre-fail Always - 31
174 Unexpect_Power_Loss_Ct 0x0032 100 100 001 Old_age Always - 537
181 Non4k_Aligned_Access 0x0022 100 100 001 Old_age Always - 4123 1405 2717
183 SATA_Iface_Downshift 0x0032 100 100 001 Old_age Always - 0
184 End-to-End_Error 0x0033 100 100 050 Pre-fail Always - 0
187 Reported_Uncorrect 0x0032 100 100 001 Old_age Always - 0
188 Command_Timeout 0x0032 100 100 001 Old_age Always - 0
189 Factory_Bad_Block_Ct 0x000e 100 100 001 Old_age Always - 82
194 Temperature_Celsius 0x0022 100 100 000 Old_age Always - 0
195 Hardware_ECC_Recovered 0x003a 100 100 001 Old_age Always - 100707
196 Reallocated_Event_Count 0x0032 100 100 001 Old_age Always - 0
197 Current_Pending_Sector 0x0032 100 100 001 Old_age Always - 0
198 Offline_Uncorrectable 0x0030 100 100 001 Old_age Offline - 0
199 UDMA_CRC_Error_Count 0x0032 100 100 001 Old_age Always - 0
202 Perc_Rated_Life_Used 0x0018 099 099 001 Old_age Offline - 1
206 Write_Error_Rate 0x000e 100 100 001 Old_age Always - 0


Read SMART Log Directory failed.


Error SMART Error Log Read failed: scsi error aborted command
Smartctl: SMART Error Log Read Failed
Error SMART Error Self-Test Log Read failed: scsi error aborted command
Smartctl: SMART Self Test Log Read Failed
Error SMART Read Selective Self-Test Log failed: scsi error aborted command
Smartctl: SMART Selective Self Test Log Read Failed

```[COLOR=#141414][FONT=&amp]
[/FONT][/COLOR]

---


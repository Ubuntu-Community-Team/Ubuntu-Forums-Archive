---
title: "Error writing partition table"
date: 2022-03-06
forum: General Help
---

### Post by rsteinmetz70112 on 2022-03-06
I just installed 2 new hards drive in a computer /dev/sdd /dev/sde. I started to partition them. Using parted I was able to write a new GPT partition table to /dev/sde. When I tried to write a partition table to /dev/sdd i got an I/O error. I also tried using gdisk and got this:

```
# gdisk
GPT fdisk (gdisk) version 1.0.5

Type device filename, or press <Enter> to exit: /dev/sdd
Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries in memory.

Command (? for help): x

Expert command (? for help): z
About to wipe out GPT on /dev/sdd. Proceed? (Y/N): Y
Warning! GPT backup partition table not overwritten! Error is 5
GPT data structures destroyed! You may now partition the disk using fdisk or
other utilities.

Expert command (? for help): o

Disk size is 3907029168 sectors (1.8 TiB)
MBR disk identifier: 0x00000000
MBR partitions:

Number  Boot  Start Sector   End Sector   Status      Code
   1                     1   3907029167   primary     0xEE

Expert command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sdd.
Unable to save backup partition table! Perhaps the 'e' option on the experts'
menu will resolve this problem.
Warning! An error was reported when writing the partition table! This error
MIGHT be harmless, or the disk might be damaged! Checking it is advisable.

Expert command (? for help): quit
```

It looks like there may be an MBR partition table but I think gdisk should have overwritten it.

```
using fdisk I get this:

# fdisk /dev/sdd

Welcome to fdisk (util-linux 2.34).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

fdisk: cannot open /dev/sdd: Input/output error
```

I ran smartctl and got this output:

```
# smartctl -a /dev/sdd
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-88-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     HUA723020ALA640
Serial Number:    YFJYNW1A
Firmware Version: MK7OAA30
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Sun Mar  6 11:42:58 2022 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                (19784) seconds.
Offline data collection
capabilities:                    (0x5b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        ( 330) minutes.
SCT capabilities:              (0x003f) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   134   134   054    Pre-fail  Offline      -       87
  3 Spin_Up_Time            0x0007   100   100   024    Pre-fail  Always       -       394
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       6
  5 Reallocated_Sector_Ct   0x0033   074   074   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   123   123   020    Pre-fail  Offline      -       31
  9 Power_On_Hours          0x0012   100   100   000    Old_age   Always       -       17
 10 Spin_Retry_Count        0x0013   075   075   060    Pre-fail  Always       -       5
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       6
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       6
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       6
194 Temperature_Celsius     0x0002   162   162   000    Old_age   Always       -       37 (Min/Max 22/39)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   043   043   000    Old_age   Always       -       1220
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       2
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 69 (device log contains only the most recent five errors)
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

Error 69 occurred at disk power-on lifetime: 17 hours (0 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 00 88 e0 08  Error: UNC at LBA = 0x08e08800 = 148932608

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 68 00 88 e0 40 08      17:17:25.884  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 08      17:17:25.882  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 08      17:17:25.880  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      17:17:25.877  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 08      17:17:25.875  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]

Error 68 occurred at disk power-on lifetime: 17 hours (0 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 00 88 e0 08  Error: UNC at LBA = 0x08e08800 = 148932608

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 98 00 88 e0 40 08      17:17:22.517  READ FPDMA QUEUED
  ec 00 01 00 00 00 00 08      17:17:22.514  IDENTIFY DEVICE
  60 08 90 18 00 00 40 08      17:17:22.508  READ FPDMA QUEUED
  60 08 88 08 00 00 40 08      17:17:22.508  READ FPDMA QUEUED
  60 08 80 00 00 00 40 08      17:17:22.490  READ FPDMA QUEUED

Error 67 occurred at disk power-on lifetime: 17 hours (0 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 00 88 e0 08  Error: UNC at LBA = 0x08e08800 = 148932608

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 50 00 88 e0 40 08      17:17:19.152  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 08      17:17:19.150  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 08      17:17:19.148  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      17:17:19.147  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 08      17:17:19.145  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]

Error 66 occurred at disk power-on lifetime: 17 hours (0 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 00 88 e0 08  Error: UNC at LBA = 0x08e08800 = 148932608

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 18 00 88 e0 40 08      17:17:15.809  READ FPDMA QUEUED
  60 08 10 08 00 00 40 08      17:17:15.808  READ FPDMA QUEUED
  60 08 08 00 00 00 40 08      17:17:15.792  READ FPDMA QUEUED
  b0 da 00 00 4f c2 00 08      17:14:37.195  SMART RETURN STATUS
  b0 d0 01 00 4f c2 00 08      17:14:37.030  SMART READ DATA

Error 65 occurred at disk power-on lifetime: 17 hours (0 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 00 88 e0 08  Error: UNC at LBA = 0x08e08800 = 148932608

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 28 00 88 e0 40 08      17:10:01.600  READ FPDMA QUEUED
  27 00 00 00 00 00 e0 08      17:10:01.598  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 08      17:10:01.596  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      17:10:01.593  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 08      17:10:01.591  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]

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

Things I noticed
[LIST]
[*]The connection speed is 3.0 GB/s it should be 6
[*]The errors reported are all UNC at LBA = 0x08e08800 = 148932608 which means an uncorrectable error at that Logical Block Address.
[/LIST]

The other identical drive on the same controller shows no errors.

I swaped the cable and ports on teh controller and no change.

---

### Post by rsteinmetz70112 on 2022-03-06
Looks like the new drive may be defective. I've ordered a replacement, it will be here in a few days so I can tell. Since it's new It should be covered under warranty.

---

### Post by TheFu on 2022-03-06
```
197 Current_Pending_Sector  0x0022   043   043   000    Old_age   Always       -       [COLOR="#FF0000"]1220[/COLOR]
```

Scary!

---

### Post by rsteinmetz70112 on 2022-03-07
> **TheFu said:**
> ```
197 Current_Pending_Sector  0x0022   043   043   000    Old_age   Always       -       [COLOR="#FF0000"]1220[/COLOR]
```

Scary!

Doesn't matter much since I can't write a partition table to it anyway. 8-)

---

### Post by TheFu on 2022-03-07
> **rsteinmetz70112 said:**
> Doesn't matter much since I can't write a partition table to it anyway. 8-)

With that number of pending sectors to be relocated, even if you could lay down any data, I'd still put the drive in the "to be drilled" pile for destruction.  I like to put 5 3/8in holes through the platters after taking the magnets out. I'm not worried about govt secrets. If I where, I'd want the platters to be turned into powder, not just chips.

The magnets are fun for all sorts of things. ;)

---

### Post by rsteinmetz70112 on 2022-03-08
> **TheFu said:**
> With that number of pending sectors to be relocated, even if you could lay down any data, I'd still put the drive in the "to be drilled" pile for destruction.  I like to put 5 3/8in holes through the platters after taking the magnets out. I'm not worried about govt secrets. If I where, I'd want the platters to be turned into powder, not just chips.

The magnets are fun for all sorts of things. ;)

There is no data on the drive. I got it as a virgin and wasn't able to even write a new partition table to it. I hope to get a warranty replacement.

---

### Post by TheFu on 2022-03-08
> **rsteinmetz70112 said:**
> There is no data on the drive. I got it as a virgin and wasn't able to even write a new partition table to it. I hope to get a warranty replacement.

Whoever sold that drive is to be avoided. They aren't honest.

---

### Post by rsteinmetz70112 on 2022-03-08
Why do you say that?

---

### Post by TheFu on 2022-03-08
Run a long test and I bet you'll discover it wasn't a new device.  Manufacturers can zero all the smart data, but not the prior test runs. Those will be listed at the bottom of the smartctl report.  Drives SMART data may look like new otherwise.

How often do you see more than 0 pending sectors for relocation in any storage device?  This is a clear sign of a failing disk.

A system (or drive) shipped with **any** pending or reallocated sectors, yet claimed as new, shows they are either dishonest or have extremely bad QA processes. I consider it a ZERO excuse issue.  

If you buy a drive 'used', that's completely different.

---

### Post by MAFoElffen on 2022-03-09
But that is also the difference between Consumer drives and Enterprise Drives... The QA process is more intensive for the later, thus the longer warranty and better support. For commercial production, I recommend Enterprise drives for ease of mind, that it will work out-of-the-box and last. If I am consulting and recommend something, I want it to be a success.

But most normal consumers cannot afford the extra price of that. That is the reality. I can understand that. It doesn't mean another drive is not as good, nor the technology of better... But rather that it was tested more, and the support behind it will be better.

Is this a production system? Or for your own private use?

---

### Post by rsteinmetz70112 on 2022-03-09
This is for a production system for my company. I purchased 4 identical drives the other three are showing no issues. They show 0 Current_Pending_Sector and 0 Reallocated_Sector_Ct. 2 have been installed in another computer the other one will go into this one when the replacement arrives. 

I suspect that this one simply died, possibly it got damaged somehow, possible a bad power connection. Almost as soon as I powered it up it started having issues including going offline. The replacement is on it's way.

---

### Post by TheFu on 2022-03-09
I like the WD-Gold series for commercial use. It has a much longer MTBF rating and is designed to handle more use, more vibration, and has a 5 yr warranty for data center use.

I try to mix and match drives for my data. I'd like to avoid a bad model from multiple disks causing data loss.  I use relatively cheap storage for backups, but the primary storage gets higher quality storage.

Hopefully, everyone has seen the Backblaze reports on SSD quality. Seems SSDs aren't actually any better than spinning disks based on their data.  They have a fairly limited set of SSD models - no Samsung at all.  The failure rates are about the same as for spinning disks.

---

### Post by rsteinmetz70112 on 2022-03-10
Maybe I'm too cynical. I suspect the premium for Enterprise drives is mostly an insurance policy and that few people actually return failed drives. I know I don't. The hassle is not worth the effort given how cheap drives have become. In any event I mostly replace them for other reasons before they fail 

I'm kind of off WD drives since I had a bad run of them a few years ago when it seemed like every couple of weeks I had a failure.

---

### Post by TheFu on 2022-03-10
Those are extremely valid reasons.
WD-Gold isn't WD designed. They are Hitachi designed drives, but then WD bought Hitachi's storage arm. It is possible to get old WD-designed "gold" HDDs, but those are mostly gone at this point. WD did keep the model numbers separate, thankfully, even if they are confusing the marketing with the "gold" name.

Data center drives are designed very differently from consumer drives. It isn't all marketing. Delving into the engineering specs, it is clear. Because I trained as an engineer, I appreciate the 1000x factor of higher MTBF in the design. I didn't always feel that way, until I saw multiple consumer disks fail when used in the same slot for the same purpose, multiple times, just after the drive warranty period ended.  

Often, we get lucky with consumer drives and they outlast the warranty, sometimes by many years. The places where I was tired of dealing with the hassles of replacing a HDD every 3 yrs, after a failure, are where I use DC-designed HDDs. Being able to avoid that hassle for 5+ yrs is worth the extra 30-50% cost to me.

We each have different pain points for storage.  When multiple 3-yr warranty HDDs fail before 4 yrs of use, I'm a little frustrated.  It feels like the manufacturer almost timed the design failure point extremely well to force replacement.  5yr warranty drives seem to last 10+ yrs, which has been my experience with all of them.  I haven't had any 5 yr warrant HDDs fail. Not once. Perhaps I've been lucky.  I have 2 WD-black (model, not color) HDDs in 2 different systems working today.  One is about 13 yrs old. The other is probably 6 yrs old and has been in a 2011 laptop that used to dual boot, into Win7 for specific uses, but hasn't been booted in perhaps 6 weeks. Both are 1TB size, 7200 rpm.
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   199   199   140    Pre-fail  Always       -       1
  9 Power_On_Hours          0x0032   001   001   000    Old_age   Always       -       103625
```
The single reallocated sector happened about 5 yrs ago.
Everything else in the SMART data is pristine on that box. It has 7 HDDs and they are all 7+ yrs old. 4 are in RAID1 configs (not RAID10).

---

### Post by #&amp;thj^% on 2022-03-10
> **TheFu said:**
> Those are extremely valid reasons.
WD-Gold isn't WD designed. They are Hitachi designed drives, but then WD bought Hitachi's storage arm. It is possible to get old WD-designed "gold" HDDs, but those are mostly gone at this point. WD did keep the model numbers separate, thankfully, even if they are confusing the marketing with the "gold" name.

Data center drives are designed very differently from consumer drives. It isn't all marketing. Delving into the engineering specs, it is clear. Because I trained as an engineer, I appreciate the 1000x factor of higher MTBF in the design. I didn't always feel that way, until I saw multiple consumer disks fail when used in the same slot for the same purpose, multiple times, just after the drive warranty period ended.  

Often, we get lucky with consumer drives and they outlast the warranty, sometimes by many years. The places where I was tired of dealing with the hassles of replacing a HDD every 3 yrs, after a failure, are where I use DC-designed HDDs. Being able to avoid that hassle for 5+ yrs is worth the extra 30-50% cost to me.

We each have different pain points for storage.  When multiple 3-yr warranty HDDs fail before 4 yrs of use, I'm a little frustrated.  It feels like the manufacturer almost timed the design failure point extremely well to force replacement.  5yr warranty drives seem to last 10+ yrs, which has been my experience with all of them.  I haven't had any 5 yr warrant HDDs fail. Not once. Perhaps I've been lucky.  I have 2 WD-black (model, not color) HDDs in 2 different systems working today.  One is about 13 yrs old. The other is probably 6 yrs old and has been in a 2011 laptop that used to dual boot, into Win7 for specific uses, but hasn't been booted in perhaps 6 weeks. Both are 1TB size, 7200 rpm.
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   199   199   140    Pre-fail  Always       -       1
  9 Power_On_Hours          0x0032   001   001   000    Old_age   Always       -       103625
```
The single reallocated sector happened about 5 yrs ago.
Everything else in the SMART data is pristine on that box. It has 7 HDDs and they are all 7+ yrs old. 4 are in RAID1 configs (not RAID10).
Impressive  103625= 11.821484 yrs >> I favor WD, Intel, when longevity is crucial.

---

### Post by TheFu on 2022-03-10
> **1fallen said:**
> Impressive  103625= 11.821484 yrs >> I favor WD, Intel, when longevity is crucial.

I certainly don't feel ripped off.  Not by any of the drives in that system. They aren't all WD.  WD Red/Black, Toshiba, SAMSUNG and Hitachi. I celebrated when the last Seagate 2TB failed after just 13 months of use ... because I got to replace it.  Never again. That's kinda sad because Seagate was a customer of my employer in the 1990s, when they were making reasonable HDDs and were honest about design issues. The Caviar line had overheating issues early on, for example.  I'd look for seagate stuff then.

---

### Post by #&amp;thj^% on 2022-03-10
> **TheFu said:**
> I certainly don't feel ripped off.
Nor would I. ;)
and to quote you " I haven't had any 5 yr warrant HDDs fail. Not once. Perhaps I've been lucky. " is my same experience.
The one Intel drive I have is approaching 20 years, alright 17 years exactly, the salesman in me kicked in for a moment. :D
I just learned to stick with the proven.
```
=== START OF INFORMATION SECTION ===
Model Family:     Intel 520 Series SSDs
Device Model:     INTEL SSDSC2BW180A3L
Serial Number:    CVCV232002KV180EGN
LU WWN Device Id: 5 001517 bb29f60a6
Firmware Version: LE1i
User Capacity:    180,045,766,656 bytes [180 GB]
```
Sorry a little meandering again :p

---

### Post by rsteinmetz70112 on 2022-03-11
I checked the oldest drives I have currently in use are a pair of 500GB Seagates they have 15,291 power on hours, which seem kind of low to me since I think they were installed in mid 2011 and have been up more or less continuously since then. But I could be wrong about the install date.

---


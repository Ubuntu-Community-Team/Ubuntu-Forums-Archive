---
title: "Bad Blocks help needed (Ubuntu 7.10, ReiserFS)"
date: 2008-03-04
forum: General Help
---

### Post by mamadu bwana on 2008-03-04
Hi,

My computer has the following partitions:

```
root@ubuntu:/home/ubuntu# fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x01840183

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20482874    10241406   83  Linux
/dev/sda2        20482875    20996954      257040   82  Linux swap / Solaris
/dev/sda3        20996955   156296384    67649715   83  Linux

Disk /dev/sdb: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders, total 60036480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x016b35db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    60034904    30017421   83  Linux
root@ubuntu:/home/ubuntu# 
```

Since I was having I/O problems which froze the computer I did a check on them and I found this:

```

root@ubuntu:/home/ubuntu# fsck.reiserfs /dev/sda1
reiserfsck 3.6.19 (2003 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will read-only check consistency of the filesystem on /dev/sda1
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
###########
reiserfsck --check started at Tue Mar  4 16:20:04 2008
###########
Replaying journal..
Reiserfs journal '/dev/sda1' in blocks [18..8211]: 0 transactions replayed
Checking internal tree..
The problem has occurred looks like a hardware problem. If you have
bad blocks, we advise you to get a new hard drive, because once you
get one bad block  that the disk  drive internals  cannot hide from
your sight,the chances of getting more are generally said to become
much higher  (precise statistics are unknown to us), and  this disk
drive is probably not expensive enough  for you to you to risk your
time and  data on it.  If you don't want to follow that follow that
advice then  if you have just a few bad blocks,  try writing to the
bad blocks  and see if the drive remaps  the bad blocks (that means
it takes a block  it has  in reserve  and allocates  it for use for
of that block number).  If it cannot remap the block,  use badblock
option (-B) with  reiserfs utils to handle this block correctly.

bread: Cannot read the block (1114121): (Input/output error).

Aborted (core dumped)


```

Then I tried this:

```
root@ubuntu:/home/ubuntu# badblocks /dev/sda1
4456448
4456484
4456485
4456486
4456487
4456488
4456489
4456490
4456491
4456492
4456493
4456494
4456495
4456496
4456497
4456498
4456499
4456500
4456501
4456502
4456503
```

My other partitions did not report any errors.

Interestingly, I also tried a smart tools check which my partition passed:

```
root@ubuntu:/home/ubuntu# sudo smartctl -H /dev/sda1
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

root@ubuntu:/home/ubuntu# smartctl -i /dev/sda1
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax D540X-4K family
Device Model:     MAXTOR 4K080H4
Serial Number:    674120623352
Firmware Version: A08.1500
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  ATA/ATAPI-5 T13 1321D revision 1
Local Time is:    Tue Mar  4 17:42:35 2008 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
```

I am currently running my system off a live-CD so I am able to access the web (and this forum).

My questions are:

1) Is there a way to map and isolate the bad blocks and keep on living happily with my hard drive

or

2) what is the safest way to clone my partition to another hard disk (which I rather not do, since I am very short on cash)

Of course, if I have missed anything, please let me know how I could otherwise fix my computer.

Many thanks in advance,

Mamadu

PS:

/dev/sda1 is my / partition with the system on it
/dev/sda2 is my /swap partition
**/dev/sda2 is my /home partition with my data on it and this is the one I *really* would like to save, if possible**.
/dev/sdb1 is my /usr partition

---

### Post by articpenguin on 2008-03-04
bad blocks mean that the hdd is on its way out. I doubt that that there is an issue with bad blocks as the harddisk would automatically replace the bad block with a spare sector unless your harddisk has already used up all the spare sectors.

try doing smartctl this way

> sudo smartctl -a /dev/xdax

replace both xs with your drive like /sda1.

post what your smartctl is

here is mine

> john@john-desktop:~$ sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     ST3160815AS
Serial Number:    Hidden
Firmware Version: 3.AAC
User Capacity:    160,041,885,696 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Mar  4 16:49:31 2008 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever
                                        been run.
Total time to complete Offline
data collection:                 ( 430) seconds.
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
recommended polling time:        (  54) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   100   006    Pre-fail  Always       -       234256095
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       656
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   076   060   030    Pre-fail  Always       -       43723711
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1020
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       658
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   067   058   045    Old_age   Always       -       555155489
194 Temperature_Celsius     0x0022   033   042   000    Old_age   Always       -       33 (Lifetime Min/Max 0/15)
195 Hardware_ECC_Recovered  0x001a   083   061   000    Old_age   Always       -       209911836
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       448         -

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


---

### Post by articpenguin on 2008-03-04
one more thing

You can check for bad blocks when creating a new filesystem with

> sudo mkfs.ext3 -c /dev/sda1


Do note that is for making an ext3 filesystem i dont know about JFS Reiserfs or XFS.

---

### Post by mamadu bwana on 2008-03-04
Artcticpenguin,

Thanks for the reply!  Here is the output you asked me to get:

```
root@ubuntu:~# smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax D540X-4K family
Device Model:     MAXTOR 4K080H4
Serial Number:    674120623352
Firmware Version: A08.1500
User Capacity:    80,026,361,856 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   5
ATA Standard is:  ATA/ATAPI-5 T13 1321D revision 1
Local Time is:    Tue Mar  4 23:20:34 2008 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 (  44) seconds.
Offline data collection
capabilities:                    (0x1b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        No Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  50) minutes.

SMART Attributes Data Structure revision number: 11
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0029   100   253   020    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   076   075   020    Pre-fail  Always       -       3102
  4 Start_Stop_Count        0x0032   100   100   008    Old_age   Always       -       436
  5 Reallocated_Sector_Ct   0x0033   098   098   020    Pre-fail  Always       -       10
  7 Seek_Error_Rate         0x000b   100   093   023    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0012   093   093   001    Old_age   Always       -       4918
 10 Spin_Retry_Count        0x0026   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   008    Old_age   Always       -       435
 13 Read_Soft_Error_Rate    0x000b   100   085   023    Pre-fail  Always       -       0
194 Temperature_Celsius     0x0022   086   084   042    Old_age   Always       -       38
195 Hardware_ECC_Recovered  0x001a   006   002   000    Old_age   Always       -       415459378
196 Reallocated_Event_Count 0x0010   100   253   020    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0032   100   099   020    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x001a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 213 (device log contains only the most recent five errors)
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

Error 213 occurred at disk power-on lifetime: 4912 hours (204 days + 16 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 d1 04 87 00 88 e0  Error: UNC 4 sectors at LBA = 0x00880087 = 8913031

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 04 87 00 88 e0 88      00:07:24.708  READ DMA
  f8 00 00 00 00 00 e0 88      00:07:24.679  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 88      00:07:24.671  IDENTIFY DEVICE
  ef 00 45 00 00 00 a0 88      00:07:24.664  SET FEATURES [Reserved subcommand]
  f8 00 00 00 00 00 e0 88      00:07:24.664  READ NATIVE MAX ADDRESS

Error 212 occurred at disk power-on lifetime: 4912 hours (204 days + 16 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 d1 04 87 00 88 e0  Error: UNC 4 sectors at LBA = 0x00880087 = 8913031

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 04 87 00 88 e0 88      00:07:12.404  READ DMA
  f8 00 00 00 00 00 e0 88      00:07:12.361  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 88      00:07:12.353  IDENTIFY DEVICE
  ef 00 45 00 00 00 a0 88      00:07:12.346  SET FEATURES [Reserved subcommand]
  f8 00 00 00 00 00 e0 88      00:07:12.345  READ NATIVE MAX ADDRESS

Error 211 occurred at disk power-on lifetime: 4912 hours (204 days + 16 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 d1 04 87 00 88 e0  Error: UNC 4 sectors at LBA = 0x00880087 = 8913031

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 04 87 00 88 e0 88      00:07:00.902  READ DMA
  f8 00 00 00 00 00 e0 88      00:07:00.827  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 88      00:07:00.809  IDENTIFY DEVICE
  ef 00 45 00 00 00 a0 88      00:07:00.799  SET FEATURES [Reserved subcommand]
  f8 00 00 00 00 00 e0 88      00:07:00.799  READ NATIVE MAX ADDRESS

Error 210 occurred at disk power-on lifetime: 4912 hours (204 days + 16 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 d1 04 87 00 88 e0  Error: UNC 4 sectors at LBA = 0x00880087 = 8913031

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 04 87 00 88 e0 88      00:06:48.551  READ DMA
  f8 00 00 00 00 00 e0 88      00:06:48.509  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 88      00:06:48.501  IDENTIFY DEVICE
  ef 00 45 00 00 00 a0 88      00:06:48.493  SET FEATURES [Reserved subcommand]
  f8 00 00 00 00 00 e0 88      00:06:48.493  READ NATIVE MAX ADDRESS

Error 209 occurred at disk power-on lifetime: 4912 hours (204 days + 16 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 d1 04 87 00 88 e0  Error: UNC 4 sectors at LBA = 0x00880087 = 8913031

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 04 87 00 88 e0 88      00:06:36.246  READ DMA
  f8 00 00 00 00 00 e0 88      00:06:36.214  READ NATIVE MAX ADDRESS
  ec 00 00 00 00 00 a0 88      00:06:36.206  IDENTIFY DEVICE
  ef 00 45 00 00 00 a0 88      00:06:36.199  SET FEATURES [Reserved subcommand]
  f8 00 00 00 00 00 e0 88      00:06:36.198  READ NATIVE MAX ADDRESS

SMART Self-test log structure revision number 0
Warning: ATA Specification requires self-test log structure revision number = 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Device does not support Selective Self Tests/Logging
root@ubuntu:~# 
```

Does that show something definitive?

Mamadu

---

### Post by articpenguin on 2008-03-05
yes your harddrive has found 10 bad sectors and reallocated them with spare ones. your best bet is to replace that drive as soon as possible because more bad sectors will appear.

---

### Post by mamadu bwana on 2008-03-05
thanks.  a new drive it shall be.

---


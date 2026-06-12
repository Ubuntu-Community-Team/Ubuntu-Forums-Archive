---
title: "cannot boot fresh ubuntu 7.10 install - completely clueless :("
date: 2008-01-22
forum: General Help
---

### Post by jabibi on 2008-01-22
Hello guys i just registered in the forum and sadly it is to ask for help for a problem i have not been able to solve on my own, I've looked all over this forum and google for a solution but havent found one yet

first of all my pc specs:
amd athlon 64 x2 4200 2,2 GHz
1 GB ram
nvidia 7300 512 MB
Biostar Motherboard with Nvidia Chipset
and the most important in this case: 1 SATA hard drive and 1 IDE hard drive

well i got windows in the SATA drive and I am installing ubuntu 7.10 gutsy on the IDE drive
installation goes all okay

PROBLEM: when i boot i get to Grub and select linux instead of windows, then it gets to the ubuntu logo screen and the hard drive read led sometimes blinks very briefly and most times doesnt even blink at all and it just stays there without loading anything for a while then throwing me to a busybox prompt

I think the problem is that my IDE hard drive is not accesible i have reached this conclusion becase when i use live cd and try to mount the IDE drive (hda) where i installed ubuntu and i go to /dev/ i find that there is no hda1 nor hda2 nor anything just one hda file that i dont know what to do with. curious thing is that the sata drive with the ntfs partition is okay because i can totally find the sda1 file under /dev/ folder

plus here's a screenshot of an error i get with GParted while using the live cd

i tried to find a solution for this but wasnt successful & i'm totally clueless now

it seems that the hda drive is blocked for some reason and keeps it from creating the hda1 file or something i dont know, already tried to set the jumpers, didnt work


I can get on a live cd but i cannot access hda1 (main boot partition for ubuntu) at all as a consequence of that I cannot access /etc/fstab file

And this is how i set up my hard drives: SATA drive completely partitioned with NTFS for windows, IDE drive completely used for ubuntu ext3 partition only 2.8 GB for swap


thank you guys for reading it came out longer than i tought

[IMG]http://img115.imageshack.us/img115/1374/parterrorcc8.png[/IMG]

---

### Post by dcstar on 2008-01-23
> **jabibi said:**
> Hello guys i just registered in the forum and sadly it is to ask for help for a problem i have not been able to solve on my own, I've looked all over this forum and google for a solution but havent found one yet

first of all my pc specs:
amd athlon 64 x2 4200 2,2 GHz
1 GB ram
nvidia 7300 512 MB
Biostar Motherboard with Nvidia Chipset
and the most important in this case: 1 SATA hard drive and 1 IDE hard drive

well i got windows in the SATA drive and I am installing ubuntu 7.10 gutsy on the IDE drive
installation goes all okay
........]

Delete and recreate the partition manually using the Live CD, then do a reinstall and select the "manual" option at the partitioning stage, and use the existing partitions on the IDE disk.

---

### Post by jabibi on 2008-01-23
yea i already tried that
didnt work
do you think my hard drive is damaged?

---

### Post by logos34 on 2008-01-23
try wiping it completely with [Darik's Boot and nuke]("http://dban.sourceforge.net/") or Active Killdisk.  Then reinstall.

There's a small chance it could be physically damaged.  SMART will tell you about that.
(from live cd:
 sudo apt-get install smartmontools
sudo smartctl /dev/hda (or sdb, whatever)

What does

sudo fdisk -l 

show?

---

### Post by jabibi on 2008-01-23
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

**ubuntu@ubuntu:~$ sudo apt-get install smartmontools**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  smartmontools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 288kB of archives.
After unpacking 700kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main smartmontools 5.37-5ubuntu2 [288kB]
Fetched 288kB in 6s (43.0kB/s)                                                 
Selecting previously deselected package smartmontools.
(Reading database ... 92004 files and directories currently installed.)
Unpacking smartmontools (from .../smartmontools_5.37-5ubuntu2_i386.deb) ...
Setting up smartmontools (5.37-5ubuntu2) ...


**ubuntu@ubuntu:~$ sudo smartctl /dev/hda**
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

**ubuntu@ubuntu:~$ sudo fdisk -l**

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f213f20

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9356    75152038+  83  Linux
/dev/hda2            9357        9733     3028252+   5  Extended
/dev/hda5            9357        9733     3028221   82  Linux swap / Solaris

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x747c747c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10011    80413326    7  HPFS/NTFS


**ubuntu@ubuntu:~$ ls /dev/hd***
/dev/hda  /dev/hdc  /dev/hdd

 
**ubuntu@ubuntu:~$ ls /dev/sd***
/dev/sda  /dev/sda1




i guess it's not damaged or maybe i didnt used the command right and it didnt really check anything, didnt seem like it did... i'm gonna try that dariks boot and nuke

---

### Post by logos34 on 2008-01-23
sorry, I left out one letter:

> sudo smartctl **-a** /dev/hda

smartctl -h

man smartctl

---

### Post by jabibi on 2008-01-23
sure here it is
dont understand much of it though


ubuntu@ubuntu:~$ sudo smartctl -a /dev/hda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG SP0822N
Serial Number:    S06QJ10Y490330
Firmware Version: WA100-10
User Capacity:    80,060,424,192 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 1
Local Time is:    Wed Jan 23 22:23:04 2008 UTC

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

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
data collection:                 (1980) seconds.
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
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (  33) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   091   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   067   060   011    Pre-fail  Always       -       5000
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       1155
  5 Reallocated_Sector_Ct   0x0033   252   252   011    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   252   252   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   252   252   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       374944
 10 Spin_Retry_Count        0x0033   252   252   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       615
194 Temperature_Celsius     0x0022   118   094   000    Old_age   Always       -       45
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   199   199   000    Old_age   Always       -       60
200 Multi_Zone_Error_Rate   0x000a   252   100   051    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   252   252   051    Old_age   Always       -       0

Warning! SMART ATA Error Log Structure error: invalid SMART checksum.
SMART Error Log Version: 1
ATA Error Count: 82 (device log contains only the most recent five errors)
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

Error 82 occurred at disk power-on lifetime: 3109 hours (129 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 5f 03 00 e0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------

Error 81 occurred at disk power-on lifetime: 3109 hours (129 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 5f 03 00 e0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  10 00 3f 00 00 00 e0 00      00:59:56.000  RECALIBRATE [OBS-4]

Error 80 occurred at disk power-on lifetime: 3109 hours (129 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 40 87 99 05 e0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------

Error 79 occurred at disk power-on lifetime: 3109 hours (129 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 40 87 99 05 e0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------

Error 78 occurred at disk power-on lifetime: 3109 hours (129 days + 13 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 c8 b7 99 05 e0  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------

Warning! SMART Self-Test Log Structure error: invalid SMART checksum.
SMART Self-test log structure revision number 0
Warning: ATA Specification requires self-test log structure revision number = 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      3124         -
# 2  Abort offline test  Aborted by host               90%      3124         -

SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN       MIN_LBA          MAX_LBA  CURRENT_TEST_STATUS
    1  545460846592  281474976710656  Not_testing
    2             0                0  Not_testing
    3             0                0  Not_testing
    4             0            90000  Not_testing
    5        604800                4  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

---

### Post by jabibi on 2008-01-24
fixed, i changed the IDE cable... who wouldve tought

---

### Post by logos34 on 2008-01-24
> **jabibi said:**
> fixed, i changed the IDE cable... who wouldve tought

yeah, odd.  I'd never have guessed.  Usually if it's a bad cable the bios won't even detect it properly, let alone the OS.  Maybe it was an older 40-pin cable...Anyhoo, glad you fixed it.

The disk passed the overall-health smart test...it apparently had some hiccup at boot at 3109 hours.  no big deal

---

### Post by jabibi on 2008-01-25
thank you for your assistance logos

---


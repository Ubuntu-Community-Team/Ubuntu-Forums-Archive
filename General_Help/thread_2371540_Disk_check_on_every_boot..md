---
title: "Disk check on every boot."
date: 2017-09-15
forum: General Help
---

### Post by CaptainMark on 2017-09-15
I had a power outage last week, I think there was a brief power surge just before which blew the power out completely. I had to remove the battery from my mother board to get my PC booting up properly (I should invest in surge protection sockets)
My PC seems fine except that Ubuntu runs a disk check on every single boot, it doesn't take long (about 30 seconds) and reports no errors but it gets tedious because it used to only happen once in a while. I'm seeing no negative effects but would like to stop this constant disk checking. I've never had drive issues so could someone help me with how to diagnose this issue.

I've run some commands that I have found online in the hope that it might shed some light on the issue. I have a main drive and a backup external USB drive, both 2TB which are sda and sdb in the following

```

[18:24:30] mark@desktop ~ $ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=38fa9d54-d71d-4b64-8973-094aa2d609cd /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=8a421b5e-f42b-496c-b005-9ce7366ee421 /home           ext4    defaults        0       2
# /media/samsung2tb was on /dev/sdb1 during installation
UUID=acb4d475-1cf0-47fd-865b-6d9c841ba4ee /media/samsung_2tb ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=041209ad-4eec-4274-85d5-af19c5889374 none            swap    sw              0       0
[17:48:10] mark@desktop ~ $ sudo smartctl -i /dev/sda 
[sudo] password for mark: 
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.8.0-53-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Green
Device Model:     WDC WD20EZRX-00D8PB0
Serial Number:    WD-WCC4NC389ND4
LU WWN Device Id: 5 0014ee 20a8d9e6b
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Sep 15 18:23:20 2017 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


[18:23:20] mark@desktop ~ $ sudo smartctl -H /dev/sda
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.8.0-53-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


[18:23:36] mark@desktop ~ $ sudo smartctl --test=short /dev/sda
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.8.0-53-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 2 minutes for test to complete.
Test will complete after Fri Sep 15 18:25:55 2017


Use smartctl -X to abort test.
[18:23:55] mark@desktop ~ $ sudo smartctl -a /dev/sda
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.8.0-53-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Green
Device Model:     WDC WD20EZRX-00D8PB0
Serial Number:    WD-WCC4NC389ND4
LU WWN Device Id: 5 0014ee 20a8d9e6b
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Sep 15 18:27:26 2017 BST
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
data collection:         (27360) seconds.
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
recommended polling time:      ( 276) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   173   164   021    Pre-fail  Always       -       6333
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1395
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3189
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1395
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       542
193 Load_Cycle_Count        0x0032   163   163   000    Old_age   Always       -       112901
194 Temperature_Celsius     0x0022   118   102   000    Old_age   Always       -       32
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      3189         -
# 2  Short offline       Completed without error       00%      3181         -


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



[18:24:49] mark@desktop ~ $ sudo smartctl -i /dev/sda 
[sudo] password for mark: 
[18:25:12] mark@desktop ~ $ clear
[18:25:13] mark@desktop ~ $ sudo smartctl -i /dev/sdb
[sudo] password for mark: 
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.8.0-53-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Samsung SpinPoint M9TU (USB)
Device Model:     ST2000LM005 HN-M201AAD
Serial Number:    F9433H26AA9E9L
LU WWN Device Id: 0 000000 000000000
Firmware Version: 2BC10006
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Sep 15 18:25:20 2017 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


[18:25:20] mark@desktop ~ $ sudo smartctl -H /dev/sdb
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.8.0-53-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF READ SMART DATA SECTION ===
SMART Status not supported: Incomplete response, ATA output registers missing
SMART overall-health self-assessment test result: PASSED
Warning: This result is based on an Attribute check.


[18:25:38] mark@desktop ~ $ sudo smartctl --test=short /dev/sdb
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.8.0-53-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 1 minutes for test to complete.
Test will complete after Fri Sep 15 18:26:51 2017


Use smartctl -X to abort test.
[18:25:51] mark@desktop ~ $ sudo smartctl -a /dev/sdb
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.8.0-53-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Samsung SpinPoint M9TU (USB)
Device Model:     ST2000LM005 HN-M201AAD
Serial Number:    F9433H26AA9E9L
LU WWN Device Id: 0 000000 000000000
Firmware Version: 2BC10006
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Sep 15 18:27:50 2017 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART Status not supported: Incomplete response, ATA output registers missing
SMART overall-health self-assessment test result: PASSED
Warning: This result is based on an Attribute check.


General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (22980) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 383) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   087   086   025    Pre-fail  Always       -       4081
  4 Start_Stop_Count        0x0032   088   088   000    Old_age   Always       -       12659
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       1332
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1399
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       43
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   056   000    Old_age   Always       -       29 (Min/Max 5/45)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       7
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   096   096   000    Old_age   Always       -       47878


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1332         -


SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


[18:27:51] mark@desktop ~ $
```If anyone could help that would be appreciated.

Regards
Mark

---

### Post by SeijiSensei on 2017-09-15
Any chance you have a file called /forcefsck on your machine?  If so, remove it, and the problem should go away.

---

### Post by untrustytahr on 2017-09-15
What happens if you put the battery back in and set the hardware time in bios?

---

### Post by ajgreeny on 2017-09-15
Are you sure it is carrying out a fsck check, and not simply reporting, as my 16.04 systems do, that the filesystem is clean?

If you run command ```
sudo tune2fs -l /dev/sda1 | grep "Last checked:"
``` changing sda1 to whatever is your root partition, you will see the date that fsck was last fully run on your system.
If you run just the first part of that command, ```
sudo tune2fs -l /dev/sda1
``` you will get a lot more useful info about how often fsck is set to run, here's my output:-
```
Filesystem created:       Fri Mar 29 15:01:08 2013
Last mount time:          Fri Sep 15 15:35:17 2017
Last write time:          Fri Sep 15 15:35:17 2017
Mount count:              32
Maximum mount count:      90
Last checked:             Mon Aug  7 10:30:58 2017
Check interval:           5616000 (2 months, 5 days)
Next check after:         Wed Oct 11 10:30:58 2017
```

---

### Post by CaptainMark on 2017-09-15
@untrustytahr The battery went back in after a short period, just to clear the cmos (if that's the right term, I don't know but it worked and got the PC running) checking hwclock has the wrong date and time so I'll set it correctly and check it in the Bios.

@ajgreeny I'm not sure how its checking, this isn't a message from the bootup log that get spat out if you hit tab (or whichever key does that) it literally pops up over the plymouth splashscreen and just says something like "Checking Disk XX% Complete" It doesn't say if its fsck that's doing it. Either way the output from tune2fs looks fishy, I get this
```

Filesystem created:       Mon Jul  4 07:36:39 2016
Last mount time:          Tue Feb 23 19:49:28 2016
Last write time:          Tue Feb 23 19:49:24 2016
Mount count:              405
Maximum mount count:      -1
Last checked:             Mon Jul  4 07:36:40 2016
Check interval:           0 (<none>)

```
I guess it read 2016 because that's when my hwclock was set to until just a few minutes ago.

---

### Post by CaptainMark on 2017-09-15
Okay, thanks untrustytahr, it was simply the hardware clock that was causing the issue, rebooted after setting it and now the check doesn't happen.

I still have this for tune2fs though ```
Filesystem created:       Mon Jul  4 07:36:39 2016
Last mount time:          Fri Sep 15 21:33:36 2017
Last write time:          Fri Sep 15 21:33:32 2017
Mount count:              406
Maximum mount count:      -1
Last checked:             Mon Jul  4 07:36:40 2016
Check interval:           0 (<none>)

``` Should I be worried or should I change some settings to ensure filesystems are being checked correctly?

---

### Post by ajgreeny on 2017-09-16
As you can see from my tune2fs output my filesystem is checked either every 90 mounts or after 65 days (I'm not sure if one takes preference over the other but it works for me).

You can change your settings using tune2fs, eg ```
sudo tune2fs -c 60 /dev/sda1
``` to set it to check every 60 mounts.
See **man tune2fs** for all the options available.

---


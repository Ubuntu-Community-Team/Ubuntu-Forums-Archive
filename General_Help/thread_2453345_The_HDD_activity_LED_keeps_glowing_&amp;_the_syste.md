---
title: "The HDD activity LED keeps glowing &amp; the system becomes very slow"
date: 2020-11-08
forum: General Help
---

### Post by linuxyogi on 2020-11-08
The HDD activity LED keeps glowing & the system becomes very slow.
How do I troubleshoot this ? Please tell me what commands I need to run which will tell us the needed info.

---

### Post by CelticWarrior on 2020-11-08
It can be due to excessive use of swap.
Check your running processes.

---

### Post by linuxyogi on 2020-11-08
> **CelticWarrior said:**
> It can be due to excessive use of swap.
Check your running processes.

```
$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3810        1983         164         251        1662        1337
Swap:          1158           1        1157


```

It just happened again. Only streaming Youtube on Firefox. It continued for like 5-7 mins & the hdd activity returned to normal. After that the system was responsive again.

---

### Post by linuxyogi on 2020-11-08
Do you think my PC is running out of Ram ?

```
$ sudo inxi -m
Memory:    Used/Total: 2063.4/3810.5MB
           Array-1 capacity: 64 GB devices: 4 EC: None
           Device-1: DIMM_A1 size: 4 GB speed: 2133 MT/s type: DDR4
           Device-2: DIMM_A2 size: No Module Installed type: N/A
           Device-3: DIMM_B1 size: No Module Installed type: N/A
           Device-4: DIMM_B2 size: No Module Installed type: N/A


```

---

### Post by CelticWarrior on 2020-11-08
Check with 'top'

---

### Post by linuxyogi on 2020-11-08
> **CelticWarrior said:**
> Check with 'top'
[ATTACH=CONFIG]287325[/ATTACH]
(click to enlarge)

---

### Post by Autodave on 2020-11-08
RAM usage looks fine.  Try disabling all of your ad blockers and then enable uBlock and see what happens.

---

### Post by CatKiller on 2020-11-08
> **linuxyogi said:**
> It just happened again. Only streaming Youtube on Firefox. It continued for like 5-7 mins & the hdd activity returned to normal. After that the system was responsive again.

Do you have some kind of file indexer running when it happens?

---

### Post by pushbike06 on 2020-11-08
I recently experienced HD hyperactivity and I suggest three possible causes.
I have 4 GB ram.
1. Unattended system/ apps update / upgrade will slow down user activity and cause HD activity.
2. Some apps, Firefox, have unattended update settings, this could slow down user activity.
3. I use "sleep /hibernate" shut down and found that this caused hyper HD activity. Solved by shutting down completely and restart. Probably caused by excessive swap activity and limited ram space.

---

### Post by dinkidonk on 2020-11-09
The EXT4 filesystem may also be doing "optimizations" if the file system is starting to fragment. This may cause lots of drive activity because blocks are being moved around, but I have never experienced any significant slow downs when this happens and it is usually only happening when the drive is idle.

---

### Post by linuxyogi on 2020-12-12
I found a weird solution. Since Firefox & Youtube was causing the freezes I am using Google Chrome to watch Youtube & doing all my other web activity using Firefox.

I am not alone please [read this]("https://support.mozilla.org/en-US/questions/1269008")

---

### Post by linuxyogi on 2020-12-27
Today it happened again when I was watching Youtube using Google Chrome. 

Someone please help. This problem is very depressing.

---

### Post by maglin2 on 2020-12-27
Something that happens for 5-7 minutes should surely be detectable from system monitor (or lubuntu equivalent)? Check that you are showing all processes and look for the one using most disk/cpu/RAM?
I have seen this happen before on my system due to:
kubuntu file indexer (they seemed to fix that, not seen similar for a long time)
xapian index (again not seen for a long time - don't think it's part of normal install any more)
snaps auto-updating (especially browser snaps)
AV updating in the days when I ran one.

---

### Post by linuxyogi on 2020-12-27
> **maglin2 said:**
> Something that happens for 5-7 minutes should surely be detectable from system monitor (or lubuntu equivalent)? Check that you are showing all processes and look for the one using most disk/cpu/RAM? 

Please understand that when the problem starts there is absolutely nothing that I can do. Mouse clicks doesn't work, & no keyboard response. I tried pressing CTRL+ALT+T but got no resposnse. Only way out is REISUB.

---

### Post by dinkidonk on 2020-12-27
What you experience is something often seen prior to a drive failure.

Which hard drive are you using for the system and how much free space is available on it? Have you checked the SMART data (smartmontools) for the drive to see if there are any bad sectors? Has your system been upgraded from a previous version or is it a fresh install?

---

### Post by linuxyogi on 2020-12-27
> **dinkidonk said:**
> What you experience is something often seen prior to a drive failure.

Which hard drive are you using for the system and how much free space is available on it? Have you checked the SMART data (smartmontools) for the drive to see if there are any bad sectors? Has your system been upgraded from a previous version or is it a fresh install?

         
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           381M  1.6M  379M   1% /run
/dev/sdb2       110G   16G   89G  15% /
tmpfs           1.9G     0  1.9G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           1.9G  4.0K  1.9G   1% /tmp
/dev/loop2       56M   56M     0 100% /snap/core18/1944
/dev/loop1      243M  243M     0 100% /snap/chromium/1421
/dev/loop3       56M   56M     0 100% /snap/core18/1932
/dev/loop0      119M  119M     0 100% /snap/chromium/1424
/dev/loop4      163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop5      173M  173M     0 100% /snap/spotify/43
/dev/loop6       65M   65M     0 100% /snap/gtk-common-themes/1513
/dev/loop7       65M   65M     0 100% /snap/gtk-common-themes/1514
/dev/loop8       32M   32M     0 100% /snap/snapd/10238
/dev/loop9       32M   32M     0 100% /snap/snapd/10492
/dev/sdb1       511M  7.9M  504M   2% /boot/efi
tmpfs           381M   12K  381M   1% /run/user/1000
/dev/sda1       146G   28G  111G  21% /media/lubuntu/SEAGATE
/dev/loop10     2.3M  2.3M     0 100% /snap/ksnip/265
/dev/loop11     261M  261M     0 100% /snap/kde-frameworks-5-core18/32


```
 
sdb is the SSD where Lubuntu is installed
sda is a spinning HDD where some of my already backed up data is stored.

Note: sda is not mentioned in /etc/fstab & therefore not automatically mounted. I mount it as per need.

```
$ sudo smartctl --all /dev/sdb
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-58-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Samsung based SSDs
Device Model:     Samsung SSD 750 EVO 120GB
Serial Number:    S33MNB0H582786V
LU WWN Device Id: 5 002538 d40eadaf3
Firmware Version: MAT01B6Q
User Capacity:    120,034,123,776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2, ATA8-ACS T13/1699-D revision 4c
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sun Dec 27 17:57:58 2020 IST
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
data collection:                (    0) seconds.
Offline data collection
capabilities:                    (0x53) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        No Offline surface scan supported.
                                        Self-test supported.
                                        No Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  64) minutes.
SCT capabilities:              (0x003d) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       8349
 12 Power_Cycle_Count       0x0032   095   095   000    Old_age   Always       -       4254
177 Wear_Leveling_Count     0x0013   092   092   000    Pre-fail  Always       -       40
179 Used_Rsvd_Blk_Cnt_Tot   0x0013   100   100   010    Pre-fail  Always       -       0
181 Program_Fail_Cnt_Total  0x0032   100   100   010    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   010    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0013   100   099   010    Pre-fail  Always       -       0
187 Uncorrectable_Error_Cnt 0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0032   070   048   000    Old_age   Always       -       30
195 ECC_Error_Rate          0x001a   200   200   000    Old_age   Always       -       0
199 CRC_Error_Count         0x003e   100   100   000    Old_age   Always       -       0
235 POR_Recovery_Count      0x0012   099   099   000    Old_age   Always       -       211
241 Total_LBAs_Written      0x0032   099   099   000    Old_age   Always       -       10234908204

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Aborted by host               40%      7906         -
# 2  Extended offline    Aborted by host               90%      5986         -
# 3  Short offline       Completed without error       00%      5042         -
# 4  Short offline       Completed without error       00%      5041         -
# 5  Short offline       Completed without error       00%      5033         -
# 6  Short offline       Completed without error       00%      5032         -
# 7  Short offline       Completed without error       00%      5026         -
# 8  Short offline       Completed without error       00%      5025         -
# 9  Short offline       Completed without error       00%      5024         -
#10  Short offline       Completed without error       00%      5018         -
#11  Short offline       Completed without error       00%      5018         -
#12  Short offline       Completed without error       00%      5017         -
#13  Short offline       Completed without error       00%      5013         -
#14  Short offline       Completed without error       00%      5011         -
#15  Short offline       Completed without error       00%      5010         -
#16  Short offline       Completed without error       00%      5009         -
#17  Short offline       Completed without error       00%      5008         -
#18  Extended offline    Aborted by host               30%      5007         -
#19  Short offline       Completed without error       00%      5002         -
#20  Short offline       Completed without error       00%      5000         -
#21  Short offline       Completed without error       00%      4999         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
  255        0    65535  Read_scanning was never started
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


```

```
$ sudo smartctl --all /dev/sda
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-58-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10
Device Model:     ST3160215AS
Serial Number:    6RAAA8P8
Firmware Version: 4.AAB
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA/ATAPI-7 (minor revision not indicated)
Local Time is:    Sun Dec 27 17:58:29 2020 IST
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
data collection:                (  430) seconds.
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
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   088   088   020    Old_age   Always       -       12308
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   088   060   030    Pre-fail  Always       -       724803665
  9 Power_On_Hours          0x0032   077   077   000    Old_age   Always       -       20161
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   088   088   020    Old_age   Always       -       12457
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       115
189 High_Fly_Writes         0x003a   090   090   000    Old_age   Always       -       10
190 Airflow_Temperature_Cel 0x0022   063   050   045    Old_age   Always       -       37 (Min/Max 23/38)
194 Temperature_Celsius     0x0022   037   050   000    Old_age   Always       -       37 (0 20 0 0 0)
195 Hardware_ECC_Recovered  0x001a   073   067   000    Old_age   Always       -       9111615
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       2
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       2
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 Data_Address_Mark_Errs  0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 121 (device log contains only the most recent five errors)
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

Error 121 occurred at disk power-on lifetime: 520 hours (21 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 72 5a 0d e0  Error: UNC at LBA = 0x000d5a72 = 875122

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 01 72 5a 0d e0 00      00:08:52.207  READ DMA EXT
  35 00 01 71 5a 0d e0 00      00:08:52.207  WRITE DMA EXT
  25 00 01 71 5a 0d e0 00      00:08:55.415  READ DMA EXT
  25 00 01 72 5a 0d e0 00      00:08:55.415  READ DMA EXT
  25 00 01 71 5a 0d e0 00      00:08:55.391  READ DMA EXT

Error 120 occurred at disk power-on lifetime: 520 hours (21 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 72 5a 0d e0  Error: UNC at LBA = 0x000d5a72 = 875122

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 01 72 5a 0d e0 00      00:08:52.207  READ DMA EXT
  25 00 01 71 5a 0d e0 00      00:08:52.207  READ DMA EXT
  25 00 01 70 5a 0d e0 00      00:08:52.206  READ DMA EXT
  25 00 01 6f 5a 0d e0 00      00:08:52.206  READ DMA EXT
  25 00 01 6e 5a 0d e0 00      00:08:52.206  READ DMA EXT

Error 119 occurred at disk power-on lifetime: 520 hours (21 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 72 5a 0d e0  Error: UNC at LBA = 0x000d5a72 = 875122

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  41 00 01 72 5a 0d e0 00      00:43:33.999  READ VERIFY SECTOR(S) (w/o retry) [OBS-5]
  41 00 01 71 5a 0d e0 00      00:43:33.991  READ VERIFY SECTOR(S) (w/o retry) [OBS-5]
  41 00 01 70 5a 0d e0 00      00:43:33.983  READ VERIFY SECTOR(S) (w/o retry) [OBS-5]
  41 00 01 6f 5a 0d e0 00      00:43:33.983  READ VERIFY SECTOR(S) (w/o retry) [OBS-5]
  41 00 01 6e 5a 0d e0 00      00:43:33.974  READ VERIFY SECTOR(S) (w/o retry) [OBS-5]

Error 118 occurred at disk power-on lifetime: 520 hours (21 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 72 5a 0d e0  Error: UNC at LBA = 0x000d5a72 = 875122

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  42 00 00 00 5a 0d e0 00      00:43:30.570  READ VERIFY SECTOR(S) EXT
  42 00 00 00 59 0d e0 00      00:43:30.595  READ VERIFY SECTOR(S) EXT
  42 00 00 00 58 0d e0 00      00:43:30.592  READ VERIFY SECTOR(S) EXT
  42 00 00 00 57 0d e0 00      00:43:30.591  READ VERIFY SECTOR(S) EXT
  42 00 00 00 56 0d e0 00      00:43:30.589  READ VERIFY SECTOR(S) EXT

Error 117 occurred at disk power-on lifetime: 519 hours (21 days + 15 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 72 5a 0d e0  Error: UNC at LBA = 0x000d5a72 = 875122

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 03 40 70 5a 0d e0 00      00:02:40.034  READ DMA EXT
  25 03 01 00 00 00 e0 00      00:02:40.023  READ DMA EXT
  35 03 08 8f dc 94 e0 00      00:02:40.023  WRITE DMA EXT
  35 03 10 f7 23 91 e0 00      00:02:40.023  WRITE DMA EXT
  25 03 1e 81 71 90 e0 00      00:02:40.023  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     13440         -
# 2  Short offline       Completed without error       00%     12632         -
# 3  Short offline       Completed without error       00%     11525         -
# 4  Extended offline    Completed without error       00%     10486         -
# 5  Short offline       Completed without error       00%      3978         -
# 6  Extended offline    Aborted by host               90%      3715         -
# 7  Short offline       Completed without error       00%      3714         -
# 8  Extended offline    Completed: read failure       90%       118         11322720
# 9  Extended offline    Completed: read failure       90%       118         11322720
#10  Short offline       Completed: read failure       90%       118         11322720
3 of 3 failed self-tests are outdated by newer successful extended offline self-test # 1

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

This is a fresh installation. Not upgraded.

---

### Post by dino99 on 2020-12-27
For each hitted problem, glance at 'journal-b' output from a terminal. Pay attention to red line(s) as 'error'; yellow line(s) are warnings. You might found something pointing to your browser problem. Then you are able to dig further.

Note that such issue is also often seen with buggy extension(s); so deactivate it (them) via the tweaks tool, or purge it (them) and restart the session to find/know about the faulty extension..

---

### Post by maglin2 on 2020-12-27
> **linuxyogi said:**
> Please understand that when the problem starts there is absolutely nothing that I can do. Mouse clicks doesn't work, & no keyboard response. I tried pressing CTRL+ALT+T but got no resposnse. Only way out is REISUB.

Well your thread is titled
[h=2][SIZE=2]The HDD activity LED keeps glowing & the system becomes very slow 		[/SIZE][SIZE=2][FONT=arial][/FONT][/SIZE][/h]perhaps edit it to System Freezes?

---

### Post by dinkidonk on 2020-12-27
Looking through the SMART data I've spotted some concerns:

[sda]
197 Current Pending Sector = 2
198 Offline Uncorrectable = 2

The drive has bad sectors waiting to be remapped, this indicates that the drive is about to fail. This should not cause system lockups, but try to disconnect the drive from the computer and see if that does a difference.


[sdb]
235 POR Recovery Count = 211

The drive has recovered from sudden power loss 211 times. When a SSD suffers a power loss, data may become dirty and this causes the drives internal firmware to start a recovery procedure on the next power on to regain the mapping of the user data and this may cause the drive to become slow or unresponsive. Even after recovery, data on the drive (eg. the file system) may be corrupted which can cause all sorts of trouble. You should find out why this number is so high and what causes it to increase. A bad power cable or the use of hibernation could be possible causes.

---

### Post by jay-eich on 2020-12-27
Hi there,

My sincere sympathies..
I have a few more debug suggesions.
 
  If you have another system on a 'live' USB, boot it and run fsck on both sda and sdb
  (( I alive system is needed so thet the usual systems on sda and sdb are not mounted.))

I agree that another choice is to try to set your home page in firefox to about:blank ar a static html page that you created and use the file:///somewhere/my.html  as home page.

By 'freeze', how long do you wait? Is there a CPU activitity light? I have had to wait several minutes on an old -i86 system with about 500Meg of memory. It worked for me.(after much debug)

( I also unstalled/purged firefox and reinstalled to get rid of add-ons. After purge, double-check .mozill to be sure all firefox is removed)

Try installing and running gkrellm ( a reference to the movie "Forbidden Planet"). Be sure The memory and swap indicators are configured. Start it up before you start Firefox, then watch it as you start firefox. Start firefox on a command line so you can <ctl-c> it to stop and see any more error messgaes that pop out.

On my small system (laptop), I was stuck - couldn't add memory. In my desktop, I added a lot of memory - then swap is  not needed. as:
  $swapon
NAME      TYPE      SIZE USED PRIO
/dev/sdb4 partition 9.3G   0B   -2

I do hope this is helpful.
Coffee helps.
To a point, beer also works for me.

Cheers!!
Jay

edited: fixed typo . addred firefox purge stuff.

---

### Post by linuxyogi on 2020-12-30
> **dino99 said:**
> For each hitted problem, glance at 'journal-b' output from a terminal. Pay attention to red line(s) as 'error'; yellow line(s) are warnings. You might found something pointing to your browser problem. Then you are able to dig further.

Note that such issue is also often seen with buggy extension(s); so deactivate it (them) via the tweaks tool, or purge it (them) and restart the session to find/know about the faulty extension..

When the problem occurs the system freezes completely. I cant even launch the terminal. How do I look at journal -b output ?
I don't think this is due to a faulty extension because the freezes occur with both Firefox & Chrome. In case of Chrome I haven't installed any addon. 

> **dinkidonk said:**
> Looking through the SMART data I've spotted some concerns:

[sda]
197 Current Pending Sector = 2
198 Offline Uncorrectable = 2

The drive has bad sectors waiting to be remapped, this indicates that  the drive is about to fail. This should not cause system lockups, but  try to disconnect the drive from the computer and see if that does a  difference.


[sdb]
235 POR Recovery Count = 211

The drive has recovered from sudden power loss 211 times. When a SSD  suffers a power loss, data may become dirty and this causes the drives  internal firmware to start a recovery procedure on the next power on to  regain the mapping of the user data and this may cause the drive to  become slow or unresponsive. Even after recovery, data on the drive (eg.  the file system) may be corrupted which can cause all sorts of trouble.  You should find out why this number is so high and what causes it to  increase. A bad power cable or the use of hibernation could be possible  causes.


I tried disconnecting the sda drive. The freezes still occured. I have no idea why it shows 211 times of sudden power loss. Since I purchased I may have done hard reboot/shutdown 5-6 times max.

> **jay-eich said:**
> Hi there,

My sincere sympathies..
I have a few more debug suggesions.
 
  If you have another system on a 'live' USB, boot it and run fsck on both sda and sdb
  (( I alive system is needed so thet the usual systems on sda and sdb are not mounted.))

I agree that another choice is to try to set your home page in firefox to about:blank ar a static html page that you created and use the file:///somewhere/my.html  as home page.

By 'freeze', how long do you wait? Is there a CPU activitity light? I  have had to wait several minutes on an old -i86 system with about 500Meg  of memory. It worked for me.(after much debug)

( I also unstalled/purged firefox and reinstalled to get rid of add-ons.  After purge, double-check .mozill to be sure all firefox is removed)

Try installing and running gkrellm ( a reference to the movie "Forbidden  Planet"). Be sure The memory and swap indicators are configured. Start  it up before you start Firefox, then watch it as you start firefox.  Start firefox on a command line so you can <ctl-c> it to stop and  see any more error messgaes that pop out.

On my small system (laptop), I was stuck - couldn't add memory. In my  desktop, I added a lot of memory - then swap is  not needed. as:
  $swapon
NAME      TYPE      SIZE USED PRIO
/dev/sdb4 partition 9.3G   0B   -2

I do hope this is helpful.
Coffee helps.
To a point, beer also works for me.

Cheers!!
Jay

edited: fixed typo . addred firefox purge stuff.


At first I suspected the spinning HDD was causing the freezes so I booted from a live media & used Gparted to check both sda & sbd. In both cases no errors were found.

Its been 4 days since the last freeze. Its so sudden & unexpected its becoming very difficult to troubleshoot.

---

### Post by dinkidonk on 2020-12-30
> **linuxyogi said:**
> I have no idea why it shows 211 times of sudden power loss. Since I purchased I may have done hard reboot/shutdown 5-6 times max.

I suggest that you every once in a while check up on that tally, if it rises for no apparent reason there might be a problem there. I would try to use another power cable for the drive right away, though.

---


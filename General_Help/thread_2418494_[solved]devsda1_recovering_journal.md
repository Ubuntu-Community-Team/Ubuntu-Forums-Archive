---
title: "[solved]/dev/sda1: recovering journal"
date: 2019-05-07
forum: General Help
---

### Post by missmoondog on 2019-05-07
i keep getting the error /dev/sda1: recovering journal and then it says clean after that but then computer goes through the boot process a second time after which i get the advanced boot option. i just go to the ubuntu option and computer starts correctly. seems like this started happening after last kernel update. everything seems to run fine once i get logged in. this is on lubuntu 18.04.2, i believe is most recent version. only thing i have tried is reinstalling grub, which made no difference. 

anyone have any ideas?

thank you

---

### Post by oldos2er on 2019-05-07
Using ext4? Tried booting into an older kernel? Have you run smartctl on this disk? [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by missmoondog on 2019-05-07
don't know about ext4! using xfce. this is a rather old, single core laptop. will that smartctl even work on it? no, didn't try older kernel as newest one works, just makes it go through boot 2 times, every time. don't use laptop very often either.

---

### Post by oldos2er on 2019-05-07
```
df -T
``` will show which file systems are in use. And yes, smartctl will work.

---

### Post by missmoondog on 2019-05-08
thank you

will give that a try in a few days and get back with you.

---

### Post by missmoondog on 2019-05-18
sorry took so long to get back. had other issues.

yes, file system is ext 4 and running ```
sudo smartctl -t long /dev/sda
``` now. 44 minutes to complete.

---

### Post by missmoondog on 2019-05-19
had to give up on that test above. doubt if i would've known what to do afterwards anyway considering when setting up the tool, i had to enter some info about mail of which i didn't know what to do!

just noticed this morning on my other 32bit machine that it does the same thing as far as starting and restarting twice. in fact, both machines simply quit booting on first try and have to hold power button to get it to resrart then goes through boot precoess twice which brings up boot options. simply hit boot normally and finally get to desktop.

almost inclined to believe this is more of a 32bit bug than any other issue?

---

### Post by oldos2er on 2019-05-19
> **missmoondog said:**
> almost inclined to believe this is more of a 32bit bug than any other issue?

No idea what that means, sorry. Potentially failing hardware doesn't have much if anything to do with bitness. 

Instead of running the long SMART test the short one might suffice for now; it shouldn't take more than a few minutes. You can check this with ```
sudo smartctl -c /dev/sda
``` 

```
sudo smartctl -t short /dev/sda
```

I hope you have good backups of any sensitive data.

---

### Post by missmoondog on 2019-05-19
ok, here's what i get from that short test:
```

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   253   253   033    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0012   099   099   000    Old_age   Always       -       2846
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   086   086   000    Old_age   Always       -       6425
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       2769
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       273
193 Load_Cycle_Count        0x0012   089   089   000    Old_age   Always       -       119590
194 Temperature_Celsius     0x0002   196   196   000    Old_age   Always       -       28 (Min/Max 16/60)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       4
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      6424         -
# 2  Extended offline    Interrupted (host reset)      90%      6424         -

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

### Post by missmoondog on 2019-05-19
this is the results of a long test:
```

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Travelstar 5K160
Device Model:     Hitachi HTS541680J9SA00
Serial Number:    SB2211SGK6E2MB
LU WWN Device Id: 5 000cca 51ced31db
Firmware Version: SB2OC7DP
User Capacity:    80,026,361,856 bytes [80.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA/ATAPI-7 T13/1532D revision 1
Local Time is:    Sun May 19 22:09:16 2019 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

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
data collection: 		(  645) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  44) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   253   253   033    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0012   099   099   000    Old_age   Always       -       2846
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   086   086   000    Old_age   Always       -       6425
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       2769
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       273
193 Load_Cycle_Count        0x0012   089   089   000    Old_age   Always       -       119590
194 Temperature_Celsius     0x0002   148   148   000    Old_age   Always       -       37 (Min/Max 16/60)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       4
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      6425         -
# 2  Extended offline    Completed without error       00%      6425         -
# 3  Short offline       Completed without error       00%      6424         -
# 4  Extended offline    Interrupted (host reset)      90%      6424         -

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

### Post by missmoondog on 2019-05-22
issue has been solved. i installed antix linux and everything is working correctly again. pretty sure it was one of the last couple kernel updates that have messed up my 2, 32bit machines. found a few other topics in other forums that had people having same issue.

---

### Post by quirinovix on 2019-09-08
I have the same problem. 64 bit CPU. I thought it could be the SSD. So i bought a new and bigger one. But got the same error. Fresh install. I do not got the error every time, but must of them. First time, it "freezes". Have to hard reset. So, the grub menu shows 30 seconds to select windows or Ubuntu (ubuntu is default) instead of the usual 10 seconds. Them i get:
/dev/sda3: recovering journal
/dev/sda3: clean xxx/xxxx files, xxx/xxx blocks
and everything goes fine...

Any idea?

---

### Post by guiverc on 2019-09-08
@quirnovix you should probably have started a new thread instead of adding to a solved thread.

If it freezes and you hard reset (and not use [magic] sysrq keys to tell kernel to reboot; reisub for example) then the `fsck` messages are a result of the hard-reset and expected (to ensure the unclean shutdown didn't do damage).  Your issue is no the `fsck` messages, but whatever is causing you to "hard reset"  (and use magic-sysrq keys instead of hard-reset; though if they aren't working it's useful information if you chase down your 'freeze' issue.

---

### Post by quirinovix on 2019-09-09
You're right. There is the [solved] tag and i didn't notice it. I understood there is no solution since the "solution" was to change to Antix.
I'm having this problem for some time. As i told, i thought it was my SSD and now a realized it's not. I will be sure next time, but i believe sysrq, ctrl+alt+del, and everything else did not work. I never got video at all when it freezes. But i will be sure as soon it freezes again.

---


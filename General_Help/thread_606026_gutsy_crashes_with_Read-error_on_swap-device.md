---
title: "gutsy crashes with Read-error on swap-device"
date: 2007-11-07
forum: General Help
---

### Post by sammael666 on 2007-11-07
i usually leave my box on for a week or so it never crashed with feisty. i did a clean install of gutsy, i like it, its faster and everything, but this thing occured two times now. when i come home from work, screen is on, but blank and system do not response to keyboard or mouse. num/caps lock don't work.

i am able to do alt+sysrq+k, then ctrl+alt+f1 to get to prompt, but as soon as i try to type in name and passwd, this error mesage comes up several times. after that i can only reboot.

Read-error on swap-device [some number:some other number]
Read-error on swap-device [some number:some other number]

i use only official repositories and while this happens these things are active: Google Desktop, azureus, boinc,apache2,vsftpd,gnump3d,pidgin,checkgmail, maybe one swiftfox.

i googled a bit and someone somewhere suggested i might have a bad sector on my swap disk and should do mkswap -c /dev/my_swap_partition. i did that and it reported no errors just my swap UUID.

if anybody has any suggestion i'll be most grateful as i am REALLY not in mood to do another clean install in so short time.

if i should post any logs or something let me know i'll post them.

---

### Post by antmenj on 2007-11-08
Hard disk on the way out??

Just a thought if you leave it on all week.
[I]
If I had a doller for ever time I'v been told "it was working proberly before it played up"....[/I]

---

### Post by sammael666 on 2007-11-08
that's what i thought , but i run smartctl -all /dev/sda and see no alarming info. besides i checked the swap partition, heck i even booted from live cd and checked whole hdd and no errors reported.

output of smartctl -all /dev/sda
```
sammael@high-flyer:~$ sudo smartctl --all /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.9 family
Device Model:     ST3160212AS
Serial Number:    4LS52GP0
Firmware Version: 3.AAE
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Nov  8 10:16:58 2007 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

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
  1 Raw_Read_Error_Rate     0x000f   079   072   006    Pre-fail  Always       -       11486673
  3 Spin_Up_Time            0x0003   095   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       168
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   077   060   030    Pre-fail  Always       -       58547078
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1154
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       259
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   098   098   000    Old_age   Always       -       2
190 Temperature_Celsius     0x0022   063   038   045    Old_age   Always   In_the_past 623116325
194 Temperature_Celsius     0x0022   037   062   000    Old_age   Always       -       37 (Lifetime Min/Max 0/13)
195 Hardware_ECC_Recovered  0x001a   048   046   000    Old_age   Always       -       139136086
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1154         -

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

i am really lost here. i'll probably make up some space on my other disk and make swap partition there to see if it makes a difference
for a while i suspected azureus as the crash didn't occur while azureus wasn't running (so far)


EDIT* i also ran extended offline test of disk when i went to work at noon, here is the result, so i don't think hw error is the issue. please don't prove me wrong :D
```

Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1156         -
```

---

### Post by frankabel on 2007-12-18
I have this error in a server...all seen work fine, just get that error 

```
"[  123.657443] Read-error on swap-device (9:3:8)"
```

when the server boot. I'm using gutsy server and have raid1 software as swap partition.

top say 0k of swap.

Salute
Frank Abel

---


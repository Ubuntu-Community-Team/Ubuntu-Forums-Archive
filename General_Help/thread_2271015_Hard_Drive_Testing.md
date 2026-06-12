---
title: "Hard Drive Testing"
date: 2015-03-26
forum: General Help
---

### Post by RogerDavis on 2015-03-26
Which of the following can I use on a mounted system hard drive (like in use right now) without risk of damaging it?


badblocks


fsck (command variations to check only?)  
What kind of tricks do I need to do to use this with a live CD to actually fix any bad blocks?


Is the drive automatically checked by fsck on startup and restarts?


Smart (drive firmware) - how to see this?  
Especially, how to see:
SMART ID 187 (0xBB): Reported Uncorrectable Errors
SMART ID 188 (0xBC): Command Timeout


Any other ways?

---

### Post by TheFu on 2015-03-27
Don't know how to do stuff on mounted file systems, except read SMART data, but that is next to useless for 1 reading.  Capture SMART data weekly, over time, and compare the results.  There's a **smartctl** package. Put it into a crontab to run weekly and store the output somewhere. Might want to use meld/compare to check for differences between runs.  There is usually a SMART toggle in the BIOS. Enable it.


fsck runs at periodic intervals, not every reboot. I think every 30 reboots or 60 days, but don't believe me. This is tunable in the file system parameters. **tune2fs** was the old name of the program. Look for something similar.  You can force an fsck at boot for / by creating a /forcefsck file. For all other partitions, you'll need to umount the partition and manually run it. Probably best to switch to single-user mode which should shutdown most services.

There are not any tricks.  Check the manpage for any command you want to use. Read it carefully to avoid doing something that causes data loss. If you ask Linux to do something stupid and it does it, who's fault is it?  Yours.  

**hdparm** is another tool. It has safe and dangerous modes. Check the manpage.

Or ... you can boot almost any liveCD and run all these commands safely on unmounted ext2/3/4 partitions. Things are a little different for RAID stuff.  I run RAID scrubbing weekly on each software RAID array here. The root crontab:```

12 6 * * 3 echo check > /sys/block/md1/md/sync_action
```
Takes a few hrs to run, depending on other file system use at the time.

---

### Post by Mark Phelps on 2015-03-27
> to actually fix any bad blocks?Sorry, but this is a hardware problem and can't be fixed with software.

When blocks are considered bad, the disk controller moves the content to a spare block and marks the bad block as unusable.

If an app is claiming to "fix" bad blocks, it's actually doing the same as above.

---

### Post by TheFu on 2015-03-27
IME, sometimes blocks marked as bad are just lazy bytes that need to be refreshed. The badblocks tool can refresh bytes, but not when online.  badblocks can also force drive firmware to see that a block is bad and relocate it to available spare block areas until those are used up.

If a disk is failing - heavy usage can cause more failures, so be certain you already have a know-you-can-restore backup before starting. It is best to have versioned backups BEFORE the data is lost. If you don't already do that, use ddrescue to mirror the disk ASAP - offline when doing this.

---

### Post by RogerDavis on 2015-03-28
1) Found I can use GSmartControl to access "Extended Self Test", safe to user data, to test the drive.  Total time is to be 2 hrs, 47 minutes, now about 2.5 hours to go.  Any comments on usefulness of this test?  I figure since it is probably very low level, and user data safe, it might be my best option even over fsck.  All the basic tests say the drive is fine.

2) Since Harry Potter chants make me nervous, especially where the health of my system depends on my total error-free-ness, I wonder if there is a ISO disk image that has a CLEAR menu, like "Disk Information", "Recover Files", "Check Disk Only", "Repair Disk", Wipe Disk ... other useful utilites...  Burn to CD, boot from CD, perform the tasks, simple, clean, done, no fumble-finger worries.

SMART DATA: (Before extended test completion)
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Black
Device Model:     WDC WD1002FAEX-00Y9A0
Serial Number:    WD-WCAW33728906
LU WWN Device Id: 5 0014ee 2b1b0a4d0
Firmware Version: 05.01D05
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sat Mar 28 14:01:09 2015 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(16200) seconds.
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
recommended polling time: 	 ( 167) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x3035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       4
  3 Spin_Up_Time            0x0027   174   171   021    Pre-fail  Always       -       4258
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1285
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       5649
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1275
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       166
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1118
194 Temperature_Celsius     0x0022   104   098   000    Old_age   Always       -       43
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Conveyance offline  Completed without error       00%      5643         -
# 2  Short offline       Completed without error       00%      5642         -
# 3  Short offline       Completed without error       00%       242         -

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

2) Since Harry Potter chants make me nervous, especially where the health of my system depends on my total error-free-ness, I wonder if there is a ISO disk image that has a CLEAR menu, like "Disk Information", "Recover Files", "Check Disk Only", "Repair Disk", Wipe Disk ... other useful utilites...  Burn to CD, boot from CD, perform the tasks, simple, clean, done, no fumble-finger worries.

---

### Post by RogerDavis on 2015-03-28
1) Found I can use GSmartControl to access "Extended Self Test", safe to user data, to test the drive.  Total time is to be 2 hrs, 47 minutes, now about 2.5 hours to go.  Any comments on usefulness of this test?  I figure since it is probably very low level, and user data safe, it might be my best option even over fsck.

2) Since Harry Potter chants make me nervous, especially where the health of my system depends on my total error-free-ness, I wonder if there is a ISO disk image that has a CLEAR menu, like "Disk Information", "Recover Files", "Check Disk Only", "Repair Disk", Wipe Disk ... other useful utilites...  Burn to CD, boot from CD, perform the tasks, simple, clean, done, no fumble-finger worries.

---

### Post by RogerDavis on 2015-03-28
Update - SmartDisk, extended self-test, completed without error.

---

### Post by dcstar on 2015-04-05
```
e2fsck -c
```

       -c     This option causes e2fsck to use badblocks(8) program  to  do  a
              read-only  scan  of  the device in order to find any bad blocks.
              If any bad blocks are found, they are added  to  the  bad  block
              inode  to  prevent them from being allocated to a file or direc&#8208;
              tory.  If this option is specified twice,  then  the  bad  block
              scan will be done using a non-destructive read-write test.

---

### Post by RogerDavis on 2015-04-05
By "twice" do you mean

e2fsck -c
e2fsck -c

or 

e2fsck -c -c

Whichever is correct, will it also notify me of any  problems found?

Thanks!

---


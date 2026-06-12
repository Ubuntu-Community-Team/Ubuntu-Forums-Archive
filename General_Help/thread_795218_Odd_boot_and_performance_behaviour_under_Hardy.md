---
title: "Odd boot and performance behaviour under Hardy"
date: 2008-05-15
forum: General Help
---

### Post by engstrom on 2008-05-15
I recently did a clean install of Hardy on my laptop and it's now exhibiting some strange behaviour. 

It would occasionally take up to 30-40 mins to boot up (continual hdd activity) for a few attempts then settle down to around 5 mins.

I got a message a few times while booting that the volume had been mounted 28 times without checking so FSCK would check the drive (no errors reported)

Extended hard disk activity - sometimes it can take 5 mins from login to actually get onto the desktop (I've disabled/removed Tracker from the default Session to no avail).

After removing Firefox Beta 3 I was unable to install add-ons etc. to the replacement Firefox 2. I cured this by deleting the extensions.rdf file but starting the browser again results in serious disk-thrashing for up to 5 mins.

The laptop froze in screensaver mode and I had to power down and reboot. For the next hour or so when booting I was presented with a message saying "[70.9765] Critical temperature reached [105c] Shutting down" or similar. The laptop wouldn't actually shut down but instead the initial number would increment by 10-15 and repeat the message. This would go on indefinitely until I powered down again.

After about an hour of this it would boot up and display the boot log as it booted (it never usually did this) and then start displaying the critical temp. message but still not turn off. After a while (i.e. several fruitless boots later)I noticed that a lot of the booting messages had errors saying that the drive was read-only.

After a while the boot-sequence would return to normal i.e. the ubuntu progress bar would show but it would get so far then seemingly go into power down mode then swtich off with out ever booting. Oddly enough I had a similar problem with XP. It would almost boot up and at the last moment prior to logging on it would give an error message about a certain file and power down. This was a known problem about a particular security file being corrupt. The remedy that worked involved removing the battery and at the right time (just before the error popped up) and pulling the power lead out, XP would then boot normally for a few weeks whereupon it would start happening again. After about 30 mins of the ubuntu laptop doing a similar thing in my frustration I took the battery out, yanked the power just before it would crash and...it worked next time I booted (albeit with assorted disk thrashing and slow firefox starting)

Is my hdd knackered or does it sound like the hardware of the laptop playing up?

Is there anyway to check the integrity of the ubuntu install?
What should I use to check the hdd?
I used the package manager to remove the firefox beta 3 but it still left some items behind (causing the firefox add-on install problem). What is the correct way to make sure it's all gone?

---

### Post by bingoUV on 2008-05-15
1. Hard disk health : Run the following and post the result here to diagnose. Replace sdX by the hard disk device (most likely sda)
```

sudo smartctl -a /dev/sdX

```

Bad blocks : 
```

sudo badblocks /dev/sdX

```

2. Temperature : Is it hot at your place? A large part of Norther Hemisphere is boiling at this time so could be. Does the laptop have a reputation of getting heated? Hardware details would be helpful. P4 / Pentium-D processor? Nvidia 6 series graphics?

3. Firefox : create a new profile to get rid of remnants of last install (FF3b5). From a terminal, 
```

firefox -ProfileManager

```
Here, create new profile, make it default.

---

### Post by engstrom on 2008-05-15
"2. Temperature : Is it hot at your place? "

Not at all.I left the laptop off for a while and then rebooted. It didn't even feel warm to the touch.
It's an AMD64 (don't recall the speed offhand)
I'll try the other suggestions though, thanks.

Update - Results from smartctl
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Fujitsu MHV series
Device Model:     FUJITSU MHV2100AT
Serial Number:    NSC8T6125W9F
Firmware Version: 000000A0
User Capacity:    100,030,242,816 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 4a
Local Time is:    Thu May 15 22:11:26 2008 BST
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
data collection: 		 ( 694) seconds.
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
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  88) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   091   058   046    Pre-fail  Always       -       8590056507
  2 Throughput_Performance  0x0005   100   100   030    Pre-fail  Offline      -       35717120
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1577
  5 Reallocated_Sector_Ct   0x0033   087   087   024    Pre-fail  Always       -       7249925243267
  7 Seek_Error_Rate         0x000f   100   100   047    Pre-fail  Always       -       1092
  8 Seek_Time_Performance   0x0005   100   100   019    Pre-fail  Offline      -       0
  9 Power_On_Seconds        0x0032   091   091   000    Old_age   Always       -       4540h+21m+48s
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1565
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       35
193 Load_Cycle_Count        0x0032   097   097   000    Old_age   Always       -       62999
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       42 (Lifetime Min/Max 16/59)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       8225
196 Reallocated_Event_Count 0x0032   087   087   000    Old_age   Always       -       9005302147
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   097   097   000    Old_age   Offline      -       7
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000f   100   100   060    Pre-fail  Always       -       6119
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       3728085417322

SMART Error Log Version: 1
No Errors Logged

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

---

### Post by engstrom on 2008-05-16
Should the "badblocks" command take any great length of time? When I tried it the terminal sat there with no output for over 45 mins and the hd light on constantly.

Also running the firefox command results in outout saying firefox 3 not installed and I should install it!

---

### Post by bingoUV on 2008-05-16
Yes, badblocks takes quite a lot of time. It is OK. I once badblocked a 500GB IDE hard disk and it took about 8 hours.

Firefox : You have installed firefox 2? Maybe its executable is not /usr/bin/firefox but something else. Can you check the properties of the launcher of firefox (panel's web browser icon -> right click -> Properties -> command). Use that instead of "firefox" in the command I mentioned.

---

### Post by bingoUV on 2008-05-16
Hard disk seems to be healthy enough. 


Note that smart does not catch all errors, but if it says the disk is not healthy(not in your case) then it is definitely going to die soon.

---


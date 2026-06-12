---
title: "Reboot mount '/' read only failed message"
date: 2020-05-10
forum: General Help
---

### Post by usndmac on 2020-05-10
I have a laptop with 19.10.

When I reboot I see the message mount failed '/' read only.

I don't see it when booting from power off state, only during reboot.

It doesn't seem to cause any issues and does not show in output from dmesg.

Just my other machines running 19.10 don't seem to see the same message.

Suggestions or fixes?

Thanks.

---

### Post by TheFu on 2020-05-10
I'd check the SSD for faults and failures.  Use the SMART data.  I think gnome-disks has a few that will show SMART data, though it doesn't show the raw numbers, which is what I need to determine any issues.  **smartctl** is the CLI command I'd use.

When SSDs are failing, it is common for the storage to flip to read-only mode.  I've seen this twice just before failures.

---

### Post by usndmac on 2020-05-11
smartctl shows no errors/issues.

badblocks all good.

---

### Post by TheFu on 2020-05-11
> **usndmac said:**
> smartctl shows no errors/issues.

badblocks all good.

How confident are you?  You can just say "it shows no errors" and we believe you, but wouldn't showing the data get more eyes on the data to see something you may have missed?  At this point, I cannot suggest anything else.

SMART provides early failure data only 78% of the time according to Backblaze reports.

---

### Post by usndmac on 2020-05-12
You're right of course...

```

smartctl 7.0 2018-12-30 r4883 [x86_64-linux-5.3.0-51-lowlatency] (local build)
Copyright (C) 2002-18, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Marvell based SanDisk SSDs
Device Model:     SanDisk SD8SN8U256G1122
Serial Number:    162025803650
LU WWN Device Id: 5 001b44 8b44ae5dc
Firmware Version: X4120000
User Capacity:    256,060,514,304 bytes [256 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Form Factor:      M.2
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.2, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Tue May 12 15:13:10 2020 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x11) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    No Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  10) minutes.

SMART Attributes Data Structure revision number: 4
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0032   100   100   ---    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   ---    Old_age   Always       -       5424
 12 Power_Cycle_Count       0x0032   100   100   ---    Old_age   Always       -       1148
165 Total_Write/Erase_Count 0x0032   100   100   ---    Old_age   Always       -       103126008422
166 Min_W/E_Cycle           0x0032   100   100   ---    Old_age   Always       -       2
167 Min_Bad_Block/Die       0x0032   100   100   ---    Old_age   Always       -       44
168 Maximum_Erase_Cycle     0x0032   100   100   ---    Old_age   Always       -       12
169 Total_Bad_Block         0x0032   100   100   ---    Old_age   Always       -       513
170 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       0
171 Program_Fail_Count      0x0032   100   100   ---    Old_age   Always       -       0
172 Erase_Fail_Count        0x0032   100   100   ---    Old_age   Always       -       0
173 Avg_Write/Erase_Count   0x0032   100   100   ---    Old_age   Always       -       5
174 Unexpect_Power_Loss_Ct  0x0032   100   100   ---    Old_age   Always       -       43
184 End-to-End_Error        0x0032   100   100   ---    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   ---    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   ---    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   064   064   ---    Old_age   Always       -       36 (Min/Max 4/64)
199 SATA_CRC_Error          0x0032   100   100   ---    Old_age   Always       -       0
230 Perc_Write/Erase_Count  0x0032   100   100   ---    Old_age   Always       -       1421638828363
232 Perc_Avail_Resrvd_Space 0x0033   100   100   004    Pre-fail  Always       -       100
233 Total_NAND_Writes_GiB   0x0032   100   100   ---    Old_age   Always       -       1437
234 Perc_Write/Erase_Ct_BC  0x0032   100   100   ---    Old_age   Always       -       2955
241 Total_Writes_GiB        0x0030   253   253   ---    Old_age   Offline      -       2426
242 Total_Reads_GiB         0x0030   253   253   ---    Old_age   Offline      -       2853
244 Thermal_Throttle        0x0032   000   100   ---    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      5418         -

Selective Self-tests/Logging not supported

```

---

### Post by TheFu on 2020-05-12
Have you run an fsck on the partition file system yet?  To do that, looks like you'll need to boot and at the grub menu, choose "Advanced ... something".  Then a menu will be shown and run fsck on all disks is an option.  Try that.  

Unexpected power loss often leaves file systems with inconsistent states.  An fsck should clean that up - losing whatever storage writes weren't complete when the power was removed.

So, I'd look at the non-zero "raw values" and do some google research on those to be certain I understood what they meant. These are the ones I'd look up first:

```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
167 Min_Bad_Block/Die       0x0032   100   100   ---    Old_age   Always       -       44
169 Total_Bad_Block         0x0032   100   100   ---    Old_age   Always       -       513
174 Unexpect_Power_Loss_Ct  0x0032   100   100   ---    Old_age   Always       -       43
230 Perc_Write/Erase_Count  0x0032   100   100   ---    Old_age   Always       -       1421638828363
232 Perc_Avail_Resrvd_Space 0x0033   100   100   004    Pre-fail  Always       -       100
233 Total_NAND_Writes_GiB   0x0032   100   100   ---    Old_age   Always       -       1437
234 Perc_Write/Erase_Ct_BC  0x0032   100   100   ---    Old_age   Always       -       2955
241 Total_Writes_GiB        0x0030   253   253   ---    Old_age   Offline      -       2426

```

I don't have any SanDisk SSDs, so many of the numbers and characteristic descriptions above aren't something I've seen previously.

513 bad blocks?  Seems high.  Any number over 0 means I'd replace the storage.
43 unexpected power loss counts?  Get a UPS. 1 is too many.

#230 needs to be calculated using the block size to check the TBW specs for the device. Guessing that #234 is the vendor claimed TBW number, but I've not seen these before.  My SSDs (Micro and Samsung) just provide the blocks written/erased using #246 .  Looked up the specs earlier today and on my VM server (really just a Ryzen desktop), the warranty is for 340 TBW.  Currently at about 4.5 TBW after 16 months of use.  I keep only OSes and servers that don't really have much "write" to them on the SSD.  For video stuff, I keep all that on the spinning rust.

Be aware that the lines below just mean the test worked. It isn't any statement about the status of the SSD:
```
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      5418         -
```

---

### Post by usndmac on 2020-05-13
Hmm...

Was able to see more of the error, by chance, as it flew by.

After the reboot is issued, as it's shutting down:

Failed to remount '/' Resource or device busy 

Then after grub counts down and starts to load the kernel, it shows a message that says clean and mounts.

That said, the SSD is several years old, so, that it may need to be replaced is not surprising.

As for the power losses. It's a laptop. I've never seen any indication of battery issues. So, I'm not sure what that indicates.

---

### Post by TheFu on 2020-05-13
Just redirect the output to a file.

```
sudo smartctl -a /dev/sda | tee /tmp/smart.data
```

Redirection is our friend.

---

### Post by usndmac on 2020-05-13
Umm...what does redirecting the smartctl on the command line have to do with information that flashes during shutdown/boot?

Not trying to be funny or anything...I just don't get it. :confused:

---

### Post by ActionParsnip on 2020-05-13
You could run an fsck from Ubuntu Live CD (Or similar) to make sure the file system is consistent

---

### Post by TheFu on 2020-05-13
> **usndmac said:**
> Umm...what does redirecting the smartctl on the command line have to do with information that flashes during shutdown/boot?

Not trying to be funny or anything...I just don't get it. :confused:

Excellent point.  I've been jumping between a few different threads today and got confused.

To see messages boot and otherwise, use journalctl.

To see the messages from 2 boots ago, use **journalctl -b2  **
To see errors, use **journalctl -p err**
journalctl has a built-in regex matching capability which can be handy.  Also can filter based on start-end times.  It is pretty powerful. The manpage for it hopefully describes all the options.

If there aren't a few boots available, it is likely the system isn't saving the boot data between boots. There's a way to enable that in the /etc/systemd/journald.conf  There's a manpage for that config file.

---

### Post by usndmac on 2020-05-15
the journal never shows the error I see flash by.

---


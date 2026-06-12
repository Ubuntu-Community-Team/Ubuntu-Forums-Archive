---
title: "Help systemd journald 464"
date: 2018-10-06
forum: General Help
---

### Post by Chrismallia on 2018-10-06
Hi guys 

I am new to ubuntu server just replaced windows server with Ubuntu and ZFS so please be gentle :)). I am getting a problem sometimes my ubuntu server 18.04 will have some services like plex stop responding then I ssh and some commands do not work like sudo reboot, so I plug in a monitor and get logs like this, could anyone help me find out whats going on? 

[ATTACH=CONFIG]281269[/ATTACH]

---

### Post by TheFu on 2018-10-06
Storage is about to fail.  Backup anything you dont want to lose.
Run smartctl on the disk and see how bad it is.

---

### Post by Chrismallia on 2018-10-06
> **TheFu said:**
> Storage is about to fail. Backup anything you dont want to lose.
Run smartctl on the disk and see how bad it is.

wow thanks for that I will run smartctl, This is a new Kingston 120GB ssd maybe 4months used as the main drive in this server did not expect it to fail so quickly

---

### Post by Chrismallia on 2018-10-06
This is the result. does not look bad right?

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 0
Warning: ATA Specification requires self-test log structure revision number = 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      2141         -
# 2  Extended offline    Interrupted (host reset)      80%       204         -

---

### Post by Chrismallia on 2018-10-06
```
=== START OF INFORMATION SECTION ===
Device Model: KINGSTON SUV400S37120G
Serial Number: 50026B777C01BE5C
LU WWN Device Id: 5 0026b7 77c01be5c
Firmware Version: 0C3J96R9
User Capacity: 120,034,123,776 bytes [120 GB]
Sector Sizes: 512 bytes logical, 4096 bytes physical
Rotation Rate: Solid State Device
Form Factor: M.2
Device is: Not in smartctl database [for details use: -P showall]
ATA Version is: Unknown(0x0ffe), ATA8-ACS T13/1699-D revision 6
SATA Version is: SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is: Sat Oct 6 23:16:07 2018 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status: (0x00) Offline data collection activity
was never started.
Auto Offline Data Collection: Disabled.
Self-test execution status: ( 0) The previous self-test routine completed
without error or no self-test has ever
been run.
Total time to complete Offline
data collection: ( 5) seconds.
Offline data collection
capabilities: (0x71) SMART execute Offline immediate.
No Auto Offline data collection support.
Suspend Offline collection upon new
command.
No Offline surface scan supported.
Self-test supported.
Conveyance Self-test supported.
Selective Self-test supported.
SMART capabilities: (0x0003) Saves SMART data before entering
power-saving mode.
Supports SMART auto save timer.
Error logging capability: (0x01) Error logging supported.
General Purpose Logging supported.
Short self-test routine
recommended polling time: ( 2) minutes.
Extended self-test routine
recommended polling time: ( 5) minutes.
Conveyance self-test routine
recommended polling time: ( 0) minutes.
SCT capabilities: (0x003d) SCT Status supported.
SCT Error Recovery Control supported.
SCT Feature Control supported.
SCT Data Table supported.


SMART Attributes Data Structure revision number: 48
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME FLAG VALUE WORST THRESH TYPE UPDATED WHEN_ FAILED RAW_VALUE
1 Raw_Read_Error_Rate 0x002f 100 100 000 Pre-fail Always - 0
5 Reallocated_Sector_Ct 0x0033 100 100 010 Pre-fail Always - 0
9 Power_On_Hours 0x0032 100 100 000 Old_age Always - 2141
12 Power_Cycle_Count 0x0032 100 100 000 Old_age Always - 129
100 Unknown_Attribute 0x0032 100 100 000 Old_age Always - 889216
101 Unknown_Attribute 0x0032 100 100 000 Old_age Always - 155920
170 Unknown_Attribute 0x0032 100 100 000 Old_age Always - 0
171 Unknown_Attribute 0x0032 100 100 000 Old_age Always - 0
172 Unknown_Attribute 0x0032 100 100 000 Old_age Always - 0
174 Unknown_Attribute 0x0032 100 100 000 Old_age Always - 27
175 Program_Fail_Count_Chip 0x0032 100 100 000 Old_age Always - 0
176 Erase_Fail_Count_Chip 0x0032 100 100 000 Old_age Always - 0
177 Wear_Leveling_Count 0x0032 099 099 000 Old_age Always - 524
178 Used_Rsvd_Blk_Cnt_Chip 0x0002 100 100 000 Old_age Always - 0
180 Unused_Rsvd_Blk_Cnt_Tot 0x0002 100 100 000 Old_age Always - 601
183 Runtime_Bad_Block 0x0032 099 099 000 Old_age Always - 7
187 Reported_Uncorrect 0x0033 100 100 000 Pre-fail Always - 0
194 Temperature_Celsius 0x0022 029 100 000 Old_age Always - 29 (Min/Max 17/41)
195 Hardware_ECC_Recovered 0x0032 100 100 000 Old_age Always - 0
196 Reallocated_Event_Count 0x0032 100 100 000 Old_age Always - 0
197 Current_Pending_Sector 0x0032 100 100 000 Old_age Always - 0
199 UDMA_CRC_Error_Count 0x0012 100 100 000 Old_age Always - 0
201 Unknown_SSD_Attribute 0x0032 100 100 000 Old_age Always - 0
204 Soft_ECC_Correction 0x0032 100 100 000 Old_age Always - 0
231 Temperature_Celsius 0x0032 099 099 000 Old_age Always - 1
233 Media_Wearout_Indicator 0x0032 100 100 000 Old_age Always - 1521
234 Unknown_Attribute 0x0032 100 100 000 Old_age Always - 881
241 Total_LBAs_Written 0x0032 100 100 000 Old_age Always - 1151
242 Total_LBAs_Read 0x0032 100 100 000 Old_age Always - 561
250 Read_Error_Retry_Rate 0x0032 100 100 000 Old_age Always - 0


SMART Error Log Version: 0
No Errors Logged


SMART Self-test log structure revision number 0
Warning: ATA Specification requires self-test log structure revision number = 1
Num Test_Description Status Remaining LifeTime(hours) LBA _of_first_error
# 1 Extended offline Completed without error 00% 2141 -
# 2 Extended offline Interrupted (host reset) 80% 204 -


SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been ru n
SPAN MIN_LBA MAX_LBA CURRENT_TEST_STATUS
1 0 0 Not_testing
2 0 0 Not_testing
3 0 0 Not_testing
4 0 0 Not_testing
5 0 0 Not_testing
Selective self-test flags (0x0):
After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by Chrismallia on 2018-10-06
So could it still be the drive failing?

---

### Post by TheFu on 2018-10-06
Please edit the posts to use _code tags,_ so the output lines up. Too hard to read as posted.
Could be a bad cable or bad controller too.

Im confused. Why use ZFS if there is only 1 disk?  ZFS isnt a supported config for Ubuntu on anything except data partitions. It isnt supported for boot or the OS.

---

### Post by Chrismallia on 2018-10-06
Sorry, I was not clear, I am not using ZFS on the rood drive, I have a 24TB pool using ZFS on this server. how do I do the code tag thing never did that? sorry again. 
btw a few weeks ago I got something like I/O Error  I replaced the sata cable already but now this happened

---

### Post by Chrismallia on 2018-10-06
Well I left the monitor plugged in also replaced cable and plugged the ssd into my lsi card to rule out the mainboard controller, then I wrote a large file from my pool  to the ssd and got this,

[ATTACH=CONFIG]281271[/ATTACH]

---

### Post by Chrismallia on 2018-10-06
[ATTACH=CONFIG]281272[/ATTACH]
zpool looks fine, so could the ssd be failing with no smart error?

---

### Post by TheFu on 2018-10-07
```
183 Runtime_Bad_Block 0x0032 099 099 000 Old_age Always - 7
```
I would research that number for what it means.

All disks can fail without warning.  SMART is helpful, but something like 22% of storage failures show no accepted SMART errors.

Had an SSD fail on me after 3 yrs. For 6 months prior, it kept switching to read-only mode first. Always have daily, automatic, backups that you know you can restore.  The easy test is to replace the problem disk and see if the problem stops.  If it doesnt, then the problem is up the HW chain somewhere.

Or it could be a driver issue.

Instead of posting images, please use the log files as text.  Be kind to people paying by the bit in these forums.

---

### Post by Chrismallia on 2018-10-08
Thanks, dude for all your help.

I replaced the Kingston SSD with a Samsung EvO and till this time of writing the problem has gone, I wrote multiple large files to the SSD and it did not have the same problem, sorry for the pcs as the server was plugged  into a monitor and did not know if I can get the logs so I took a pic of the screen

---

### Post by TheFu on 2018-10-08
**dmesg** has most of the HW logs.
You can also ask **journalctl** for boot logs or logs from a specific daemon or level ... assuming the system is 16.04 or later.  All of this can be accessed locally or over ssh from anywhere with access.   journalctl is pretty amazing.  

Boot logs: journalctl -b 
Lots of output modes available (simple, precise,json,pretty).  Pick 10 boots back or yesterday or use a regex to limit the output.

And nobody knows all this stuff. I always have to look up the commands for almost everything around systemd/journalctl still.  25+ yrs of habits don't change quickly.

I would completely fill up any new SSD to ensure it is real and had the capacity expected.  Reputable sellers have been tricked occasionally too.  More of an issue for flash storage, but ...

---

### Post by Chrismallia on 2018-10-08
WOW.
Thank you really for everything,  nice info I still have waayyy to learn but I am really pleased with ubuntu server, coming from a windows environment using the GUI  I really am finding cli faster to do thinks and also using dockers makes the server much more fun, also loving ZFS btw :). Will have a go at the SSD as I really would like to know if I should throw it out or use it for something, will fill it as you suggested and see what happens

---

### Post by Chrismallia on 2018-10-08
Strange I plugged  the SSD on a windows machine formatted and filled it up with large files and it did not give any trouble    confused

---

### Post by TheFu on 2018-10-08
SSDs can fail at any point. Not all SSD controllers are compatible with all drivers.  It is more important with bleeding edge HW if Linux is the target platform.  Most vendors don't try to make Linux drivers, so it is up to some guy who happens to get the same HW AND has the skills AND the desire to make a driver.  
I made a driver for a network card decades ago. Basically, I stole some work from other smart people for a very similar card using the same chips and it worked. ;)   But lots of the newer storage solutions are coming that don't use normal SATA connections or controllers.  A few years ago the NVMe storage didn't work at all on Linux and it took 1-2 yrs for most of that type of hardware to be supported.

With Linux, avoid the bleeding edge, unless you want to make drivers yourself or can use some alternative for 6-18 months.   Always look for Linux issues with any hardware or controller you might be considering BEFORE purchase.  The days of assuming an impulse computer part purchase will just work are over when you leave Windows ecosystem.

---

### Post by Chrismallia on 2018-12-09
Sorry for bringing this up again, This happened again yesterday, now the server has Samsung EVO SSD with Ubuntu fresh install ran fine for nearly 2 months. A question does ram have anything to do with this? I ran memtest86 and got 2 errors.

Thanks again

---


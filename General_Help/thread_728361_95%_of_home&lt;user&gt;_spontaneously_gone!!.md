---
title: "95% of /home/&lt;user&gt; spontaneously gone!!"
date: 2008-03-18
forum: General Help
---

### Post by michurch on 2008-03-18
So two days ago the contents of my /home/<user> showed up on the desktop.  Obnoxious to say the least but I didn't have time to deal with it so I just let it be for the moment.  Today when i logged on, almost all of the contents were gone.  A small folder with a few documents remain but even that folder is not complete.  Many of the hidden config files like my conkyrc are gone but some remain ./wine is still there for example.  My home directory was a dedicated drive that had ~100GB of 300GB of data.  I opened gparted to see what was still on the disk or if it got moved to my other "/" disk.  The /home hard drive only reads 5GB of used space, 292GB free.  What could have caused this and more importantly, how can I get my stuff back? I don't think its a drive failure because it's still mounted and some files remain.   it's formatted as ext3 for whatever thats worth.  Please help!
Mike

---

### Post by sumguy231 on 2008-03-18
You should run the fsck command from recovery mode just to rule out filesystem problems. I hope you had all that stuff backed up somewhere.

---

### Post by HunterK on 2008-03-18
Thats an ironic avatar you have there sumguy231.

---

### Post by sumguy231 on 2008-03-18
I hate to derail this thread, but what's ironic about my avatar, HunterK?

---

### Post by HunterK on 2008-03-19
Sorry as well, for going off topic.  (I really hope you do discover where your data went.)  I just couldn't help chuckle after reading the OP and *then* immediately seeing your avatar.  All I can could think about was him saying "Ha ha!!!"

Ok....thread back on track...all aboard!!

---

### Post by tgalati4 on 2008-03-19
Check your log files in /var/log, especially syslog.  If you had read/write errors then they would show up.  It's possible that your drive had an automatic fsck (due to numerous reboots) and it automatically cleaned up loose blocks, including your data.

A failing power supply or loose power connector on the back of the drive can cause big problems for a file system.  Sometimes these problems are not easily fixable using fsck.

I had a file system fail because of a fan-power connector hooked up to hard drive connector.  The 5V pin was loose and it would cause spontaneous drive shut downs.  The file system was corrupted beyond belief and numerous fsck's repaired it, but a lot of data was lost.  

But I did have a back up.  Ha ha . . .

---

### Post by vahnx on 2008-03-19
> **HunterK said:**
>   I just couldn't help chuckle after reading the OP and then immediately seeing your avatar.  All I can could think about was him saying "Ha ha!!!"

Haha, good catch! 

Yeah that sucks about the data loss. I know in XP, TuneUp Utilities has an un-delete feature. And there are $1000 recovery tools the government and some people use that can recover lost data. I'm not too sure in your case though. And those programs I heard of were only for Windows (and i doubt they'd run in emulation very well).

Best idea is to order an external drive. Like half a year ago I got a 500GB external hard drive for only $129.99 + tax 'n' shipping approx. less than $150 from Dell. Manually back up all of your data (music, video, setups, etc.) to it. Saves a lot of hassle if you need to reformat too.

---

### Post by michurch on 2008-03-19
So after some digging I found an old external with both of the directory backed up (good thing) but I am still missing about two months of stuff.  Not that big of a deal, but I want to be sure that if I rebuild it all it's not going to poof again, also I don't want to over write the drive if I might me able to restore it somehow; is it true you can't undelete on ext3?.  I'll check the mentioned log when I get home from work.  Any other ideas of what might have caused this if not a physical drive error? Is there a log somewhere of any rouge scripts that might have been executed on my system? The / disc appears to be unscathed.  Thanks for the replies.

---

### Post by tgalati4 on 2008-03-19
You can install smartmontools:

>sudo apt-get install smartmontools

Your hard drive has SMART monitoring and the smartd daemon can capture errors providing an early warning.  The types of conditions monitored will capture about 2/3's of drive failures.  The other 1/3 is probably what you will get hit with.

Double check your cables and power connector.  Also check your voltage levels, 5V and 12V.  If they drop during bootup then that could also cause problems.

[https://wiki.ubuntu.com/DiskMonitoring](https://wiki.ubuntu.com/DiskMonitoring)

More information than you want, but this is what smartmontools provides:

tgalati4@minty6:~$ sudo smartctl -a -d ata /dev/sdb
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Raptor family
Device Model:     WDC WD740ADFD-00NLR5
Serial Number:    WD-WMANS1040308
Firmware Version: 21.07QR5
User Capacity:    74,355,769,344 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 published, ANSI INCITS 397-2005
Local Time is:    Wed Mar 19 12:42:39 2008 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84) Offline data collection activity
                                        was suspended by an interrupting command from host.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                 (2391) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  39) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   169   168   021    Pre-fail  Always       -       2591
  4 Start_Stop_Count        0x0032   100   100   040    Old_age   Always       -       238
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       431
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       238
194 Temperature_Celsius     0x0022   106   092   000    Old_age   Always       -       37
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0012   200   200   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

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

### Post by michurch on 2008-03-19
I looked through some of my /var/log files but there was alot of stuff in those, especially syslog, I didn't see anything about any hard drive errors, mostly stuff about my network connection although I don't know my way around those files at all, they may be completely normal.   I don't have  multimeter on hand but baring a loose connection, I can't imagine I'm pushing  the limits on my PSU, I think it's 600W and my system is pretty barebones, my CPU is even underclocked. As for smartmontools: are these errors something to worry about on the alleged "good drive"? will reboot and run fsck in a moment...


sudo smartctl -a -d ata /dev/sdb   ->  (the drive that got trashed)

returned no errors and looked alot like the one you posted above.  However,

sudo smartctl -a -d ata /dev/sda   ->   (my root disk)  had 531 errors.


mike@Churchill-PC:~$ sudo smartctl -a -d ata /dev/sda
smartctl version 5.37 [x86_64-unknown-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Raptor family
Device Model:     WDC WD740GD-00FLA1
Serial Number:     
Firmware Version: 27.08D27
User Capacity:    74,355,769,344 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Mar 19 17:57:31 2008 EDT
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
data collection:                 (1725) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        No General Purpose Logging support.
Short self-test routine 
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  30) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   200   164   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   112   111   021    Pre-fail  Always       -       4916
  4 Start_Stop_Count        0x0032   100   100   040    Old_age   Always       -       151
  5 Reallocated_Sector_Ct   0x0033   173   173   140    Pre-fail  Always       -       432
  7 Seek_Error_Rate         0x000b   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   073   073   000    Old_age   Always       -       20306
 10 Spin_Retry_Count        0x0013   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0013   100   100   051    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       151
194 Temperature_Celsius     0x0022   112   104   000    Old_age   Always       -       38
196 Reallocated_Event_Count 0x0032   192   192   000    Old_age   Always       -       8
197 Current_Pending_Sector  0x0012   162   156   000    Old_age   Always       -       466
198 Offline_Uncorrectable   0x0012   163   156   000    Old_age   Always       -       451
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   166   179   051    Pre-fail  Offline      -       520

SMART Error Log Version: 1
ATA Error Count: 531 (device log contains only the most recent five errors)
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

Error 531 occurred at disk power-on lifetime: 261 hours (10 days + 21 hours)
  When the command that caused the error occurred, the device was doing SMART Offline or Self-test.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f0 bc 23 02 e2  Error: UNC 240 sectors at LBA = 0x020223bc = 33694652

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 f0 b1 23 02 02 00   1d+16:58:12.250  READ DMA
  c8 00 08 a9 23 02 02 00   1d+16:58:12.250  READ DMA
  25 00 10 99 22 02 02 00   1d+16:58:12.250  READ DMA EXT
  c8 00 e8 b1 21 02 02 00   1d+16:58:12.250  READ DMA
  c8 00 08 a9 21 02 02 00   1d+16:58:12.250  READ DMA

Error 530 occurred at disk power-on lifetime: 216 hours (9 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 92 30 02 e2  Error: UNC 7 sectors at LBA = 0x02023092 = 33697938

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 07 92 30 02 02 00      01:09:32.700  READ DMA
  27 00 00 00 00 00 00 00      01:09:32.700  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      01:09:32.700  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 00      01:09:32.700  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      01:09:32.700  READ NATIVE MAX ADDRESS EXT

Error 529 occurred at disk power-on lifetime: 216 hours (9 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  01 51 07 92 30 02 e2  Error: AMNF 7 sectors at LBA = 0x02023092 = 33697938

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 07 92 30 02 02 00      01:09:29.850  READ DMA
  27 00 00 00 00 00 00 00      01:09:29.850  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      01:09:29.850  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 00      01:09:29.850  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      01:09:29.850  READ NATIVE MAX ADDRESS EXT

Error 528 occurred at disk power-on lifetime: 216 hours (9 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 92 30 02 e2  Error: UNC 7 sectors at LBA = 0x02023092 = 33697938

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 07 92 30 02 02 00      01:09:26.850  READ DMA
  27 00 00 00 00 00 00 00      01:09:26.850  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      01:09:26.850  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 00      01:09:26.850  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      01:09:26.850  READ NATIVE MAX ADDRESS EXT

Error 527 occurred at disk power-on lifetime: 216 hours (9 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 07 92 30 02 e2  Error: UNC 7 sectors at LBA = 0x02023092 = 33697938

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 07 92 30 02 02 00      01:09:23.850  READ DMA
  27 00 00 00 00 00 00 00      01:09:23.850  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 00      01:09:23.850  IDENTIFY DEVICE
  ef 03 45 00 00 00 00 00      01:09:23.850  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 00      01:09:23.850  READ NATIVE MAX ADDRESS EXT

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

### Post by michurch on 2008-03-19
ubuntu@ubuntu:~$ sudo fsck  /dev/sdb1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sdb1: clean, 7341/39075840 files, 1741360/78142160 blocks (check in 2 mounts)

when I right click and select properties, this disk says it contains 51 files; is this 7341 files my data or just the hidden files in /home/<user>? I feel like I had closer to 20k files.

---

### Post by tgalati4 on 2008-03-19
Check your /lost+found directory.  If there is stuff in there, then those are files that were not associated with the inodes table and have been dumped there.

Your second drive is an older model Raptor.  They generally have 5-year warranties.  I would replace it, or reseat the cables and watch it.  It looks like DMA, memory, or controller errors as opposed to bad sector errors.  Also, reset the power and data cables.  Sometimes a loose cable will appear to be a hardware error.

---

### Post by The Cog on 2008-03-19
I might well be blowing bubbles, but did your /home live on a separate partition? Could it be that the separate partition isn't mounting for some reason, and you are seeing a home directory on your / partitoin that normally gets mounted over?

Just a hopeful thought.

---

### Post by michurch on 2008-03-19
@The Cog
The entire physical drive was the /home.  It is mounting, and even has a few of its former files still in it.  All my hidden files and 95% of my regular data (music, pics, files, videos etc) are gone. The hidden folders (./) appear to still be at least mostly there as well as their contents.  I suspected it was related to all my files jumping to the desktop a few days before (home became desktop) but don't understand why they would do that in the first place without me changing anything and also why they would then get deleted.  

@tgalati4
nothing in lost+found, and /home was monstrous compared to the rest of the filesystem so I don't think it could be hiding anywhere on the raptor (/).   Is the Idea at this point that my data is toast and I should back-up from my sub-par backup? I've been holding out for a way to miraculously get my recent /home back but I'm starting to think I might be better off forgetting it and stick to figuring out what caused the issue in the first place.

fsck auto-deleting files sounds plausible but wouldn't this have recorded a notice of that either within fsck or smartmontools? All physical connections are tight; both HDDs run off of the same rail from my PSU but that shouldn't matter should it?  Are you confident this was a hardware issue?  I can send the syslog files for the relevant days it if would help, it doesn't mean much to me, and it is very long. 

As for the raptor, I'll watch it to make sure it doesn't accumulate any more errors, but I'm thinking  those errors are older, that drive has seen a lot of OS's although its hard to say when the timestamp rolls over every 50 days.

---

### Post by chrisccoulson on 2008-03-19
Did you make sure to check /home/lost+found instead of /lost+found? There should be a lost+found folder at the root of every partition.

---

### Post by michurch on 2008-03-19
yes, checked both

---

### Post by michurch on 2008-03-19
Update:  
Apparently the reason all my files went to the desktop was because /home/<user>/desktop was one of the first files to get deleted.  This merged /home with the desktop.  I have now fixed this by remapping ./config/user-dirs.dirs.  What this means though, because many of my files appeared on the desktop days before they were deleted; there were multiple instances of deleting going on rather than a total failure in which everything would be wiped out.  This is even more alarming as files could trickle away without me noticing.

---

### Post by tgalati4 on 2008-03-20
I assume that you have your /home disk formatted as ext3.  My theory is that the file system developed a problem--possibly with the /home/user/Desktop directory and remapped all files at that point.  If you remember when this happened, then check the logs during that time period.

smartmontools will only log if you set it up to do so, check the previous links for how to set it up to perform logging.  You have to change a file in /etc/default/smartmontools and add some stuff to /etc/smartd.conf.

So the problem really occurred earlier when your Desktop became flooded with all files.  How did you recover from this situation?  Did you drag and drop files using "cut" and then somehow the operation aborted before finishing?

How full is your root partition?  If you are tight on space, then problems can occur when doing large operations.

Helpful wiki page for what some of those SMART parameters really mean:

[http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology](http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology)

---


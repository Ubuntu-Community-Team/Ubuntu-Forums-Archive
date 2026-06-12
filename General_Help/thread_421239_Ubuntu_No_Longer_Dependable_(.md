---
title: "Ubuntu No Longer Dependable :("
date: 2007-04-24
forum: General Help
---

### Post by currentshades on 2007-04-24
**********  BEFORE READING: Note that this problem is related to Windows hibernation, how it handles the shared drive, and hardware issues.  If you're new to Ubuntu and Linux, you must certainly give Ubuntu a try (meaning, disregard the silly thread title)!  If you have the same problem, read on!  ********  **

Well, I was truly happy with the new Feisty release.  That was until I started noticing that some of my files were not being saved after shutting down.  I can no longer trust this OS.  :(

_Details_

Example1: Use gEdit and create a quick document - Save it to a specific location - Close gEdit properly - Browse the Internet - Shut Down - Reboot --> Where's my saved file?  --> Boot into Windows --> It's gone; never saved.  It shows in Recent Document in Ubuntu, but click that and it says "can not be found."

Example2: Download some MP3s using the Soulseek equivalent program, Nicotine, I believe.  Listen to them.  Read a PDF or type a document.  Shut down or restart.  Where are my MP3s?  Reboot into windows and find nothing.  Reboot into Ubuntu and find files thrown in my FAT32 partition (where I keep my files) and find files named, in order, fsck000#, where # is some number, like 9.  They are my MP3s, but I need to rename them.  

...

What is happening?  Why did Ubuntu all-of-a-sudden decide to no longer be dependable?  Any suggestions to solving this problems will be appreciated, especially considering this long post in a jungle of many many others.

Thank you!

---

### Post by MetalMusicAddict on 2007-04-24
Instead of throwing out sensationalist titles why dont you ask for specific help?

Many things come down to user error.

Where are you saving the files to? Whats the formatting of the drive? Oh I see. Whats the permissions of the drive?

---

### Post by ashz on 2007-04-24
fsck000#.rec usually is a recovered file...could be any number of reasons...

if a file is recovered then it could mean the hd is on the way out, and u usually only get this prob (the fsck000# one) with FAT32 formatted drives..

i agree with MetalMusicAddict though, there is no reason to put titles out like that because it can put newbies off!!

---

### Post by currentshades on 2007-04-24
Yikes!  I'm sorry. I truly didn't mean for the title to be offensive!  I'm still using Ubuntu when I don't need to save anything!!  ^_^  Thank you for your responses despite being offended by my stupid thread title.  

Is there a way for me to change the thread title?

If my HD is on the way out, why does it only happen in Ubuntu?  Is it the way that it handles writing the disk that helps users find out more quickly about a failing component instead of suddenly crapping-out without notice?  If so, I would see that as wonderful design so I can be ready for a future component failure and not be surprised.  :)  I hope this is the problem.  If not, what else could it be?

* Linux partition is ext-3
* Windows is NTFS
* "Desk" partition, where I save all of my files, is FAT32
* Permissions are all set for me to be able to access them all, except with not having write support in the NTFS partition

---

### Post by ashz on 2007-04-24
you say its gone when you go from ubuntu to windows..

say you download it in ubuntu, then reboot, but go back into ubuntu instead of windows is it gone then?

cheers
ash

---

### Post by MetalMusicAddict on 2007-04-24
> **currentshades said:**
> Yikes!  I'm sorry. I truly didn't mean for the title to be offensive!  I'm still using Ubuntu when I don't need to save anything!!  ^_^  Thank you for your responses despite being offended by my stupid thread title.  

Is there a way for me to change the thread title?
Don't worry about it for know. Its just a good rule of thumb to title your thread specific to your issue. People who title threads this way are usually looking for attention and get it in a negative way. ;)
> If my HD is on the way out, why does it only happen in Ubuntu?  Is it the way that it handles writing the disk?

I think its a permission thing. Some things to look at: Is the user called the same thing on Win/Linux? What permissions are set? What does the line in your FSTAB look like for this drive?

---

### Post by riksweeney on 2007-04-24
Are you sure you're not saving stuff to /tmp?

That directory gets wiped when you boot, I learned that the hard way one day...

---

### Post by darrenm on 2007-04-24
I don't get what you mean. Why boot into Windows to see a file you downloaded and saved in Ubuntu?

---

### Post by onelife151 on 2007-04-24
what he said was that he has windows XP  on an NTFS partition. Ubuntu on an ext3 partition and he's sharing data on a Fat32 partition. He said he would download stuff to the fat32 partition. reboot the machine and when he navigated to the fat32 partition via windows the file doesn't exist. I haven't seen that problem yet. not using Ubuntu at the moment like that. I just dump everything to a network share or a flash drive. lol. Hope we can figure out how to help him.

---

### Post by orb9220 on 2007-04-24
This is my fat32 share between xp and feisty

> # /dev/sdb1
/dev/sdb1     /home/orb/Drives/114GB-fat32/     vfat    defaults,utf8,umask=007,gid=46 0       0

Notice No UUID!

Works just fine.

---

### Post by tgalati4 on 2007-04-24
Linux can behave strangely with faulty hardware.  We first point to the OS--perhaps because we are conditioned from using Windows too long.

Why don't you examine your disk a little more closely.

In a terminal:

sudo apt-get install smartmontools
man smartctl   (spacebar to go forward, q to quit manual pages)
sudo smartctl -s on /dev/hda           (turn on smart)
sudo smartctl -s on /dev/hdb           (include all of your disk drives:  df -h will find them all)
sudo smartctl -t short /dev/hda        (run a short test on the drive--OK while logged it.)
sudo smartctl -l selftest /dev/hda     (print out results of selftest)
sudo smartctl -a /dev/hda     (print out everything about the drive

These commands are from memory, so there may be typos.

Pay attention to the temperature of the drive:  30C is good, 45C is bad
Pay attention to the power_on hours:  2000 hours is good, 20,000 hours is risky

That said, I have several operating drives at 22K or more hours still working nicely, but I do get smart warnings because the excessive hours on the disk.

Make sure your hardware is bullet-proof first, then your comments on reliability will have some foundation.

---

### Post by currentshades on 2007-04-24
Thank you all so much for trying to help me here.  I really appreciate it.

_Quick Replies_

* Files created in Windows remain after a reboot.  Ubuntu does save the files sometimes but renames them at other times after a 2nd boot-up (see explanation below), which seems to be a feature, not a bug, problem, or sign of not being dependable!

* In Ubuntu, when I save a file in my FAT32 Desk partition, it seems like it saves.  I reboot, and it is missing.  I then, without booting into Ubuntu a 2nd time, boot into the Windows partition to see if I can find it in that OS (where's the logic there?  I know...).  BUT!  When I enter Ubuntu for the 2nd time, the files all show up.  HOWEVER!  They are named fsck000#.rec which can also then be seen in the Windows OS.

* Files are being saved to a folder in my FAT32 partition, which isn't tmp.  :(  I wish that was the problem!

* You're right; I've been conditioned to immediately blame the OS because of Windows.  :(  That frame of mind will soon change now!

* tgalati4, you're absolutely correct that my wording was extremely poor and certainly was offensive (regret has been expressed).  :(  I did as you said (THANK YOU!), and it does indeed seem that my ol' HD isn't in the best condition (at least that's what it seems like using my brain of limited abilities).  

_Outcome_

So, I guess this is just really great design by Linux/Ubuntu (I don't know which team to praise, so I praise both)!!  ^_^  This OS is giving me notice that my little HD needs to be heading off to a new life soon.  I say it's great design, because instead of suddenly not powering up one day, I'm given notice and enough time to back up my data!  In the mean time, Ubuntu will KEEP my data (which is what I recently found out is consistent), although it will rename it to that fsck000#.rec title...


**Thank you all once again!**  And for future posts, I'll wait a few hours before posting so I can be sure not to create such a stupid thread title that will only upset people and make me look like a complete fool.  


_Below is the report from SMART Monitor that tgalati4 (thanks again!) suggested I use._
```
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     22360         -
# 2  Short offline       Completed without error       00%         7         -

rainwind@rainwind-desktop:~$ sudo smartctl -a /dev/hda
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Maxtor DiamondMax Plus 9 family
Device Model:     Maxtor 6Y120P0
Serial Number:    Y40R1E5E
Firmware Version: YAR41VW0
User Capacity:    122,942,324,736 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 0
Local Time is:    Tue Apr 24 17:53:10 2007 MST
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
data collection:                 ( 242) seconds.
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
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  63) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   203   201   063    Pre-fail  Always       -       18737
  4 Start_Stop_Count        0x0032   252   252   000    Old_age   Always       -       2240
  5 Reallocated_Sector_Ct   0x0033   252   252   063    Pre-fail  Always       -       14
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   252   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   251   237   187    Pre-fail  Always       -       56839
  9 Power_On_Minutes        0x0032   185   185   000    Old_age   Always       -       913h+20m
 10 Spin_Retry_Count        0x002b   253   252   157    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   247   247   000    Old_age   Always       -       2503
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0032   253   253   000    Old_age   Always       -       35
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       1067
196 Reallocated_Event_Count 0x0008   253   253   000    Old_age   Offline      -       0
197 Current_Pending_Sector  0x0008   253   253   000    Old_age   Offline      -       0
198 Offline_Uncorrectable   0x0008   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0008   191   173   000    Old_age   Offline      -       27
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   248   000    Old_age   Always       -       1
202 TA_Increase_Count       0x000a   253   252   000    Old_age   Always       -       0
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       0
204 Shock_Count_Write_Opern 0x000a   253   252   000    Old_age   Always       -       0
205 Shock_Rate_Write_Opern  0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   253   252   000    Old_age   Always       -       0
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   198   196   000    Old_age   Offline      -       0
 99 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
100 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
101 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
Warning: ATA error count 31 inconsistent with error log pointer 5

ATA Error Count: 31 (device log contains only the most recent five errors)
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

Error 31 occurred at disk power-on lifetime: 22340 hours (930 days + 20 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 10 b6 bb e6  Error: ICRC, ABRT at LBA = 0x06bbb610 = 112965136

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ca 00 00 10 b6 bb e6 08      00:14:39.216  WRITE DMA
  ca 00 00 10 b5 bb e6 08      00:14:39.216  WRITE DMA
  ca 00 00 10 b4 bb e6 08      00:14:39.200  WRITE DMA
  ca 00 00 10 b3 bb e6 08      00:14:39.200  WRITE DMA
  ca 00 00 10 b2 bb e6 08      00:14:39.200  WRITE DMA

Error 30 occurred at disk power-on lifetime: 21760 hours (906 days + 16 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 70 60 3c 10 e5  Error: ICRC, ABRT at LBA = 0x05103c60 = 84950112

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ca 00 b0 20 3c 10 e5 08      03:20:20.720  WRITE DMA
  ca 00 b0 20 3c 10 e5 08      03:20:20.672  WRITE DMA
  10 00 ff 00 00 00 e0 08      03:20:20.672  RECALIBRATE [OBS-4]
  ca 00 b0 20 3c 10 e5 08      03:20:20.624  WRITE DMA
  ca 00 b0 20 3c 10 e5 08      03:20:20.400  WRITE DMA

Error 29 occurred at disk power-on lifetime: 21760 hours (906 days + 16 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 70 60 3c 10 e5  Error: ICRC, ABRT at LBA = 0x05103c60 = 84950112

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ca 00 b0 20 3c 10 e5 08      03:20:20.672  WRITE DMA
  10 00 ff 00 00 00 e0 08      03:20:20.672  RECALIBRATE [OBS-4]
  ca 00 b0 20 3c 10 e5 08      03:20:20.624  WRITE DMA
  ca 00 b0 20 3c 10 e5 08      03:20:20.400  WRITE DMA
  ca 00 00 20 3b 10 e5 08      03:20:20.400  WRITE DMA

Error 28 occurred at disk power-on lifetime: 21760 hours (906 days + 16 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 70 60 3c 10 e5  Error: ICRC, ABRT at LBA = 0x05103c60 = 84950112

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ca 00 b0 20 3c 10 e5 08      03:20:20.624  WRITE DMA
  ca 00 b0 20 3c 10 e5 08      03:20:20.400  WRITE DMA
  ca 00 00 20 3b 10 e5 08      03:20:20.400  WRITE DMA
  ca 00 d8 40 3a 10 e5 08      03:20:20.384  WRITE DMA
  ca 00 d8 60 39 10 e5 08      03:20:20.384  WRITE DMA

Error 27 occurred at disk power-on lifetime: 21760 hours (906 days + 16 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 6b 65 3c 10 e5  Error: ICRC, ABRT at LBA = 0x05103c65 = 84950117

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ca 00 b0 20 3c 10 e5 08      03:20:20.400  WRITE DMA
  ca 00 00 20 3b 10 e5 08      03:20:20.400  WRITE DMA
  ca 00 d8 40 3a 10 e5 08      03:20:20.384  WRITE DMA
  ca 00 d8 60 39 10 e5 08      03:20:20.384  WRITE DMA
  ca 00 40 18 39 10 e5 08      03:20:20.384  WRITE DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     22360         -
# 2  Short offline       Completed without error       00%         7         -

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

### Post by darrenm on 2007-04-25
Very interesting. I'll be having a look at SMARTmon more from now on :)

---

### Post by astralsin on 2007-04-25
if nothing else, you can read and write ext2 and ext3 with this

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by tgalati4 on 2007-04-26
I'm glad that you got smart to run.  Be mindful that SMART only catches perhaps 2/3 of impending disk failures.  The other 1/3 are spontaneous.  That is why various RAID configurations are popular.  RAID can supposedly capture that 1/3 by mirroring drives with fail-safe switchover when one drive goes down suddenly.

The other thing to consider is your power supply.  If the 12V power feed is wonky, that can cause drive write problems (since writing takes more power than reading).  The "Abort" error messages are consistent with power dropouts.

I have a few drives with 20k+ hours.  That's a lot for a consumer-grade drive, so if it works great.  If it fails, then some engineer at Maxtor did their job since some of my Maxtor drives give me SMART errors once they surpassed 20K hours.

I had a Dapper server that ran for 165 days straight with no problems.  I only had to bring it down to change UPS batteries and to upgrade with about 100 patches.  That is why the title of your thread caught my eye.  I suspected hardware over software in this situation.

When testing my UPS with the old batteries, they couldn't hold the current load and it caused spontaneous shutdowns of my Ubuntu server.  I performed this test three times.  Each time resulted in a hard shutdown.

I examined the disk and I got similar SMART abort errors.  So I am guessing that there might be a power problem.  One thing I noticed, after almost 6 months of continuous use, the power connectors on the back of the drive became loose.  I had to take a screwdriver to mash the female connectors to make a tight fit.

It could be as simple as a loose power connector to the drive.  Vibration will loosen them over time.

---

### Post by darkdays on 2007-04-26
Edit: nevermind, missed that you seem to have found the explanation.

---

### Post by neillo on 2007-04-26
currentshades, I'm not sure if you're watching this thread anymore, but I've just had precisely the same problem.  I created files in Ubuntu, then when I went to windows they were gone.  I've managed to isolate the problem however, and I think it has to do with hibernating windows.  When I hibernate windows, then use Ubuntu to modify/create files on my FAT32 partition, then go back into windows the files are "gone"  then if I go back to Ubuntu it recovers my files for me.  This never happens if I fully shut down windows, and I realize hibernating it in the first place wasn't the brightest idea.  In summation, I'm not so sure you're having purely a hardware problem, as I've experienced the exact same effects with jumping between windows and linux with a FAT32 partition.  I'm brand new to linux so I don't know much about it all, but I just thought you might like to know you're not the only one, and I'm curious if you hibernated windows as well, since I would obviously like to replace my hard drive if it is indeed hardware.

The coincidence makes me wonder...

---

### Post by wiley692 on 2007-04-27
I have been having the exact same problem with my installation also. I save a file in ubuntu to a common fat32 partition but it does not show up when I boot in windows. If I boot in ubuntu again the files are right where I saved them. It was working fine until a couple days ago and I dont know what I might have done to cause this.

---

### Post by currentshades on 2007-04-27
tgalati4, I'll surely check my hardware this weekend.  Thank you for all of your help and insight.  :)

Wow, neillo.  I'll need to look into the hibernating issue.  That's interesting, especially considering that, yes, I do hibernate Windows (very often)!  

wiley692, try not hibernating as well and see if that may be the problem...

Until soon...

---

### Post by darkdays on 2007-04-27
Damn, my reply that I scrapped thinking that you found your problem was about the Windows, hibernation & filesystems issue.

The problem with hibernation is that Windows doesn't unmount the filesystems, so when you load it up after saving some files on the disk in Ubuntu, Windows is still using the old cached tables from before the changes. This bad practice makes all changes between hibernation and resuming go unnoticed by Windows and will probably in the long run lead to a *_very_* corrupt filesystem. I don't know if this applies to all Windows-versions.

In short, don't  hibernate Windows in a dualboot with drives shared between OS's as it will most definitely mess up your data until M$ fixes this issue.

---

### Post by tgalati4 on 2007-04-28
Yes, hibernation in Windows does cause disk problems.  Sometimes a snapshot is written to disk and I'm not entirely sure where on the disk this snapshot is placed.  If it overwrites any part of the Linux partition then you have a problem and you will get fsck0001.rec files  (fsck is geekspeak for file system check and *.rec are "recovered" files).  

If a Linux partition is "dirty", that is written to without the operating system's control, then fsck will automatically check the disk and repair the damage and recover files if possible.

Also, Windows knows nothing about a Type 82 Linux partition so any files saved in Ubuntu will not be visible in Windows unless you create a FAT32 partition.  Linux and see Windows files, but Windows cannot see Linux files--as a general rule.  Also Linux is aware that Windows exists on the disk and takes steps not to screw it up.  Windows thinks it's the only operating system and writes to the disk at will.

For a desktop system, it's helpful to put your Ubuntu on a separate disk.  On a dual-boot laptop with a single disk, one Windows virus can take out the partition table and leave you without a way to boot into Ubuntu.  But of course, we always keep our Ubuntu Live CD with us for those special occasions.

---

### Post by kelvin spratt on 2007-04-28
why do all the messing about with out dated fat 32 partions enable ntfs 3g using automatix not the ubuntu version as i get a write permissions problem with the ubuntu version reformat that drive enable 3g it will remount your drives give you full permission read and write then you can write directly to that folder with no restiction
i think you are having a similer prob as i had i was downloading files but for some reason the file were being held in temp and not writen to the files i was using ubuntu version at the time and it came out of the blue iv'e used the automatix version in edgy and now in fiesty and its faultless in use and you can drop and drag between both distros safely  i do lots of photo and vid editing and drag and drog or cut and paste is am must for mei hope this is helpfull to you

---

### Post by tgalati4 on 2007-04-28
Well I have stopped using windows for the past few years, so I don't have that problem.  But your experience with ntfs 3g may help others make the transisition.

---

### Post by currentshades on 2007-04-29
Now I REALLY wish I could change the thread title!!  Software-wise, the problem was in fact concerning Windows (and user ignorance).  

For now, I just turned off hibernation completely in Windows (thank you for the great explanation, darkdays and tgalati4).  

Ubuntu/Linux is such an incredible OS.  Windows is simply corrupting my files while Ubuntu does the best it can to recover them if needed (or if there is suspicion of error).  :)

Also, I should concretely state that my hard drive is not out of the red; it only has so much longer.  :(  But for now, this problem is solved (with an occasional miss here and there due to the hard drive acting up).  

Thank you for the incredibly informative responses (and I'll consider that option, kelvin spratt).  I think I mostly understand the problem now (not just the symptom and vague solution).  Hopefully this thread will help others having the same problem.

---


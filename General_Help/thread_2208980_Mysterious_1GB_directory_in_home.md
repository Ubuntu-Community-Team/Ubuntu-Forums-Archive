---
title: "Mysterious 1GB directory in /home"
date: 2014-03-03
forum: General Help
---

### Post by wafitzpatrick on 2014-03-03
Hi guys,

Not my first post to this forum, but it's been a while (had an older login before SSO which I seem to have lost).

I have a strange issue. One or two of my applications seemed to hang and go grey when I did a directory search. I used an strace and worked out that these applications must be doing a subdirectory scan of all files in the working directory because they were getting to a particular directory and getting bogged down:

```
openat(AT_FDCWD, "/home/wafitz/bRom Gh2kR", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 19
getdents(19, /* 125 entries */, 32768)  = 32520
getdents(19, /* 124 entries */, 32768)  = 32736
getdents(19, /* 124 entries */, 32768)  = 32736
getdents(19, /* 124 entries */, 32768)  = 32736
getdents(19, /* 124 entries */, 32768)  = 32736
getdents(19, /* 124 entries */, 32768)  = 32736
getdents(19, /* 124 entries */, 32768)  = 32736
getdents(19, /* 124 entries */, 32768)  = 32736
getdents(19, /* 124 entries */, 32768)  = 32736
getdents(19, /* 124 entries */, 32768)  = 32736
getdents(19, /* 124 entries */, 32768)  = 32736
getdents(19, /* 124 entries */, 32768)  = 32736
getdents(19, /* 124 entries */, 32768)  = 32736
getdents(19, /* 124 entries */, 32768)  = 32736
....

```
This just continues until I Crtl-C. I have a lot of junk in my /home directory but generally I know what files/dirs relate to what or can find out easily but this one I do not recognise, nor does it turn up on google search.

What's more it's almost 1GB in size. I'm trying a "ls -l" on it now and it's not outputted anything for the last 20 minutes.

```

drwxr-xr-x   2 wafitz wafitz 1054867456 Jan 26 00:43 bRom Gh2kR/


```

Unfortunately, I can't quite recall what I was doing at that time either but it's been sitting on there that long without me noticing. Thankfully, it doesn't appear to be growing or collecting anything.

I want to delete it, but I wonder if there's a way I can check this faster, just in case it is something important. I also wonder if there's a way I can chronologically list the files that have modified on my filesystem since Jan 25th? Or is there a log file I can lookup?

Any help appreciated.

---

### Post by tgalati4 on 2014-03-03
If you install WINE, you will get a 1GB file or larger.  That is your Windows image.  You can delete it, but then you lose your WINE session.  Check your log files around that time and see what else was going on.  It's possible that a process failed and left some breadcrumbs.

Check the SMART status of the drive:

```
sudo smartctl -a /dev/sda
```

---

### Post by wafitzpatrick on 2014-03-03
I recently installed MS Office with Wine (PlayOnLinux) but that was only a few weeks ago. Here is my SMART output:

```
$ sudo smartctl -a /dev/sda
smartctl 6.2 2013-04-20 r3812 [x86_64-linux-3.11.0-17-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Device Model:     WDC WD5000LPVX-22V0TT0
Serial Number:    WD-WX11E33KD862
LU WWN Device Id: 5 0014ee 6ae252f76
Firmware Version: 01.01A01
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Mon Mar  3 19:01:36 2014 GMT
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
data collection:         ( 8040) seconds.
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
recommended polling time:      (  93) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x7035)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   151   145   021    Pre-fail  Always       -       1416
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       258
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       2
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       4498
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       145
191 G-Sense_Error_Rate      0x0032   099   099   000    Old_age   Always       -       1
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       6
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       2443
194 Temperature_Celsius     0x0022   106   086   000    Old_age   Always       -       37
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0


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

```

Doesn't seem to be any problems unless I'm misreading. I ran the following command to see if I could find what it might be related to:

```
find /home/ -newermt "Jan 25" ! -newermt "Jan 26" -ls
```

But my last modified files were 3 hours out from the timestamp of this directory. I had been doing some MongoDB courses, I might have done something there causing a dump of some kind, but it doesn't look like typical MongoDB dump files.

Running an "ls -1 -f" produces the following files that look like encrypted data chunks of some kind, but are unreadable.

```
bRom Gh2kR$ ls -1 -f
.
..
njb_1H                                                                                                                                                                                                                                         
GOWqdZ                                                                                                                                                                                                                                         
jdntQZ                                                                                                                                                                                                                                         
JpWBEV                                                                                                                                                                                                                                         
q3LRej                                                                                                                                                                                                                                         
yvGUzL                                                                                                                                                                                                                                         
Vr9Bwh                                                                                                                                                                                                                                         
KvHQ_L                                                                                                                                                                                                                                         
dkz8CW                                                                                                                                                                                                                                         
tELlcf                                                                                                                                                                                                                                         
VFdyLG                                                                                                                                                                                                                                         
jDi66K                                                                                                                                                                                                                                         
WGQ2_1                                                                                                                                                                                                                                         
XfCXgL                                                                                                                                                                                                                                         
wkrHkg

```



```
$ cat njb_1H
cat: njb_1H: No such file or directory

```

I've decided to rename the directory and see if anything falls over.

---

### Post by bapoumba on 2014-03-03
> **wafitzpatrick said:**
> Hi guys,

Not my first post to this forum, but it's been a while (had an older login before SSO which I seem to have lost).



Just to point out that you can post a thread in the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123"), an admin will assist you recovering your previous account.

---

### Post by tgalati4 on 2014-03-03
Do you have any encryption set up on this disk?  The disk physically looks fine, so that rules out disk controller problem.

Does your MS_Office install still work?  If not, did you delete it completely?

There is a crypto-locker virus that is going around.  It encrypts your data and then demands a payment to unlock it.  I would proceed carefully.  Check your browsing history during that time frame as well.  The first thing that happens when the virus is activated is that it grabs your data files and dumps them into an encrypted file.  So if your personal data files are OK, it may have simply copied the files but did not have permission to delete them.

---

### Post by wafitzpatrick on 2014-03-06
@[COLOR=#000000]bapoumba

Thanks for the info, I did realise that after I had logged in and posted, but I guess I'm just being lazy, and I'll stick to my One account.

@[/COLOR][COLOR=#000000]tgalati4

Thanks for all the suggestions so far. I checked my browser history - nothing untoward, checked my downloads folder and nothing struck out. As an IT professional I'm aware of the type of click-bait that exists on the web and I'm very conscious of malware and security issues - that is what I first assumed. I've done a few basic checks, including 'netstat' to see if anything is connected that shouldn't be, but I guess I'm going to have to do a full audit now just to be sure.

I do use full disk encryption set up with[/COLOR] eCryptfs at install. [COLOR=#000000]I don't seem to have lost any data and my laptop has survived a reboot fine so I've trashed this random directory.

Funnily enough my Office install was misbehaving when I attempted to "Open File" whilst in my Home directory - it greyed out and crashed, just like Filezilla. I didn't realise at the time that this could be the issue, I just assumed it was because it was a Windows program, now it works just fine!

So far, all I've learned that Office and Filezilla do a recursive search of all subdirectories in the directory they're in, when you attempt to open one subdirectory! I will leave this thread a little while longer in case anyone comes up with any further suggestions, but then I'll mark it as solved.[/COLOR]

---

### Post by tgalati4 on 2014-03-06
It's possible that Office and Filezilla were doing a directory indexing (and greyed out--and acted frozen) and that was the 1GB dump when it crashed.  I think you can turn off those indexing features.  When running in emulation mode, such indexing can be slow and seem unresponsive, but let it run its course.

The other possibility is a problem with running some programs (like Office) using full body encryption.

---

### Post by wafitzpatrick on 2014-03-06
> **tgalati4 said:**
> It's possible that Office and Filezilla were doing a directory indexing (and greyed out--and acted frozen) and that was the 1GB dump when it crashed.  I think you can turn off those indexing features.  When running in emulation mode, such indexing can be slow and seem unresponsive, but let it run its course.

The other possibility is a problem with running some programs (like Office) using full body encryption.

I guess it's possible, though as I said creation time was before I installed Office. I tend to run VirtualBox, qBittorrent, MongoDB and I have some background widgets that include Skype, Everpad, HPLIP, Dropbox. Sometimes I'll get a crash - like Everpad will crash or Skype - I don't have the time to look into the issues. It may have been one of these types of crashes that caused it.

For now, I've wiped the directory from my system (it took a while) and I've done a security audit with find, lsof, netstat and some other tools. Not a huge substantial audit, but enough to be fairly confident that I don't have hacker problem. I might install Tripwire as a precaution.

Thanks for all the suggestions. I'll mark this as solved for now!

---


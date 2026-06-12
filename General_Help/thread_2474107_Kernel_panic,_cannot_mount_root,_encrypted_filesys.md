---
title: "Kernel panic, cannot mount root, encrypted filesystem"
date: 2022-04-22
forum: General Help
---

### Post by ct952 on 2022-04-22
Hi All,
I am suddenly experiencing a kernel panic most probably after some regular updates, so I cannot boot the os anymore. I am (I was actually...) running Ubuntu 20.04 (Slimbook OS) kernel 5.13. The ssd disk is encrypted, both home and system folders. I have been able to reboot with an USB stick, access the partitions and backup all the data on a usb HD. I would like to fix the issue in a lighter way instead of rebuilding the machine from scratch, which I don't think is a good general fix for a kernel panic.

Normally, when I booted the machine, I was prompted for file system password and then the system booted. Now this does not happen, I have the options for booting just the last kernel, the same in rescue mode or to access the EFI bios. I would have liked to try booting an older kernel, but this is not in the options.

Using boot-repair I generated the following report: [https://pastebin.ubuntu.com/p/vzS7BtY9d7/](https://pastebin.ubuntu.com/p/vzS7BtY9d7/) ; anyhow, boot-repair is actually not able to repair in my scenario.

I tryed to re-install the OS from the USB stick, but the setup wizard does not detect the existing OS, even if the encrypted partion is mounted and readable, so the only option it leaves to me is to install from skratch (i.e. erase OS and home folders), which I don't want.

I have the option to access grub in rescue mode from the boot menu, I followed the recommendations of some posts here and there but I have not been able to do so much with grub.

Does anybody have a hint on how to restore?

Here below a picture of the kernel error stack
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290312&stc=1[/IMG]

Thanks in advance

Carlo

---

### Post by TheFu on 2022-04-22
Looks like a corrupted block on the SSD.  

From a "Try Ubuntu" flash drive boot, you should be able to mount the storage, run an fsck against the different file systems. If that doesn't fix the issue, then get your files off it and do a fresh install.

However, I'd also check the SMART data for the SSD to see how bad the failure is.  If the blocks aren't automatically relocated, then the SSD lifespan is over.

This is the reason everyone needs solid backups.  We don't get to choose when things fail.  I fear that at this point, if it truly is a storage failure, then the SSD won't be readable. I've had SSD storage fails a few times.  IME, they fail to read-only mode for a few days before refusing to allow any access at all.  I'm not saying hardware failure is the issue here. We don't know until you run an **fsck** and look at the SMART data (use **smartctl**).

---

### Post by ct952 on 2022-04-22
Theanks for your reply. I performed the suggested checks and here below the results:

```

ubuntu@ubuntu:~$ sudo fsck -V /dev/dm-1
fsck from util-linux 2.34
[/usr/sbin/fsck.ext4 (1) -- /dev/mapper/vgubuntu-root] fsck.ext4 /dev/mapper/vgubuntu-root
e2fsck 1.45.5 (07-Jan-2020)
/dev/mapper/vgubuntu-root: clean, 755194/60907520 files, 62071815/243616768 blocks

ubuntu@ubuntu:~$ sudo fsck -V /dev/nvme0n1p2
fsck from util-linux 2.34
[/usr/sbin/fsck.ext4 (1) -- /dev/nvme0n1p2] fsck.ext4 /dev/nvme0n1p2
e2fsck 1.45.5 (07-Jan-2020)
/dev/nvme0n1p2: clean, 340/46848 files, 84569/187392 blocks

```

so the file system is clean, no errors.

```

ubuntu@ubuntu:~$ smartctl --scan
/dev/sdd -d sat # /dev/sdd [SAT], ATA device
/dev/nvme0 -d nvme # /dev/nvme0, NVMe device

--------------------------------------------------------------------------------------------------

ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdd
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.13.13-051313-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD50NDZM-59A8KS1
Serial Number:    WD-WXH2E510KK16
LU WWN Device Id: 5 0014ee 214476f29
Firmware Version: 01.01A01
User Capacity:    5,000,947,523,584 bytes [5.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-3 T13/2161-D revision 5
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Apr 22 18:48:35 2022 UTC
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
data collection:         ( 4320) seconds.
Offline data collection
capabilities:              (0x1b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
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
recommended polling time:      (  66) minutes.
SCT capabilities:            (0x30b5)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   253   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   253   253   021    Pre-fail  Always       -       4758
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       18
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       3
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       16
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       10
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       49
194 Temperature_Celsius     0x0022   127   107   000    Old_age   Always       -       25
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]

Selective Self-tests/Logging not supported

-------------------------------------------------------------------------------------

ubuntu@ubuntu:~$ sudo smartctl -a /dev/nvme0
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.13.13-051313-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Number:                       WDC WDS100T2B0C-00PXH0
Serial Number:                      21245J802636
Firmware Version:                   211210WD
PCI Vendor/Subsystem ID:            0x15b7
IEEE OUI Identifier:                0x001b44
Total NVM Capacity:                 1,000,204,886,016 [1.00 TB]
Unallocated NVM Capacity:           0
Controller ID:                      1
Number of Namespaces:               1
Namespace 1 Size/Capacity:          1,000,204,886,016 [1.00 TB]
Namespace 1 Formatted LBA Size:     512
Namespace 1 IEEE EUI-64:            001b44 8b41949d1d
Local Time is:                      Fri Apr 22 18:49:13 2022 UTC
Firmware Updates (0x14):            2 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL Self_Test
Optional NVM Commands (0x005f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat Timestmp
Maximum Data Transfer Size:         128 Pages
Warning  Comp. Temp. Threshold:     80 Celsius
Critical Comp. Temp. Threshold:     85 Celsius
Namespace 1 Features (0x02):        NA_Fields

Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     3.50W    2.90W       -    0  0  0  0        0       0
 1 +     2.70W    1.80W       -    0  0  0  0        0       0
 2 +     1.90W    1.50W       -    0  0  0  0        0       0
 3 -   0.0250W       -        -    3  3  3  3     3900   11000
 4 -   0.0050W       -        -    4  4  4  4     5000   39000

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         2
 1 -    4096       0         1

=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        31 Celsius
Available Spare:                    100%
Available Spare Threshold:          10%
Percentage Used:                    0%
Data Units Read:                    1,343,626 [687 GB]
Data Units Written:                 945,999 [484 GB]
Host Read Commands:                 11,052,433
Host Write Commands:                7,457,291
Controller Busy Time:               52
Power Cycles:                       307
Power On Hours:                     146
Unsafe Shutdowns:                   22
Media and Data Integrity Errors:    0
Error Information Log Entries:      1
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0

Error Information (NVMe Log 0x01, max 256 entries)
No Errors Logged

```

so to me also the SDD is ok, it is quite a new machine

---

### Post by TheFu on 2022-04-22
smartctl requires running a test first. Looks like not tests have ever been run on either device.

```
sudo smartclt -t long -d sat /dev/sdd
sudo smartclt -t long -d nvme  /dev/nvme0 

```
then wait the required time for each to complete.
The run the **smartctl -a **report for each drive.

---

### Post by ct952 on 2022-04-23
Hi, I tested your suggestion, not really sure a test have been performed actually, it completed instantly. In the former output there was an additional device which was a portable usb hd, this time it was not connected, so we have only the relevant output.

```

ubuntu@ubuntu:~$ sudo smartctl --scan

/dev/nvme0 -d nvme # /dev/nvme0, NVMe device

ubuntu@ubuntu:~$ sudo smartctl -t long -d nvme /dev/nvme0

smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.13.13-051313-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

NVMe device successfully opened

Use 'smartctl -a' (or '-x') to print SMART (and more) information

ubuntu@ubuntu:~$ sudo smartctl -a /dev/nvme0

smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.13.13-051313-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Number:                       WDC WDS100T2B0C-00PXH0
Serial Number:                      21245J802636
Firmware Version:                   211210WD
PCI Vendor/Subsystem ID:            0x15b7
IEEE OUI Identifier:                0x001b44
Total NVM Capacity:                 1,000,204,886,016 [1.00 TB]
Unallocated NVM Capacity:           0
Controller ID:                      1
Number of Namespaces:               1
Namespace 1 Size/Capacity:          1,000,204,886,016 [1.00 TB]
Namespace 1 Formatted LBA Size:     512
Namespace 1 IEEE EUI-64:            001b44 8b41949d1d
Local Time is:                      Sat Apr 23 08:23:33 2022 UTC
Firmware Updates (0x14):            2 Slots, no Reset required
Optional Admin Commands (0x0017):   Security Format Frmw_DL Self_Test
Optional NVM Commands (0x005f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat Timestmp
Maximum Data Transfer Size:         128 Pages
Warning  Comp. Temp. Threshold:     80 Celsius
Critical Comp. Temp. Threshold:     85 Celsius
Namespace 1 Features (0x02):        NA_Fields

Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     3.50W    2.90W       -    0  0  0  0        0       0
 1 +     2.70W    1.80W       -    0  0  0  0        0       0
 2 +     1.90W    1.50W       -    0  0  0  0        0       0
 3 -   0.0250W       -        -    3  3  3  3     3900   11000
 4 -   0.0050W       -        -    4  4  4  4     5000   39000

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         2
 1 -    4096       0         1

=== START OF SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

SMART/Health Information (NVMe Log 0x02)
Critical Warning:                   0x00
Temperature:                        28 Celsius
Available Spare:                    100%
Available Spare Threshold:          10%
Percentage Used:                    0%
Data Units Read:                    1,343,758 [688 GB]
Data Units Written:                 946,002 [484 GB]
Host Read Commands:                 11,054,962
Host Write Commands:                7,457,408
Controller Busy Time:               52
Power Cycles:                       308
Power On Hours:                     146
Unsafe Shutdowns:                   22
Media and Data Integrity Errors:    0
Error Information Log Entries:      1
Warning  Comp. Temperature Time:    0
Critical Comp. Temperature Time:    0

Error Information (NVMe Log 0x01, max 256 entries)
No Errors Logged

```

---

### Post by TheFu on 2022-04-23
Well, crap. That isn't very useful.  For SATA HDDs, there is lots of useful information. Looking at the available data, nothing seems clearly bad to me.
Can you boot from a different kernel?  I don't have 5.13 here. Much too new for me.

BTW, can you open and access the data on the LUKS encrypted LVs?  It would be good to get your data off that thing, since doing a fresh install may be the next step, if someone can't help with the boot-info information. I can't see it, since it requires a separate login and I'm not exactly the best at dealing with boot issues.  I would have wiped, done a fresh install, then restored from my backups after 30 minutes of trying to fix it.  I do use encrypted storage with LUKS and LVM.  Think I've posted steps to access that here a few times. I know that Caja will unlock and access the storage just by clicking - this works from a *Try Ubuntu-Mate* flash installer. It is also possible manually, but the steps take longer to type.

---

### Post by ct952 on 2022-04-23
Hi! Thanks for keep helping. I was already thinking to follow you philosphy: fresh install. If recovery takes so much time, then I think in few hours I can re-build the machine and close the topic. Unfortunately, I cannot boot a previous kernel, quite a shame since often that can fix. In the next install I will configure the system to keep the old kernels, this is what I learn from this experience. Also, recovering from a full encrypted scenario is much more difficult than on a regular one.
Luckily, I can have full access to the data from a live USB and already recovered everything.
But... if somebody has a hint, I still would like try the recovery...

---

### Post by TheFu on 2022-04-23
Restoring backup files into a fresh install shouldn't take more than 15-30 minutes for all but the largest amount of data, which is typically media files.  But everything else should be back so it feels like YOUR SYSTEM within 30 minutes with prior packages all freshly installed, assuming they are in the standard repos.

The trick for this is to .... backup the server and personal data (typically in HOME), back up system settings (files), backup personal settings (in HOME) and create a list of APT manually installed packages and back up that list.  **apt-mark showmanual** is the command.  

At restore time, 
[LIST=1]
[*]do a fresh install of the same OS (or a new release ***can*** work for about 90% of packages), 
[*]restore selected system config files - not everything - but the specific files in /etc/ that you've modified.  On a new system, get into the habit of adding a comment/tag to system settings that can easily be found during restore operations later.
[*]restore all user's HOME directories. This will get the personal settings and data, typically.  
[*]restore system data ... if you run a DBMS or web server, those files need to be put back where they were.  Just drop them into the directory where they were with the same owner, group and permissions for the directories and all files.
[*]Feed the list of manually installed packages back into APT.  When APT sees the prior settings from step 2, it will assume the package is being either reinstalled or upgraded and use those settings. It will see the data for those packages in the expected locations and perform any data migrations (almost always) that are required.
[/LIST]
Following those steps, takes about 15 minutes for each major part.
[LIST]
[*]0-15m - Fresh OS install
[*]15-30m - System and personal settings, along with non-media files ... so DBMS, websites, and personal documents
[*]30-45m - Reinstall packages from the list of manually installed packages. It may not take 15 minutes - the time depends on how many manually installed packages are in the list. A few hundreds are common.

[/LIST]

So, in less than 45 min, we have a fresh install with all the critical programs, settings, data and files ready to go. All that is missing are media files - music, videos, which really should be stored on other storage devices anyways.

In short, if it takes a few hours to rebuild a system, you are doing it wrong.

IMHO.

---

### Post by ct952 on 2022-04-26
I cut the thing and performed a fresh install.
cheers

---


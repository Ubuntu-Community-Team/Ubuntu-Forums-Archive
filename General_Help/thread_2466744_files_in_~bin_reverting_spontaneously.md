---
title: "files in ~/bin reverting spontaneously"
date: 2021-09-04
forum: General Help
---

### Post by bvargo on 2021-09-04
I've been using a script that I've been honing for a while and when I went to use it just now, has reverted to a version over a week old.  In addition, a new script I wrote this morning reverted to a version before it was written (i.e., it's gone).

This happened last weekend except that the latter script had not yet existed and the former one reverted to a version before it was written (i.e., gone).  I asked on IRC #ubuntu and the only response was "ext4 has some self-healing functions."

My drive:
```
$ sudo smartctl --all /dev/sda 
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.8.0-48-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     SandForce Driven SSDs
Device Model:     KINGSTON SH103S3120G
Serial Number:    50026B732C01B03D
LU WWN Device Id: 5 0026b7 32c01b03d
Firmware Version: 526ABBF0
User Capacity:    120,034,123,776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS, ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sat Sep  4 14:31:12 2021 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x02)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x79) SMART execute Offline immediate.
                    No Auto Offline data collection support.
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
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  36) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x0025)    SCT Status supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0033   095   095   050    Pre-fail  Always       -       0/213296763
  5 Retired_Block_Count     0x0033   100   100   003    Pre-fail  Always       -       0
  9 Power_On_Hours_and_Msec 0x0032   047   047   000    Old_age   Always       -       47080h+35m+07.690s
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       189
171 Program_Fail_Count      0x000a   000   000   000    Old_age   Always       -       0
172 Erase_Fail_Count        0x0032   000   000   000    Old_age   Always       -       0
174 Unexpect_Power_Loss_Ct  0x0030   000   000   000    Old_age   Offline      -       309
177 Wear_Range_Delta        0x0000   000   000   000    Old_age   Offline      -       3
181 Program_Fail_Count      0x000a   000   000   000    Old_age   Always       -       0
182 Erase_Fail_Count        0x0032   000   000   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0012   100   100   000    Old_age   Always       -       0
189 Airflow_Temperature_Cel 0x0000   028   077   000    Old_age   Offline      -       28 (Min/Max 3/77)
194 Temperature_Celsius     0x0022   028   077   000    Old_age   Always       -       28 (Min/Max 3/77)
195 ECC_Uncorr_Error_Count  0x001c   120   120   000    Old_age   Offline      -       0/213296763
196 Reallocated_Event_Count 0x0033   100   100   003    Pre-fail  Always       -       0
201 Unc_Soft_Read_Err_Rate  0x001c   120   120   000    Old_age   Offline      -       0/213296763
204 Soft_ECC_Correct_Rate   0x001c   120   120   000    Old_age   Offline      -       0/213296763
230 Life_Curve_Status       0x0013   100   100   000    Pre-fail  Always       -       100
231 SSD_Life_Left           0x0013   095   095   010    Pre-fail  Always       -       0
233 SandForce_Internal      0x0032   000   000   000    Old_age   Always       -       34179
234 SandForce_Internal      0x0032   000   000   000    Old_age   Always       -       24039
241 Lifetime_Writes_GiB     0x0032   000   000   000    Old_age   Always       -       24039
242 Lifetime_Reads_GiB      0x0032   000   000   000    Old_age   Always       -       21472


SMART Error Log not supported


SMART Self-test Log not supported


SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
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

Version:
```
 OS: Ubuntu 20.04 focal
 Kernel: x86_64 Linux 5.8.0-48-generic
 Uptime: 3d 7h 23m
 Packages: 2856
 Shell: bash 5.0.17
 Resolution: 7840x2560
 DE: GNOME 3.36.5
 WM: Metacity
 GTK Theme: Yaru [GTK2/3]
 Icon Theme: ubuntu-mono-light
 Font: Ubuntu 11
 Disk: 3.2T / 3.7T (91%)
 CPU: Intel Core i5-3570K @ 4x 3.8GHz [44.0°C]
 GPU: GeForce GTX 650 Ti BOOST
 RAM: 11903MiB / 24011MiB
XDG_CURRENT_DESKTOP=GNOME-Flashback:GNOME
default-display-manager: /usr/sbin/gdm3
Kernel info (uname): Linux 5.8.0-48-generic #54~20.04.1-Ubuntu SMP Sat Mar 20 13:40:25 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

```

At this point should I assume that this is the ubuntu oracle telling me that my future includes this drive imminently failing?

---

### Post by TheFu on 2021-09-04
```
174 Unexpect_Power_Loss_Ct  0x0030   000   000   000    Old_age   Offline      -       309
```
yes.
And that you have a bad cable to the SSD.
And stop pulling the power plug to stop a system.  You'll have much less data loss that way.

---

### Post by bvargo on 2021-09-05
> **TheFu said:**
> ```
174 Unexpect_Power_Loss_Ct  0x0030   000   000   000    Old_age   Offline      -       309
```
yes.
And that you have a bad cable to the SSD.
And stop pulling the power plug to stop a system.  You'll have much less data loss that way.

Well, I rebooted [properly] yesterday and the files came back.  It is really very puzzling, but I copied ~/bin from the SSD to my data HDD so at least there's another copy.  I'll have to start rsyncing it daily I guess.

---

### Post by TheFu on 2021-09-05
> **bvargo said:**
> Well, I rebooted [properly] yesterday and the files came back.  It is really very puzzling, but I copied ~/bin from the SSD to my data HDD so at least there's another copy.  I'll have to start rsyncing it daily I guess.

Or how about using a real backup tool.  rsync is great at a mirror, but it does nothing to fight against corruption or to show how corrupted files change over time.  Use a real backup tool that has versioning to see that.  There are tools that have the most recent backup appear as a mirror of the source, but put older versions into a different area which can be restored, compared, and held for very little extra storage.  I keep 90-180 days of versioned backups for my systems - how long depends on the risks of attacks to the system.  Each backup version is very fast to create after the 1st one (which takes as much time/storage as rsync).

Whatever you do, please, please, please, automate it.  Otherwise, it won't get done.  I speak from experience.

---

### Post by bvargo on 2021-09-05
> **TheFu said:**
> Whatever you do, please, please, please, automate it. Otherwise, it won't get done. I speak from experience.  Yeah, that's pretty much human nature.

> Or how about using a real backup tool.  rsync is great at a mirror, but it does nothing to fight against corruption or to show how corrupted files change over time.  Use a real backup tool that has versioning to see that.  There are tools that have the most recent backup appear as a mirror of the source, but put older versions into a different area which can be restored, compared, and held for very little extra storage.  I keep 90-180 days of versioned backups for my systems - how long depends on the risks of attacks to the system.  Each backup version is very fast to create after the 1st one (which takes as much time/storage as rsync).


I have a recent clonezilla backup that would be sufficient for what I need to recover in the event the drive fails.  That said, I feel like people preach backing up, e.g., as above, but yet leave out the important parts, namely, how to perform the backup and how to automate it.  Is there an authoritative guide to this somewhere?  I can search backup ubuntu home directory on the internet and have more results than I can possibly read through and still not know what best practices are or how to restore in the event of a loss.

---

### Post by TheFu on 2021-09-05
I've probably posted in these forums over 100 times.  There are lots of links about backups to my posts.  They usually point to a script or 5.
rdiff-backup is nearly like rsync, so if you post your rsync script, someone can change it to use rdiff-backup in a few minutes.

Here's a very simple example to backup a single HOME directory, run as that specific userid.
[Https://ubuntuforums.org/showthread.php?t=2465035&p=14049979#post14049979](Https://ubuntuforums.org/showthread.php?t=2465035&p=14049979#post14049979)
This is all that 80% of people need.  Start there, then add more as needed/desired.  

1 source directory tree is easy.  When we add more than one, it becomes easier to exclude everything, say to backup /, but then explicitly include the 2-500 directories we really want.

That link above has other, more capable, backup examples too.

To automate it, use the userid's crontab for 1 userid.  **crontab -e** is the command.
To automate more complex backups that include multiple userids, use root's crontab. **sudo crontab -e** is the command.  Or you can put the backup script into /etc/cron.daily/ and it will be run automatically once a day, assuming the computer is powered on.

Of course, you need to know the correct file format for crontabs. There are a few of different crontab control line formats. Which is needed depends on the location of the crontab file.  /etc/crontab is the overall system crontab. It uses a specific format.
Anacron can't be set to run at more resolution than 1 day.  That's what the cron.daily/.hourly/.monthly/.yearly  directories do.  I want my backups to run when I know the system won't be busy, so I use crontabs under /var/spool/cron/crontabs .... with is where the **crontab -e** command puts the files. It also validates syntax and tells crond there were updates.  These have 1 minute resolution.

---


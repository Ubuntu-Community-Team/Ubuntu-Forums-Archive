---
title: "SSD Drive Failing?  Remount read-only"
date: 2012-12-07
forum: General Help
---

### Post by NertSkull on 2012-12-07
So I have an SSD drive (Crucial m4) that I have had in my machine for about 11 months now with no issue.

Yesterday, I started having problems.  It appears that after my machine is turned on for 20-40 minutes, it will remount my root filesystem as read-only.  At which point my computer becomes unusable.  I can't even "sudo" anything because I can't write to any file.  

I am not positive, but I'm pretty sure my issue is what is described here in [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/992424") bug.

But, according to the bug (if I'm reading it right) it says its been "fixed".  But, from what I read, it just appears that they decided it was a bad drive.  But lots of people had the same issue, that seems unlikely.

My fear is that that (a bad drive) is exactly what I have.  Since it worked for many months, and now has issues.  But I thought I'd maybe check here first, before going out and buying a new expensive (less so now, than a year ago) SSD drive.

I ran "dmesg | grep read" right after the computer became unstable last night.  And this is the output

```
[    2.409155] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.412708] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.439469] Write protecting the kernel read-only data: 12288k
[   28.954520] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.067563] SP5100 TCO timer: mmio address 0xb8fe00 already in use
[   30.954536] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.955081] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   33.885278] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2077.948053] ata1: softreset failed (device not ready)
[ 2087.960057] ata1: softreset failed (device not ready)
[ 2098.532057] ata1: link is slow to respond, please be patient (ready=0)
[ 2123.008050] ata1: softreset failed (device not ready)
[ 2128.196054] ata1: softreset failed (device not ready)
[ 2128.267256] EXT4-fs (dm-1): Remounting filesystem read-only

```

So, I don't know if that helps, but something is not good.

I don't know how to read it, but here is the output of the SMART monitoring for the drive.  Maybe from this, others can tell me for sure if the drive is bad or not.  I don't know.

```
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-34-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     M4-CT128M4SSD2
Serial Number:    00000000115009000F6C
LU WWN Device Id: 5 00a075 109000f6c
Firmware Version: 0009
User Capacity:    128,035,676,160 bytes [128 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Fri Dec  7 11:09:45 2012 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x80)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  595) seconds.
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
recommended polling time: 	 (   9) minutes.
Conveyance self-test routine
recommended polling time: 	 (   3) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   050    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   100   100   001    Old_age   Always       -       5351
 12 Power_Cycle_Count       0x0032   100   100   001    Old_age   Always       -       383
170 Unknown_Attribute       0x0033   100   100   010    Pre-fail  Always       -       0
171 Unknown_Attribute       0x0032   100   100   001    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   100   100   001    Old_age   Always       -       0
173 Unknown_Attribute       0x0033   100   100   010    Pre-fail  Always       -       15
174 Unknown_Attribute       0x0032   100   100   001    Old_age   Always       -       0
181 Program_Fail_Cnt_Total  0x0022   100   100   001    Old_age   Always       -       1949934551197
183 Runtime_Bad_Block       0x0032   100   100   001    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   050    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   001    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   001    Old_age   Always       -       0
189 High_Fly_Writes         0x000e   100   100   001    Old_age   Always       -       80
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       0
195 Hardware_ECC_Recovered  0x003a   100   100   001    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   100   100   001    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   001    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   001    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   100   100   001    Old_age   Always       -       0
202 Data_Address_Mark_Errs  0x0018   100   100   001    Old_age   Offline      -       0
206 Flying_Height           0x000e   100   100   001    Old_age   Always       -       0

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

I'm running Kubuntu 12.04 and have all the updates from the muon package manager installed as of last night.  And I have the drive set to AHCI mode in the BIOS

So, is my hard drive just bad?  Or is there something wrong here that I can fix?

---

### Post by duke.tim on 2012-12-07
I found on Google this

> Re: M4 SMART Parameters - which ones matter?
Options
&#8206;04-07-2012 02:45 AM

That is not the SMART layout for an SSD. try using more recent SMART software.  CrystalDiskInfo 4 or newer will do the job well.

[http://forums.crucial.com/t5/Solid-State-Drives-SSD/M4-SMART-Parameters-which-ones-matter/td-p/93110](http://forums.crucial.com/t5/Solid-State-Drives-SSD/M4-SMART-Parameters-which-ones-matter/td-p/93110)

The output looks very similar to the results you have, so you might want to try a different program. I can't read the smart data though so, I don't know. Have you used disk utility (located on Ubuntu by default) , it is graphical, has a nice button for smart data, and then shows a pretty green, gray, or red icon indicating if it is good, neutral, or bad.(lol)



Have you tried running fsck? It would be able to run a filesystem scan and determine if there are bad blocks (which I would expect if the drive is dying)

[http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/](http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/)

---

### Post by oldfred on 2012-12-07
All I know from Disk Utility is green is good & it looks like your drive has passed. 

I have not run fsck from Disk Utility. I thought all partitions had to be unmounted. and standard fsck does not do a full check.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

    
Do you have discard & noatime set in fstab and AHCI enabled in BIOS to ensure trim is working? I did not intially so I ran the fstrim and it trimmed some data.

       [https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

---

### Post by NertSkull on 2012-12-08
So, I mounted from live CD and did all the fsck and bad sectors (badblocks) checks and everything comes out clean.  Disk utility says everything is good, no bad sectors, everything is green and ok.

I did however discover I didn't have discard set (I had noatime set).  So I have fixed that problem.  

But even after doing that, I still have had it remount read-only.  So, unless all the scans are wrong, I'm assuming my SSD is fine, but there is something else going on?

Or, alternatively, the scans don't work well on SSD and the drive really is failing.

What should I do next?

---

### Post by oldfred on 2012-12-08
If you did not have discard set, then I think you need the fstrim command like I ran on mine.

Not sure if that would be related or not to your read-only issue or not.

---

### Post by Mark Phelps on 2012-12-08
You need to go to the Crucial forum where they can tell you how to check the Firmware version on your SSD.

Crucial M4s have a KNOWN problem where they become unreliable after a certain number of hours use -- which was fixed with a firmware upgrade.

By check the firmware version, you will be able to see if that problem has already been fixed on yours.

I know because I have a Crucial SSD and applied the firmware update from their site.

---

### Post by duke.tim on 2012-12-08
Since fsck didn't show anything and smart is all good(and green),
The drive is likely having another problem. 
I second doing what Mark Phelps suggested, since that sounds just like what the 'another problem' would be.

---

### Post by NertSkull on 2012-12-12
Thanks Mark Phelps.  That was exactly my issue.  I had old firmware, and I went to the crucial website and figured out how to update it (to the latest 040H).  

Everything is back to normal.  The forums never cease to amaze me in everything they can fix for me.  

So if anyone else is reading this, and you have a crucial m4 approaching 5000 or so hours of on-time, make sure your firmware is update.  I believe what I read said it needs to be anything past the 0009 version.  But search the crucial forums and you can figure it out.

Thanks again.

---


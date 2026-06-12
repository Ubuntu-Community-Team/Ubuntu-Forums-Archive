---
title: "Slow bootup!"
date: 2019-03-03
forum: General Help
---

### Post by peyre on 2019-03-03
I know this may not be the right place to post this, but judging by what I've seen on Google, if I ask it anywhere else I'll get a bunch of irrelevant advice for speeding up Windows: remove adware, disable startup of unneeded services, etc.  So--I think this may be a hardware issue, but maybe someone here has some ideas or at least explanations.

Starting around the release of 18.04, as I recall, my desktop and laptop both started taking a long time to boot up.  I used to boast to my brother about "my 0 to 60" on my Xubuntu laptop once I outfitted it with an SSD--it was fast!  But now it takes forever to boot.  (Also on the laptop the Taskbar comes up for just a half second then disappears and the computer doesn't respond to a lot of my keyboard shortcuts.  I have to Ctrl-Alt-F2 to drop to command line, execute rm -rf ~/.cache, and reboot, and wait a **second** time for it to boot, so this is especially aggravating on the laptop.)

I realize these are old machines (they're from about 2009 and 2008 respectively), but it takes a *long* time to start either of them to start up, it happened to both of them at (about?) the same time, and the hardware hasn't changed on either of them.  Does anyone have any ideas about this issue?

---

### Post by crip720 on 2019-03-03
Two machines giving the same problem near the same time almost sounds more like an update/software issue than hardware.  If you can save data, I would try to reinstall OS or try another live OS on one machine and see if that helps.  I have an older laptop that liked 12.04s, but nothing past that till 16.04 when I could used any except the one I was using since 12.04(LXDE?).

---

### Post by peyre on 2019-03-03
Good idea.  I've tried reinstalling from scratch and it didn't help.  Maybe if I tried an older version.

---

### Post by him610 on 2019-03-03
Yes, I hear you. I too run Xubuntu on some vintage machines, both laptop and desktop; and I have installed SSDs on a couple of them. Sounds like a process running at boot time.  After it has booted up, you can determine what is causing the extended boot process by entering, from the command line, > systemd-analyze blame


After not having booted one system for a few days, this is what mine looked like,
```
$ systemd-analyze blame
         51.598s apt-daily-upgrade.service
         36.488s apt-daily.service
          3.939s systemd-fsck@dev-disk-by\x2duuid-dc8ad078\x2d8577\x2d42a4\x2d85b9\x2dd682be1e574f.s
          2.062s NetworkManager-wait-online.service
          1.170s dev-sda5.device
           418ms speech-dispatcher.service
           416ms NetworkManager.service
....

```

then after an update and reboot, this is what it looked like,
```
$ systemd-analyze blame
          2.148s NetworkManager-wait-online.service
          1.121s dev-sda5.device
           449ms networkd-dispatcher.service
           382ms NetworkManager.service
           359ms udisks2.service
....
```
You can see in the first example, the first two lines take nearly 1-1/2 minutes to complete, and they are not even present in the second example.

---

### Post by peyre on 2019-03-04
**Very** nice, him610!  Thanks for that--I'll give that a try first.

---

### Post by peyre on 2019-03-08
Interesting!  I used systemd-analyze blame to find the services that were hogging my bootup (thanks mucho for that!), and tried tweaking the problematic services.  That actually seemed to make things worse though, yugh!  So I backed up my files and reinstalled 18.04 from scratch.  It worked great, including following a reboot after installing updates.  So then I started installing the programs I had had before (Chromium, Audacious, Flowblade, Skype, etc.), and installed the drivers and firmware for my webcam, rebooted, and...the problem's back!  So maybe this isn't an issue with Xubuntu itself, but with one of the programs I had installed.  I think I'll try installing 18.10 and adding programs back one at a time, rebooting in between, to see where the trouble lies.

---

### Post by Autodave on 2019-03-08
I would stick to 18.04.  If you go with 18.10, then you could possibly go again with the same problem when you have to upgrade in  another month.  Stick with the long term releases.

---

### Post by peyre on 2019-03-08
That might be a good idea.  I like using the latest & greatest, but my laptop seems to be more sensitive to problems with new releases: my desktop isn't nearly as slow to boot up and it doesn't have this miserable problem with the Taskbar and keyboard shortcuts.  Maybe I'll follow your advice and stick with the LTS for my laptop.

---

### Post by peyre on 2019-03-09
Strange (and frustrating).  I reinstalled 18.04 from scratch again, and started installing things one, two, or three at a time and shutting down and starting in between, to see which program was causing this - and timing bootups each time.  (Bootups are 3-4½ minutes.)  Well each time Xubuntu booted fine, no problems.  So I shut it down for the night, and damn me if the same problem didn't reappear when I started in the morning!  wth is going on?

If it helps, these are my notes.

Finish installing 18.04 and updates 
  Shut down - bootup 3:33 minutes
Install Synaptic, Audacious, Flowblade
  Shut down - bootup 3:03
Install gedit, gpicview
  Shut down - bootup 4:04
Install gnome-system-monitor, mpv movie player
  Shut down - bootup 4:34
Install Sony webcam driver (r5u87x)
  Shut down - bootup 3:03
Install SMPlayer, VLC
  Shut down - bootup 3:01
Install Wine
  Shut down - bootup 4:03
Install Skype
  Shut down - bootup 3:01

Also, at some point during the installs (I wish I'd made a note of it), it stopped shutting down on its own - it hangs at the end splash screen.  Strange.

Oh, also: it seems that only half the problem is back.  The Taskbar is there and the computer responds to keyboard shortcuts.  But the icons on my Desktop are missing and when I open something the title bar is missing.  What the?

---

### Post by HermanAB on 2019-03-09
You mentioned Skype.

Nuff sed!

---

### Post by peyre on 2019-03-09
All right.  I was thinking about wiping again and reinstalling Xubuntu but leaving Skype out.  I'll try that now.

---

### Post by peyre on 2019-03-09
Hey, I could try just installing Skype and see if that's the culprit!

---

### Post by jdeca57 on 2019-03-09
I wonder... does your PC really takes 3 minutes to boot after an install of 18.04? And is that from an SSD? My boot is less than 30 seconds, using 18.10.

---

### Post by peyre on 2019-03-09
Yes!  I don't get it.  It's a fresh install of 18.04 onto an SSD.  My desktop is only about a year younger and it only takes about 2-2½ minutes to boot - also an SSD, a newer bigger one, but a much older install of Xubuntu.

This laptop used to boot up surprisingly fast, about like your machine does, when I first set it up with an SSD, but now it takes 3+ minutes.  That was a 90GB SSD.  It died a few months ago so I bought a new 256GB for my desktop and upgraded it to that, then took its 128GB SSD and put it in this machine.  So if anything it should boot faster than before.

Aha!  I think I've found our culprit.  After installing Skype and rebooting, the issue where the Taskbar disappears is back.

These are the results of running [FONT=Courier New]systemd-analyze blame[/FONT] right after bootup, with a fresh install of 18.04 with updates and Skype installed and nothing else:
>          11.149s NetworkManager-wait-online.service
          4.155s dev-sda1.device
          2.164s dev-loop0.device
          2.118s dev-loop1.device
          1.924s snapd.service
          1.459s udisks2.service
           833ms snapd.seeded.service
           694ms systemd-rfkill.service
           606ms networkd-dispatcher.service
           576ms NetworkManager.service
           553ms ModemManager.service
           499ms keyboard-setup.service
           422ms apparmor.service
           410ms accounts-daemon.service
           398ms systemd-udev-trigger.service
           385ms systemd-journald.service
           351ms wpa_supplicant.service
           290ms systemd-journal-flush.service
           277ms speech-dispatcher.service
           273ms rsyslog.service
           267ms apport.service
           224ms lm-sensors.service
           222ms avahi-daemon.service
           222ms pppd-dns.service
           222ms upower.service
           198ms swapfile.swap
           186ms grub-common.service
           175ms plymouth-quit-wait.service
           140ms systemd-resolved.service
           133ms systemd-udevd.service
           127ms systemd-timesyncd.service
           111ms thermald.service
           104ms gpu-manager.service
            94ms snap-skype-66.mount
            91ms systemd-modules-load.service
            90ms [email]user@1000.servic[/email]e
            70ms plymouth-start.service
            65ms systemd-tmpfiles-setup-dev.service
            64ms polkit.service
            64ms snap-core-6405.mount
            62ms dev-mqueue.mount
            61ms systemd-tmpfiles-setup.service
            60ms systemd-remount-fs.service
            58ms ufw.service
            56ms systemd-sysctl.service
            52ms systemd-logind.service
            51ms systemd-random-seed.service
            51ms sys-kernel-debug.mount
            48ms kmod-static-nodes.service
            41ms sys-fs-fuse-connections.mount
            41ms systemd-user-sessions.service
            37ms console-setup.service
            36ms hddtemp.service
            35ms dev-hugepages.mount
            33ms plymouth-read-write.service
            29ms kerneloops.service
            27ms lightdm.service
            25ms sys-kernel-config.mount
            20ms systemd-update-utmp.service
            14ms ureadahead-stop.service
            14ms rtkit-daemon.service
            11ms setvtrgb.service
            11ms systemd-update-utmp-runlevel.service
            10ms [email]systemd-backlight@backlight:acpi_video0.servic[/email]e
            10ms [email]systemd-backlight@backlight:intel_backlight.servic[/email]e
             5ms snapd.socket

---

### Post by pqwoerituytrueiwoq on 2019-03-09
On a live session run a benchmark on your ssd, start with a read-only pass, if that preforms poorly you may be able to fix it with a secure erase (this will wipe the drive of all data) and or a firmware update (sometimes updates will wipe your data, depends on the controller)
make sure the speeds look to be correct for what your drive is rated for, it is possible the drive is nearing the end of it's life
I try not to run a write benchmark unless i need to, as SSDs do have a write limit and i am paranoid about it (bad exp. with a early 16gb ssd)

be sure your sata controller is set for AHCI mode and not IDE mode in your system BIOS, IDE does not support trim (at least with the discard option, not sure about the fstrim command), without trim a ssd will eventually get very slow
```
sudo fstrim -v /
```

[gsmartcontrol]("apt:gsmartcontrol") and [gnome-disks]("apt:gnome-disks") may be of use to you
i use gsmartcontrol to get the diagnostic reports from a drive and gome-disks to to a performance check

---

### Post by jdeca57 on 2019-03-09
Well without the details:

$ systemd-analyze
Startup finished in 2.997s (kernel) + 31.494s (userspace) = 34.492s
graphical.target reached after 11.637s in userspace

---

### Post by peyre on 2019-03-09
Ok, this SSD is a Crucial MX100.  I reseated it and booted with an old Lubuntu CD I keep around for checking SMART data - it has a utility on it for reading that.  both the short and extended test say the disk is healthy..  Of course I know SMART data often doesn't diagnose problems that exist, including if the disk is just about to die.

sudo fstrim -v / results: /: 109.8 GiB (117009385216 bytes) trimmed

GSmartControl extended test result:
```
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-46-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Crucial/Micron MX100/MX200/M5x0/M600 Client SSDs
Device Model:     Crucial_CT128MX100SSD1
Serial Number:    14360D233F89
LU WWN Device Id: 5 00a075 10d233f89
Firmware Version: MU01
User Capacity:    128,034,594,304 bytes [128 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2, ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Sat Mar  9 11:29:01 2019 PST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
AAM feature is:   Unavailable
APM level is:     254 (maximum performance)
Rd look-ahead is: Enabled
Write cache is:   Enabled
ATA Security is:  Disabled, frozen [SEC2]

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
recommended polling time: 	 (   3) minutes.
Conveyance self-test routine
recommended polling time: 	 (   3) minutes.
SCT capabilities: 	       (0x0035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     POSR-K   100   100   000    -    0
  5 Reallocate_NAND_Blk_Cnt PO--CK   100   100   000    -    0
  9 Power_On_Hours          -O--CK   100   100   000    -    15335
 12 Power_Cycle_Count       -O--CK   100   100   000    -    1477
171 Program_Fail_Count      -O--CK   100   100   000    -    0
172 Erase_Fail_Count        -O--CK   100   100   000    -    0
173 Ave_Block-Erase_Count   -O--CK   081   081   000    -    579
174 Unexpect_Power_Loss_Ct  -O--CK   100   100   000    -    229
180 Unused_Reserve_NAND_Blk PO--CK   000   000   000    -    1036
183 SATA_Interfac_Downshift -O--CK   100   100   000    -    0
184 Error_Correction_Count  -O--CK   100   100   000    -    0
187 Reported_Uncorrect      -O--CK   100   100   000    -    0
194 Temperature_Celsius     -O---K   060   046   000    -    40 (Min/Max 13/54)
196 Reallocated_Event_Count -O--CK   100   100   000    -    16
197 Current_Pending_Sector  -O--CK   100   100   000    -    0
198 Offline_Uncorrectable   ----CK   100   100   000    -    0
199 UDMA_CRC_Error_Count    -O--CK   100   100   000    -    3026
202 Percent_Lifetime_Used   P---CK   081   081   000    -    19
206 Write_Error_Rate        -OSR--   100   100   000    -    0
210 Success_RAIN_Recov_Cnt  -O--CK   100   100   000    -    0
246 Total_Host_Sector_Write -O--CK   100   100   000    -    28003501335
247 Host_Program_Page_Count -O--CK   100   100   000    -    887109323
248 Bckgnd_Program_Page_Cnt -O--CK   100   100   000    -    2939109028
                            ||||||_ K auto-keep
                            |||||__ C event count
                            ||||___ R error rate
                            |||____ S speed/performance
                            ||_____ O updated online
                            |______ P prefailure warning

General Purpose Log Directory Version 1
SMART           Log Directory Version 1 [multi-sector log support]
Address    Access  R/W   Size  Description
0x00       GPL,SL  R/O      1  Log Directory
0x01           SL  R/O      1  Summary SMART error log
0x02           SL  R/O     51  Comprehensive SMART error log
0x03       GPL     R/O  16383  Ext. Comprehensive SMART error log
0x04       GPL,SL  R/O    255  Device Statistics log
0x06           SL  R/O      1  SMART self-test log
0x07       GPL     R/O      1  Extended self-test log
0x09           SL  R/W      1  Selective self-test log
0x10       GPL     R/O      1  SATA NCQ Queued Error log
0x11       GPL     R/O      1  SATA Phy Event Counters log
0x13       GPL     R/O      1  SATA NCQ Send and Receive log
0x24       GPL     R/O    429  Current Device Internal Status Data log
0x25       GPL     R/O    145  Saved Device Internal Status Data log
0x30       GPL,SL  R/O      9  IDENTIFY DEVICE data log
0x80-0x9f  GPL,SL  R/W     16  Host vendor specific log
0xa0       GPL     VS    2000  Device vendor specific log
0xa0       SL      VS     208  Device vendor specific log
0xa1-0xbf  GPL,SL  VS       1  Device vendor specific log
0xc0       GPL,SL  VS      80  Device vendor specific log
0xc1-0xdf  GPL,SL  VS       1  Device vendor specific log
0xe0       GPL,SL  R/W      1  SCT Command/Status
0xe1       GPL,SL  R/W      1  SCT Data Transfer

SMART Extended Comprehensive Error Log Version: 1 (16383 sectors)
No Errors Logged

SMART Extended Self-test Log Version: 1 (1 sectors)
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     15335         -
# 2  Extended offline    Completed without error       00%     15334         -
# 3  Short offline       Completed without error       00%     15334         -
# 4  Vendor (0xff)       Completed without error       00%     11092         -
# 5  Vendor (0xff)       Completed without error       00%     10903         -
# 6  Short offline       Completed without error       00%     10053         -
# 7  Conveyance offline  Completed without error       00%      8736         -
# 8  Extended offline    Completed without error       00%      8736         -
# 9  Short offline       Completed without error       00%      8736         -
#10  Conveyance offline  Completed without error       00%      8727         -
#11  Short offline       Completed without error       00%      8727         -
#12  Extended offline    Completed without error       00%      8724         -
#13  Extended offline    Completed without error       00%      8719         -
#14  Vendor (0xff)       Completed without error       00%      8220         -
#15  Vendor (0xff)       Completed without error       00%      8145         -
#16  Extended offline    Completed without error       00%      8095         -
#17  Conveyance offline  Completed without error       00%      8095         -
#18  Extended offline    Completed without error       00%      8095         -
#19  Short offline       Completed without error       00%      8095         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (113246209-113311744)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

SCT Status Version:                  3
SCT Version (vendor specific):       1 (0x0001)
SCT Support Level:                   0
Device State:                        Active (0)
Current Temperature:                    40 Celsius
Power Cycle Min/Max Temperature:     39/40 Celsius
Lifetime    Min/Max Temperature:     13/54 Celsius
Under/Over Temperature Limit Count:   0/0

SCT Temperature History Version:     2
Temperature Sampling Period:         1 minute
Temperature Logging Interval:        1 minute
Min/Max recommended Temperature:      0/70 Celsius
Min/Max Temperature Limit:           -5/75 Celsius
Temperature History Size (Index):    478 (127)

Index    Estimated Time   Temperature Celsius
 128    2019-03-09 03:32    37  ******************
 129    2019-03-09 03:33    37  ******************
 130    2019-03-09 03:34    37  ******************
 131    2019-03-09 03:35     ?  -
 132    2019-03-09 03:36    34  ***************
 133    2019-03-09 03:37    35  ****************
 134    2019-03-09 03:38    35  ****************
 135    2019-03-09 03:39    36  *****************
 ...    ..(  5 skipped).    ..  *****************
 141    2019-03-09 03:45    36  *****************
 142    2019-03-09 03:46    37  ******************
 143    2019-03-09 03:47    37  ******************
 144    2019-03-09 03:48     ?  -
 145    2019-03-09 03:49    36  *****************
 146    2019-03-09 03:50    37  ******************
 ...    ..(  5 skipped).    ..  ******************
 152    2019-03-09 03:56    37  ******************
 153    2019-03-09 03:57    36  *****************
 154    2019-03-09 03:58    37  ******************
 155    2019-03-09 03:59    38  *******************
 156    2019-03-09 04:00    37  ******************
 157    2019-03-09 04:01    37  ******************
 158    2019-03-09 04:02     ?  -
 159    2019-03-09 04:03    36  *****************
 160    2019-03-09 04:04    35  ****************
 161    2019-03-09 04:05    35  ****************
 162    2019-03-09 04:06    36  *****************
 ...    ..(  3 skipped).    ..  *****************
 166    2019-03-09 04:10    36  *****************
 167    2019-03-09 04:11    35  ****************
 168    2019-03-09 04:12    37  ******************
 169    2019-03-09 04:13    37  ******************
 170    2019-03-09 04:14    36  *****************
 171    2019-03-09 04:15    36  *****************
 172    2019-03-09 04:16     ?  -
 173    2019-03-09 04:17    35  ****************
 ...    ..(  2 skipped).    ..  ****************
 176    2019-03-09 04:20    35  ****************
 177    2019-03-09 04:21    36  *****************
 178    2019-03-09 04:22    36  *****************
 179    2019-03-09 04:23    36  *****************
 180    2019-03-09 04:24    35  ****************
 181    2019-03-09 04:25     ?  -
 182    2019-03-09 04:26    35  ****************
 183    2019-03-09 04:27    35  ****************
 184    2019-03-09 04:28    36  *****************
 ...    ..(  2 skipped).    ..  *****************
 187    2019-03-09 04:31    36  *****************
 188    2019-03-09 04:32    37  ******************
 ...    ..(  8 skipped).    ..  ******************
 197    2019-03-09 04:41    37  ******************
 198    2019-03-09 04:42    36  *****************
 199    2019-03-09 04:43    36  *****************
 200    2019-03-09 04:44    37  ******************
 201    2019-03-09 04:45    36  *****************
 ...    ..( 22 skipped).    ..  *****************
 224    2019-03-09 05:08    36  *****************
 225    2019-03-09 05:09    38  *******************
 226    2019-03-09 05:10    39  ********************
 ...    ..(  3 skipped).    ..  ********************
 230    2019-03-09 05:14    39  ********************
 231    2019-03-09 05:15    38  *******************
 232    2019-03-09 05:16    38  *******************
 233    2019-03-09 05:17    39  ********************
 234    2019-03-09 05:18    38  *******************
 235    2019-03-09 05:19    38  *******************
 236    2019-03-09 05:20     ?  -
 237    2019-03-09 05:21    18  -
 238    2019-03-09 05:22    19  -
 239    2019-03-09 05:23    20  *
 240    2019-03-09 05:24    21  **
 241    2019-03-09 05:25    22  ***
 242    2019-03-09 05:26    22  ***
 243    2019-03-09 05:27    23  ****
 244    2019-03-09 05:28    24  *****
 245    2019-03-09 05:29    25  ******
 246    2019-03-09 05:30    25  ******
 247    2019-03-09 05:31    26  *******
 248    2019-03-09 05:32    26  *******
 249    2019-03-09 05:33    27  ********
 250    2019-03-09 05:34    27  ********
 251    2019-03-09 05:35    27  ********
 252    2019-03-09 05:36    29  **********
 253    2019-03-09 05:37    31  ************
 ...    ..(  5 skipped).    ..  ************
 259    2019-03-09 05:43    31  ************
 260    2019-03-09 05:44    32  *************
 ...    ..(  2 skipped).    ..  *************
 263    2019-03-09 05:47    32  *************
 264    2019-03-09 05:48     ?  -
 265    2019-03-09 05:49    33  **************
 ...    ..(  2 skipped).    ..  **************
 268    2019-03-09 05:52    33  **************
 269    2019-03-09 05:53    34  ***************
 270    2019-03-09 05:54    34  ***************
 271    2019-03-09 05:55    34  ***************
 272    2019-03-09 05:56     ?  -
 273    2019-03-09 05:57    34  ***************
 ...    ..(  2 skipped).    ..  ***************
 276    2019-03-09 06:00    34  ***************
 277    2019-03-09 06:01    35  ****************
 ...    ..(  4 skipped).    ..  ****************
 282    2019-03-09 06:06    35  ****************
 283    2019-03-09 06:07     ?  -
 284    2019-03-09 06:08    35  ****************
 285    2019-03-09 06:09    35  ****************
 286    2019-03-09 06:10    35  ****************
 287    2019-03-09 06:11    36  *****************
 ...    ..(  6 skipped).    ..  *****************
 294    2019-03-09 06:18    36  *****************
 295    2019-03-09 06:19    37  ******************
 296    2019-03-09 06:20    38  *******************
 297    2019-03-09 06:21    39  ********************
 298    2019-03-09 06:22    39  ********************
 299    2019-03-09 06:23    38  *******************
 300    2019-03-09 06:24    37  ******************
 301    2019-03-09 06:25    36  *****************
 302    2019-03-09 06:26     ?  -
 303    2019-03-09 06:27    35  ****************
 304    2019-03-09 06:28    35  ****************
 305    2019-03-09 06:29    35  ****************
 306    2019-03-09 06:30    36  *****************
 ...    ..(  5 skipped).    ..  *****************
 312    2019-03-09 06:36    36  *****************
 313    2019-03-09 06:37    37  ******************
 ...    ..(  2 skipped).    ..  ******************
 316    2019-03-09 06:40    37  ******************
 317    2019-03-09 06:41     ?  -
 318    2019-03-09 06:42    37  ******************
 ...    ..(  5 skipped).    ..  ******************
 324    2019-03-09 06:48    37  ******************
 325    2019-03-09 06:49     ?  -
 326    2019-03-09 06:50    37  ******************
 327    2019-03-09 06:51    37  ******************
 328    2019-03-09 06:52    38  *******************
 329    2019-03-09 06:53    39  ********************
 330    2019-03-09 06:54    38  *******************
 ...    ..(  9 skipped).    ..  *******************
 340    2019-03-09 07:04    38  *******************
 341    2019-03-09 07:05    37  ******************
 342    2019-03-09 07:06    36  *****************
 343    2019-03-09 07:07    36  *****************
 344    2019-03-09 07:08    36  *****************
 345    2019-03-09 07:09    35  ****************
 346    2019-03-09 07:10    35  ****************
 347    2019-03-09 07:11    35  ****************
 348    2019-03-09 07:12    34  ***************
 ...    ..(  4 skipped).    ..  ***************
 353    2019-03-09 07:17    34  ***************
 354    2019-03-09 07:18    33  **************
 355    2019-03-09 07:19    33  **************
 356    2019-03-09 07:20    34  ***************
 357    2019-03-09 07:21    34  ***************
 358    2019-03-09 07:22    34  ***************
 359    2019-03-09 07:23    35  ****************
 360    2019-03-09 07:24    35  ****************
 361    2019-03-09 07:25    36  *****************
 362    2019-03-09 07:26     ?  -
 363    2019-03-09 07:27    36  *****************
 364    2019-03-09 07:28    36  *****************
 365    2019-03-09 07:29    37  ******************
 ...    ..(  9 skipped).    ..  ******************
 375    2019-03-09 07:39    37  ******************
 376    2019-03-09 07:40    36  *****************
 377    2019-03-09 07:41    36  *****************
 378    2019-03-09 07:42    36  *****************
 379    2019-03-09 07:43     ?  -
 380    2019-03-09 07:44    35  ****************
 ...    ..(  3 skipped).    ..  ****************
 384    2019-03-09 07:48    35  ****************
 385    2019-03-09 07:49    36  *****************
 386    2019-03-09 07:50    36  *****************
 387    2019-03-09 07:51    36  *****************
 388    2019-03-09 07:52    37  ******************
 ...    ..(  3 skipped).    ..  ******************
 392    2019-03-09 07:56    37  ******************
 393    2019-03-09 07:57    38  *******************
 ...    ..( 10 skipped).    ..  *******************
 404    2019-03-09 08:08    38  *******************
 405    2019-03-09 08:09    37  ******************
 406    2019-03-09 08:10    38  *******************
 407    2019-03-09 08:11    37  ******************
 408    2019-03-09 08:12     ?  -
 409    2019-03-09 08:13    35  ****************
 410    2019-03-09 08:14    36  *****************
 411    2019-03-09 08:15    36  *****************
 412    2019-03-09 08:16    36  *****************
 413    2019-03-09 08:17    37  ******************
 ...    ..(  2 skipped).    ..  ******************
 416    2019-03-09 08:20    37  ******************
 417    2019-03-09 08:21    38  *******************
 ...    ..(  4 skipped).    ..  *******************
 422    2019-03-09 08:26    38  *******************
 423    2019-03-09 08:27     ?  -
 424    2019-03-09 08:28    38  *******************
 425    2019-03-09 08:29    38  *******************
 426    2019-03-09 08:30    39  ********************
 427    2019-03-09 08:31    40  *********************
 428    2019-03-09 08:32    39  ********************
 429    2019-03-09 08:33    39  ********************
 430    2019-03-09 08:34    38  *******************
 431    2019-03-09 08:35     ?  -
 432    2019-03-09 08:36     ?  -
 433    2019-03-09 08:37    30  ***********
 434    2019-03-09 08:38    31  ************
 435    2019-03-09 08:39    32  *************
 436    2019-03-09 08:40    34  ***************
 437    2019-03-09 08:41    37  ******************
 438    2019-03-09 08:42    36  *****************
 439    2019-03-09 08:43    39  ********************
 440    2019-03-09 08:44    39  ********************
 441    2019-03-09 08:45    39  ********************
 442    2019-03-09 08:46     ?  -
 443    2019-03-09 08:47    38  *******************
 444    2019-03-09 08:48    38  *******************
 445    2019-03-09 08:49    38  *******************
 446    2019-03-09 08:50    39  ********************
 ...    ..(  3 skipped).    ..  ********************
 450    2019-03-09 08:54    39  ********************
 451    2019-03-09 08:55     ?  -
 452    2019-03-09 08:56    39  ********************
 ...    ..(  5 skipped).    ..  ********************
 458    2019-03-09 09:02    39  ********************
 459    2019-03-09 09:03    40  *********************
 ...    ..( 13 skipped).    ..  *********************
 473    2019-03-09 09:17    40  *********************
 474    2019-03-09 09:18    39  ********************
 475    2019-03-09 09:19    40  *********************
 476    2019-03-09 09:20    40  *********************
 477    2019-03-09 09:21    40  *********************
   0    2019-03-09 09:22    36  *****************
 ...    ..(  2 skipped).    ..  *****************
   3    2019-03-09 09:25    36  *****************
   4    2019-03-09 09:26    37  ******************
   5    2019-03-09 09:27    38  *******************
   6    2019-03-09 09:28    39  ********************
   7    2019-03-09 09:29    39  ********************
   8    2019-03-09 09:30    38  *******************
   9    2019-03-09 09:31    37  ******************
  10    2019-03-09 09:32    37  ******************
  11    2019-03-09 09:33    37  ******************
  12    2019-03-09 09:34    36  *****************
 ...    ..(  2 skipped).    ..  *****************
  15    2019-03-09 09:37    36  *****************
  16    2019-03-09 09:38    35  ****************
  17    2019-03-09 09:39     ?  -
  18    2019-03-09 09:40    35  ****************
 ...    ..(  4 skipped).    ..  ****************
  23    2019-03-09 09:45    35  ****************
  24    2019-03-09 09:46    37  ******************
  25    2019-03-09 09:47    38  *******************
  26    2019-03-09 09:48    38  *******************
  27    2019-03-09 09:49    38  *******************
  28    2019-03-09 09:50     ?  -
  29    2019-03-09 09:51    20  *
  30    2019-03-09 09:52    21  **
  31    2019-03-09 09:53    24  *****
  32    2019-03-09 09:54    26  *******
  33    2019-03-09 09:55    26  *******
  34    2019-03-09 09:56    26  *******
  35    2019-03-09 09:57    27  ********
  36    2019-03-09 09:58    27  ********
  37    2019-03-09 09:59    28  *********
  38    2019-03-09 10:00    28  *********
  39    2019-03-09 10:01    29  **********
  40    2019-03-09 10:02    29  **********
  41    2019-03-09 10:03    30  ***********
  42    2019-03-09 10:04    30  ***********
  43    2019-03-09 10:05    31  ************
  44    2019-03-09 10:06    31  ************
  45    2019-03-09 10:07    32  *************
  46    2019-03-09 10:08    32  *************
  47    2019-03-09 10:09    32  *************
  48    2019-03-09 10:10    33  **************
 ...    ..( 11 skipped).    ..  **************
  60    2019-03-09 10:22    33  **************
  61    2019-03-09 10:23     ?  -
  62    2019-03-09 10:24    33  **************
  63    2019-03-09 10:25    33  **************
  64    2019-03-09 10:26    34  ***************
  65    2019-03-09 10:27    34  ***************
  66    2019-03-09 10:28    35  ****************
  67    2019-03-09 10:29    35  ****************
  68    2019-03-09 10:30    35  ****************
  69    2019-03-09 10:31    36  *****************
  70    2019-03-09 10:32    35  ****************
  71    2019-03-09 10:33    36  *****************
 ...    ..(  6 skipped).    ..  *****************
  78    2019-03-09 10:40    36  *****************
  79    2019-03-09 10:41    35  ****************
  80    2019-03-09 10:42     ?  -
  81    2019-03-09 10:43    35  ****************
 ...    ..(  4 skipped).    ..  ****************
  86    2019-03-09 10:48    35  ****************
  87    2019-03-09 10:49     ?  -
  88    2019-03-09 10:50    35  ****************
  89    2019-03-09 10:51    36  *****************
 ...    ..(  2 skipped).    ..  *****************
  92    2019-03-09 10:54    36  *****************
  93    2019-03-09 10:55    37  ******************
  94    2019-03-09 10:56    37  ******************
  95    2019-03-09 10:57     ?  -
  96    2019-03-09 10:58    36  *****************
 ...    ..(  5 skipped).    ..  *****************
 102    2019-03-09 11:04    36  *****************
 103    2019-03-09 11:05     ?  -
 104    2019-03-09 11:06    36  *****************
 ...    ..(  5 skipped).    ..  *****************
 110    2019-03-09 11:12    36  *****************
 111    2019-03-09 11:13     ?  -
 112    2019-03-09 11:14    36  *****************
 ...    ..(  2 skipped).    ..  *****************
 115    2019-03-09 11:17    36  *****************
 116    2019-03-09 11:18    37  ******************
 ...    ..(  4 skipped).    ..  ******************
 121    2019-03-09 11:23    37  ******************
 122    2019-03-09 11:24    36  *****************
 123    2019-03-09 11:25     ?  -
 124    2019-03-09 11:26    36  *****************
 125    2019-03-09 11:27    36  *****************
 126    2019-03-09 11:28    36  *****************
 127    2019-03-09 11:29    37  ******************

SCT Error Recovery Control command not supported

Device Statistics (GP Log 0x04)
Page  Offset Size        Value Flags Description
0x01  =====  =               =  ===  == General Statistics (rev 2) ==
0x01  0x008  4            1477  ---  Lifetime Power-On Resets
0x01  0x010  4           15335  ---  Power-on Hours
0x01  0x018  6     28003501335  ---  Logical Sectors Written
0x01  0x020  6       946501281  ---  Number of Write Commands
0x01  0x028  6     55471058399  ---  Logical Sectors Read
0x01  0x030  6       863631449  ---  Number of Read Commands
0x04  =====  =               =  ===  == General Errors Statistics (rev 1) ==
0x04  0x008  4               0  ---  Number of Reported Uncorrectable Errors
0x04  0x010  4            1254  ---  Resets Between Cmd Acceptance and Completion
0x05  =====  =               =  ===  == Temperature Statistics (rev 1) ==
0x05  0x008  1              40  ---  Current Temperature
0x05  0x010  1              34  ---  Average Short Term Temperature
0x05  0x018  1              35  ---  Average Long Term Temperature
0x05  0x020  1              54  ---  Highest Temperature
0x05  0x028  1              13  ---  Lowest Temperature
0x05  0x030  1              51  ---  Highest Average Short Term Temperature
0x05  0x038  1              23  ---  Lowest Average Short Term Temperature
0x05  0x040  1              47  ---  Highest Average Long Term Temperature
0x05  0x048  1              25  ---  Lowest Average Long Term Temperature
0x05  0x050  4               -  ---  Time in Over-Temperature
0x05  0x058  1              70  ---  Specified Maximum Operating Temperature
0x05  0x060  4               -  ---  Time in Under-Temperature
0x05  0x068  1               0  ---  Specified Minimum Operating Temperature
0x06  =====  =               =  ===  == Transport Statistics (rev 1) ==
0x06  0x008  4               1  ---  Number of Hardware Resets
0x06  0x010  4               0  ---  Number of ASR Events
0x06  0x018  4            3026  ---  Number of Interface CRC Errors
0x07  =====  =               =  ===  == Solid State Device Statistics (rev 1) ==
0x07  0x008  1               6  N--  Percentage Used Endurance Indicator
                                |||_ C monitored condition met
                                ||__ D supports DSN
                                |___ N normalized value

SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x0001  4            0  Command failed due to ICRC error
0x000a  4            1  Device-to-host register FISes sent due to a COMRESET
```

---

### Post by peyre on 2019-03-09
> **jdeca57 said:**
> Well without the details:

$ systemd-analyze
Startup finished in 2.997s (kernel) + 31.494s (userspace) = 34.492s
graphical.target reached after 11.637s in userspace

So what's taking 3+ minutes?  This is just to the point where it challenges for a password - doesn't count time to sign me in and pull up my profile.

---

### Post by peyre on 2019-03-09
I'm trying going back to 17.10 now to see what happens.

---

### Post by jdeca57 on 2019-03-09
> **peyre said:**
> So what's taking 3+ minutes?  This is just to the point where it challenges for a password - doesn't count time to sign me in and pull up my profile.
Well, these are seconds, not minutes. After 11 seconds I have a login screen and of course typing in the password may take more time than the 20+ seconds to finish the boot.

---

### Post by peyre on 2019-03-09
> **jdeca57 said:**
> Well, these are seconds, not minutes. After 11 seconds I have a login screen and of course typing in the password may take more time than the 20+ seconds to finish the boot.

OHH!  That's on your system.  Sorry, I misunderstood.

---

### Post by peyre on 2019-03-09
Wow, what a difference!  Xubuntu 17.10 with all those programs installed (including Skype), and my boot time's cut in half: 1:18 this time around.

One difference though: the webcam driver won't install.  Says it can't find it.  Hm, maybe the r5u87x driver makes some kind of difference?  (But I didn't install it earlier on 18.04...)

---

### Post by vidtek on 2019-03-10
> **peyre said:**
> Wow, what a difference!  Xubuntu 17.10 with all those programs installed (including Skype), and my boot time's cut in half: 1:18 this time around.

One difference though: the webcam driver won't install.  Says it can't find it.  Hm, maybe the r5u87x driver makes some kind of difference?  (But I didn't install it earlier on 18.04...)

Peyre-  Maybe it's not the actual distribution, but the kernel that particular flavour is using.

You could try installing UKUU kernel update utility and seeing if after installing your preferred flavour of Ubuntu, swapping kernels make a difference.  You may even find your camera works on 

some but not others.

Just a thought, Tony.

---

### Post by peyre on 2019-03-10
That could be!  I seem to recall having some kind of trouble with Skype that cleared up - don't recall whether the change was between 17.10 and 18.04 or 18.04 and 17.10.

The odd thing about the webcam is that the error returned is "Unable to locate package r5u87x".  I'm puzzled why it would have trouble *finding* the package - I would've expected it to download it and then have trouble installing it.  I was able to download and install r5u87x earlier yesterday when I was running 18.04.  Is there a way I can download the package for easy installation later?

I was able to skype with Mom last night by plugging in a USB webcam, but that's obviously not good as a permanent solution.

---

### Post by pqwoerituytrueiwoq on 2019-03-10
that driver has a ppa, i'm guess you forgot you added it in the past
[https://launchpad.net/~r5u87x-loader/+archive/ubuntu/ppa](https://launchpad.net/~r5u87x-loader/+archive/ubuntu/ppa)

---

### Post by peyre on 2019-03-10
Well, the instructions I've always followed (from [http://ubuntuforums.org/showthread.php?t=1744189http://]("http://ubuntuforums.org/showthread.php?t=1744189http://")) to install it run as follows:

sudo add-apt-repository ppa:r5u87x-loader/ppa
sudo apt-get update
sudo apt-get install r5u87x
sudo /usr/share/r5u87x/r5u87x-download-firmware.sh 

The first two run fine, but the third says it can't locate it...if I do it in 17.10.  In 18.04 it runs successfully.

---

### Post by pqwoerituytrueiwoq on 2019-03-10
this is the 64bit deb  file for 17.10
[https://launchpad.net/~r5u87x-loader/+archive/ubuntu/ppa/+files/r5u87x_0.2.1+r64+dfsg1-0ppa12_amd64.deb](https://launchpad.net/~r5u87x-loader/+archive/ubuntu/ppa/+files/r5u87x_0.2.1+r64+dfsg1-0ppa12_amd64.deb)
you can manually install it, no idea why it can not find it after adding the ppa, if something were to go wrong i would expect it on line 4 not 3

---

### Post by peyre on 2019-03-10
Woohoo!  Thanks!  Yoinked it.  I'll try installing it.

---

### Post by vidtek on 2019-03-11
pqwoerituytrueiwoq-

Off-topic, sorry, just saw your signature, are you still maintaining the PHP Scanner software?
If so, can it be made to work with the existing web server in Mythtv?

Cheers, Tony.

---

### Post by pqwoerituytrueiwoq on 2019-03-11
You should just be able to slap it into a sub directory on the server or run it under a different port

---

### Post by peyre on 2019-03-11
Thank you, pqwoerituytrueiwoq!  It installed and I was able to complete the installation of driver and firmware.  The webcam lights up when I open Skype, but neither Skype nor Cheese can find the webcam.

Taking stock of the options, I think I'll stick with this install of 17.10 for now.  All told, it's more important to have a decent bootup (1.5 minutes vs. 10 after second boot) than to be able to use the built-in webcam for our weekly Skype sessions,  I can use my work laptop or plug in a USB webcam, and who knows, this thing might spontaneously start working again at some point.  When 19.04 comes out I might try upgrading to that and see what happens (imaging this first so I can fall back to a decent install if 19.04 chokes on this thing too).

---

### Post by vidtek on 2019-03-12
Thanks, I'll try it and let you know.
Tony

---


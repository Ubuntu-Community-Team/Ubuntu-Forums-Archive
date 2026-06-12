---
title: "Hardlock with many ^@ in syslog"
date: 2014-10-21
forum: General Help
---

### Post by alexey-brusenskiy on 2014-10-21
I am fairly new to ubuntu (~1 year of running a server) and from Russia (I appologise for my grammar and punctuation in advance),
For long time i had to reboot server manualy(because of the freeze), lackily it's  at home, but as soon as i had time to dig a little into logs, I found this error, that I couldn't search for or figure out myself. Google doesn't understand those simbols, I hoped that in the forum it will find someone with this sort of an error:
*/var/log/syslog.1*
```
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
```
*uname -a*
```
Linux zonda-serv 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
Any more logs needed? (I will add here)
Is it more of a hardware problem?

---

### Post by tgalati4 on 2014-10-21
Looks like hardware to me.  Clean out the machine, reseat everything.  Run *memtest* for 30 complete cycles.

---

### Post by alexey-brusenskiy on 2014-10-22
30 cycles of memtest86+ 4.2 is about a day of testing!! Really?

I have reseated(unplugged and plugged back with a bit of left-to-right up-to-down movements - to clean the contacts) memory and sata cables. There is a PCI network card did you mean this one too? Or I don't get it... :confused:

---

### Post by tgalati4 on 2014-10-22
Yes.  30 cycles represents a large population.  If it passes, then you can be pretty sure your RAM and motherboard data path are working.  Network cards can cause data bus errors, so yes, move the card to another slot if possible.  The syslog error looks like a buffer overflow from either a stuck process or a hardware error.  What was the error before that or in older syslog files?

If you are still having problems, take out the network card and any extraneous stuff.  Get your system down to a bare minimum.  Check the voltages of your PSU in BIOS or with a voltmeter.

---

### Post by alexey-brusenskiy on 2014-10-22
I am not yet a  great debugger, so if you can give me some filter of what to look for in the syslog (e.g. /var/log/syslog | grep fail), I would print it in here. I wasn't able to see anything strange or errors of some kind that could lead to this.
I can even add some debug feature to rsyslog (or any other logger), if you can give howto :) (or a link)

---

### Post by tgalati4 on 2014-10-22
Hardware errors generally don't leave meaningful syslog entries.  And if they do, they are misleading entries.  So if you can't grep any errors in your syslog, then you need to validate your hardware and isolate the possible causes.  What is the SMART status of your hard drive?

```
sudo smartctl -a /dev/sda
```

---

### Post by alexey-brusenskiy on 2014-10-23
sda is not my primary hard drive.
```
sudo smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-37-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue Serial ATA
Device Model:     WDC WD1600AAJS-00L7A0
Serial Number:    WD-WMAV34827745
LU WWN Device Id: 5 0014ee 0abee5491
Firmware Version: 01.03E01
User Capacity:    160 041 885 696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.5, 3.0 Gb/s
Local Time is:    Thu Oct 23 22:23:10 2014 MSK
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 3180) seconds.
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
recommended polling time:      (  41) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       20540
  3 Spin_Up_Time            0x0027   141   136   021    Pre-fail  Always       -       3925
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       210
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   037   037   000    Old_age   Always       -       46389
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       150
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       86
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       210
194 Temperature_Celsius     0x0022   108   099   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

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
and
sdb is not /
```
sudo smartctl -a /dev/sdb
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-37-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue Serial ATA
Device Model:     WDC WD1600AAJS-00L7A0
Serial Number:    WD-WMAV35212414
LU WWN Device Id: 5 0014ee 0abee555b
Firmware Version: 01.03E01
User Capacity:    160 041 885 696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.5, 3.0 Gb/s
Local Time is:    Thu Oct 23 22:24:03 2014 MSK
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 3180) seconds.
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
recommended polling time:      (  41) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   139   134   021    Pre-fail  Always       -       4033
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       210
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   037   037   000    Old_age   Always       -       46355
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       150
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       86
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       210
194 Temperature_Celsius     0x0022   108   099   000    Old_age   Always       -       35
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

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
sdc is one. And it's SSD :)
```
sudo smartctl -a /dev/sdc
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-37-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     SandForce Driven SSDs
Device Model:     Corsair Force 3 SSD
Serial Number:    1208820100000712058A
LU WWN Device Id: 0 000000 000000000
Firmware Version: 1.3.3
User Capacity:    90 028 302 336 bytes [90,0 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS, ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Thu Oct 23 22:24:14 2014 MSK
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
data collection:         ( 2097) seconds.
Offline data collection
capabilities:              (0x7f) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Abort Offline collection upon new
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
recommended polling time:      (  48) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x0021)    SCT Status supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   094   094   050    Pre-fail  Always       -       0/33354282
  5 Retired_Block_Count     0x0033   100   100   003    Pre-fail  Always       -       0
  9 Power_On_Hours_and_Msec 0x0032   075   075   000    Old_age   Always       -       22028h+22m+48.650s
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       104
171 Program_Fail_Count      0x0032   000   000   000    Old_age   Always       -       0
172 Erase_Fail_Count        0x0032   000   000   000    Old_age   Always       -       0
174 Unexpect_Power_Loss_Ct  0x0030   000   000   000    Old_age   Offline      -       21
177 Wear_Range_Delta        0x0000   000   000   000    Old_age   Offline      -       6
181 Program_Fail_Count      0x0032   000   000   000    Old_age   Always       -       0
182 Erase_Fail_Count        0x0032   000   000   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   030   030   000    Old_age   Always       -       30 (Min/Max 30/30)
195 ECC_Uncorr_Error_Count  0x001c   120   120   000    Old_age   Offline      -       0/33354282
196 Reallocated_Event_Count 0x0033   100   100   003    Pre-fail  Always       -       0
201 Unc_Soft_Read_Err_Rate  0x001c   120   120   000    Old_age   Offline      -       0/33354282
204 Soft_ECC_Correct_Rate   0x001c   120   120   000    Old_age   Offline      -       0/33354282
230 Life_Curve_Status       0x0013   100   100   000    Pre-fail  Always       -       100
231 SSD_Life_Left           0x0013   100   100   010    Pre-fail  Always       -       0
233 SandForce_Internal      0x0000   000   000   000    Old_age   Offline      -       7125
234 SandForce_Internal      0x0032   000   000   000    Old_age   Always       -       5442
241 Lifetime_Writes_GiB     0x0032   000   000   000    Old_age   Always       -       5442
242 Lifetime_Reads_GiB      0x0032   000   000   000    Old_age   Always       -       11871

SMART Error Log not supported

SMART Self-test Log not supported

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

### Post by tgalati4 on 2014-10-24
So, your drives look OK.  Does your SSD drive really have 22,000 power-on hours?  That seems like a lot.  2.5 years of 24/7 use.  Perhaps it has developed a subtle problem and it can't write to syslog anymore.  How full is the drive?

```
df -h 
```

---

### Post by alexey-brusenskiy on 2014-10-25
It writes to syslog and I got an error in the first post from it. 
```
/dev/sdc1         75G          60G   12G           85% /
none             4,0K            0  4,0K            0% /sys/fs/cgroup
udev             1,9G         4,0K  1,9G            1% /dev
tmpfs            383M          12M  371M            4% /run
none              50M            0   50M            0% /run/lock
none             1,9G         120K  1,9G            1% /run/shm
none             100M            0  100M            0% /run/user


```

---

### Post by tgalati4 on 2014-10-25
Normally 15% free space would not be a problem on a spinning hard drive, but on an SSD with a wear-leveling controller, it's possible that it can't keep up anymore with moving bits around.

What was the error in the first post?  I don't see any error.  Just a bunch of gibberish in the syslog, not a specific error at a specific time.  That tells me that either the syslog file is damaged and you are looking at a mis-directed sector, or that the logger really is writing ^@ to the file because it is broken.  Neither is what I would consider a kernel software error.

---

### Post by alexey-brusenskiy on 2014-10-27
This gibberish, not always present in the logs before crush.
If there were any specific error, I would've been asking google about it.... 
Now, I can give logs from syslog before the recent crush. 
Last time there were no keyboard and monitor activity, but I could access server by ssh. 
syslog
```
Oct 26 22:43:57 zonda-serv smbd[5489]: [2014/10/26 22:43:57.421917,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
Oct 26 22:43:57 zonda-serv smbd[5489]:   failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
Oct 26 22:44:14 zonda-serv kernel: [24189.119221] init: zentyal.webadmin-uwsgi main process (15756) terminated with status 1
Oct 26 22:44:14 zonda-serv kernel: [24189.119252] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:44:15 zonda-serv kernel: [24189.792145] init: zentyal.webadmin-uwsgi main process (15879) terminated with status 1
Oct 26 22:44:15 zonda-serv kernel: [24189.792179] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:44:44 zonda-serv kernel: [24219.131787] init: zentyal.webadmin-uwsgi main process (15892) terminated with status 255
Oct 26 22:44:44 zonda-serv kernel: [24219.131825] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:44:45 zonda-serv kernel: [24219.804500] init: zentyal.webadmin-uwsgi main process (16013) terminated with status 255
Oct 26 22:44:45 zonda-serv kernel: [24219.804536] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:44:57 zonda-serv dhcpd: DHCPINFORM from 192.168.137.4 via eth0
Oct 26 22:44:57 zonda-serv dhcpd: DHCPACK to 192.168.137.4 (00:1d:7d:09:27:30) via eth0
Oct 26 22:45:01 zonda-serv CRON[16086]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 26 22:45:01 zonda-serv CRON[16088]: (root) CMD (/usr/share/zentyal-users/slave-sync)
Oct 26 22:45:01 zonda-serv postfix/sendmail[16090]: warning: /etc/postfix/main.cf, line 104: overriding earlier entry: smtpd_sasl_local_domain=
Oct 26 22:45:01 zonda-serv postfix/postdrop[16091]: warning: /etc/postfix/main.cf, line 104: overriding earlier entry: smtpd_sasl_local_domain=
Oct 26 22:45:14 zonda-serv kernel: [24249.162983] init: zentyal.webadmin-uwsgi main process (16017) terminated with status 1
Oct 26 22:45:14 zonda-serv kernel: [24249.163033] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:45:15 zonda-serv kernel: [24249.843196] init: zentyal.webadmin-uwsgi main process (16149) terminated with status 1
Oct 26 22:45:15 zonda-serv kernel: [24249.843234] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:45:24 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.33 from 90:18:7c:f2:3a:6c (android-a6c190c669866412) via eth0
Oct 26 22:45:24 zonda-serv dhcpd: DHCPACK on 192.168.137.33 to 90:18:7c:f2:3a:6c (android-a6c190c669866412) via eth0
Oct 26 22:45:44 zonda-serv kernel: [24279.134430] init: zentyal.webadmin-uwsgi main process (16160) terminated with status 1
Oct 26 22:45:44 zonda-serv kernel: [24279.134534] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:46:14 zonda-serv kernel: [24309.131616] init: zentyal.webadmin-uwsgi main process (16281) terminated with status 1
Oct 26 22:46:14 zonda-serv kernel: [24309.131661] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:46:17 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.3 from 00:e0:4c:39:0a:08 via eth0
Oct 26 22:46:17 zonda-serv dhcpd: DHCPACK on 192.168.137.3 to 00:e0:4c:39:0a:08 via eth0
Oct 26 22:46:43 zonda-serv named[4553]: success resolving '29.146.109.218.in-addr.arpa/PTR' (in '109.218.in-addr.arpa'?) after reducing the advertised EDNS UDP packet size to 512 octets
Oct 26 22:46:44 zonda-serv kernel: [24339.119420] init: zentyal.webadmin-uwsgi main process (16412) terminated with status 1
Oct 26 22:46:44 zonda-serv kernel: [24339.119454] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:46:45 zonda-serv kernel: [24339.794401] init: zentyal.webadmin-uwsgi main process (16533) terminated with status 1
Oct 26 22:46:45 zonda-serv kernel: [24339.794432] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:47:14 zonda-serv kernel: [24369.119876] init: zentyal.webadmin-uwsgi main process (16537) terminated with status 1
Oct 26 22:47:14 zonda-serv kernel: [24369.119908] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:47:15 zonda-serv kernel: [24369.801670] init: zentyal.webadmin-uwsgi main process (16674) terminated with status 1
Oct 26 22:47:15 zonda-serv kernel: [24369.801771] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:47:38 zonda-serv kernel: [24392.432123] audit_printk_skb: 24 callbacks suppressed
Oct 26 22:47:38 zonda-serv kernel: [24392.432136] type=1400 audit(1414352857.999:777): apparmor="ALLOWED" operation="capable" profile="/usr/sbin/sssd" pid=5528 comm="sssd_be" capability=36  capname="block_suspend"
Oct 26 22:47:44 zonda-serv kernel: [24399.133537] init: zentyal.webadmin-uwsgi main process (16678) terminated with status 1
Oct 26 22:47:44 zonda-serv kernel: [24399.133571] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:47:44 zonda-serv kernel: [24399.158976] type=1400 audit(1414352864.723:778): apparmor="ALLOWED" operation="open" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=16802 comm="ldap_child" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Oct 26 22:47:44 zonda-serv kernel: [24399.159006] type=1400 audit(1414352864.723:779): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=16802 comm="ldap_child" requested_mask="k" denied_mask="k" fsuid=0 ouid=0
Oct 26 22:47:44 zonda-serv kernel: [24399.159048] type=1400 audit(1414352864.723:780): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=16802 comm="ldap_child" requested_mask="k" denied_mask="k" fsuid=0 ouid=0
Oct 26 22:47:44 zonda-serv kernel: [24399.159181] type=1400 audit(1414352864.723:781): apparmor="ALLOWED" operation="open" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=16802 comm="ldap_child" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Oct 26 22:47:44 zonda-serv kernel: [24399.159200] type=1400 audit(1414352864.723:782): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=16802 comm="ldap_child" requested_mask="k" denied_mask="k" fsuid=0 ouid=0
Oct 26 22:47:44 zonda-serv kernel: [24399.159249] type=1400 audit(1414352864.723:783): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=16802 comm="ldap_child" requested_mask="k" denied_mask="k" fsuid=0 ouid=0
Oct 26 22:47:44 zonda-serv kernel: [24399.172452] type=1400 audit(1414352864.739:784): apparmor="ALLOWED" operation="open" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=16802 comm="ldap_child" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Oct 26 22:47:44 zonda-serv kernel: [24399.172480] type=1400 audit(1414352864.739:785): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=16802 comm="ldap_child" requested_mask="k" denied_mask="k" fsuid=0 ouid=0
Oct 26 22:47:44 zonda-serv kernel: [24399.172537] type=1400 audit(1414352864.739:786): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=16802 comm="ldap_child" requested_mask="k" denied_mask="k" fsuid=0 ouid=0
Oct 26 22:48:14 zonda-serv kernel: [24429.121751] init: zentyal.webadmin-uwsgi main process (16800) terminated with status 1
Oct 26 22:48:14 zonda-serv kernel: [24429.121787] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:48:15 zonda-serv kernel: [24429.795374] init: zentyal.webadmin-uwsgi main process (16933) terminated with status 1
Oct 26 22:48:15 zonda-serv kernel: [24429.795439] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:48:44 zonda-serv kernel: [24459.121186] init: zentyal.webadmin-uwsgi main process (16937) terminated with status 1
Oct 26 22:48:44 zonda-serv kernel: [24459.121223] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:48:45 zonda-serv kernel: [24459.803013] init: zentyal.webadmin-uwsgi main process (17058) terminated with status 1
Oct 26 22:48:45 zonda-serv kernel: [24459.803177] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:49:14 zonda-serv kernel: [24489.124049] init: zentyal.webadmin-uwsgi main process (17071) terminated with status 1
Oct 26 22:49:14 zonda-serv kernel: [24489.124080] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:49:15 zonda-serv kernel: [24489.801024] init: zentyal.webadmin-uwsgi main process (17193) terminated with status 255
Oct 26 22:49:15 zonda-serv kernel: [24489.801067] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:49:44 zonda-serv kernel: [24519.120414] init: zentyal.webadmin-uwsgi main process (17197) terminated with status 1
Oct 26 22:49:44 zonda-serv kernel: [24519.120445] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:49:45 zonda-serv kernel: [24519.803887] init: zentyal.webadmin-uwsgi main process (17318) terminated with status 1
Oct 26 22:49:45 zonda-serv kernel: [24519.803921] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:50:01 zonda-serv CRON[17399]: (root) CMD (/usr/share/zentyal-users/slave-sync)
Oct 26 22:50:01 zonda-serv postfix/sendmail[17401]: warning: /etc/postfix/main.cf, line 104: overriding earlier entry: smtpd_sasl_local_domain=
Oct 26 22:50:01 zonda-serv postfix/postdrop[17402]: warning: /etc/postfix/main.cf, line 104: overriding earlier entry: smtpd_sasl_local_domain=
Oct 26 22:50:14 zonda-serv kernel: [24549.138453] init: zentyal.webadmin-uwsgi main process (17331) terminated with status 255
Oct 26 22:50:14 zonda-serv kernel: [24549.138485] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:50:44 zonda-serv kernel: [24579.131835] init: zentyal.webadmin-uwsgi main process (17458) terminated with status 1
Oct 26 22:50:44 zonda-serv kernel: [24579.131870] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:51:14 zonda-serv kernel: [24609.116965] init: zentyal.webadmin-uwsgi main process (17579) terminated with status 255
Oct 26 22:51:14 zonda-serv kernel: [24609.117016] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:51:44 zonda-serv kernel: [24639.119343] init: zentyal.webadmin-uwsgi main process (17710) terminated with status 255
Oct 26 22:51:44 zonda-serv kernel: [24639.119429] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:51:59 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.200 from 1c:7e:e5:2a:08:e4 via eth0
Oct 26 22:51:59 zonda-serv dhcpd: DHCPACK on 192.168.137.200 to 1c:7e:e5:2a:08:e4 via eth0
Oct 26 22:52:14 zonda-serv kernel: [24669.121649] init: zentyal.webadmin-uwsgi main process (17840) terminated with status 1
Oct 26 22:52:14 zonda-serv kernel: [24669.121681] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:52:37 zonda-serv samba[5486]: [2014/10/26 22:52:37.076745,  0] ../lib/util/util_runcmd.c:317(samba_runcmd_io_handler)
Oct 26 22:52:37 zonda-serv samba[5486]:   /usr/sbin/samba_spnupdate: params.c:pm_process() - Processing configuration file "/etc/samba/shares.conf"
Oct 26 22:52:37 zonda-serv samba[5486]: [2014/10/26 22:52:37.109537,  0] ../lib/util/util_runcmd.c:317(samba_runcmd_io_handler)
Oct 26 22:52:37 zonda-serv samba[5486]:   /usr/sbin/samba_dnsupdate: params.c:pm_process() - Processing configuration file "/etc/samba/shares.conf"
Oct 26 22:52:37 zonda-serv samba[5486]: [2014/10/26 22:52:37.110189,  0] ../lib/util/util_runcmd.c:317(samba_runcmd_io_handler)
Oct 26 22:52:37 zonda-serv samba[5486]:   /usr/sbin/samba_dnsupdate: not adding non-broadcast interface tun0
Oct 26 22:52:44 zonda-serv kernel: [24699.120460] init: zentyal.webadmin-uwsgi main process (17969) terminated with status 1
Oct 26 22:52:44 zonda-serv kernel: [24699.120493] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:52:47 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.4 from 00:1d:7d:09:27:30 via eth0
Oct 26 22:52:47 zonda-serv dhcpd: DHCPACK on 192.168.137.4 to 00:1d:7d:09:27:30 via eth0
Oct 26 22:52:49 zonda-serv dhcpd: DHCPINFORM from 192.168.137.4 via eth0
Oct 26 22:52:49 zonda-serv dhcpd: DHCPACK to 192.168.137.4 (00:1d:7d:09:27:30) via eth0
Oct 26 22:53:14 zonda-serv kernel: [24729.122888] init: zentyal.webadmin-uwsgi main process (18101) terminated with status 1
Oct 26 22:53:14 zonda-serv kernel: [24729.122923] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:53:15 zonda-serv kernel: [24729.801335] init: zentyal.webadmin-uwsgi main process (18223) terminated with status 255
Oct 26 22:53:15 zonda-serv kernel: [24729.801388] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:53:44 zonda-serv kernel: [24759.134721] init: zentyal.webadmin-uwsgi main process (18231) terminated with status 1
Oct 26 22:53:44 zonda-serv kernel: [24759.134766] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:53:45 zonda-serv kernel: [24759.807246] init: zentyal.webadmin-uwsgi main process (18357) terminated with status 1
Oct 26 22:53:45 zonda-serv kernel: [24759.807285] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:54:14 zonda-serv kernel: [24789.117226] init: zentyal.webadmin-uwsgi main process (18361) terminated with status 1
Oct 26 22:54:14 zonda-serv kernel: [24789.117264] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:54:44 zonda-serv kernel: [24819.120535] init: zentyal.webadmin-uwsgi main process (18483) terminated with status 1
Oct 26 22:54:44 zonda-serv kernel: [24819.120568] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:54:45 zonda-serv kernel: [24819.794937] init: zentyal.webadmin-uwsgi main process (18613) terminated with status 1
Oct 26 22:54:45 zonda-serv kernel: [24819.794971] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:54:59 zonda-serv named[4553]: success resolving '4.251.222.222.in-addr.arpa/PTR' (in '222.222.in-addr.arpa'?) after reducing the advertised EDNS UDP packet size to 512 octets
Oct 26 22:54:59 zonda-serv dhcpd: DHCPINFORM from 192.168.137.4 via eth0
Oct 26 22:54:59 zonda-serv dhcpd: DHCPACK to 192.168.137.4 (00:1d:7d:09:27:30) via eth0
Oct 26 22:55:01 zonda-serv CRON[18686]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Oct 26 22:55:01 zonda-serv CRON[18687]: (root) CMD (/usr/share/zentyal-users/slave-sync)
Oct 26 22:55:01 zonda-serv postfix/sendmail[18690]: warning: /etc/postfix/main.cf, line 104: overriding earlier entry: smtpd_sasl_local_domain=
Oct 26 22:55:01 zonda-serv postfix/postdrop[18691]: warning: /etc/postfix/main.cf, line 104: overriding earlier entry: smtpd_sasl_local_domain=
Oct 26 22:55:14 zonda-serv kernel: [24849.132306] init: zentyal.webadmin-uwsgi main process (18617) terminated with status 255
Oct 26 22:55:14 zonda-serv kernel: [24849.132336] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:55:15 zonda-serv kernel: [24849.810736] init: zentyal.webadmin-uwsgi main process (18747) terminated with status 1
Oct 26 22:55:15 zonda-serv kernel: [24849.810767] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:55:41 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.102 from 08:00:27:05:23:73 via eth0
Oct 26 22:55:41 zonda-serv dhcpd: DHCPACK on 192.168.137.102 to 08:00:27:05:23:73 via eth0
Oct 26 22:55:44 zonda-serv kernel: [24879.162306] init: zentyal.webadmin-uwsgi main process (18760) terminated with status 255
Oct 26 22:55:44 zonda-serv kernel: [24879.162345] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:55:45 zonda-serv kernel: [24879.835789] init: zentyal.webadmin-uwsgi main process (18881) terminated with status 1
Oct 26 22:55:45 zonda-serv kernel: [24879.835828] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:56:14 zonda-serv kernel: [24909.132254] init: zentyal.webadmin-uwsgi main process (18885) terminated with status 255
Oct 26 22:56:14 zonda-serv kernel: [24909.132289] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:56:44 zonda-serv kernel: [24939.119976] init: zentyal.webadmin-uwsgi main process (19007) terminated with status 1
Oct 26 22:56:44 zonda-serv kernel: [24939.120048] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:56:45 zonda-serv kernel: [24939.794886] init: zentyal.webadmin-uwsgi main process (19137) terminated with status 1
Oct 26 22:56:45 zonda-serv kernel: [24939.794916] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:56:58 zonda-serv smbd[19204]: [2014/10/26 22:56:58.199156,  0] ../source3/printing/print_cups.c:151(cups_connect)
Oct 26 22:56:58 zonda-serv smbd[19204]:   Unable to connect to CUPS server localhost:631 - Bad file descriptor
Oct 26 22:56:58 zonda-serv smbd[5489]: [2014/10/26 22:56:58.199912,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
Oct 26 22:56:58 zonda-serv smbd[5489]:   failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
Oct 26 22:57:14 zonda-serv kernel: [24969.120980] init: zentyal.webadmin-uwsgi main process (19141) terminated with status 1
Oct 26 22:57:14 zonda-serv kernel: [24969.121032] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:57:15 zonda-serv kernel: [24969.796619] init: zentyal.webadmin-uwsgi main process (19279) terminated with status 1
Oct 26 22:57:15 zonda-serv kernel: [24969.796664] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:57:36 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.200 from 1c:7e:e5:2a:08:e4 via eth0
Oct 26 22:57:36 zonda-serv dhcpd: DHCPACK on 192.168.137.200 to 1c:7e:e5:2a:08:e4 via eth0
Oct 26 22:57:44 zonda-serv kernel: [24999.118203] init: zentyal.webadmin-uwsgi main process (19283) terminated with status 1
Oct 26 22:57:44 zonda-serv kernel: [24999.118236] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:58:14 zonda-serv kernel: [25029.123437] init: zentyal.webadmin-uwsgi main process (19404) terminated with status 1
Oct 26 22:58:14 zonda-serv kernel: [25029.123468] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:58:15 zonda-serv kernel: [25029.796883] init: zentyal.webadmin-uwsgi main process (19535) terminated with status 1
Oct 26 22:58:15 zonda-serv kernel: [25029.796915] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:58:44 zonda-serv kernel: [25059.131866] init: zentyal.webadmin-uwsgi main process (19539) terminated with status 1
Oct 26 22:58:44 zonda-serv kernel: [25059.131896] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:58:45 zonda-serv kernel: [25059.808975] init: zentyal.webadmin-uwsgi main process (19660) terminated with status 1
Oct 26 22:58:45 zonda-serv kernel: [25059.809052] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:59:14 zonda-serv kernel: [25089.150474] init: zentyal.webadmin-uwsgi main process (19666) terminated with status 1
Oct 26 22:59:14 zonda-serv kernel: [25089.150519] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:59:15 zonda-serv kernel: [25089.826556] init: zentyal.webadmin-uwsgi main process (19795) terminated with status 1
Oct 26 22:59:15 zonda-serv kernel: [25089.826639] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:59:29 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.3 from 00:e0:4c:39:0a:08 via eth0
Oct 26 22:59:29 zonda-serv dhcpd: DHCPACK on 192.168.137.3 to 00:e0:4c:39:0a:08 via eth0
Oct 26 22:59:44 zonda-serv kernel: [25119.121029] init: zentyal.webadmin-uwsgi main process (19799) terminated with status 1
Oct 26 22:59:44 zonda-serv kernel: [25119.121073] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:59:45 zonda-serv kernel: [25119.802035] init: zentyal.webadmin-uwsgi main process (19920) terminated with status 1
Oct 26 22:59:45 zonda-serv kernel: [25119.802064] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 22:59:48 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.33 from 90:18:7c:f2:3a:6c (android-a6c190c669866412) via eth0
Oct 26 22:59:48 zonda-serv dhcpd: DHCPACK on 192.168.137.33 to 90:18:7c:f2:3a:6c (android-a6c190c669866412) via eth0
Oct 26 23:00:01 zonda-serv CRON[20002]: (root) CMD (/usr/share/zentyal-users/slave-sync)
Oct 26 23:00:01 zonda-serv CRON[20005]: (clamav) CMD (/usr/bin/freshclam --quiet)
Oct 26 23:00:01 zonda-serv postfix/sendmail[20004]: warning: /etc/postfix/main.cf, line 104: overriding earlier entry: smtpd_sasl_local_domain=
Oct 26 23:00:01 zonda-serv postfix/postdrop[20006]: warning: /etc/postfix/main.cf, line 104: overriding earlier entry: smtpd_sasl_local_domain=
Oct 26 23:00:14 zonda-serv kernel: [25149.120589] init: zentyal.webadmin-uwsgi main process (19933) terminated with status 1
Oct 26 23:00:14 zonda-serv kernel: [25149.120626] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:00:15 zonda-serv kernel: [25149.810710] init: zentyal.webadmin-uwsgi main process (20063) terminated with status 1
Oct 26 23:00:15 zonda-serv kernel: [25149.810740] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:00:24 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.200 from 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:00:24 zonda-serv dhcpd: DHCPACK on 192.168.137.200 to 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:00:44 zonda-serv kernel: [25179.136815] init: zentyal.webadmin-uwsgi main process (20067) terminated with status 255
Oct 26 23:00:44 zonda-serv kernel: [25179.136855] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:00:45 zonda-serv kernel: [25179.838764] init: zentyal.webadmin-uwsgi main process (20188) terminated with status 1
Oct 26 23:00:45 zonda-serv kernel: [25179.838805] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:01:14 zonda-serv kernel: [25209.123670] init: zentyal.webadmin-uwsgi main process (20201) terminated with status 1
Oct 26 23:01:14 zonda-serv kernel: [25209.123703] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:01:15 zonda-serv kernel: [25209.806204] init: zentyal.webadmin-uwsgi main process (20323) terminated with status 1
Oct 26 23:01:15 zonda-serv kernel: [25209.806241] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:01:44 zonda-serv kernel: [25239.175561] init: zentyal.webadmin-uwsgi main process (20327) terminated with status 1
Oct 26 23:01:44 zonda-serv kernel: [25239.175629] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:01:45 zonda-serv kernel: [25239.868923] init: zentyal.webadmin-uwsgi main process (20448) terminated with status 1
Oct 26 23:01:45 zonda-serv kernel: [25239.868963] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:01:48 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.200 from 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:01:48 zonda-serv dhcpd: DHCPACK on 192.168.137.200 to 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:02:14 zonda-serv kernel: [25269.127394] init: zentyal.webadmin-uwsgi main process (20461) terminated with status 1
Oct 26 23:02:14 zonda-serv kernel: [25269.127426] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:02:30 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.200 from 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:02:30 zonda-serv dhcpd: DHCPACK on 192.168.137.200 to 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:02:37 zonda-serv samba[5486]: [2014/10/26 23:02:37.129981,  0] ../lib/util/util_runcmd.c:317(samba_runcmd_io_handler)
Oct 26 23:02:37 zonda-serv samba[5486]:   /usr/sbin/samba_spnupdate: params.c:pm_process() - Processing configuration file "/etc/samba/shares.conf"
Oct 26 23:02:37 zonda-serv samba[5486]: [2014/10/26 23:02:37.165454,  0] ../lib/util/util_runcmd.c:317(samba_runcmd_io_handler)
Oct 26 23:02:37 zonda-serv samba[5486]:   /usr/sbin/samba_dnsupdate: params.c:pm_process() - Processing configuration file "/etc/samba/shares.conf"
Oct 26 23:02:37 zonda-serv samba[5486]: [2014/10/26 23:02:37.166157,  0] ../lib/util/util_runcmd.c:317(samba_runcmd_io_handler)
Oct 26 23:02:37 zonda-serv samba[5486]:   /usr/sbin/samba_dnsupdate: not adding non-broadcast interface tun0
Oct 26 23:02:44 zonda-serv kernel: [25299.122109] init: zentyal.webadmin-uwsgi main process (20590) terminated with status 1
Oct 26 23:02:44 zonda-serv kernel: [25299.122161] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:02:44 zonda-serv kernel: [25299.155542] audit_printk_skb: 27 callbacks suppressed
Oct 26 23:02:44 zonda-serv kernel: [25299.155569] type=1400 audit(1414353764.718:796): apparmor="ALLOWED" operation="open" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=20721 comm="ldap_child" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Oct 26 23:02:44 zonda-serv kernel: [25299.155589] type=1400 audit(1414353764.718:797): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=20721 comm="ldap_child" requested_mask="k" denied_mask="k" fsuid=0 ouid=0
Oct 26 23:02:44 zonda-serv kernel: [25299.155634] type=1400 audit(1414353764.718:798): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=20721 comm="ldap_child" requested_mask="k" denied_mask="k" fsuid=0 ouid=0
Oct 26 23:02:44 zonda-serv kernel: [25299.155799] type=1400 audit(1414353764.718:799): apparmor="ALLOWED" operation="open" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=20721 comm="ldap_child" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Oct 26 23:02:44 zonda-serv kernel: [25299.155817] type=1400 audit(1414353764.718:800): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=20721 comm="ldap_child" requested_mask="k" denied_mask="k" fsuid=0 ouid=0
Oct 26 23:02:44 zonda-serv kernel: [25299.155867] type=1400 audit(1414353764.718:801): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=20721 comm="ldap_child" requested_mask="k" denied_mask="k" fsuid=0 ouid=0
Oct 26 23:02:44 zonda-serv kernel: [25299.170693] type=1400 audit(1414353764.734:802): apparmor="ALLOWED" operation="open" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=20721 comm="ldap_child" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Oct 26 23:02:44 zonda-serv kernel: [25299.170724] type=1400 audit(1414353764.734:803): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=20721 comm="ldap_child" requested_mask="k" denied_mask="k" fsuid=0 ouid=0
Oct 26 23:02:44 zonda-serv kernel: [25299.170785] type=1400 audit(1414353764.734:804): apparmor="ALLOWED" operation="file_lock" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=20721 comm="ldap_child" requested_mask="k" denied_mask="k" fsuid=0 ouid=0
Oct 26 23:02:44 zonda-serv kernel: [25299.227269] type=1400 audit(1414353764.790:805): apparmor="ALLOWED" operation="open" profile="/usr/sbin/sssd" name="/var/lib/samba/private/secrets.keytab" pid=20725 comm="ldap_child" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Oct 26 23:02:51 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.200 from 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:02:51 zonda-serv dhcpd: DHCPACK on 192.168.137.200 to 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:02:51 zonda-serv dhcpd: DHCPINFORM from 192.168.137.4 via eth0
Oct 26 23:02:51 zonda-serv dhcpd: DHCPACK to 192.168.137.4 (00:1d:7d:09:27:30) via eth0
Oct 26 23:03:02 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.200 from 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:03:02 zonda-serv dhcpd: DHCPACK on 192.168.137.200 to 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:03:07 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.200 from 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:03:07 zonda-serv dhcpd: DHCPACK on 192.168.137.200 to 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:03:10 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.200 from 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:03:10 zonda-serv dhcpd: DHCPACK on 192.168.137.200 to 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:03:11 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.200 from 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:03:11 zonda-serv dhcpd: DHCPACK on 192.168.137.200 to 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:03:13 zonda-serv dhcpd: DHCPREQUEST for 192.168.137.200 from 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:03:13 zonda-serv dhcpd: DHCPACK on 192.168.137.200 to 1c:7e:e5:2a:08:e4 via eth0
Oct 26 23:03:14 zonda-serv kernel: [25329.133820] init: zentyal.webadmin-uwsgi main process (20717) terminated with status 1
Oct 26 23:03:14 zonda-serv kernel: [25329.133865] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:03:15 zonda-serv kernel: [25329.813664] init: zentyal.webadmin-uwsgi main process (20846) terminated with status 1
Oct 26 23:03:15 zonda-serv kernel: [25329.813706] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:03:44 zonda-serv kernel: [25359.128574] init: zentyal.webadmin-uwsgi main process (20850) terminated with status 255
Oct 26 23:03:44 zonda-serv kernel: [25359.128687] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:04:14 zonda-serv kernel: [25389.140603] init: zentyal.webadmin-uwsgi main process (20980) terminated with status 1
Oct 26 23:04:14 zonda-serv kernel: [25389.140648] init: zentyal.webadmin-uwsgi main process ended, respawning
Oct 26 23:09:17 zonda-serv dhclient: DHCPREQUEST of 79.164.40.228 on eth1 to 10.181.192.1 port 67 (xid=0x27afbff0)
Oct 26 23:12:37 zonda-serv samba[5486]: [2014/10/26 23:12:37.162870,  0] ../lib/util/util_runcmd.c:317(samba_runcmd_io_handler)
Oct 26 23:12:37 zonda-serv samba[5486]:   /usr/sbin/samba_spnupdate: params.c:pm_process() - Processing configuration file "/etc/samba/shares.conf"
Oct 26 23:12:37 zonda-serv collectd[4855]: Not sleeping because the next interval is 465.107 seconds in the past!
Oct 26 23:12:37 zonda-serv collectd[4855]: Filter subsystem: Built-in target `write': Dispatching value to all write plugins failed with status -1.
Oct 26 23:12:37 zonda-serv smbd[21217]: [2014/10/26 23:12:37.444759,  0] ../source3/printing/print_cups.c:151(cups_connect)
Oct 26 23:12:37 zonda-serv smbd[21217]:   Unable to connect to CUPS server localhost:631 - Bad file descriptor
Oct 26 23:12:37 zonda-serv smbd[5489]: [2014/10/26 23:12:37.445423,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
Oct 26 23:12:37 zonda-serv smbd[5489]:   failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
Oct 26 23:25:38 zonda-serv smbd[21219]: [2014/10/26 23:25:38.212190,  0] ../source3/printing/print_cups.c:151(cups_connect)
Oct 26 23:25:38 zonda-serv smbd[21219]:   Unable to connect to CUPS server localhost:631 - Bad file descriptor
Oct 26 23:25:38 zonda-serv smbd[5489]: [2014/10/26 23:25:38.212940,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
Oct 26 23:25:38 zonda-serv smbd[5489]:   failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
Oct 26 23:38:38 zonda-serv smbd[21221]: [2014/10/26 23:38:38.991664,  0] ../source3/printing/print_cups.c:151(cups_connect)
Oct 26 23:38:38 zonda-serv smbd[21221]:   Unable to connect to CUPS server localhost:631 - Bad file descriptor
Oct 26 23:38:38 zonda-serv smbd[5489]: [2014/10/26 23:38:38.992416,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
Oct 26 23:38:38 zonda-serv smbd[5489]:   failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
Oct 26 23:51:39 zonda-serv smbd[21223]: [2014/10/26 23:51:39.771734,  0] ../source3/printing/print_cups.c:151(cups_connect)
Oct 26 23:51:39 zonda-serv smbd[21223]:   Unable to connect to CUPS server localhost:631 - Bad file descriptor
Oct 26 23:51:39 zonda-serv smbd[5489]: [2014/10/26 23:51:39.772513,  0] ../source3/printing/print_cups.c:528(cups_async_callback)
Oct 26 23:51:39 zonda-serv smbd[5489]:   failed to retrieve printer list: NT_STATUS_UNSUCCESSFUL
Oct 27 08:30:26 zonda-serv rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="636" x-info="http://www.rsyslog.com"] start
Oct 27 08:30:26 zonda-serv rsyslogd-2307: warning: ~ action is deprecated, consider using the 'stop' statement instead [try http://www.rsyslog.com/e/2307 ]
Oct 27 08:30:26 zonda-serv rsyslogd: rsyslogd's groupid changed to 103
Oct 27 08:30:26 zonda-serv rsyslogd: rsyslogd's userid changed to 101
Oct 27 08:30:26 zonda-serv kernel: [    0.000000] Initializing cgroup subsys cpuset

```
Xorg
```
[    43.051] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    43.051] X Protocol Version 11, Revision 0
[    43.051] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    43.051] Current Operating System: Linux zonda-serv 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    43.051] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=ca5c361e-9aa5-4405-af05-ef88ddca2339 ro zswap.enabled=1 debug ignore_loglevel
[    43.051] Build Date: 30 July 2014  12:21:54AM
[    43.051] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    43.051] Current version of pixman: 0.30.2
[    43.051]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    43.051] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    43.051] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 26 16:01:48 2014
[    43.056] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    43.057] (==) No Layout section.  Using the first Screen section.
[    43.057] (==) No screen section available. Using defaults.
[    43.057] (**) |-->Screen "Default Screen Section" (0)
[    43.057] (**) |   |-->Monitor "<default monitor>"
[    43.057] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    43.057] (==) Automatically adding devices
[    43.057] (==) Automatically enabling devices
[    43.057] (==) Automatically adding GPU devices
[    43.058] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    43.058]     Entry deleted from font path.
[    43.058] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    43.058]     Entry deleted from font path.
[    43.058] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    43.058]     Entry deleted from font path.
[    43.058] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    43.058]     Entry deleted from font path.
[    43.058] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    43.059]     Entry deleted from font path.
[    43.059] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    43.059] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    43.059] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    43.059] (II) Loader magic: 0x7f075da6fd40
[    43.059] (II) Module ABI versions:
[    43.059]     X.Org ANSI C Emulation: 0.4
[    43.059]     X.Org Video Driver: 15.0
[    43.059]     X.Org XInput driver : 20.0
[    43.059]     X.Org Server Extension : 8.0
[    43.061] (--) PCI:*(0:0:16:0) 10de:07e1:1043:82ae rev 162, Mem @ 0xed000000/16777216, 0xd0000000/268435456, 0xee000000/16777216, BIOS @ 0x????????/131072
[    43.061] Initializing built-in extension Generic Event Extension
[    43.061] Initializing built-in extension SHAPE
[    43.061] Initializing built-in extension MIT-SHM
[    43.061] Initializing built-in extension XInputExtension
[    43.061] Initializing built-in extension XTEST
[    43.061] Initializing built-in extension BIG-REQUESTS
[    43.061] Initializing built-in extension SYNC
[    43.061] Initializing built-in extension XKEYBOARD
[    43.061] Initializing built-in extension XC-MISC
[    43.061] Initializing built-in extension SECURITY
[    43.061] Initializing built-in extension XINERAMA
[    43.061] Initializing built-in extension XFIXES
[    43.061] Initializing built-in extension RENDER
[    43.061] Initializing built-in extension RANDR
[    43.061] Initializing built-in extension COMPOSITE
[    43.061] Initializing built-in extension DAMAGE
[    43.061] Initializing built-in extension MIT-SCREEN-SAVER
[    43.061] Initializing built-in extension DOUBLE-BUFFER
[    43.061] Initializing built-in extension RECORD
[    43.061] Initializing built-in extension DPMS
[    43.061] Initializing built-in extension Present
[    43.061] Initializing built-in extension DRI3
[    43.061] Initializing built-in extension X-Resource
[    43.061] Initializing built-in extension XVideo
[    43.061] Initializing built-in extension XVideo-MotionCompensation
[    43.061] Initializing built-in extension SELinux
[    43.061] Initializing built-in extension XFree86-VidModeExtension
[    43.061] Initializing built-in extension XFree86-DGA
[    43.061] Initializing built-in extension XFree86-DRI
[    43.061] Initializing built-in extension DRI2
[    43.061] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    43.061] (II) "glx" will be loaded by default.
[    43.061] (WW) "xmir" is not to be loaded by default. Skipping.
[    43.061] (II) LoadModule: "glx"
[    43.063] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    43.136] (II) Module glx: vendor="NVIDIA Corporation"
[    43.136]     compiled for 4.0.2, module version = 1.0.0
[    43.136]     Module class: X.Org Server Extension
[    43.136] (II) NVIDIA GLX Module  304.117  Tue Nov 26 21:45:09 PST 2013
[    43.136] Loading extension GLX
[    43.136] (==) Matched nvidia as autoconfigured driver 0
[    43.136] (==) Matched nouveau as autoconfigured driver 1
[    43.136] (==) Matched modesetting as autoconfigured driver 2
[    43.136] (==) Matched fbdev as autoconfigured driver 3
[    43.136] (==) Matched vesa as autoconfigured driver 4
[    43.136] (==) Assigned the driver to the xf86ConfigLayout
[    43.136] (II) LoadModule: "nvidia"
[    43.136] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    43.137] (II) Module nvidia: vendor="NVIDIA Corporation"
[    43.137]     compiled for 4.0.2, module version = 1.0.0
[    43.137]     Module class: X.Org Video Driver
[    43.137] (II) LoadModule: "nouveau"
[    43.149] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    43.150] (II) Module nouveau: vendor="X.Org Foundation"
[    43.150]     compiled for 1.15.0, module version = 1.0.10
[    43.150]     Module class: X.Org Video Driver
[    43.150]     ABI class: X.Org Video Driver, version 15.0
[    43.150] (II) LoadModule: "modesetting"
[    43.150] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    43.150] (II) Module modesetting: vendor="X.Org Foundation"
[    43.150]     compiled for 1.15.0, module version = 0.8.1
[    43.150]     Module class: X.Org Video Driver
[    43.150]     ABI class: X.Org Video Driver, version 15.0
[    43.150] (II) LoadModule: "fbdev"
[    43.150] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    43.151] (II) Module fbdev: vendor="X.Org Foundation"
[    43.151]     compiled for 1.15.0, module version = 0.4.4
[    43.151]     Module class: X.Org Video Driver
[    43.151]     ABI class: X.Org Video Driver, version 15.0
[    43.151] (II) LoadModule: "vesa"
[    43.151] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    43.151] (II) Module vesa: vendor="X.Org Foundation"
[    43.151]     compiled for 1.15.0, module version = 2.3.3
[    43.151]     Module class: X.Org Video Driver
[    43.151]     ABI class: X.Org Video Driver, version 15.0
[    43.151] (II) NVIDIA dlloader X Driver  304.117  Tue Nov 26 21:27:08 PST 2013
[    43.151] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    43.151] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    43.151] (II) NOUVEAU driver for NVIDIA chipset families :
[    43.151]     RIVA TNT        (NV04)
[    43.151]     RIVA TNT2       (NV05)
[    43.151]     GeForce 256     (NV10)
[    43.151]     GeForce 2       (NV11, NV15)
[    43.151]     GeForce 4MX     (NV17, NV18)
[    43.151]     GeForce 3       (NV20)
[    43.151]     GeForce 4Ti     (NV25, NV28)
[    43.151]     GeForce FX      (NV3x)
[    43.151]     GeForce 6       (NV4x)
[    43.151]     GeForce 7       (G7x)
[    43.151]     GeForce 8       (G8x)
[    43.151]     GeForce GTX 200 (NVA0)
[    43.151]     GeForce GTX 400 (NVC0)
[    43.151] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    43.152] (II) FBDEV: driver for framebuffer: fbdev
[    43.152] (II) VESA: driver for VESA chipsets: vesa
[    43.152] (++) using VT number 7

[    43.154] (II) Loading sub module "fb"
[    43.154] (II) LoadModule: "fb"
[    43.154] (II) Loading /usr/lib/xorg/modules/libfb.so
[    43.154] (II) Module fb: vendor="X.Org Foundation"
[    43.154]     compiled for 1.15.1, module version = 1.0.0
[    43.154]     ABI class: X.Org ANSI C Emulation, version 0.4
[    43.154] (II) Loading sub module "wfb"
[    43.154] (II) LoadModule: "wfb"
[    43.155] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    43.155] (II) Module wfb: vendor="X.Org Foundation"
[    43.155]     compiled for 1.15.1, module version = 1.0.0
[    43.155]     ABI class: X.Org ANSI C Emulation, version 0.4
[    43.155] (II) Loading sub module "ramdac"
[    43.155] (II) LoadModule: "ramdac"
[    43.155] (II) Module "ramdac" already built-in
[    43.155] (WW) Falling back to old probe method for modesetting
[    43.155] (EE) open /dev/dri/card0: No such file or directory
[    43.155] (WW) Falling back to old probe method for fbdev
[    43.155] (II) Loading sub module "fbdevhw"
[    43.155] (II) LoadModule: "fbdevhw"
[    43.155] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    43.155] (II) Module fbdevhw: vendor="X.Org Foundation"
[    43.155]     compiled for 1.15.1, module version = 0.0.2
[    43.155]     ABI class: X.Org Video Driver, version 15.0
[    43.155] (EE) open /dev/fb0: No such file or directory
[    43.155] (WW) Falling back to old probe method for vesa
[    43.155] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    43.155] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    43.156] (==) NVIDIA(0): RGB weight 888
[    43.156] (==) NVIDIA(0): Default visual is TrueColor
[    43.156] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    43.156] (**) NVIDIA(0): Enabling 2D acceleration
[    43.873] (II) NVIDIA(GPU-0): Display (Acer AL1916W (CRT-0)) does not support NVIDIA 3D
[    43.873] (II) NVIDIA(GPU-0):     Vision stereo.
[    43.874] (II) NVIDIA(0): NVIDIA GPU GeForce 7100 / nForce 630i (C73) at PCI:0:16:0
[    43.874] (II) NVIDIA(0):     (GPU-0)
[    43.874] (--) NVIDIA(0): Memory: 524288 kBytes
[    43.874] (--) NVIDIA(0): VideoBIOS: 05.73.32.10.00
[    43.874] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    43.874] (--) NVIDIA(0): Valid display device(s) on GeForce 7100 / nForce 630i at PCI:0:16:0
[    43.874] (--) NVIDIA(0):     Acer AL1916W (CRT-0) (connected)
[    43.874] (--) NVIDIA(0):     DFP-0
[    43.874] (--) NVIDIA(0): Acer AL1916W (CRT-0): 350.0 MHz maximum pixel clock
[    43.874] (--) NVIDIA(0): DFP-0: 165.0 MHz maximum pixel clock
[    43.874] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    43.874] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    43.874] (**) NVIDIA(0):     device Acer AL1916W (CRT-0) (Using EDID frequencies has
[    43.874] (**) NVIDIA(0):     been enabled on all display devices.)
[    43.874] (==) NVIDIA(0): 
[    43.874] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    43.874] (==) NVIDIA(0):     will be used as the requested mode.
[    43.874] (==) NVIDIA(0): 
[    43.874] (II) NVIDIA(0): Validated MetaModes:
[    43.874] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[    43.874] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    43.876] (WW) NVIDIA(0): Unable to support custom viewPortOut 1440 x 810 +0 +45
[    43.876] (WW) NVIDIA(0): Unable to support custom viewPortOut 1440 x 810 +0 +45
[    43.876] (--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config
[    43.876] (--) NVIDIA(0):     option
[    43.876] (II) UnloadModule: "nouveau"
[    43.876] (II) Unloading nouveau
[    43.876] (II) UnloadModule: "modesetting"
[    43.876] (II) Unloading modesetting
[    43.876] (II) UnloadModule: "fbdev"
[    43.876] (II) Unloading fbdev
[    43.876] (II) UnloadSubModule: "fbdevhw"
[    43.876] (II) Unloading fbdevhw
[    43.876] (II) UnloadModule: "vesa"
[    43.876] (II) Unloading vesa
[    43.877] (--) Depth 24 pixmap format is 32 bpp
[    43.881] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[    43.967] Loading extension NV-GLX
[    43.984] (==) NVIDIA(0): Disabling shared memory pixmaps
[    43.984] (==) NVIDIA(0): Backing store enabled
[    43.984] (==) NVIDIA(0): Silken mouse enabled
[    43.985] (==) NVIDIA(0): DPMS enabled
[    43.985] Loading extension NV-CONTROL
[    43.985] Loading extension XINERAMA
[    43.985] (II) Loading sub module "dri2"
[    43.985] (II) LoadModule: "dri2"
[    43.985] (II) Module "dri2" already built-in
[    43.985] (II) NVIDIA(0): [DRI2] Setup complete
[    43.985] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    43.985] (--) RandR disabled
[    43.991] (II) SELinux: Disabled on system
[    43.992] (II) Initializing extension GLX
[    44.019] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    44.023] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    44.024] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    44.024] (II) LoadModule: "evdev"
[    44.028] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    44.029] (II) Module evdev: vendor="X.Org Foundation"
[    44.029]     compiled for 1.15.0, module version = 2.8.2
[    44.029]     Module class: X.Org XInput Driver
[    44.029]     ABI class: X.Org XInput driver, version 20.0
[    44.029] (II) Using input driver 'evdev' for 'Power Button'
[    44.029] (**) Power Button: always reports core events
[    44.029] (**) evdev: Power Button: Device: "/dev/input/event1"
[    44.029] (--) evdev: Power Button: Vendor 0 Product 0x1
[    44.029] (--) evdev: Power Button: Found keys
[    44.029] (II) evdev: Power Button: Configuring as keyboard
[    44.029] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    44.029] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    44.029] (**) Option "xkb_rules" "evdev"
[    44.029] (**) Option "xkb_model" "pc105"
[    44.029] (**) Option "xkb_layout" "us,ru"
[    44.029] (**) Option "xkb_variant" ","
[    44.029] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    44.031] (II) XKB: reuse xkmfile /var/lib/xkb/server-5BD46092C922CD443B4EABE4B26B5EFCDED629BD.xkm
[    44.032] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    44.032] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    44.032] (II) Using input driver 'evdev' for 'Power Button'
[    44.032] (**) Power Button: always reports core events
[    44.032] (**) evdev: Power Button: Device: "/dev/input/event0"
[    44.032] (--) evdev: Power Button: Vendor 0 Product 0x1
[    44.032] (--) evdev: Power Button: Found keys
[    44.032] (II) evdev: Power Button: Configuring as keyboard
[    44.032] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    44.032] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    44.032] (**) Option "xkb_rules" "evdev"
[    44.032] (**) Option "xkb_model" "pc105"
[    44.033] (**) Option "xkb_layout" "us,ru"
[    44.033] (**) Option "xkb_variant" ","
[    44.033] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    44.033] (II) config/udev: Adding input device USB KVM (/dev/input/event2)
[    44.033] (**) USB KVM: Applying InputClass "evdev keyboard catchall"
[    44.033] (II) Using input driver 'evdev' for 'USB KVM'
[    44.033] (**) USB KVM: always reports core events
[    44.033] (**) evdev: USB KVM: Device: "/dev/input/event2"
[    44.034] (--) evdev: USB KVM: Vendor 0x2101 Product 0x1407
[    44.034] (--) evdev: USB KVM: Found keys
[    44.034] (II) evdev: USB KVM: Configuring as keyboard
[    44.034] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.0/usb2/2-3/2-3.4/2-3.4:1.0/input/input5/event2"
[    44.034] (II) XINPUT: Adding extended input device "USB KVM" (type: KEYBOARD, id 8)
[    44.034] (**) Option "xkb_rules" "evdev"
[    44.034] (**) Option "xkb_model" "pc105"
[    44.034] (**) Option "xkb_layout" "us,ru"
[    44.034] (**) Option "xkb_variant" ","
[    44.034] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    44.035] (II) config/udev: Adding input device USB KVM (/dev/input/event3)
[    44.035] (**) USB KVM: Applying InputClass "evdev pointer catchall"
[    44.035] (**) USB KVM: Applying InputClass "evdev keyboard catchall"
[    44.035] (II) Using input driver 'evdev' for 'USB KVM'
[    44.035] (**) USB KVM: always reports core events
[    44.035] (**) evdev: USB KVM: Device: "/dev/input/event3"
[    44.035] (--) evdev: USB KVM: Vendor 0x2101 Product 0x1407
[    44.035] (--) evdev: USB KVM: Found 3 mouse buttons
[    44.035] (--) evdev: USB KVM: Found scroll wheel(s)
[    44.035] (--) evdev: USB KVM: Found relative axes
[    44.035] (--) evdev: USB KVM: Found x and y relative axes
[    44.035] (--) evdev: USB KVM: Found keys
[    44.035] (II) evdev: USB KVM: Configuring as mouse
[    44.035] (II) evdev: USB KVM: Configuring as keyboard
[    44.035] (II) evdev: USB KVM: Adding scrollwheel support
[    44.035] (**) evdev: USB KVM: YAxisMapping: buttons 4 and 5
[    44.035] (**) evdev: USB KVM: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    44.035] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.0/usb2/2-3/2-3.4/2-3.4:1.1/input/input6/event3"
[    44.035] (II) XINPUT: Adding extended input device "USB KVM" (type: KEYBOARD, id 9)
[    44.035] (**) Option "xkb_rules" "evdev"
[    44.035] (**) Option "xkb_model" "pc105"
[    44.035] (**) Option "xkb_layout" "us,ru"
[    44.035] (**) Option "xkb_variant" ","
[    44.035] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[    44.035] (II) evdev: USB KVM: initialized for relative axes.
[    44.036] (**) USB KVM: (accel) keeping acceleration scheme 1
[    44.036] (**) USB KVM: (accel) acceleration profile 0
[    44.036] (**) USB KVM: (accel) acceleration factor: 2.000
[    44.036] (**) USB KVM: (accel) acceleration threshold: 4
[    44.036] (II) config/udev: Adding input device USB KVM (/dev/input/mouse0)
[    44.036] (II) No input driver specified, ignoring this device.
[    44.036] (II) This device may have been added with another device file.
[    44.036] (II) config/udev: Adding input device HDA NVidia Line Out Front (/dev/input/event8)
[    44.036] (II) No input driver specified, ignoring this device.
[    44.036] (II) This device may have been added with another device file.
[    44.037] (II) config/udev: Adding input device HDA NVidia Line Out Surround (/dev/input/event7)
[    44.037] (II) No input driver specified, ignoring this device.
[    44.037] (II) This device may have been added with another device file.
[    44.037] (II) config/udev: Adding input device HDA NVidia Line Out CLFE (/dev/input/event6)
[    44.037] (II) No input driver specified, ignoring this device.
[    44.037] (II) This device may have been added with another device file.
[    44.037] (II) config/udev: Adding input device HDA NVidia Line Out Side (/dev/input/event5)
[    44.037] (II) No input driver specified, ignoring this device.
[    44.037] (II) This device may have been added with another device file.
[    44.038] (II) config/udev: Adding input device HDA NVidia Front Headphone (/dev/input/event4)
[    44.038] (II) No input driver specified, ignoring this device.
[    44.038] (II) This device may have been added with another device file.
[    44.038] (II) config/udev: Adding input device HDA NVidia Rear Mic (/dev/input/event11)
[    44.038] (II) No input driver specified, ignoring this device.
[    44.038] (II) This device may have been added with another device file.
[    44.038] (II) config/udev: Adding input device HDA NVidia Front Mic (/dev/input/event10)
[    44.038] (II) No input driver specified, ignoring this device.
[    44.038] (II) This device may have been added with another device file.
[    44.039] (II) config/udev: Adding input device HDA NVidia Line (/dev/input/event9)
[    44.039] (II) No input driver specified, ignoring this device.
[    44.039] (II) This device may have been added with another device file.
[    46.410] (II) XKB: reuse xkmfile /var/lib/xkb/server-7322F64E96E11C1E4CA97145438BDBC2D43A31B0.xkm
[    46.445] (II) XKB: reuse xkmfile /var/lib/xkb/server-719093A33B468275582F0A78CA52014F76EC337E.xkm
[    46.587] (II) XKB: reuse xkmfile /var/lib/xkb/server-7322F64E96E11C1E4CA97145438BDBC2D43A31B0.xkm
[    46.611] (II) XKB: reuse xkmfile /var/lib/xkb/server-719093A33B468275582F0A78CA52014F76EC337E.xkm
[    46.856] (II) XKB: reuse xkmfile /var/lib/xkb/server-B92350FD23984F1D3E367D504F9F6348956BCE63.xkm
```

---

### Post by tgalati4 on 2014-10-27
This is troubling:

> Unable to connect to CUPS server localhost:631 - Bad file descriptor

You also have a lot of zentyal/webmin processes respawning.  Is this normal?  Does webmin work correctly and is this normal behavior for this server?

---

### Post by alexey-brusenskiy on 2014-10-27
the First one is easy to fix thought I don't have any printers and disabled it.
Second one seems to be accidental, happens time to time, so I couldn't find it in today's log (end Google didn't seem to find anyone but us dealing with it), but webmin was used (works correct).

If you can advice for some debug options that can be used to log more of a stuff, it could help. Some time later I will give logs after I fixed cups. I am not sure that is was so critical, so it freezes X and then everything else...

---

### Post by tgalati4 on 2014-10-28
To stop CUPS, just turn it off:

```
sudo service cups stop
```

If X-windows is crashing, then you have other issues, possibly power supply or motherboard or both.

To modify logging behavior:

```
man rsyslogd
```

---


---
title: "Harddisks getting corrupted"
date: 2021-12-02
forum: General Help
---

### Post by herrb on 2021-12-02
Hello together

I recently got into ubuntu server 20.04 and after quite some frustration, I think I managed navigating around ubuntu by now.
There is this issue which is giving me a lot of headaches though: My attached harddisks get corrupted very frequently. Recovery is very painful (but I finally manage to do the recovery)

So this is what happens:
1. My server is up and running, all fine.

2. All of a sudden I find my server not responding. It is pingable though. If I try to ssh into it, I receive "connection refused".

3. Driving on site to physically access the server, I find the server to be running (all fans on and moving, hdds spinning)
At this Point I cannot have a display attached as there is no onboard gpu.

The server will not react to a shot shutdown button press in order to initiate a shutdown.
My best guess is that the server for some reason rebooted, the attached hdds got corrupted during that process and now the server is stuck in cloud init.
I may access the server physically tomorrow and try to hit ctrl + d in order to proceed booting.

I found that the only way till now was to forcibly shutdown the server by long pressing the powerbutton. After which I connect a debugging gpu and power on the machine.
Usually multiple ext4 file systems are corrupted at this stage. Rarely the server is able to boot with a corrupted file system. The primary drive will not corrupt.
The stage at which the system gets stuck during boot is the previously mentioned cloud init. I may proceed by hitting control + d or by pressing enter and uncommenting all drives from fstab.
After pressing enter im in some sort of recovery mode (?) with a root shell but the shutdown command for example wont register.

4. when the system is up and running again, I collect the systemlogs. Nothing special in the syslogs, except they stop all of a sudden, continuing with my next boot, as if there was no issue.
I may attach a syslog tomorrow after collecting the next failure...

5. I start disk regeneration using the following command:
```
sudo fsck.ext4 /dev/disk/by-uuid/0a005fab-99d8-4b65-b09a-6171d3317a81
```
this mostly does not take too much time and is done quite quickly. Today however, It took me a good 3.5 hours to fix a 18 TB drive for which I had to create a 50 gb swap file as e2fsck would run out of memory.

I found that this state would happen as well when I used 
```
shutdown -r 0
```
from my understanding, this should not break something?
For this very reason, I created a "safe shutdown" script, stopping services accessing the harddrives and unmounting the drives before attempting a reboot. This was without success. My Server seems stuck again.

any guidance what I can try and check or what information I could give is much appreciated.
The next steps Ill do is to leave the debug gpu plugged in so that I can hopefully see better where the server is getting stuck at. I kind of feels that im walking in the dark with no log entries whatsoever.

---

### Post by TheFu on 2021-12-02
Run hardware tests.
Look at the **dmesg** - use **journalctl -b -1**.

Does this server not have IPMI or a RIBLO card?  Think of how much time that would have saved.

Even with failing RAM, I get messages in dmesg/systemd-journals. This only happens when I've pushed the RAM speeds beyond what they can handle (still under the speed they are rated).

Anyway, it is probably hardware at fault, so start testing everything from the SAS cables to the HBAs to the RAM to the MB.

BTW, you didn't really provide **any** overview of the OS or server. That could be important.

---

### Post by herrb on 2021-12-03
Os Information:
```

kryptominer@golddigger:~$ lsb_release -aNo LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:        20.04
Codename:       focal

```

thank you so much for the hint with the Ipmi card. 
I am currently using a desktop motherboard, no IPMI support. I will look into that in the future but right now need to keep the cost of new purchases down in those times.

Coming into the office this morning, I found the server in described mode again. Upon pressing ctrl + d the server would continue its boot. Apparently, HDDs corrupted again.
If I understand correctly, demsg are the logs coming from the kernel on boot. I could not find anything specific, except that hdd´s are corrupted:
```

[   45.906105] kernel: EXT4-fs (sdf): ext4_check_descriptors: Block bitmap for group 26364 overlaps superblock[   45.906106] kernel: EXT4-fs (sdf): group descriptors corrupted!
[   45.921040] kernel: EXT4-fs (sdc): mounted filesystem with ordered data mode. Opts: (null)
[   45.928974] kernel: EXT4-fs (sdb): mounted filesystem with ordered data mode. Opts: (null)
[   45.975869] kernel: EXT4-fs (sdl): mounted filesystem with ordered data mode. Opts: (null)
[   49.493289] kernel: igb 0000:08:00.0 enp8s0: igb: enp8s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[   49.600971] kernel: IPv6: ADDRCONF(NETDEV_CHANGE): enp8s0: link becomes ready
[41254.343198] kernel: EXT4-fs (sdf): ext4_check_descriptors: Block bitmap for group 27152 overlaps superblock
[41254.367200] kernel: EXT4-fs (sdf): group descriptors corrupted!

```

I have attached the most recent log with failed boot as well as the  most recent one from yesterday

fsck tells:
```
fsck.ext4: Group descriptors look bad... trying backup blocks...
/dev/disk/by-uuid/16a71f3e-7131-4ab7-bc44-4bb1c1c2da27 was not cleanly unmounted, check forced.

```

do you have a good hardware test suite in recommendation or would you use tools which come with the motherboard?

---

### Post by TheFu on 2021-12-03
If the HDDs are failing, then corruption is to be expected.  Make backups of any data you don't want to lose.  Run some SMART tests to see how many blocks have already been relocated.  If none, replace the cable.  Bad CRCs in the SMART test results is an indication of a bad cable.

The command is **smartctl**.  I don't recall the exact package name, it is definitely different - perhaps smartmontools?  On a full install, if you run smartctl, bash will tell you the name of the missing package to install.  Next run a "short" test, wait for that to complete.  I'd run a test on each physical storage device.  Usually less than 5 minutes, then run a report for each device.  Google will help explain what the parameters in the report mean.  In general, we want to see "0" as the answer in the raw column and non-zero numbers are bad. Pay attention to parameters with "error" or "relocated" in the names.  There are some that purely contain counts - like hours powered. There are a few of those.  Every SSD/HDD model has different meanings for each parameter. There is no standard, even when the parameter number is the same.  I've found the "threshold" numbers listed to be useless.
I think gnome-disks has a way to do SMART testing and reporting. I don't recall if it shows the raw parameter output. I know it didn't for years.

IPMI isn't an add-on card. It has to be built into the motherboard and system.  Low-end "server" hardware typically doesn't have it. Also beware that IPMI (and iDRAC/RibLO) have a long history really poor security. Never connect these to a normal network, only to the admin-only network and only where very strong authentication is required even to use that network.  For as important as these interfaces are, we'd hope that the vendors wouldn't make dumb mistakes, but alas, they seem to screw up every year.  For some time the Dell server iDRAC didn't need a password for a connection.  They had a login screen and a password could be used, but 
> Kiguradze&#8217;s team announced last week that they had found the path transversal vulnerability in the Integrated Dell Remote Access Controller (iDRAC).
It isn't just Dell. All the vendors have failed at some point ... and after a fix is issued, sometimes new problems are uncovered.  Don't allow random access to these devices is the take-away.

I have 2 identical motherboards, so testing hardware between those 2 systems isn't hard.  At home, I've just used deductive reasoning to figure out which part(s) have failed, then replaced or disabled those parts.  I've never had a motherboard disk controller fail, but I have had OSes refuse to boot using them.  That's when I'd go into the junk shelf and pull out a SATA-I controller, put it in the system and connect a HDD.  Same for NICs.  Had a NIC start dropping packets, so I added a $10 NIC that was lying around to the system and started using that instead.  Ran for a few years, getting about 1/3rd the throughput, but at least no dropped packets.  It was clear that the MB NIC was the issue.  Disabled it in BIOS and used that system another 5 yrs, before replacing it about 2 months ago.  This time, I paid attention to the MB NIC and got the Intel NIC I wanted, which was NOT the latest available.  Deduction.

---

### Post by herrb on 2021-12-03
I have informed myself about management interfaces. Unfortunately this would mean switching mainboard, processor + ram.

This is way out of budget for me right now for 3 computers unfortunately. Also I do not (yet) have a proper firewall. Its in the budget for the upcoming month.

I have further found a service which would not stop properly. It is my only service accessing those data drives as far as I know. Could this block the unmounting procedure at shutdown? 
I have managed to rewrite the service in order to stop properly.

Additionally, I identified two drives at 100% capacity (full) which I set to readonly mount in fstab. I hope this also may prevent corruption of those specific drives.
Sata Cables are a very good point. I have long 1 Meter cables and am not 100% happy with their quality. i may exchange them next time im in the office. I have plenty of spares, but I shall order shorter ones (need to measure the min required cable length)

For the HDD's I did a self test and then readout of the smart Data. So far I cannot find errors. I suppose the high number in error count is meant as bits/bytes written/read per one error?
```

sudo smartctl -a /dev/disk/by-uuid/e5d4ea17-a48d-4d8e-9bbb-5d50504aa49a
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-91-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Device Model:     ST18000NM000J-2TV103
Serial Number:    ZR52G99H
LU WWN Device Id: 5 000c50 0dba37b44
Firmware Version: SN01
User Capacity:    18,000,207,937,536 bytes [18.0 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      3.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-4 (minor revision not indicated)
SATA Version is:  SATA 3.3, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Fri Dec  3 19:12:09 2021 CET
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
data collection:                (  567) seconds.
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
recommended polling time:        (   1) minutes.
Extended self-test routine
recommended polling time:        (1534) minutes.
Conveyance self-test routine
recommended polling time:        (   2) minutes.
SCT capabilities:              (0x70bd) SCT Status supported.
                                        SCT Error Recovery Control supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   075   064   044    Pre-fail  Always       -       34411440
  3 Spin_Up_Time            0x0003   092   089   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       86
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   075   060   045    Pre-fail  Always       -       30313429
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       2009
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       89
 18 Unknown_Attribute       0x000b   100   100   050    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       8590065666
190 Airflow_Temperature_Cel 0x0022   074   054   000    Old_age   Always       -       26 (Min/Max 20/32)
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       21
193 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       4171
194 Temperature_Celsius     0x0022   026   046   000    Old_age   Always       -       26 (0 20 0 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0023   100   100   001    Pre-fail  Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       1024 (63 38 0)
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       38794074162
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       37315803905


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      2009         -


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
I may initialize a long self test. no sectors seem faulty.

Unfortunately no free sata controller there, both of mine are in use. the replacement is on its way.

---

### Post by TheFu on 2021-12-03
The **seek** and **read** error rates are very concerning. So is the Command_Timeout.  Especially for a disk THAT new.
On a disk here:
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
**  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0**
  2 Throughput_Performance  0x0005   131   131   054    Pre-fail  Offline      -       148
  3 Spin_Up_Time            0x0007   133   133   024    Pre-fail  Always       -       299 (Average 276)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       85
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
**  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0**
  8 Seek_Time_Performance   0x0005   131   131   020    Pre-fail  Offline      -       29
  9 **Power_On_Hours**          0x0012   093   093   000    Old_age   Always       -       **55130**
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       85
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       787
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       787
194 Temperature_Celsius     0x0002   166   166   000    Old_age   Always       -       36 (Min/Max 21/51)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       [COLOR="#FF0000"]3[/COLOR]
```
55130 hrs powered on is over 6 yrs of use. That drive had a 3 yr warranty.

I think your HDD is failing - or the controller is failing.

---

### Post by herrb on 2021-12-04
I dont think its the disk. The numbers go through all my 11 Disks. I guess it's the controller.
The connection is somewhat loose on the mainboard. This is also something to be fixed asap.

Apparently these smart values cannot be reset. So when I plug the drive directly to the mainboard connector, there is no way to tell, if the high values are gone?
Or if i was due to a bad connection, will thosevalues go down eventually or stay there forever?

I checked the smart values on my other server and the values seem okay there.

---

### Post by HermanAB on 2021-12-04
Bad power quality is frequently the reason for corruptions.  Maybe you just need to upgrade your UPS.

---

### Post by TheFu on 2021-12-04
> **herrb said:**
> I dont think its the disk. The numbers go through all my 11 Disks. I guess it's the controller.
The connection is somewhat loose on the mainboard. This is also something to be fixed asap.

Apparently these smart values cannot be reset. So when I plug the drive directly to the mainboard connector, there is no way to tell, if the high values are gone?
Or if i was due to a bad connection, will thosevalues go down eventually or stay there forever?

I checked the smart values on my other server and the values seem okay there.

The way to use SMART is to save the results weekly and compare the changes over time.  This is for every OS.  Manufacturers have tools to reset SMART, but that isn't available to normal people.  I've purchased used enterprise HDDs a few times and everything was reset to 0, except the Power-On hours and data tied to that - SMART Self-test history.  I put a date-stamp in the output file name.

BTW, the reason I **do** think the SATA cable is at fault is from the last parameter, 199 UDMA_CRC_Error_Count. That's where cable issues tend to show.

---

### Post by herrb on 2022-02-04
Long time no see.

I have had the machine running for some time (without the Hard disk expander card).
A couple of days before I did a standard maintenance reboot with the command `shutdown -r 0` after which one of the harddrives needed a scan again. This time it was connected directly to the mainboard.
Is there anything wrong with rebooting with shutdown -r 0?

LG,

Julian

---

### Post by HermanAB on 2022-02-04
Next time, plug a laptop  computer into an ethernet port of the server and try to connect with SSH.  It may help if you use a static IP address.

---


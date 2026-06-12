---
title: "The disk drive for /tmp is not ready yet or not present - Ubuntu 12.04 LTS"
date: 2014-03-07
forum: General Help
---

### Post by Joe_Johnston on 2014-03-07
Hi All,

I have been getting this error when booting and followed the direction from this link: [http://akovid.blogspot.com/2014/01/the-disk-drive-for-tmp-is-not-ready-yet.html](http://akovid.blogspot.com/2014/01/the-disk-drive-for-tmp-is-not-ready-yet.html)

If you get the error "The disk drive for /tmp is not ready yet or not present" during boot process then run the following command in ubuntu:


sudo mv /tmp /tmp_old
sudo mkdir /tmp
sudo chmod -R 777 /tmp


Reboot your system and if you want you can delete the /tmp_old folder.

But need to know how to remove the old /tmp_old folder. It has files in it that seem locked and will not allow me to delete. Does anyone have some advice to help me remove this folder? Thank you.

Java Joe

P.S. I had to reboot earlier and the /tmp error is still happening. Is there any way to get rid of this?

---

### Post by Bashing-om on 2014-03-07
Joe_Johnston; Hi !

Kinda strange, is not that temporary directory not gone after a re-boot ?
Else; 
> 
RMDIR(1)                         User Commands                        RMDIR(1)
NAME
       rmdir - remove empty directories

SYNOPSIS
       rmdir [OPTION]... DIRECTORY...
DESCRIPTION
       Remove the DIRECTORY(ies), if they are empty.

Maybe with root access, delete the files first in the directory /tmp-old, then remove the directory ?

Elseif: post back for inspection:
```

ls -la /tmp-old

``` and we will see if we can figure out what is going on !

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Joe_Johnston on 2014-03-07
> **Bashing-om said:**
> Joe_Johnston; Hi !

Kinda strange, is not that temporary directory not gone after a re-boot ?
Else; 

Maybe with root access, delete the files first in the directory /tmp-old, then remove the directory ?

Elseif: post back for inspection:
```

ls -la /tmp-old

``` and we will see if we can figure out what is going on !
[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]


Thank you for the quick reply. Here is my output for both directories:

joe@joe-Satellite-A105:~$ sudo ls -la /tmp_old
total 56
drwxrwxrwt 13 root    root    4096 Mar  7 09:41 .
drwxr-xr-x 26 root    root    4096 Mar  7 09:42 ..
drwxrwxrwt  2 lightdm lightdm 4096 Mar  5 08:38 at-spi2
drwx------  2 joe     joe     4096 Mar  5 08:40 .com.google.Chrome.Nc5oDU
drwxrwxrwt  2 root    root    4096 Mar  5 08:38 .ICE-unix
drwx------  2 joe     joe     4096 Mar  5 08:39 keyring-omELL7
drwx------  2 root    root    4096 Mar  5 08:38 pulse-2L9K88eMlGn7
drwx------  2 lightdm lightdm 4096 Mar  5 08:39 pulse-CcctT9RwKSB1
drwx------  2 joe     joe     4096 Mar  5 08:39 pulse-do51PII1XWP5
drwx------  2 root    root    4096 Mar  5 08:38 pulse-PKdhtXMmr18n
drwx------  2 joe     joe     4096 Mar  5 08:38 ssh-siEOpjIM1841
drwxrwxrwx 12 root    root    4096 Mar  7 09:35 tmp
-rw-rw-r--  1 lightdm lightdm    0 Mar  5 08:38 unity_support_test.0
-r--r--r--  1 root    root      11 Mar  5 08:38 .X0-lock
drwxrwxrwt  2 root    root    4096 Mar  5 08:38 .X11-unix


joe@joe-Satellite-A105:~$ sudo ls -la /tmp
total 60
drwxrwxrwx 14 root    root    4096 Mar  7 11:53 .
drwxr-xr-x 26 root    root    4096 Mar  7 09:42 ..
drwxrwxrwt  2 lightdm lightdm 4096 Mar  7 10:51 at-spi2
drwx------  2 joe     joe     4096 Mar  7 10:53 .com.google.Chrome.asGNyk
drwxrwxrwt  2 root    root    4096 Mar  7 10:52 .ICE-unix
drwx------  2 joe     joe     4096 Mar  7 10:52 keyring-cvs6Oq
drwx------  2 joe     joe     4096 Mar  7 11:35 MozillaMailnews
drwx------  2 root    root    4096 Mar  7 10:51 pulse-2L9K88eMlGn7
drwx------  2 lightdm lightdm 4096 Mar  7 10:52 pulse-CcctT9RwKSB1
drwx------  2 joe     joe     4096 Mar  7 10:52 pulse-LSXeOn91Mg1y
drwx------  2 root    root    4096 Mar  7 10:51 pulse-PKdhtXMmr18n
drwx------  2 joe     joe     4096 Mar  7 10:52 ssh-BqZPQRWG1876
-rw-rw-r--  1 lightdm lightdm    0 Mar  7 10:51 unity_support_test.0
drwxr-xr-x  2 root    root    4096 Mar  7 10:51 .winbindd
-r--r--r--  1 root    root      11 Mar  7 10:51 .X0-lock
drwxrwxrwt  2 root    root    4096 Mar  7 10:51 .X11-unix

Let me know if you need anything further.

---

### Post by Bashing-om on 2014-03-07
Joe_Johnston; Well !

Let's poke at it a bit.
> 
 By default, rm does not remove directories.  Use the --recursive (-r or
       -R) option to remove each listed directory, too, along with all of  its
       contents.

```

sudo rm -R /tmp-old

```

[INDENT][/INDENT]all in the process of learning

---

### Post by Joe_Johnston on 2014-03-07
> **Bashing-om said:**
> Joe_Johnston; Well !

Let's poke at it a bit.

```

sudo rm -R /tmp-old

```
all in the process of learning

That got it! Now, do I need to leave the /tmp folder or remove that as well? Thank you.

---

### Post by Bashing-om on 2014-03-07
Joe_Johnston; Good deal !

See - reading- is good !

As to the present /tmp directory, like this, it resides in ram space and as such is rebuilt upon each boot (cold boot that is) instance. It is required for the well being of the operating system ! You should not have to do anything to it as the operating system will take care of it.


all in the care and feeding
[INDENT][INDENT]of your ubuntu
[/INDENT][/INDENT]

---

### Post by tgalati4 on 2014-03-07
Why is the disk drive not ready?  Check the health of the disk drive:

```
sudo smartctl -a /dev/sda
```

---

### Post by Joe_Johnston on 2014-03-07
> **tgalati4 said:**
> Why is the disk drive not ready?  Check the health of the disk drive:

```
sudo smartctl -a /dev/sda
```


Here is the output:

joe@joe-Satellite-A105:~$ sudo smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.11.0-18-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)


=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD (80 GB and above)
Device Model:     TOSHIBA MK1234GSX
Serial Number:    26SM9358S
Firmware Version: AH001A
User Capacity:    120,034,123,776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Mar  7 15:14:11 2014 MST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  435) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  86) minutes.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1620
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       4727
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       76
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   060   060   000    Old_age   Always       -       16364
 10 Spin_Retry_Count        0x0033   194   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       4568
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       53
193 Load_Cycle_Count        0x0032   037   037   000    Old_age   Always       -       637261
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       47 (Min/Max 9/65)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       30
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       8
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       8290
222 Loaded_Hours            0x0032   081   081   000    Old_age   Always       -       7640
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       293
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0


SMART Error Log Version: 1
ATA Error Count: 77 (device log contains only the most recent five errors)
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


Error 77 occurred at disk power-on lifetime: 16295 hours (678 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 4a be 17 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x0017be4a = 1556042


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 40 91 bc 17 e0 00      10:37:07.636  READ DMA
  c8 00 0f b6 d2 33 e0 00      10:37:07.581  READ DMA
  e7 00 00 00 00 00 a0 00      10:37:07.577  FLUSH CACHE
  e7 00 00 00 00 00 a0 00      10:37:07.576  FLUSH CACHE
  c8 00 40 51 a4 16 e0 00      10:37:07.567  READ DMA


Error 76 occurred at disk power-on lifetime: 16271 hours (677 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 cb bd 17 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x0017bdcb = 1555915


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 40 c9 bb 17 e0 00      01:18:36.966  READ DMA
  c8 00 40 91 bc 17 e0 00      01:18:36.950  READ DMA
  c8 00 38 e1 30 2c e0 00      01:18:36.837  READ DMA
  c8 00 20 a1 32 2c e0 00      01:18:36.836  READ DMA
  c8 00 18 f9 31 2c e0 00      01:18:36.835  READ DMA


Error 75 occurred at disk power-on lifetime: 16192 hours (674 days + 16 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 7c 3f 43 e1  Error: ICRC, ABRT 1 sectors at LBA = 0x01433f7c = 21184380


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d7 3d 43 e1 00   8d+12:34:19.414  READ DMA
  e7 00 00 00 00 00 a0 00   8d+12:34:19.414  FLUSH CACHE
  c8 00 18 7f 60 5e e9 00   8d+12:34:19.398  READ DMA
  e7 00 00 00 00 00 a0 00   8d+12:34:19.397  FLUSH CACHE
  c8 00 08 bf b3 41 e1 00   8d+12:34:19.387  READ DMA


Error 74 occurred at disk power-on lifetime: 15980 hours (665 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 9f 92 1a e0  Error: ICRC, ABRT 1 sectors at LBA = 0x001a929f = 1741471


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 1a 6c 92 1a e0 00      15:00:59.254  READ DMA
  e7 00 00 00 00 00 a0 00      15:00:58.136  FLUSH CACHE
  ca 00 08 4f e4 5b e0 00      15:00:58.094  WRITE DMA
  ca 00 08 47 e4 5b e0 00      15:00:58.094  WRITE DMA
  ca 00 08 57 e4 5b e0 00      15:00:58.093  WRITE DMA


Error 73 occurred at disk power-on lifetime: 15979 hours (665 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 40 3f 85 e4  Error: ICRC, ABRT 1 sectors at LBA = 0x04853f40 = 75841344


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 3f 3d 85 e4 00      14:20:59.090  READ DMA
  c8 00 08 2f d7 3a e3 00      14:20:59.084  READ DMA
  c8 00 08 1f d7 3a e3 00      14:20:59.079  READ DMA
  c8 00 08 7f 18 5a e4 00      14:20:59.073  READ DMA
  c8 00 08 17 d7 3a e3 00      14:20:59.068  READ DMA


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


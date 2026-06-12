---
title: "Boot Issue on Linux - &quot;I/O error&quot; on dev sda"
date: 2024-08-24
forum: General Help
---

### Post by corradopatruno on 2024-08-24
Hi everyone,
I'm facing a serious issue when trying to boot my Linux PC. The system hangs during startup and displays a series of error messages that I can't fully understand. Below is the complete error message that appears:
less
Copia codice

```
[6.314461] blk_update_request: I/O error, dev sda, sector 2142 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[6.314504] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[6.314516] ata6.00: failed command: READ FPDMA QUEUED
[6.314522] ata6.00: cmd 60/08:00:60:00:00/00:00:00:00:00/40 tag 5 ncq dma 4096 in
         res 51/40:00:60:00:00/00:00:00:00:00/00 Emask 0x9 (media error)
[6.314545] ata6.00: status: { DRDY ERR }
[6.314550] ata6.00: error: { UNC }
[6.315037] blk_update_request: I/O error, dev sda, sector 2142 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[6.315057] Buffer I/O error on dev sda1, logical block 11, async page read
[7.332588] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[7.332610] ata6.00: failed command: READ FPDMA QUEUED
[7.332620] ata6.00: cmd 60/08:00:60:00:00/00:00:00:00:00/40 tag 5 ncq dma 4096 in
         res 51/40:00:60:00:00/00:00:00:00:00/00 Emask 0x9 (media error)
[7.332662] ata6.00: status: { DRDY ERR }
[7.332669] ata6.00: error: { UNC }
[7.332701] blk_update_request: I/O error, dev sda, sector 2142 op 0x0:(READ) flags 0x0 phys_seg 1 prio class 0
[7.332719] Buffer I/O error on dev sda1, logical block 11, async page read
```


I&#8217;m not exactly sure what these messages mean, but it seems like there&#8217;s a problem with the disk (sda). I&#8217;ve tried rebooting several times, but the issue persists. I haven&#8217;t made any recent changes to the system.
Does anyone know how I can proceed to resolve this issue? Are there any diagnostic commands or tests I can run to better identify the root cause?
Thanks in advance for your help!

---

### Post by &amp;KyT$0P# on 2024-08-24
Do you have backup of your data?

Can you boot this system from live USB?  If so, start with this in the live USB
```
sudo apt install smartmontools
sudo systemctl disable --now smartd
sudo smartctl -t short /dev/sda
```

After the short SMART test completes, please run
```
sudo smartctl -a /dev/sda
```
and post the output here.

Note that the disk in question might not still be "/dev/sda" in the live USB session - use [FONT=monospace]lsblk[/FONT] to help find it

---

### Post by corradopatruno on 2024-08-24
this is the output:

```
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sdc
smartctl 7.4 2023-06-25 r5336 [x86_64-linux-6.8.0-31-generic] (local build)
Copyright (C) 2002-23, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)


=== START OF INFORMATION SECTION ===
Model Family:     Marvell based SanDisk SSDs
Device Model:     SanDisk SSD PLUS 480GB
Serial Number:    2014B4307558
LU WWN Device Id: 5 001b44 e25e09d44
Firmware Version: UE6100RL
User Capacity:    480,103,981,056 bytes [480 GB]
Sector Sizes:     512 bytes logical, 512 bytes physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
TRIM Command:     Available, deterministic
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-3 T13/2161-D revision 5
SATA Version is:  SATA 3.2, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sat Aug 24 17:12:38 2024 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00) Offline data collection activity
                                        was never started.
                                        Auto Offline Data Collection: Disabled.
Self-test execution status:      (  0) The previous self-test routine completed
                                        without error or no self-test has ever 
                                        been run.
Total time to complete Offline 
data collection:                (   120) seconds.
Offline data collection
capabilities:                    (0x1b) SMART execute Offline immediate.
                                        Auto Offline data collection support.    
                                        Suspend Offline collection upon new
                                        command.
                                        No Offline surface scan supported.    
                                        Self-test supported.    
                                        No Conveyance Self-test supported.    
                                        Selective Self-test supported.    
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.    
Error logging capability:        (0x01) Error logging supported.    
                                        General Purpose Logging supported.    
Short self-test routine       
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        (  85) minutes.
SCT capabilities:              (0x0032) SCT Status supported.
                                        SCT Data Table supported.


SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0032   100   100   100    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       2684
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1784
166 Min_W/E_Cycle           0x0022   100   100   000    Old_age   Always       -       582
167 Min_Bad_Block/Die       0x0022   100   100   010    Old_age   Always       -       0
168 Maximum_Erase_Cycle     0x0032   100   100   000    Old_age   Always       -       1094
169 Total_Bad_Block         0x0032   100   100   000    Old_age   Always       -       0
170 Unknown_Marvell_Attr    0x0032   100   100   010    Old_age   Always       -       1
171 Program_Fail_Count      0x0032   100   100   000    Old_age   Always       -       0
172 Erase_Fail_Count        0x0032   100   100   000    Old_age   Always       -       0
173 Avg_Write/Erase_Count   0x0032   100   100   000    Old_age   Always       -       528
174 Unexpected_Power_Loss_Ct0x0030   100   100   000    Old_age   Offline      -       48 (Min/Max 0/52)
180 Unused_Rsvd_Blk_Cnt_Tot 0x0033   100   100   052    Pre-fail  Always       -       322 60 322
184 End-to-End_Error        0x0032   100   100   090    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   068   062   000    Old_age   Always       -       32 (Min/Max 22/43)
199 SATA_CRC_Error          0x0032   100   100   000    Old_age   Always       -       0
202 Perc_Worn_Blocks        0x0032   100   100   000    Old_age   Offline      -       1393
206 Perc_Avail_Resvd_Space  0x0032   100   100   000    Old_age   Offline      -       169
210 Total_NAND_Writes_GB    0x0032   100   100   000    Old_age   Offline      -       6553
246 Total_Writes_GiB        0x0032   100   100   000    Old_age   Offline      -       2526
247 Total_Reads_GiB         0x0032   100   100   000    Old_age   Offline      -       3528
248 Thermal_Throttle        0x0032   100   100   000    Old_age   Offline      -       0


SMART Error Log Version: 1
No Errors Logged


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      2685         -


Selective Self-tests/Logging not supported


The above only provides legacy SMART information - try `smartctl -x` for more
```

---

### Post by deadflowr on 2024-08-24
Support thread
moved to General Help sub-forum

---

### Post by corradopatruno on 2024-08-26
Any suggestions?

---

### Post by currentshaft on 2024-08-26
How is the disk connected to your PC?

---

### Post by corradopatruno on 2024-08-27
The PC has two hard drives and an SSD. The SSD is the one causing problems. All three are connected to the motherboard with SATA cables. The SSD has a dual boot setup with Windows and Linux, while the two hard drives are used as storage partitions for Windows. The Windows partition on the SSD works correctly, as I was able to recover Linux data from Windows. I initially thought it was a connection problem, so I swapped the SATA cables, but that didn&#8217;t solve the issue. I also ran software tests to check the disk's health, but everything appears to be in good condition. I suspected a filesystem issue, but even after running the fsck command from a live USB, no errors were found. Now I&#8217;m stuck and considering whether I should try cloning the SSD to another drive.

---

### Post by sudodus on 2024-08-27
When you boot the computer from a live drive (for example a USB pendrive with Ubuntu), can you mount the linux partition on the SSD and read the files there?

In other words, is the file system good? In that case 'only' some file involved in booting is bad.

Are there important data on the SSD, that you have not backed up? Or would it be OK to reinstall your linux system (by overwriting the current one)?

---

### Post by corradopatruno on 2024-08-28
to install linux on that partition would be enough to do it from the live usb? Allow me to choose the partition I want without erasing the windows part on that hard disk?

---

### Post by sudodus on 2024-08-28
Current versions of Ubuntu and flavours of Ubuntu (Kubuntu, Lubuntu, ... Xubuntu) have an option to select which partition to install into.

But you must be *very careful *when you select options in order to select the correct one before you start the process, and generally it is a good idea to *back up everything that you cannot afford to lose* before you start the installation process.

---

### Post by yancek on 2024-08-28
As pointed out in the post above, if you have not installed any Linux previously, you will need to familiarize your self with Linux device/partition naming conventions so you can select the correct device/partition during install so as not to overwrite something accidentally.  You will be given options during the install but you need to know what to select.

What is currently on /dev/sda1 as that is the source of your Input/Output error.  In fact at the very beginning of that partition and device.  Is this your Linux partition?

---


---
title: "Ubuntu 14.04: fereezes with ATA  DRDY ERR"
date: 2017-09-30
forum: General Help
---

### Post by WDYSUN on 2017-09-30
Dear All

it's now two days that I am getting crazy with my desktop computer. I have installed Ubuntu 14.04 and it worked perfect for almost two years.

Two days ago started to do some strange thing: the system boot as usual, then after something like 2-3 minutes whatever I am doing (even nothing at all) the computer freezes, I can't even   do CTRL + ALT + F2 and try to reboot from cli. I have to physicaly swicht off the power mains and then switch it on again, and the same thing happens.

I recorded the time it happens and next time I got into /var/log/syslog, this is the bit that includes the failure time:

```

Sep 30 08:12:33 oak pulseaudio[2284]: [pulseaudio] pid.c: Daemon already running.
Sep 30 08:12:33 oak dbus[1259]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Sep 30 08:12:33 oak dbus[1259]: [system] Successfully activated service 'org.freedesktop.locale1'
Sep 30 08:12:33 oak colord: Automatic database add icc-02562f8bf1ec6d87eb3f913967d51cc7 to xrandr-Dell Inc.-DELL U2715H-GH85D4AL04TL
Sep 30 08:12:33 oak colord: Automatic metadata add icc-02562f8bf1ec6d87eb3f913967d51cc7 to xrandr-Dell Inc.-DELL U2715H-GH85D4AL04TL
Sep 30 08:12:33 oak colord: Profile added: icc-02562f8bf1ec6d87eb3f913967d51cc7
Sep 30 08:12:34 oak dbus[1259]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Sep 30 08:12:34 oak udisksd[2600]: udisks daemon version 2.1.3 starting
Sep 30 08:12:34 oak dbus[1259]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Sep 30 08:12:34 oak udisksd[2600]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Sep 30 08:12:40 oak NetworkManager[1390]: <info> (eth0): IP6 addrconf timed out or failed.
Sep 30 08:12:40 oak NetworkManager[1390]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 30 08:12:40 oak NetworkManager[1390]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 30 08:12:40 oak NetworkManager[1390]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep 30 08:13:54 oak kernel: [  122.018223] ata2.00: exception Emask 0x0 SAct 0x1000 SErr 0x0 action 0x0
Sep 30 08:13:54 oak kernel: [  122.018226] ata2.00: irq_stat 0x40000008
Sep 30 08:13:54 oak kernel: [  122.018229] ata2.00: failed command: READ FPDMA QUEUED
Sep 30 08:13:54 oak kernel: [  122.018232] ata2.00: cmd 60/10:60:a0:4c:78/00:00:14:00:00/40 tag 12 ncq 8192 in
Sep 30 08:13:54 oak kernel: [  122.018232]          res 41/40:10:a0:4c:78/00:00:14:00:00/40 Emask 0x409 (media error) <F>
Sep 30 08:13:54 oak kernel: [  122.018234] ata2.00: status: { DRDY ERR }
Sep 30 08:13:54 oak kernel: [  122.018235] ata2.00: error: { UNC }
Sep 30 08:13:54 oak kernel: [  122.023930] ata2.00: configured for UDMA/133
Sep 30 08:13:54 oak kernel: [  122.023937] sd 1:0:0:0: [sda] tag#12 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 30 08:13:54 oak kernel: [  122.023938] sd 1:0:0:0: [sda] tag#12 Sense Key : Medium Error [current] [descriptor] 
Sep 30 08:13:54 oak kernel: [  122.023940] sd 1:0:0:0: [sda] tag#12 Add. Sense: Unrecovered read error - auto reallocate failed
Sep 30 08:13:54 oak kernel: [  122.023941] sd 1:0:0:0: [sda] tag#12 CDB: Read(10) 28 00 14 78 4c a0 00 00 10 00
Sep 30 08:13:54 oak kernel: [  122.023942] blk_update_request: I/O error, dev sda, sector 343428256
Sep 30 08:13:54 oak kernel: [  122.023948] ata2: EH complete
Sep 30 08:13:55 oak kernel: [  122.532160] ata2.00: exception Emask 0x0 SAct 0x10000 SErr 0x0 action 0x0
Sep 30 08:13:55 oak kernel: [  122.532163] ata2.00: irq_stat 0x40000008
Sep 30 08:13:55 oak kernel: [  122.532165] ata2.00: failed command: READ FPDMA QUEUED
Sep 30 08:13:55 oak kernel: [  122.532168] ata2.00: cmd 60/08:80:a0:4c:78/00:00:14:00:00/40 tag 16 ncq 4096 in
Sep 30 08:13:55 oak kernel: [  122.532168]          res 41/40:08:a0:4c:78/00:00:14:00:00/40 Emask 0x409 (media error) <F>
Sep 30 08:13:55 oak kernel: [  122.532170] ata2.00: status: { DRDY ERR }
Sep 30 08:13:55 oak kernel: [  122.532171] ata2.00: error: { UNC }
Sep 30 08:13:55 oak kernel: [  122.534197] ata2.00: configured for UDMA/133
Sep 30 08:13:55 oak kernel: [  122.534205] sd 1:0:0:0: [sda] tag#16 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 30 08:13:55 oak kernel: [  122.534208] sd 1:0:0:0: [sda] tag#16 Sense Key : Medium Error [current] [descriptor] 
Sep 30 08:13:55 oak kernel: [  122.534211] sd 1:0:0:0: [sda] tag#16 Add. Sense: Unrecovered read error - auto reallocate failed
Sep 30 08:13:55 oak kernel: [  122.534213] sd 1:0:0:0: [sda] tag#16 CDB: Read(10) 28 00 14 78 4c a0 00 00 08 00
Sep 30 08:13:55 oak kernel: [  122.534215] blk_update_request: I/O error, dev sda, sector 343428256
Sep 30 08:13:55 oak kernel: [  122.534222] ata2: EH complete
Sep 30 08:13:56 oak kernel: [  123.048612] ata2.00: exception Emask 0x0 SAct 0x200 SErr 0x0 action 0x0
Sep 30 08:13:56 oak kernel: [  123.048614] ata2.00: irq_stat 0x40000008
Sep 30 08:13:56 oak kernel: [  123.048616] ata2.00: failed command: READ FPDMA QUEUED
Sep 30 08:13:56 oak kernel: [  123.048618] ata2.00: cmd 60/08:48:a0:4c:78/00:00:14:00:00/40 tag 9 ncq 4096 in
Sep 30 08:13:56 oak kernel: [  123.048618]          res 41/40:08:a0:4c:78/00:00:14:00:00/40 Emask 0x409 (media error) <F>
Sep 30 08:13:56 oak kernel: [  123.048619] ata2.00: status: { DRDY ERR }
Sep 30 08:13:56 oak kernel: [  123.048620] ata2.00: error: { UNC }
Sep 30 08:13:56 oak kernel: [  123.050589] ata2.00: configured for UDMA/133
Sep 30 08:13:56 oak kernel: [  123.050596] sd 1:0:0:0: [sda] tag#9 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 30 08:13:56 oak kernel: [  123.050598] sd 1:0:0:0: [sda] tag#9 Sense Key : Medium Error [current] [descriptor] 
Sep 30 08:13:56 oak kernel: [  123.050600] sd 1:0:0:0: [sda] tag#9 Add. Sense: Unrecovered read error - auto reallocate failed
Sep 30 08:13:56 oak kernel: [  123.050602] sd 1:0:0:0: [sda] tag#9 CDB: Read(10) 28 00 14 78 4c a0 00 00 08 00
Sep 30 08:13:56 oak kernel: [  123.050603] blk_update_request: I/O error, dev sda, sector 343428256
Sep 30 08:13:56 oak kernel: [  123.050609] ata2: EH complete
Sep 30 08:13:56 oak kernel: [  123.559130] ata2.00: exception Emask 0x0 SAct 0x2000000 SErr 0x0 action 0x0
Sep 30 08:13:56 oak kernel: [  123.559132] ata2.00: irq_stat 0x40000008
Sep 30 08:13:56 oak kernel: [  123.559134] ata2.00: failed command: READ FPDMA QUEUED
Sep 30 08:13:56 oak kernel: [  123.559136] ata2.00: cmd 60/08:c8:a0:4c:78/00:00:14:00:00/40 tag 25 ncq 4096 in
Sep 30 08:13:56 oak kernel: [  123.559136]          res 41/40:08:a0:4c:78/00:00:14:00:00/40 Emask 0x409 (media error) <F>
Sep 30 08:13:56 oak kernel: [  123.559137] ata2.00: status: { DRDY ERR }
Sep 30 08:13:56 oak kernel: [  123.559138] ata2.00: error: { UNC }
Sep 30 08:13:56 oak kernel: [  123.561222] ata2.00: configured for UDMA/133
Sep 30 08:13:56 oak kernel: [  123.561228] sd 1:0:0:0: [sda] tag#25 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 30 08:13:56 oak kernel: [  123.561229] sd 1:0:0:0: [sda] tag#25 Sense Key : Medium Error [current] [descriptor] 
Sep 30 08:13:56 oak kernel: [  123.561231] sd 1:0:0:0: [sda] tag#25 Add. Sense: Unrecovered read error - auto reallocate failed
Sep 30 08:13:56 oak kernel: [  123.561232] sd 1:0:0:0: [sda] tag#25 CDB: Read(10) 28 00 14 78 4c a0 00 00 08 00
Sep 30 08:13:56 oak kernel: [  123.561233] blk_update_request: I/O error, dev sda, sector 343428256
Sep 30 08:13:56 oak kernel: [  123.561238] ata2: EH complete
Sep 30 08:13:57 oak kernel: [  124.069548] ata2.00: exception Emask 0x0 SAct 0x200 SErr 0x0 action 0x0
Sep 30 08:13:57 oak kernel: [  124.069556] ata2.00: irq_stat 0x40000008
Sep 30 08:13:57 oak kernel: [  124.069563] ata2.00: failed command: READ FPDMA QUEUED
Sep 30 08:13:57 oak kernel: [  124.069573] ata2.00: cmd 60/08:48:a0:4c:78/00:00:14:00:00/40 tag 9 ncq 4096 in
Sep 30 08:13:57 oak kernel: [  124.069573]          res 41/40:08:a0:4c:78/00:00:14:00:00/40 Emask 0x409 (media error) <F>
Sep 30 08:13:57 oak kernel: [  124.069579] ata2.00: status: { DRDY ERR }
Sep 30 08:13:57 oak kernel: [  124.069582] ata2.00: error: { UNC }
Sep 30 08:13:57 oak kernel: [  124.071756] ata2.00: configured for UDMA/133
Sep 30 08:13:57 oak kernel: [  124.071776] sd 1:0:0:0: [sda] tag#9 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 30 08:13:57 oak kernel: [  124.071783] sd 1:0:0:0: [sda] tag#9 Sense Key : Medium Error [current] [descriptor] 
Sep 30 08:13:57 oak kernel: [  124.071789] sd 1:0:0:0: [sda] tag#9 Add. Sense: Unrecovered read error - auto reallocate failed
Sep 30 08:13:57 oak kernel: [  124.071795] sd 1:0:0:0: [sda] tag#9 CDB: Read(10) 28 00 14 78 4c a0 00 00 08 00
Sep 30 08:13:57 oak kernel: [  124.071799] blk_update_request: I/O error, dev sda, sector 343428256
Sep 30 08:13:57 oak kernel: [  124.071816] ata2: EH complete
Sep 30 08:13:57 oak kernel: [  124.576547] ata2.00: exception Emask 0x0 SAct 0x800000 SErr 0x0 action 0x0
Sep 30 08:13:57 oak kernel: [  124.576554] ata2.00: irq_stat 0x40000008
Sep 30 08:13:57 oak kernel: [  124.576561] ata2.00: failed command: READ FPDMA QUEUED
Sep 30 08:13:57 oak kernel: [  124.576572] ata2.00: cmd 60/08:b8:a0:4c:78/00:00:14:00:00/40 tag 23 ncq 4096 in
Sep 30 08:13:57 oak kernel: [  124.576572]          res 41/40:08:a0:4c:78/00:00:14:00:00/40 Emask 0x409 (media error) <F>
Sep 30 08:13:57 oak kernel: [  124.576577] ata2.00: status: { DRDY ERR }
Sep 30 08:13:57 oak kernel: [  124.576581] ata2.00: error: { UNC }
Sep 30 08:13:57 oak kernel: [  124.578753] ata2.00: configured for UDMA/133
Sep 30 08:13:57 oak kernel: [  124.578773] sd 1:0:0:0: [sda] tag#23 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Sep 30 08:13:57 oak kernel: [  124.578780] sd 1:0:0:0: [sda] tag#23 Sense Key : Medium Error [current] [descriptor] 
Sep 30 08:13:57 oak kernel: [  124.578786] sd 1:0:0:0: [sda] tag#23 Add. Sense: Unrecovered read error - auto reallocate failed
Sep 30 08:13:57 oak kernel: [  124.578792] sd 1:0:0:0: [sda] tag#23 CDB: Read(10) 28 00 14 78 4c a0 00 00 08 00
Sep 30 08:13:57 oak kernel: [  124.578796] blk_update_request: I/O error, dev sda, sector 343428256
Sep 30 08:13:57 oak kernel: [  124.578812] ata2: EH complete

```


and you see that line saying

```
 
Sep 30 08:13:54 oak kernel: [  122.018234] ata2.00: status: { DRDY ERR }

```

I investigated a bit, but I couldn't find any solution. I checked the disk booting in rescue mode, but it seems ok.


Please help me... I am desperate.
Regards
Pierre

---

### Post by Bashing-om on 2017-09-30
WDYSUN; Hello;

The concern at this time is the health of the drive.
Post back:
```

sudo smartctl -a /dev/sda

```

let's see what the controller thinks.

[INDENT]nothing last forever, but ----[/INDENT]

---

### Post by WDYSUN on 2017-09-30
Hello,

this is the output of  'sudo smartctl -a /dev/sda'

```

sudo smartctl -a /dev/sda
[sudo] password for pietro:
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-4.4.0-96-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     SanDisk SDSSDXPS240G
Serial Number:    142773400738
LU WWN Device Id: 5 001b44 c498a30a2
Firmware Version: X21000RL
User Capacity:    240,057,409,536 bytes [240 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 T13/2015-D revision 3
SATA Version is:  SATA >3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Sat Sep 30 09:25:04 2017 CEST
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
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x11) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
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
recommended polling time:      (  10) minutes.

SMART Attributes Data Structure revision number: 4
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0032   100   100   ---    Old_age   Always -       32
  9 Power_On_Hours          0x0032   253   100   ---    Old_age   Always -       5707
 12 Power_Cycle_Count       0x0032   100   100   ---    Old_age   Always -       1473
166 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       1
167 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       54
168 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       105
169 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       1050
171 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       32
172 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       0
173 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       32
174 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       50
184 End-to-End_Error        0x0032   100   100   ---    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   ---    Old_age   Always       -       13809
188 Command_Timeout         0x0032   100   100   ---    Old_age   Always       -       31
194 Temperature_Celsius     0x0022   067   042   ---    Old_age   Always       -       33 (Min/Max 12/42)
199 UDMA_CRC_Error_Count    0x0032   100   100   ---    Old_age   Always       -       0
212 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       0
230 Unknown_SSD_Attribute   0x0032   100   100   ---    Old_age   Always       -       262
232 Available_Reservd_Space 0x0033   100   100   004    Pre-fail  Always       -       99
233 Media_Wearout_Indicator 0x0032   100   100   ---    Old_age   Always       -       8658
241 Total_LBAs_Written      0x0030   253   253   ---    Old_age   Offline      -       4158
242 Total_LBAs_Read         0x0030   253   253   ---    Old_age   Offline      -       4173
244 Unknown_Attribute       0x0032   000   100   ---    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 13051 (device log contains only the most recent five errors)
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

Error 13051 occurred at disk power-on lifetime: 5707 hours (237 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  51 40 02 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:00:00.000  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:00:00.000  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]

Error 13050 occurred at disk power-on lifetime: 5707 hours (237 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  51 40 02 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:00:00.000  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:00:00.000  SET FEATURES [Set transfer mode]

Error 13049 occurred at disk power-on lifetime: 5707 hours (237 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  51 40 02 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:00:00.000  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:00:00.000  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]

Error 13048 occurred at disk power-on lifetime: 5707 hours (237 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  51 40 02 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]

Error 13047 occurred at disk power-on lifetime: 5707 hours (237 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  51 40 02 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:00:00.000  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:00:00.000  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours) LBA_of_first_error
# 1  Extended offline    Completed: read failure       00%      3351 342304904
# 2  Extended offline    Aborted by host               00%      3351         -
# 3  Extended offline    Completed without error       00%         0         -
# 4  Extended offline    Completed: read failure       00%      3350         1352872
1 of 2 failed self-tests are outdated by newer successful extended offline self-test # 3

Selective Self-tests/Logging not supported

```

---

### Post by Bashing-om on 2017-09-30
WDYSUN; Humm ...

I can not place much confidence in what is reported :
> 
Device is:        Not in smartctl database [for details use: -P showall]


Others with the greater skills perhaps can offer a better means of determining the drive's state .

I can ask however, as this is  SSD, that you check the firmware that all settings are sane .. and make sure that AHCI is enabled .

[INDENT]sometimes, I just do not know
[/INDENT]

---

### Post by WDYSUN on 2017-09-30
> **Bashing-om said:**
> WDYSUN; Humm ...
....
I can ask however, as this is  SSD, that you check the firmware that all settings are sane .. and make sure that AHCI is enabled


it is an SSD (sandisk pro). Where do I check  AHCI is enabled?

Regards
Pierre

---

### Post by Bashing-om on 2017-09-30
WDYSUN; Hey

> 
it is an SSD (sandisk pro). Where do I check AHCI is enabled?


Will be in your firmnware (bios) . As to how to access and how to check, well all I can suggest is to read the instructions.
(yes, UNgood but the best I can say )
Each manufacturer implements different - there is no standard . I can not know what your hardware is or how to manage it, as I do not have access to said hardware .

[INDENT][INDENT]a know it all I am not[/INDENT][/INDENT]

---

### Post by WDYSUN on 2017-09-30
Hi

yes the AHCI is enabled in bios. I am not sure whether the following  is something but I tried to select a previous kernel from grub and the boot incurs in some error and the graphic device never starts. The latest kernel I have is 4.4.0-96, I tried the 4.4.0-93 and also previous, but all give me the same problem.

Can it be the graphic card? I have an nvdia with the proprietary drivers. What kind of check should  I do to very verify the graphic deparment?

Regards
Pierre

---

### Post by WDYSUN on 2017-09-30
Dear All

my suspect about the graphic card is wrong because I logged in with cli without loading the graphic device. I did some work on the terminal and after the usual 2-3 minnutes the computer freezed with the following message on the screen

```

Buffer I/O error on /dev sda2 , logical block 39854154, lost async page write 

```

So I guess is either a partition problem or disk problem. The problem here is that I can't do too much because the computer works for no more than 2-3 mins

... I am geting crazy with this!
Pierre

---

### Post by mörgæs on 2017-09-30
Here's someone with a similar problem (and a solution):

[https://www.linuxquestions.org/questions/linux-hardware-18/buffer-i-o-error-on-dev-sdb1-async-page-read-4175600715/](https://www.linuxquestions.org/questions/linux-hardware-18/buffer-i-o-error-on-dev-sdb1-async-page-read-4175600715/)

---

### Post by WDYSUN on 2017-10-02
> **mörgæs said:**
> Here's someone with a similar problem (and a solution):

[https://www.linuxquestions.org/questions/linux-hardware-18/buffer-i-o-error-on-dev-sdb1-async-page-read-4175600715/](https://www.linuxquestions.org/questions/linux-hardware-18/buffer-i-o-error-on-dev-sdb1-async-page-read-4175600715/)

Hello thanks, I noticed that but that was about an NTFS partition I am not sure I will apply in my case. Today the pc is working without problems, but I am still conceaned about the HD health. I ran a long test with ```
smartctl -t long   /dev/sda 
```, and I report the result below. 

Is there anybody in here that can read this output, I tried to go through the smartools documentation, but some of the parameters are really very difficult to understand for non HD expert like me.  Since the system is now working after two days of struggling.. I wonder whether it's really a good idea to replace the HD. Below the smartctl report done today 

Regards
Pierre 

```

smartctl 6.2 2013-07-26 r3841 [x86_64-linux-4.4.0-96-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     SanDisk SDSSDXPS240G
Serial Number:    142773400738
LU WWN Device Id: 5 001b44 c498a30a2
Firmware Version: X21000RL
User Capacity:    240.057.409.536 bytes [240 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 T13/2015-D revision 3
SATA Version is:  SATA >3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Mon Oct  2 09:08:15 2017 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 112)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		(    0) seconds.
Offline data collection
capabilities: 			 (0x11) SMART execute Offline immediate.
					No Auto Offline data collection support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					No Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  10) minutes.

SMART Attributes Data Structure revision number: 4
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0032   100   100   ---    Old_age   Always       -       32
  9 Power_On_Hours          0x0032   253   100   ---    Old_age   Always       -       5709
 12 Power_Cycle_Count       0x0032   100   100   ---    Old_age   Always       -       1482
166 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       1
167 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       54
168 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       105
169 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       1050
171 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       32
172 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       0
173 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       33
174 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       56
184 End-to-End_Error        0x0032   100   100   ---    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   ---    Old_age   Always       -       13823
188 Command_Timeout         0x0032   100   100   ---    Old_age   Always       -       31
194 Temperature_Celsius     0x0022   069   042   ---    Old_age   Always       -       31 (Min/Max 12/42)
199 UDMA_CRC_Error_Count    0x0032   100   100   ---    Old_age   Always       -       0
212 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       0
230 Unknown_SSD_Attribute   0x0032   100   100   ---    Old_age   Always       -       266
232 Available_Reservd_Space 0x0033   100   100   004    Pre-fail  Always       -       99
233 Media_Wearout_Indicator 0x0032   100   100   ---    Old_age   Always       -       8666
241 Total_LBAs_Written      0x0030   253   253   ---    Old_age   Offline      -       4158
242 Total_LBAs_Read         0x0030   253   253   ---    Old_age   Offline      -       4177
244 Unknown_Attribute       0x0032   000   100   ---    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 13057 (device log contains only the most recent five errors)
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

Error 13057 occurred at disk power-on lifetime: 5708 hours (237 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  51 40 02 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:00:00.000  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:00:00.000  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]

Error 13056 occurred at disk power-on lifetime: 5708 hours (237 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  51 40 02 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:00:00.000  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:00:00.000  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]

Error 13055 occurred at disk power-on lifetime: 5708 hours (237 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  51 40 02 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:00:00.000  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:00:00.000  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]

Error 13054 occurred at disk power-on lifetime: 5708 hours (237 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  51 40 02 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:00:00.000  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:00:00.000  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]

Error 13053 occurred at disk power-on lifetime: 5708 hours (237 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  51 40 02 00 00 00 a0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:00:00.000  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:00:00.000  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:00:00.000  SET FEATURES [Enable SATA feature]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       00%      5709         1352872
# 2  Extended offline    Completed: read failure       00%      5709         1352872
# 3  Short offline       Aborted by host               00%      5708         -
# 4  Extended offline    Aborted by host               00%      5708         -
# 5  Extended offline    Completed: read failure       00%      3351         342304904
# 6  Extended offline    Aborted by host               00%      3351         -
# 7  Extended offline    Completed without error       00%         0         -
# 8  Extended offline    Completed: read failure       00%      3350         1352872
1 of 4 failed self-tests are outdated by newer successful extended offline self-test # 7

Selective Self-tests/Logging not supported

```

---

### Post by mörgæs on 2017-10-03
> **WDYSUN said:**
> 
```

Buffer I/O error on /dev sda2 , logical block 39854154, lost async page write 

```

Since noone else has a suggestion I'll post a semigood (or -bad) one. I  have used it myself for rotating disks but have no experience with solid state.

We know the block which gives problems. The sector size is 512 bytes so let's assume the block size is 512 or 1024 bytes. This means that the error is located within the first 40 GiB of the disk.

If you back up your data you can erase the hard disk and create a partition of the first 40 GiB. This one should not be used. After that create a number of partitions for the new install (preferably something younger than 14.04).

Is the system stable now? 

If the test works well you can experiment with a partitioning scheme which does not waste all of the 40 GB.

---

### Post by WDYSUN on 2017-10-04
Dear mörgæs


In fact, it seems there were  problems on both /dev/sda1 and /dev/sda2. /dev/sda1  is a FAT booting partition, and /dev/sda2 is an ext4 partition where I installed the OS.

I booted from the live cd (Ubuntu 16.04.3),  I umounted /dev/sda and I checked with 
```

sudo fsck -n /dev/sda1
sudo fsck -n /dev/sda2

```

In both cases there where messages indicating 3-5 corrupted superblocks. I did a total backup using an external drive and I tried fsck with automatic error correction
```

sudo fsck -a /dev/sda1
sudo fsck -a /dev/sda2

```

It's now 2 days that the system works flawlessly. I am monitoring whether new erros are signaled by smartctl. I'll close the thread as soon as I have evidence that the problems is solved.

Regards
Pierre

---

### Post by WDYSUN on 2017-10-05
Dear All

I will tag this as fixed because I think the previous strategy really fixed the problem. I monitored the issue for 3 days with 


```

sudo smartctl -t long  /dev/sda

```

tracked the progress with 

```

sudo smartctl -a /dev/sda | grep "progress" -i -A 1

```

(it takes about 10 minutes to finish). At the end of the the test I compared the result with the last one done before the fix. In three days my drive did not record any new error and the 'ATA DRDY ERR' disappeared from the /var/log/syslog.


So I tag this thread as solved crossing my fingers and hoping that this really solved the issue. Thanks for contributing.

Regards
Pie

---


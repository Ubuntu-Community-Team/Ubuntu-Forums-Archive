---
title: "Ubuntu 18.04 freezes frequently - /00 binary in syslog"
date: 2018-06-26
forum: General Help
---

### Post by abxxxx on 2018-06-26
Hello everybody,

I used to be active in my native language's ubuntu forum. However, this topic seems to be a bit "deeper". That's way I wanted to address a larger community.

The issue: Unfortunately, I am experiencing frequent freezes of Ubuntu 18.04 on a Thinkpad T440p. I've been reading threads on similar problems, but reasons seem to be very diverse, so I decided to open up a new thread. Trying to give some useful information:


[LIST=1]
[*]That's my system ```
~$ inxi -ACDMNSG
System:    Host: thinkpad-t440p Kernel: 4.15.0-23-generic x86_64 bits: 64
           Desktop: Gnome 3.28.1 Distro: Ubuntu 18.04 LTS
Machine:   Device: laptop System: LENOVO product: 20AWS02800 v: ThinkPad T440p serial: N/A
           Mobo: LENOVO model: 20AWS02800 serial: N/A
           UEFI [Legacy]: LENOVO v: GLET39WW (1.14 ) date: 10/04/2013
CPU:       Dual core Intel Core i5-4300M (-MT-MCP-) cache: 3072 KB
           clock speeds: max: 3300 MHz 1: 1524 MHz 2: 1435 MHz 3: 1482 MHz
           4: 1314 MHz
Graphics:  Card-1: Intel 4th Gen Core Processor Integrated Graphics Controller
           Card-2: NVIDIA GK208M [GeForce GT 730M]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting,nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.05hz, 1920x1080@60.00hz
           OpenGL: renderer: GeForce GT 730M/PCIe/SSE2
           version: 4.6.0 NVIDIA 390.48
Audio:     Card-1 Intel 8 Series/C220 Series High Def. Audio Controller
           driver: snd_hda_intel
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-23-generic
Network:   Card-1: Intel Ethernet Connection I217-LM driver: e1000e
           Card-2: Intel Wireless 7260 driver: iwlwifi
Drives:    HDD Total Size: 500.1GB (54.0% used)
           ID-1: /dev/sda model: HGST_HTS725050A7 size: 500.1GB
``` 
[*]I initially installed 17.10 and upgraded to 18.04 
[*]I am pretty shure, the freezes I am experiencing are kernel freezes, as there is no reaction to Ctrl + Alt + F?. 
[*]I believe to observe the freezes when doing a lot of stuff at the same time or during heavy hard disk access. Especially after booting I have to wait until all applications have started up. Otherwise I am almost guaranteed to get a freeze. 
[*]Last year I droped my laptop heavily from ~1m height and experienced hard disk issues afterwards. I bought and installed a replacement HD a couple of months ago. 
[*]I run a short offline smart test with GSmartControl: Completed without error 
[*]Running the extended self-test, the system froze (I am trying again right now) 
[*]I installed the proprietary nvidia driver from the repos, as I read it might help. It didn't solve the problem for me. 
[*]I observed to have two graphical desktops booting up (is this normal?). One at tty1 and another one at tty2. 
[*]When freezing, a "binary" line of repreating /00 is written to /var/log/syslog. However, I was not able to identify a scheme in terms of cause. Posting some examples below. I cut the /00 lines at some point as they are very long. It is always hard to say, how much time passed between the last valid log and the freeze. 
[/LIST]

Example 1:

```
Jun 25 11:47:50 thinkpad-t440p rsyslogd:  [origin software="rsyslogd" swVersion="8.32.0" x-pid="984" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jun 25 11:48:01 thinkpad-t440p wpa_supplicant[976]: wlp4s0: CTRL-EVENT-SIGNAL-CHANGE above=0 signal=-69 noise=9999 txrate=240000
Jun 25 11:48:05 thinkpad-t440p wpa_supplicant[976]: wlp4s0: SME: Trying to authenticate with a0:cf:5b:3f:97:b3 (SSID='eduroam' freq=2462 MHz)
Jun 25 11:48:05 thinkpad-t440p kernel: [  371.575168] wlp4s0: disconnect from AP a0:cf:5b:3f:97:bc for new auth to a0:cf:5b:3f:97:b3
Jun 25 11:48:05 thinkpad-t440p kernel: [  371.579093] wlp4s0: authenticate with a0:cf:5b:3f:97:b3
Jun 25 11:48:05 thinkpad-t440p kernel: [  371.581519] wlp4s0: send auth to a0:cf:5b:3f:97:b3 (try 1/3)
Jun 25 11:48:05 thinkpad-t440p wpa_supplicant[976]: wlp4s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Jun 25 11:48:05 thinkpad-t440p NetworkManager[971]: <info>  [1529920085.3305] device (wlp4s0): supplicant interface state: completed -> authenticating
Jun 25 11:48:05 thinkpad-t440p wpa_supplicant[976]: wlp4s0: Trying to associate with a0:cf:5b:3f:97:b3 (SSID='eduroam' freq=2462 MHz)
Jun 25 11:48:05 thinkpad-t440p kernel: [  371.583896] wlp4s0: authenticated
Jun 25 11:48:05 thinkpad-t440p kernel: [  371.585331] wlp4s0: associate with a0:cf:5b:3f:97:b3 (try 1/3)
Jun 25 11:48:05 thinkpad-t440p kernel: [  371.593111] wlp4s0: RX ReassocResp from a0:cf:5b:3f:97:b3 (capab=0x431 status=0 aid=5)
Jun 25 11:48:05 thinkpad-t440p NetworkManager[971]: <info>  [1529920085.3421] device (wlp4s0): supplicant interface state: authenticating -> associating
Jun 25 11:48:05 thinkpad-t440p wpa_supplicant[976]: wlp4s0: Associated with a0:cf:5b:3f:97:b3
Jun 25 11:48:05 thinkpad-t440p wpa_supplicant[976]: wlp4s0: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
Jun 25 11:48:05 thinkpad-t440p wpa_supplicant[976]: wlp4s0: CTRL-EVENT-REGDOM-CHANGE init=COUNTRY_IE type=COUNTRY alpha2=DE
Jun 25 11:48:05 thinkpad-t440p kernel: [  371.594050] wlp4s0: associated
Jun 25 11:48:05 thinkpad-t440p wpa_supplicant[976]: wlp4s0: WPA: Key negotiation completed with a0:cf:5b:3f:97:b3 [PTK=CCMP GTK=CCMP]
Jun 25 11:48:05 thinkpad-t440p wpa_supplicant[976]: wlp4s0: CTRL-EVENT-CONNECTED - Connection to a0:cf:5b:3f:97:b3 completed [id=0 id_str=]
Jun 25 11:48:05 thinkpad-t440p NetworkManager[971]: <info>  [1529920085.3507] device (wlp4s0): supplicant interface state: associating -> completed
Jun 25 11:48:05 thinkpad-t440p kernel: [  371.676507] wlp4s0: Limiting TX power to 17 dBm as advertised by a0:cf:5b:3f:97:b3
Jun 25 11:48:05 thinkpad-t440p wpa_supplicant[976]: wlp4s0: CTRL-EVENT-SIGNAL-CHANGE above=1 signal=-58 noise=9999 txrate=144400
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00
```

Example 2 (unpacking an 300 MB archive with archive manager):

```
Jun 25 14:21:23 thinkpad-t440p dbus-daemon[957]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.225' (uid=1000 pid=5060 comm="file-roller /home/abx/Downloads/ThirdParty-2.3.0." label="unconfined")
Jun 25 14:21:23 thinkpad-t440p systemd[1]: Starting Hostname Service...
Jun 25 14:21:23 thinkpad-t440p dbus-daemon[957]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jun 25 14:21:23 thinkpad-t440p systemd[1]: Started Hostname Service.
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00
```

Example 3:

```
Jun 26 10:26:44 thinkpad-t440p kdeconnectd.desktop[2099]: kdeconnect.plugin.notification: Not found noti by internal Id:  "0|android|17039403|null|1000"
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\0
```

Edit: The two latest freezes:

Example 4 (running smart test in backround, firefox open, starting to compile software):


```
Jun 26 11:40:16 thinkpad-t440p smartd[1021]: Device: /dev/sda [SAT], SMART Usage Attribute: 194 Temperature_Celsius changed from 117 to 113
Jun 26 11:40:16 thinkpad-t440p smartd[1021]: Device: /dev/sda [SAT], self-test in progress, 40% remaining
Jun 26 11:41:06 thinkpad-t440p evolution-sourc[1961]: secret_service_search_sync: must specify at least one attribute to match
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00 
```

Example 5 (no /00/00 line this time):

```
Jun 26 11:52:15 thinkpad-t440p systemd[1]: Starting Stop ureadahead data collection...
Jun 26 11:52:15 thinkpad-t440p systemd[1]: Started Stop ureadahead data collection.
```



I am happy for any hint I can get and appreciate your support. Thanks a lot,

abx

---

### Post by abxxxx on 2018-06-26
Well, the extended offline smart test completed without errors. That's the report:

```
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-23-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi/HGST Travelstar Z7K500
Device Model:     HGST HTS725050A7E630
Serial Number:    RCF90KE101ZUAE
LU WWN Device Id: 5 000cca 8d4c0e80e
Firmware Version: GS2OA3E0
User Capacity:    500.107.862.016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 2.6, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Tue Jun 26 13:45:25 2018 CEST
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
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (   45) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  90) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAGS    VALUE WORST THRESH FAIL RAW_VALUE
  1 Raw_Read_Error_Rate     PO-R--   100   100   062    -    0
  2 Throughput_Performance  P-S---   100   100   040    -    0
  3 Spin_Up_Time            POS---   253   253   033    -    1
  4 Start_Stop_Count        -O--C-   100   100   000    -    582
  5 Reallocated_Sector_Ct   PO--CK   100   100   005    -    0
  7 Seek_Error_Rate         PO-R--   100   100   067    -    0
  8 Seek_Time_Performance   P-S---   100   100   040    -    0
  9 Power_On_Hours          -O--C-   097   097   000    -    1607
 10 Spin_Retry_Count        PO--C-   100   100   060    -    0
 12 Power_Cycle_Count       -O--CK   100   100   000    -    540
191 G-Sense_Error_Rate      -O-R--   100   100   000    -    0
192 Power-Off_Retract_Count -O--CK   100   100   000    -    30
193 Load_Cycle_Count        -O--C-   099   099   000    -    19511
194 Temperature_Celsius     -O----   113   113   000    -    53 (Min/Max 13/65)
196 Reallocated_Event_Count -O--CK   100   100   000    -    0
197 Current_Pending_Sector  -O---K   100   100   000    -    0
198 Offline_Uncorrectable   ---R--   100   100   000    -    0
199 UDMA_CRC_Error_Count    -O-R--   200   200   000    -    0
223 Load_Retry_Count        -O-R--   100   100   000    -    0
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
0x02           SL  R/O      1  Comprehensive SMART error log
0x03       GPL     R/O      1  Ext. Comprehensive SMART error log
0x06           SL  R/O      1  SMART self-test log
0x07       GPL     R/O      1  Extended self-test log
0x09           SL  R/W      1  Selective self-test log
0x10       GPL     R/O      1  SATA NCQ Queued Error log
0x11       GPL     R/O      1  SATA Phy Event Counters log
0x80-0x9f  GPL,SL  R/W     16  Host vendor specific log
0xe0       GPL,SL  R/W      1  SCT Command/Status
0xe1       GPL,SL  R/W      1  SCT Data Transfer

SMART Extended Comprehensive Error Log Version: 1 (1 sectors)
No Errors Logged

SMART Extended Self-test Log Version: 1 (1 sectors)
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      1607         -
# 2  Extended offline    Aborted by host               80%      1600         -
# 3  Short offline       Completed without error       00%      1599         -

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

SCT Status Version:                  3
SCT Version (vendor specific):       256 (0x0100)
SCT Support Level:                   1
Device State:                        Active (0)
Current Temperature:                    53 Celsius
Power Cycle Min/Max Temperature:     47/55 Celsius
Lifetime    Min/Max Temperature:     13/65 Celsius
Lifetime    Average Temperature:        45 Celsius
Under/Over Temperature Limit Count:   0/0

SCT Temperature History Version:     2
Temperature Sampling Period:         1 minute
Temperature Logging Interval:        1 minute
Min/Max recommended Temperature:      0/60 Celsius
Min/Max Temperature Limit:           -40/65 Celsius
Temperature History Size (Index):    128 (57)

Index    Estimated Time   Temperature Celsius
  58    2018-06-26 11:38    53  **********************************
 ...    ..(  6 skipped).    ..  **********************************
  65    2018-06-26 11:45    53  **********************************
  66    2018-06-26 11:46     ?  -
  67    2018-06-26 11:47    53  **********************************
  68    2018-06-26 11:48    53  **********************************
  69    2018-06-26 11:49    53  **********************************
  70    2018-06-26 11:50     ?  -
  71    2018-06-26 11:51    53  **********************************
  72    2018-06-26 11:52    52  *********************************
  73    2018-06-26 11:53    52  *********************************
  74    2018-06-26 11:54    51  ********************************
  75    2018-06-26 11:55    51  ********************************
  76    2018-06-26 11:56    50  *******************************
  77    2018-06-26 11:57    49  ******************************
  78    2018-06-26 11:58    49  ******************************
  79    2018-06-26 11:59    49  ******************************
  80    2018-06-26 12:00    48  *****************************
  81    2018-06-26 12:01    47  ****************************
  82    2018-06-26 12:02    48  *****************************
  83    2018-06-26 12:03    49  ******************************
 ...    ..(  4 skipped).    ..  ******************************
  88    2018-06-26 12:08    49  ******************************
  89    2018-06-26 12:09    48  *****************************
  90    2018-06-26 12:10    48  *****************************
  91    2018-06-26 12:11    48  *****************************
  92    2018-06-26 12:12    49  ******************************
  93    2018-06-26 12:13    49  ******************************
  94    2018-06-26 12:14    50  *******************************
  95    2018-06-26 12:15    51  ********************************
  96    2018-06-26 12:16    51  ********************************
  97    2018-06-26 12:17    52  *********************************
  98    2018-06-26 12:18    52  *********************************
  99    2018-06-26 12:19    52  *********************************
 100    2018-06-26 12:20    53  **********************************
 101    2018-06-26 12:21    53  **********************************
 102    2018-06-26 12:22    53  **********************************
 103    2018-06-26 12:23    54  ***********************************
 ...    ..(  5 skipped).    ..  ***********************************
 109    2018-06-26 12:29    54  ***********************************
 110    2018-06-26 12:30    55  ************************************
 ...    ..( 25 skipped).    ..  ************************************
   8    2018-06-26 12:56    55  ************************************
   9    2018-06-26 12:57    54  ***********************************
  10    2018-06-26 12:58    55  ************************************
 ...    ..( 27 skipped).    ..  ************************************
  38    2018-06-26 13:26    55  ************************************
  39    2018-06-26 13:27    54  ***********************************
 ...    ..( 14 skipped).    ..  ***********************************
  54    2018-06-26 13:42    54  ***********************************
  55    2018-06-26 13:43    53  **********************************
  56    2018-06-26 13:44    53  **********************************
  57    2018-06-26 13:45    53  **********************************

SCT Error Recovery Control:
           Read: Disabled
          Write: Disabled

Device Statistics (GP/SMART Log 0x04) not supported

SATA Phy Event Counters (GP Log 0x11)
ID      Size     Value  Description
0x0001  2            0  Command failed due to ICRC error
0x0002  2            0  R_ERR response for data FIS
0x0003  2            0  R_ERR response for device-to-host data FIS
0x0004  2            0  R_ERR response for host-to-device data FIS
0x0005  2            0  R_ERR response for non-data FIS
0x0006  2            0  R_ERR response for device-to-host non-data FIS
0x0007  2            0  R_ERR response for host-to-device non-data FIS
0x0009  2            4  Transition from drive PhyRdy to drive PhyNRdy
0x000a  2            3  Device-to-host register FISes sent due to a COMRESET
0x000b  2            0  CRC errors within host-to-device FIS
0x000d  2            0  Non-CRC errors within host-to-device FIS
```

Are there any other possible causes, I might want to check? Thank you again!

---

### Post by Holger_Gehrke on 2018-06-26
Random freezes under heavy load makes me think thermal problem or bad RAM. 

Use 'sensors' from the package 'lm-sensors' (I believe it's part of the standard install, but I could be wrong ...) to check system temperature. Clean fans and vents of any dust build-up.

A very thorough program for testing RAM should be on your GRUB menu (memtest86). Since it runs on bare metal without a loaded OS and does almost no calculations it should not make the system run hot, so if it can complete several cycles of testing -- let's say over night -- we can exclude RAM-problems as cause for the freezes.

Holger

---

### Post by abxxxx on 2018-06-26
Thank you, Holger, for the quick reply! I am going to check it and come back to you tomorrow.

---

### Post by abxxxx on 2018-06-27
> **Holger_Gehrke said:**
> Random freezes under heavy load makes me think thermal problem or bad RAM. 

Use 'sensors' from the package 'lm-sensors' (I believe it's part of the standard install, but I could be wrong ...) to check system temperature. Clean fans and vents of any dust build-up.

A very thorough program for testing RAM should be on your GRUB menu (memtest86). Since it runs on bare metal without a loaded OS and does almost no calculations it should not make the system run hot, so if it can complete several cycles of testing -- let's say over night -- we can exclude RAM-problems as cause for the freezes.

Holger

Well, the RAM test itselfs looks good to me: [IMG]https://i.imgur.com/dvbxW0U.jpg[/IMG]

However, CPU temperature was at 83°C running the test only. I think it is pretty high.
To further examinate the issue, I wrote a bash script to log temperatures with timestamp every 10 seconds
```
while [ "true" ]
do
 date >> tlog
 sensors >> tlog
 sleep 10
done
```

I tried provoking the machine to freeze while temperatures beeing logged. But, well, I didn't succeed this time.

However, those are the result:
[LIST]
[*]When running at low CPU load (10-15%), temperature is 65 - 70°C 
[*]When ramping up the CPU load to around 75% (only for 2-3 minutes), temperature goes up to 90-95°C 
[/LIST]

I think this is slightly too high. Any educated opinions?

I will now continue to open the computer and clean from dust. However, I don't think it will help much as I already cleaned when replacing the HD a couple of months ago.

Do you think it might be worthwhile to renew the cpu's thermal paste? I never did it since I purchased the computer around 5 years ago.

Thanks again and greetings,

abx

---

### Post by mrdc76 on 2018-06-27
> **abxxxx said:**
> 

However, those are the result:
[LIST]
[*]When running at low CPU load (10-15%), temperature is 65 - 70°C 
[*]When ramping up the CPU load to around 75% (only for 2-3 minutes), temperature goes up to 90-95°C 
[/LIST]

I think this is slightly too high. Any educated opinions?



I have a T450. At low CPU loads the temps are around 50 - 55°C. I have never reached temps higher than 85, even at full load.

---

### Post by abxxxx on 2018-06-27
> **mrdc76 said:**
> I have a T450. At low CPU loads the temps are around 50 - 55°C. I have never reached temps higher than 85, even at full load.

Thank you, mrdc76, for your data. As is turned out there was way to go in terms of cleaning.

Before: [IMG]https://i.imgur.com/RoKJpIP.jpg[/IMG]

After:
[IMG]https://i.imgur.com/EukK0XM.jpg[/IMG]
 
With the fan cleaned, I am reaching lower cpu temperatures now. At 10-15% load it 50-55°C (before it was 65-70°C).

Surprisingly, I experienced another freeze right away. But this time I had the temperature logging script running:
```
Mi 27. Jun 14:02:23 CEST 2018
thinkpad-isa-0000
Adapter: ISA adapter
fan1:           0 RPM

acpitz-virtual-0
Adapter: Virtual device
temp1:        +54.0°C  (crit = +200.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +54.0°C  (high = +84.0°C, crit = +100.0°C)
Core 0:        +52.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:        +50.0°C  (high = +84.0°C, crit = +100.0°C)

```

So, to me, this looks pretty OK. Again, here is the syslog. But last events logged are almost 1 minute before the freeze. So I am pretty convinced now it won't help much:
```
Jun 27 14:01:34 thinkpad-t440p dbus-daemon[998]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.186' (uid=1000 pid=2306 comm="/usr/bin/nautilus --gapplication-service " label="unconfined")
Jun 27 14:01:34 thinkpad-t440p systemd[1]: Starting Hostname Service...
Jun 27 14:01:34 thinkpad-t440p dbus-daemon[998]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jun 27 14:01:34 thinkpad-t440p systemd[1]: Started Hostname Service.
Jun 27 14:01:35 thinkpad-t440p gnome-shell[1826]: Object .Gjs_AppIndicatorIconActor__1 (0x55698b7b2c50), has been already finalized. Impossible to set any property to it.
Jun 27 14:01:35 thinkpad-t440p org.gnome.Shell.desktop[1826]: == Stack trace for context 0x556988f0e320 ==
Jun 27 14:01:35 thinkpad-t440p org.gnome.Shell.desktop[1826]: #0 0x7fff89987fe0 I   resource:///org/gnome/gjs/modules/_legacy.js:83 (0x7f8d542b5de0 @ 87)
Jun 27 14:01:35 thinkpad-t440p org.gnome.Shell.desktop[1826]: #1 0x5569893a04f0 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/indicatorStatusIcon.js:93 (0x7f8d2072f918 @ 58)
Jun 27 14:01:35 thinkpad-t440p org.gnome.Shell.desktop[1826]: #2 0x7fff89988bc0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f8d542b5de0 @ 71)
Jun 27 14:01:35 thinkpad-t440p org.gnome.Shell.desktop[1826]: #3 0x7fff89988c80 b   self-hosted:915 (0x7f8d542f12b8 @ 367)
Jun 27 14:01:35 thinkpad-t440p org.gnome.Shell.desktop[1826]: #4 0x7fff89988d70 b   resource:///org/gnome/gjs/modules/signals.js:128 (0x7f8d542d3230 @ 386)
Jun 27 14:01:35 thinkpad-t440p org.gnome.Shell.desktop[1826]: #5 0x5569893a0468 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/appIndicator.js:190 (0x7f8d207235e8 @ 22)
Jun 27 14:01:35 thinkpad-t440p org.gnome.Shell.desktop[1826]: #6 0x7fff899899c0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f8d542b5de0 @ 71)
Jun 27 14:01:35 thinkpad-t440p org.gnome.Shell.desktop[1826]: #7 0x5569893a03c0 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/statusNotifierWatcher.js:176 (0x7f8d2071f890 @ 26)
Jun 27 14:01:35 thinkpad-t440p org.gnome.Shell.desktop[1826]: #8 0x7fff8998a5a0 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f8d542b5de0 @ 71)
Jun 27 14:01:35 thinkpad-t440p org.gnome.Shell.desktop[1826]: #9 0x5569893a0320 i   /usr/share/gnome-shell/extensions/ubuntu-appindicators@ubuntu.com/statusNotifierWatcher.js:170 (0x7f8d2071f808 @ 68)
Jun 27 14:01:35 thinkpad-t440p org.gnome.Shell.desktop[1826]: #10 0x7fff8998b190 I   resource:///org/gnome/gjs/modules/_legacy.js:82 (0x7f8d542b5de0 @ 71)
Jun 27 14:01:35 thinkpad-t440p org.gnome.Shell.desktop[1826]: #11 0x7fff8998b950 b   self-hosted:917 (0x7f8d542f12b8 @ 394)
Jun 27 14:01:42 thinkpad-t440p nautilus[2306]: Called "net usershare info" but it failed: Failed to execute child process &#8220;net&#8221; (No such file or directory)
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00
```

Are there any other test I could run on the hardware beyond HD smart test and Memtest?

Edit: Sorry guy! Almost forgot to google first with you being so helpfull. I just installed phoronix (recommended here: [https://askubuntu.com/questions/389084/system-testing-tool-for-ubuntu](https://askubuntu.com/questions/389084/system-testing-tool-for-ubuntu)).

```
https://askubuntu.com/questions/389084/system-testing-tool-for-ubuntu
```

Going to post the results, but still open for other suggestions

---


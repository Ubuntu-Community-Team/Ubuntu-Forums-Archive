---
title: "Ubuntu freezes at random (?) times"
date: 2013-05-19
forum: General Help
---

### Post by tonqua on 2013-05-19
Hi,
I have experienced this problem for the past two weeks.
I was using ubuntu 11.10. As far as I can recall, I hadn't done any updates or changed anything before the computer started freezing at random moments.
The screen freezes and the sounds goes into a loop.
I updated to 12.10 hoping it might go away but it's still stopping at seamingly random intervals.
Sometimes it doesn't even go through to loading ubuntu before freezing on a blank screen.
It makes the computer almost unusable and drives me crazy when it doesn't start.
Please, any help with where to go from here?
Thank you.

---

### Post by pqwoerituytrueiwoq on 2013-05-19
hardware info [FONT=courier new]lspci[/FONT]
also post the output of this
[FONT=courier new]sudo smartctl --all /dev/sda[/FONT]

---

### Post by tonqua on 2013-05-19
```
lspci
```

> 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 Display controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z68 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF110 [GeForce GTX 570 HD] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF110 High Definition Audio Controller (rev a1)
03:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
05:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 30)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller (rev 10)

```
[FONT=courier new]sudo smartctl --all /dev/sda[/FONT]
```

> sudo: smartctl: command not found

---

### Post by tonqua on 2013-05-19
After installing smartmontools

> smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-30-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue Serial ATA
Device Model:     WDC WD3200AAKX-083CA1
Serial Number:    WD-WCAYUEF47692
LU WWN Device Id: 5 0014ee 10477ab7b
Firmware Version: 19.01H19
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun May 19 16:02:40 2013 ART
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
data collection:         ( 6360) seconds.
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
recommended polling time:      (  66) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x3037)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   136   134   021    Pre-fail  Always       -       4191
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       498
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       4570
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       496
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       62
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       435
194 Temperature_Celsius     0x0022   111   096   000    Old_age   Always       -       32
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


---

### Post by pqwoerituytrueiwoq on 2013-05-19
are you using the nvidia driver for your Nvidia GTX 570
what are your temperatures?
these 2 commands will get your temps
[FONT=courier new]nvidia-smi -q -d temperature[/FONT]
[FONT=courier new]sensors[/FONT]
please use code tags for terminal output, it preserves spacing
which desktop environment are you using? (Unity/KDE/Gnome/XFCE/LXDE/Mate/Cinnamon)

---

### Post by tonqua on 2013-05-19
aah
I don't know if I'm using the nvidia drivers or if they are working properly
how can I check?

```
[FONT=courier new]nvidia-smi -q -d temperature

[/FONT]==============NVSMI LOG==============

Timestamp                       : Sun May 19 19:30:54 2013
Driver Version                  : 304.88

Attached GPUs                   : 1
GPU 0000:01:00.0
    Temperature
        Gpu                     : 56 C

 sensors

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +37.0°C  (high = +80.0°C, crit = +98.0°C)
Core 0:         +33.0°C  (high = +80.0°C, crit = +98.0°C)
Core 1:         +36.0°C  (high = +80.0°C, crit = +98.0°C)
Core 2:         +36.0°C  (high = +80.0°C, crit = +98.0°C)
Core 3:         +36.0°C  (high = +80.0°C, crit = +98.0°C)


```

---

### Post by tonqua on 2013-05-19
I'm using the default ubuntu environment, that would be ... Unity (?)
Sorry I'm a pretty basic user.

---

### Post by tonqua on 2013-05-19
in software sources > aditional drivers > using NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-current (proprietary, tested)
is checked

should I try another option?

---

### Post by tonqua on 2013-05-19
I just opened a video to see if the graphics card would heat up and it froze within 10 seconds.

---

### Post by pqwoerituytrueiwoq on 2013-05-19
if nvidia-smi works your nvidia driver is working
if you are not gaming, you must be using unity to have temps that high on your gpu, unless it is full of dust bunnies
i would compare it to my gtx 550 ti but the gtx 570 pulls a bit more power
i find compiz to be too buggy for my taste with nvidia (nouveau actually seems better with compiz)
you may want to try another de, i use [xubuntu]("apt:xubuntu-desktop")
> **tonqua said:**
> I just opened a video to see if the graphics card would heat up and it froze within 10 seconds.
if you are dual booting run the [heaven benchmark]("http://unigine.com/products/heaven/download/") on windows and see if it freezes up, it it does you need to get rid of dust bunnies or replace your power supply (maybe both)
i assume you are dual booting based on your hardware you are probably a gamer

---

### Post by tonqua on 2013-05-19
I don't have dual boot, only ubuntu.
I use it for digital painting, compositing and occasional 3d work.
When the problem first occurred I opened the case just to make sure and it's pretty clean inside.
It used to run fine with heavy duty gpu work in 35ºC ambient temperature but now it gives up just thinking about video.
It's great that we could isolate what seems to be the problem.
I have a very basic knowledge (nonexistent?) of ubuntu's inner workings and I'm scared to break everything.
Could I uninstall the nvidia drivers an reinstall them? How would I go about it?

---

### Post by pqwoerituytrueiwoq on 2013-05-19
an upgrade is more likely to fix it than reinstalling it, i would guess you have a custom built system
you are using the 304 driver, there are the 313 driver and the 319 driver versions available
if you like unity you may want to upgrade to 13.04, otherwise i suggest trying xubuntu (especially if you need more gpu performance)
for xubuntu 12.10 i suggest using this ppa to fix a few bugs [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12)

---

### Post by tonqua on 2013-05-19
:(
I tried to uninstall all nvidia drivers then reinstall them fresh but it wont load.
Now when I restart it says it fails to load preset resolutions and defaults to something like 640*480
And it still freezes!
I'll make a fresh install of 13.04 tomorrow at work.
I think the next step might be to check and change the power supply (already? after a year?).
:(
I'll read more about xubuntu
thank you for the help,
I'll post more when i get some news.

---

### Post by pqwoerituytrueiwoq on 2013-05-20
you have to remove [FONT=courier new]/etc/X11/xorg.conf[/FONT] after removing nvidia/amd/ati drivers
What is the model on the PSU you are using? you should use a decent brand like seasonic, you probably should look at a 550W unit, assuming you you are suing a 1155 socket i5 cpu

---

### Post by tonqua on 2013-05-27
Well we did a complete format and install from 0 and everything is working fine again with 12.10. 13.04 wouldn't accept the nvidia drivers so we reverted to the previous release.
I gues "something" had happened to the graphic card's drivers but I'm too much of a newbie to understand exactly what.
Thank you for the help and this one will remain a mystery.

---

### Post by tgalati4 on 2013-05-27
If it freezes again, check the heat paste on your video card.  If the card is a few years old, it's possible that the heat paste has dried out causing the video card to overhead and stop thus locking up the pci bus and causing your computer to freeze in strange ways.

---


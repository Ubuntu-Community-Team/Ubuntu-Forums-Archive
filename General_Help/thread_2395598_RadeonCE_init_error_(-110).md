---
title: "RadeonCE init error (-110)"
date: 2018-07-04
forum: General Help
---

### Post by dshah on 2018-07-04
I did a recent update and now I have lost the wallpaper, all of icons and I am in login loop, I am using ubuntu 14.04.5 withxubuntu-desktop , when I entered tty1 ( CTRL+ALT+F1) I received an error : [COLOR=#000000]radeon 0000:01:00.0: VCE init error (-110)[/COLOR]
here unix -G
```
[COLOR=#000000][FONT=Verdana][1;34mGraphics: [0;37m [1;34mCard-1:[0;37m Intel 4th Gen Core Processor Integrated Graphics Controller 
[1;34m          [0;37m [1;34mCard-2:[0;37m Advanced Micro Devices [AMD/ATI] Mars XTX [Radeon HD 8790M] 
[1;34m          [0;37m [1;34mX.org:[0;37m 1.18.3 [1;34mdrivers:[0;37m ati,radeon,intel (unloaded: fbdev,vesa) [1;34mtty size:[0;37m 240x67 [1;34mAdvanced Data:[0;37m N/A out of X
[0m
[/FONT][/COLOR]

```here lspci
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d4)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d4)
00:1c.6 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #7 (rev d4)
00:1c.7 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #8 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM87 Express LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mars XTX [Radeon HD 8790M] (rev ff)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
0e:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)
```
Here is my /var/log/syslog[COLOR=#000000]
[/COLOR]```
http://paste.ubuntu.com/p/z4kVm7srHm/
```

I was using kubuntu desktop so tried with xfce desktop but still same issues.

---

### Post by dshah on 2018-07-05
Bump

---

### Post by dshah on 2018-07-17
I did a do-relase-upgrad from 14.04 > 16 and I was able to see all the images, icons etc...But was having login loop, I updated chown user:user .Xauthority and I am now able to login. But the error RadeonCE init error (-110) is still there.

---


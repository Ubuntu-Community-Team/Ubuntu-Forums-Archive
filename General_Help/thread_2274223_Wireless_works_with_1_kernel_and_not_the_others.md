---
title: "Wireless works with 1 kernel and not the others"
date: 2015-04-18
forum: General Help
---

### Post by Dragonbite on 2015-04-18
I just did an installation of Lubuntu 14.10  on my Gateway Netbook LT3101 and have discovered a curious situation.  The wireless worked when I was running from a LiveUSB.  After I installed it the wireless would not work EXCEPT with the oldest kernel available  In my installation I have 8 kernels
[LIST]
[*]**3.16.0-23-generic**  <-- this version works
[*]3.16.0-34-generic
[*]3.16.6-2-desktop
[*]3.16.7-7-desktop
[*]3.19.0-10-generic
[*]3.19.0- 13-generic  <-- this version does NOT work
[/LIST]

I have re-installed it a couple of time and ran the repair option during bootup for a couple of kernels.  This doesn't change anything.

Some of my system information:
```
drew@Umberhulk:~$ sudo uname -a
Linux Umberhulk **3.16.0-23-generic** #31-Ubuntu SMP Tue Oct 21 17:56:17 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
drew@Umberhulk:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 Non-Raid-5 SATA
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI0)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI1)
00:13.3 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB (OHCI3)
00:13.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB600 USB Controller (EHCI)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB600 IDE
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB600 PCI to LPC Bridge
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS690M [Radeon Xpress 1200/1250/1270]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 **Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)**

```

Previously I had full-blown Ubuntu installed and did not have any problems with the wireless during the installation or updates or any other situation.

I figure I cannot just keep using the old kernel all of the time, but am worried that my wireless is not supported with the latest kernel though that does not make sense with it not having any trouble in Ubuntu.

---

### Post by Dragonbite on 2015-04-20
The kernels outside of the oldest (3.16.0-23) fail, so it isn't a case of 3.16 vs 3.19 or the drivers are not present.  The driver seems to not be running with all but one kernel.

I don't see anywhere that the Atheros AR9285 is not compatible with any kernels.

How can I make sure the driver IS being used with all of the kernels or that it loads the drivers regardless of the kernel?

---


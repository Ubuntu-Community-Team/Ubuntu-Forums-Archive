---
title: "Acer Aspire 3100 Wifi Issue???"
date: 2007-02-01
forum: General Help
---

### Post by Mike_N on 2007-02-01
So my Wifi worked fine when I was using Dapper but... My wireless adapter can't seem to be found by Edgy, Mint Linux or even Suse 10.2

Can someone please explain to me why the current Distros can't get Wifi working where as the older ones could?

Thanks a lot, Mike

---

### Post by gramnemo on 2007-02-03
[CENTER]_Help to adjust Wi Fi en Acer 3000 I has put drivers but does not work! Tell as correctly to adjust . _           here results  ----    (  nautilus@ACER-NAUTILUS:~$ lspci 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03) 
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202 
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25) 
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller 
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] 
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) 
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0) 
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) 
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) 
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller 
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91) 
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02) 
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter 
nautilus@ACER-NAUTILUS:~$ )  nautilus@ACER-NAUTILUS:~$ ndiswrapper -i bcmwl5.inf 
Installing bcmwl5 
 nautilus@ACER-NAUTILUS:~$ lspci -n 
00:00.0 0600: 1039:0760 (rev 03)
00:01.0 0604: 1039:0002
00:02.0 0601: 1039:0963 (rev 25)
00:02.1 0c05: 1039:0016
00:02.5 0101: 1039:5513
00:02.6 0703: 1039:7013 (rev a0)
00:02.7 0401: 1039:7012 (rev a0)
00:03.0 0c03: 1039:7001 (rev 0f)
00:03.1 0c03: 1039:7001 (rev 0f)
00:03.2 0c03: 1039:7002
00:04.0 0200: 1039:0900 (rev 91)
00:06.0 0607: 104c:ac50 (rev 02)
00:0b.0 0280: 14e4:4318 (rev 02)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:00.0 0300: 1039:6330
nautilus@ACER-NAUTILUS:~$  )                (lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr off   Fragment thr off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nautilus@ACER-NAUTILUS:~$ 


  [/CENTER]

---


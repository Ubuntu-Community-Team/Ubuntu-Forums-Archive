---
title: "System Freezes"
date: 2007-01-30
forum: General Help
---

### Post by Ashton K. on 2007-01-30
I'm using a freshly installed copied of Edgy, completely updated, and the system keeps crashing.

I believe it is linked to my Atheros based wifi card, which fails at random intervals. If I attempt to restart my wireless (though System -> Administration -> Networking), my entire computer freezes completely. Won't respond to Ctl + Alt + Backspace, the whole nine yards.

Here's the output of lspci: 
```
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:0d.0 Ethernet controller: ALi Corporation M5263 Ethernet Controller (rev 40)
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0e.1 Mass storage controller: ALi Corporation ULi 5289 SATA (rev 10)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:05.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
02:07.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```


By the nature of the problem, I haven't been able to catch a dmesg about the problem, although I'll try and catch it between the wireless failure, and the computer crash next time. Tell me if there are any other logs you need to get a look into the problem.

I looked into putting a bug report up, but there are a few similar bugs out there, I'm not sure if their bugs are different, or if they don't try to restart the wireless card at the first sign of failure, hence their lack of crashing.

---

### Post by Syr0 on 2007-02-05
I have exactly the same problem! Help!

EDIT:

[This]("http://madwifi.org/wiki/UserDocs/MiniPCI") looks tasty.

---


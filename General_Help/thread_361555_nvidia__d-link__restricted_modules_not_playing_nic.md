---
title: "nvidia / d-link / restricted modules not playing nice."
date: 2007-02-14
forum: General Help
---

### Post by OldGaf on 2007-02-14
Hey all.

I am building a mythtv box and am using the latest graphics card drivers from nvidia as I get better performance from them. The problem is that I want to use a D-Link DWL-G510 wireless card. In order to get Edgy to recognize the card I need to install  the restricted modules (386). When I do this it breaks my X. When I reinstall the nvidia drivers my wireless goes away. The only fix I have found is to revert back to the nvidia drivers in the edgy repo's. There must be some way to have both......? 

uname -a
2.6.17-10-386

lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation Unknown device 0370 (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 0376 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0374 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0374 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0378 (rev a2)
00:0e.0 PCI bridge: nVidia Corporation Unknown device 0375 (rev a2)
00:0f.0 PCI bridge: nVidia Corporation Unknown device 0377 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
01:07.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
01:08.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
07:00.0 VGA compatible controller: nVidia Corporation Unknown device 01df (rev a1)

---


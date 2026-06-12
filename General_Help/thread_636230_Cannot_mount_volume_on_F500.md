---
title: "Cannot mount volume on F500"
date: 2007-12-09
forum: General Help
---

### Post by shanerdaner on 2007-12-09
Greetings everyone!!
I love Ubuntu!  The only problem i am having on just one of my three machines is in fact on my Presario F500 I cannot mount anything automatically I get it on everything I try to plug into my USB ports my 120 GB WD drive and my Card reader with a 4gb sd card neither will mount on this laptop.  It is the only one I am having this problem with.  Any suggestions or fixes? ...I deleted the 120 and made it FAT32 so I can use it between my windows machine and my 3 Ubuntu's..I think it is a pc problem because my other 2 HP's work fine 1 LT I use for work and my desktop in my office.  I know you Ubuntu guru's can help me!!  I am resorting to drinking wine ...lol won't fix much but it sure is FUN!!  I love Ubuntu btw and I am a lifer i use it for everything except syncing my treo....but that will be soon I feel!

thanks!
Shane

---

### Post by shanerdaner on 2007-12-09
> **shanerdaner said:**
> Greetings everyone!!
I love Ubuntu!  The only problem i am having on just one of my three machines is in fact on my Presario F500 I cannot mount anything automatically I get it on everything I try to plug into my USB ports my 120 GB WD drive and my Card reader with a 4gb sd card neither will mount on this laptop.  It is the only one I am having this problem with.  Any suggestions or fixes? ...I deleted the 120 and made it FAT32 so I can use it between my windows machine and my 3 Ubuntu's..I think it is a pc problem because my other 2 HP's work fine 1 LT I use for work and my desktop in my office.  I know you Ubuntu guru's can help me!!  I am resorting to drinking wine ...lol won't fix much but it sure is FUN!!  I love Ubuntu btw and I am a lifer i use it for everything except syncing my treo....but that will be soon I feel!

thanks!
Shane

 lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---


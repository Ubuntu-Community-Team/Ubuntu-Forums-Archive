---
title: "My netbook hanged during LibreOffice Impress"
date: 2016-06-23
forum: General Help
---

### Post by theforce2 on 2016-06-23
To whom it may concern,

I have downgraded my netbook 1015E, specs


[LIST]
[*]ProcessorIntel®  Celeron® Dual-Core  847  GHz Processor 
[*]Operating SystemWindows 8 
Ubuntu 
[*]ChipsetIntel® Chief River Chipset HM70 
[*]MemoryDDR3 1600(O.C.) MHz SDRAM, OnBoard Memory 2 GB / 4 GB 
[*]Display10.1" 16:9 HD (1366x768) LED Backlight anti-glare 
[*]GraphicIntegrated Intel® HD Graphics 
[*]Storage7mm SATA
320GB  5400  
500GB  5400 
[*]Card Reader2 -in-1 card reader ( SD/ SDHC/ SDXC/ MMC) 
[*]CameraHD 720p camera (Front); 5MP (Back) 
[*]NetworkingIntegrated 802.11 b/g/n or 802.11 a/b/g/n (Optional)
10/100 Base T 
[*]Interface1 x COMBO audio jack 
1 x Microphone-in/Headphone-out jack 
1 x VGA port/Mini D-sub 15-pin for external monitor
1 x USB 3.0 port(s) 
2 x USB 2.0 port(s)
1 x RJ45 LAN Jack for LAN insert 
1 x HDMI 
[*]AudioBuilt-in Speakers And Digital Array Microphone
ASUS SonicMaster Lite Technology 
[*]Battery3Cells 2.6 mAh
6Cells 2.6 mAh

I am running 32-bit i386 lubuntu 16.04 and it crashed while editing a power point presentation and simply typing into the power point slide. I do not know why it did that, I have never seen a Linux machine hang like that. It lasted about a while minute and a half. I know some linux but not enough to diagnose a hang and fix it.Can someone please guide me into how I could go about this?

I have not made any changes except changing the swap from 60 to 10 which has improved performance. I have programmed LibreOffice to use Graphics Cache as 400MB and memory per object as 21.0MB and 100 objects have cache. 2GB, my laptop has. It was fine yesterday doing the same task.

Should I lower the LibreOffice memory cap? 
[/LIST]

---

### Post by TheFu on 2016-06-24
Don't know if this will help, but I've found that on limited RAM systems, like a 2G netbook, that a 4G swap partition is needed to prevent lockups/crashes.
**free -mh** will let you know how and what memory is being used.

---


---
title: "Dell Latitude D610"
date: 2017-01-16
forum: General Help
---

### Post by jetman350 on 2017-01-16
What is the best Lubuntu for this nice little pc?  

I tried 16.04 in hopes that it would work, and it did, except for one thing...well maybe two.  While using AbiWord, there was a lot of Graphics problems in the Upper part of the document, like Screen Tearing or something, don't know how to describe it, can this be Fixed?

Also, the Wireless worked pretty well, but Dropped off a few times.  Is this common during a Test Session, and will be better during a full Install?

I did not get lshw while there, but I did get a inxi while I was in Linux Mint 17, I'll post it here for the Hardware.  If it is  better, I'll run a lshw while in Lubuntu 14.04.4 or 16.04.1. 

 I also tried to Test Lubuntu 14.04.4, but had an issue with not being able to play video in youtube, and that is what I was wanting to test out.  Wanted to see how the little guy would run using youtube.  The reason being, while using youtube in Linux Mint Mate this little guy is running the fan pretty strong, non stop, and getting pretty warm, not too warm, but a little too much for comfort, only about 60c Max, but felt like it was very unhappy.  Those Temps may not be accurate either I don't know, they are being read with lm-sensors I think, via psensor.  The Thermal Fins are all clean, but have not done the Thermal Paste.  I was hoping Lubuntu on there would run a little better.


```
mint@mint~ $ inxi -FzSystem:   Host: mint Kernel: 3.13.0-24-generic i686 (32 bit) Desktop: N/ADistro: Linux Mint 17 Qiana
Machine:  System: Dell product: Latitude D610
          Mobo: Dell model: 0D4571 Bios: Dell version: A06 date:10/02/2005
CPU:      Single core Intel Pentium M (-UP-) cache: 2048 KB flags: (nxsse sse2) clocked at 800.00 MHz 
Graphics: Card: Intel Mobile 915GM/GMS/910GML Express Graphics Controller 
          X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution:1024x768@60.0hz 
          GLX Renderer: Mesa DRI Intel 915GM x86/MMX/SSE2 GLX Version:1.4 Mesa 10.1.0
Audio:    Card: Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 AudioController driver: snd_intel8x0
          Sound: Advanced Linux Sound Architecture ver:k3.13.0-24-generic
Network:  Card-1: Broadcom NetXtreme BCM5751 Gigabit Ethernet PCI Expressdriver: tg3 
          IF: eth0 state: down mac: <filter>
          Card-2: Intel PRO/Wireless 2200BG [Calexico2] NetworkConnection driver: ipw2200 
          IF: eth1 state: dormant mac: <filter>
Drives:   HDD Total Size: 92.1GB (2.1% used) 1: id: /dev/sda model:Hitachi_HTS72106 size: 60.0GB 
          2: USB id: /dev/sdb model: USB_Flash_Drive size: 16.0GB 3: USBid: /dev/sdc model: USB_2.0_FD size: 16.1GB 
Partition:ID: / size: 497M used: 54M (11%) fs: overlayfs 
RAID:     No RAID devices detected - /proc/mdstat and md_mod kernel raidmodule present
Sensors:  None detected - is lm-sensors installed and configured?
Info:     Processes: 136 Uptime: 5 min Memory: 214.9/993.8MB Client: Shellinxi: 1.8.4 
mint@mint~ $  
```

---

### Post by vasa1 on 2017-01-16
> **jetman350 said:**
> What is the best Lubuntu for this nice little pc?  I tried 16.04 in hopes that it would work, and it did, except for one thing...well maybe two.  While using AbiWord, there was a lot of Graphics problems in the Upper part of the document.  Like Screen Tearing or something, don't know how to describe it.  I did not get lshw while there, but did while I was in Linux Mint 17, I'll post it here for the Hardware.  I also tried Lubuntu 14.04.4, but had an issue with not being able to play video in youtube, and that is what I was wanting to test out.  Wanted to see how the little guy would run using youtube.  The reason being, while using youtube in Linux Mint Mate this little guy is running the fan pretty strong, and getting pretty warm, not too warm, but a little too much for comfort, only about 60c Max, but felt like it was unhappy.  The Thermal Fins are all clean, so I guess this is to be expected, but I figure with Lubuntu on there would run even better.

Is there any way to rectify the Screen Tearing, or a way to do some testing with youtube while in 14.04.4?  I have a nice install of Linux Mint on there now so no need for me to jump to another install if not warranted.  I think right now it has Mint Mate 17.2 on it? maybe .3 I forget.
...

Could you please make the operating system you want help with clear? Despite claims, not all that's true for Mint holds for official Ubuntu flavors.

It's also more convenient if there's just one support question per thread.

---

### Post by mörgæs on 2017-01-17
> **jetman350 said:**
> While using AbiWord, there was a lot of Graphics problems in the Upper part of the document.  Like Screen Tearing or something, don't know how to describe it.

This is a well-known problem. If you click the old hardware link in my signature and search for 'flicker' you will see a solution.

---

### Post by vasa1 on 2017-01-17
> **mörgæs said:**
> This is a well-known problem. If you click the old hardware link in my signature and search for 'flicker' you will see a solution.
Hi, in that link, you recommend Crux as the widget theme. In 16.04, if not earlier, abiword is a gtk3 app and the Crux theme is gtk2 only. Please see [https://ubuntuforums.org/showthread.php?t=2321942&p=13514431#post13514431](https://ubuntuforums.org/showthread.php?t=2321942&p=13514431#post13514431) and the rest of that thread.

---

### Post by mörgæs on 2017-01-17
Interesting, thanks. I'll take a closer look when I get back to my Lubuntu computer.

---

### Post by wildmanne39 on 2017-01-17
*Thread moved to **General Help**.*

Please edit your question so there is only the main question in this thread.
Thanks

---


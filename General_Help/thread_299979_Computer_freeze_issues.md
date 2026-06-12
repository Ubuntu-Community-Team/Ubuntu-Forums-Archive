---
title: "Computer freeze issues"
date: 2006-11-15
forum: General Help
---

### Post by montgoja on 2006-11-15
Hello,
I have just recently installed edgy eft and it's running relatively well, however, both my roomate and I are experiencing a strange hangup in our computers when they go idle.  I have sat down to my computer and found a section of screensaver frozen on the screen or even just a total black screen.  I think that the computer is going to some form of sleep, but nothing I have tried to do to get it out of sleep has worked.  I looked in System --> Preferences --> Power Management, and it is set to never put display to sleep or computer to sleep, yet I am still experiencing this problem.  When this happens, my only option is to push my reset button and reboot entirely.  Has anyone else had this issue?  What can I do to fix it?

Thanks!

---

### Post by Josip Lazic on 2006-12-12
I have same problem. I can connect over ssh to computer, I can even kill X (/etc/init.d/gdm restart), but nothing can wake up monitor. Caps/Num/Scroll Lock on keyboard does not react if I press them, and only soulution is to prest reset button :(

Graphic card is ATi Radeon 9200 (Driver "ati", in xorg.conf), P4 + Asus mbo with SiS645 chipset.

---

### Post by zigot on 2006-12-13
same thing here ](*,)

---

### Post by LAI on 2007-01-20
This sounds very much like what I've been experiencing. Occasionally, after my computer has been left alone for a while, it won't wake up from a blank screen. I've turned off suspend/hibernate, but that doesn't help. I thought it happened after quite a long period of inactivity (8 hours or so) but today I got home, it was working fine, left it alone for an hour or so, and it was frozen (blank screen, nonresponsive to capslock, had to hard boot).

I'm pretty sure I remember not being able to ssh into it, but I'll check next time this happens. If you can, you should be able to execute `reboot` or `shutdown -r now`.

I've tried changing my wireless driver from bcm43xx to driverloader, and that hasn't seemed to help. I've tried installing and changing stuff in both the kde and gnome power applets, but to no effect. Here's my lspci:

```

LAI@boreas:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
```

---

### Post by Nozem on 2007-01-20
I had the same thing happening to me and have been wondering what could cause these freeze-ups. I was thinking it might have something to do with my wireless connection or videodriver / beryl-setup. Sometimes crashes also occurred once i started a torrent or during writes to a FAT32-disk. It all seemed a bit obscure really.

However: recently I fiddled around with my videodriver configuration and allowed the non-generic kernel of Ubuntu to be installed. Since booting to this version I haven't experienced a single crash yet. (But to be honest it's only been a week since I did that). Could the alternative kernel be more stable somehow?

---

### Post by [Phaedrus] on 2007-03-27
I had the same issue. Disabled the screensaver and it seems to be doing okay. You can try that option.

---

### Post by montgoja on 2007-03-27
Yeah, actually that's what I discovered as well, just forgot to post on here.  haha.  I don't know which screensaver it is in particular that causes the computer to freeze, but I set my computer to use only one screensaver (the Matrix one that flashes the pictures of the characters through the matrix stream) and it hasn't frozen since.  Could be an interesting experiment for someone who has a lot of spare time to see which one of the screensavers is doing this...  :-\"

---


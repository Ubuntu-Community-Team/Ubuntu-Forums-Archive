---
title: "Screen Resolution"
date: 2016-05-16
forum: General Help
---

### Post by Andr_Cardoso on 2016-05-16
Hello. i recently installed lubuntu on my acer aspire 3633wlmi and i&#7743; pretty satisfied. it runs real good on my laptop. but i have a problem that i still couldnt fix. its about screen resolution. its in 640-480 and it seems that its the only resolution available. i had windows xp before and the resolution was ok, how it is suppost to be. i dont know if lubuntu doesnt recognize my screen or its drivers problem. 

please help me. im very satisfied on how the system works no the pc but this problem is killing me. help please. thanks in advanced.

---

### Post by oldrocker99 on 2016-05-16
Please post the result of ```
lspci
```

That will give some idea of your hardware.

---

### Post by Andr_Cardoso on 2016-05-16
ok. here it is:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] LPC Controller (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

---

### Post by howefield on 2016-05-16
Have you had a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2215422&highlight=SIS+661%2F741%2F760") ?

---

### Post by Andr_Cardoso on 2016-05-16
So, for what i understood, there s no solution... Can you confirm, please?

---

### Post by howefield on 2016-05-17
> **Andr_Cardoso said:**
> So, for what i understood, there s no solution... Can you confirm, please?

My understanding is that SiS graphics are extremely problematic, but keep giving your thread a daily bump and perhaps those with a proper answer will chime in.

---


---
title: "Frequent gutsy crashes"
date: 2008-03-01
forum: General Help
---

### Post by shabs on 2008-03-01
Hi all,
I finally got around installing gutsy on a vista machine a day ago. I've been fiddling around with it and it has crashed 5 times in the last 6 hours! Which kinda equals vista crashes in the last 4 months since i've had this laptop.
1 crash while using firefox (application hung up after trying to open a new tab)
1 crash when it just hung up and didnt respond to anything
2 crashes while playing around with the advanced desktop effects mainly cube settings
1 crash where it just shut down abdruptly without any warning.

ubuntu starting working on my hardware from the word go so i'm not sure if its a problem with the hardware. The cd i used was the ubuntu cd ordered online. Where do u think the problem lies?

---

### Post by jeffus_il on 2008-03-01
I would start eliminating things to see if the problem goes away, the first candidate should be the compiz fancy desktop effects. Use your machine without them and see if you still have problems, if this stops the crashing, return them one by one so that you can find the culprit.

---

### Post by shabs on 2008-03-01
I should have included more information about the hardware. This is the general information. 512 mb ram. 80 gb hdd (10gb partition for ubuntu + 500 mb swap partition). And this is the result of sudo lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

is this information helpful?
thanks

---

### Post by shabs on 2008-03-01
Hi Jeffus,
does this mean eliminating firefox too and trying to use a different browser?

---

### Post by jeffus_il on 2008-03-01
No, I would only get rid of the compiz effects for a start. Making too many changes at once will make it difficult to isolate the problem. Firefox is stable, and in my opinion, the desktop effects much less so.

---

### Post by shabs on 2008-03-01
thanks! 
so its bye-bye eye candy :D
/shabs

---


---
title: "Massive issue regarding laptop! Help!"
date: 2007-09-16
forum: General Help
---

### Post by FRuMMaGe on 2007-09-16
I was downloading on my laptop the other week and left it on overnight.  I opened the screen the next day to find lots of crazy squares all over the display and nothing to do but remove the battery and reboot.

I thought this was a one-off issue so I didn't worry about it.

However, now whenever I leave my laptop lid closed for a certain  amount of time (i'm not sure exactly how long) I come back and it has completely frozen!

This is particularly annoying because I use my laptop to connect to xbox-live and when it freezes it loses connection.

The odd thing is, this only happens when the lid is closed, never when I leave the lid open.

Please help me!  I have not changed anything recently so I have no idea why this issue has come about.  :(

---

### Post by atlfalcons866 on 2007-09-16
what is the video card on the laptop?

---

### Post by FRuMMaGe on 2007-09-16
It's an integrated Intel 945G and i'm using the i810 drivers.

Here's my lspci if you need it:
```
frummage@frummage-laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:06:04.0 FireWire (IEEE 1394): O2 Micro, Inc.: Unknown device 00f7 (rev 02)
0000:06:04.2 0805: O2 Micro, Inc.: Unknown device 7120 (rev 01)
0000:06:04.3 Mass storage controller: O2 Micro, Inc.: Unknown device 7130 (rev 01)
0000:06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by AndyCooll on 2007-09-16
Haven't got an answer to your screen issues, however as an aside have you tried the ALT+SysReq approach to rebooting?
[Fix a Frozen System with the Magic SysRq Keys]("http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/")

:cool:

---

### Post by FRuMMaGe on 2007-09-16
> **AndyCooll said:**
> Haven't got an answer to your screen issues, however as an aside have you tried the ALT+SysReq approach to rebooting?
[Fix a Frozen System with the Magic SysRq Keys]("http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/")

:cool:

This is interesting and I hadn't heard of this before.  I can see you are giving me good suggestions but obviously I would much preffer to not need to use this in the first place :)

---

### Post by FRuMMaGe on 2007-09-16
bump

---


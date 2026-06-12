---
title: "Screen Resolution Issue"
date: 2008-05-30
forum: General Help
---

### Post by CollisionInc on 2008-05-30
I have an Acer 19" Wide Monitor X193W

It defaults to a screen resolution of 1440x900

Every time i try and change the resolution the screen just runs from side to side and i am unable to set it back without rebooting the machine
When I run lspci I get the following:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:04.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:06.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:06.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:06.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)


Can anyone tell me how to install the correct display drivers or if you have any ideas/suggestions that might help in any way?

---

### Post by fsmithred on 2008-05-31
> **CollisionInc said:**
> 
Can anyone tell me how to install the correct display drivers or if you have any ideas/suggestions that might help in any way?

According to a post in this first link, you should file a bug report, and it looks like someone has done that for your monitor in the second link.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409)

[https://bugs.launchpad.net/ubuntu/+bug/230571](https://bugs.launchpad.net/ubuntu/+bug/230571)

---


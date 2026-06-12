---
title: "Fresh Install...Please HELP!"
date: 2008-05-08
forum: General Help
---

### Post by coldopm on 2008-05-08
I am running Vista and Hardy. Hardy is fresh install. Not one change made from the original LiveCD Distro. I have no idea how to setup my wireless network. It runs fine in Vista but Not in Hardy.

Can someone please help me setup Hardy to detect wireless networks, or add my network or whatever I need to do to get the network running in Hardy (wirelessly) so I can be rid of Vista for GOOD!?

---

### Post by FuturePilot on 2008-05-08
What wireless card do you have? Is anything showing up when you click on the network icon in the notification area by the clock?

Also have you tried clicking on the network icon and selecting Connect to Other Wireless Network?

---

### Post by coldopm on 2008-05-08
> **FuturePilot said:**
> What wireless card do you have? Is anything showing up when you click on the network icon in the notification area by the clock?

Also have you tried clicking on the network icon and selecting Connect to Other Wireless Network?


Well I can Hardwire connect. When I try to edit wireless I just get empty box.

Card is Dell Wireless 1395 WLAN Mini-card.

---

### Post by FuturePilot on 2008-05-08
Try selecting Connect to Other Wireless Network and fill in the appropriate information.

---

### Post by coldopm on 2008-05-08
> **FuturePilot said:**
> Try selecting Connect to Other Wireless Network and fill in the appropriate information.


Only options I get are the following:
Wired Network
Connect to 802.1X Protected Wired Network 
Manual Configuration

When I go to the manual configuration I get Wired Network, which works fine obviously, and Point to point connection. I do not get the option to connect to wireless or configure a wireless????

---

### Post by FuturePilot on 2008-05-08
Hmmm. Ok, that sounds like a missing driver. If you could post the output of
```
lspci
```so we can get the details on the wireless card.
I'm sorry I can't be of more help, this is starting to get out of my area of knowledge. :(

---

### Post by coldopm on 2008-05-08
> **FuturePilot said:**
> Hmmm. Ok, that sounds like a missing driver. If you could post the output of
```
lspci
```so we can get the details on the wireless card.
I'm sorry I can't be of more help, this is starting to get out of my area of knowledge. :(

Well here is the output. Anyone else that can assist feel free.

------

coldopm@coldopm-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
coldopm@coldopm-laptop:~$ 

-----------

Does this help at all?

---

### Post by jrusso2 on 2008-05-08
You have the broadcom 4310.  There are a lot of threads about this card.

[http://ubuntuforums.org/showthread.php?t=779754&highlight=BCM4310+USB](http://ubuntuforums.org/showthread.php?t=779754&highlight=BCM4310+USB)

Is a pretty recent one

---

### Post by MaindotC on 2008-05-08
Shoot I did a site search of the forums and I didn't find those.  WTF!

---

### Post by coldopm on 2008-05-08
> **jrusso2 said:**
> You have the broadcom 4310.  There are a lot of threads about this card.

[http://ubuntuforums.org/showthread.php?t=779754&highlight=BCM4310+USB](http://ubuntuforums.org/showthread.php?t=779754&highlight=BCM4310+USB)

Is a pretty recent one

I appriciate the help but those codes did not work. I mean it downloaded the driver but I get 

wlan0: ERROR while getting interface flags: No such device

Anyone else have any ideas?

---

### Post by coldopm on 2008-05-08
Closed this thread and moved it to a more suitable section.

[http://ubuntuforums.org/showthread.php?t=787507](http://ubuntuforums.org/showthread.php?t=787507)

---


---
title: "Cannot use wi-fi connection on Toshiba laptop"
date: 2015-03-28
forum: General Help
---

### Post by Alexander_Hardge on 2015-03-28
Hey all, I'm (relatively) new to using Ubuntu. I've used it without issue on my desktop with a dual-boot for around a year now but I've been leaning towards using Windows for media and gaming. However, my laptop, which I use for school, has had numerous problems with Windows 8.1, so I decided to finally switch it over to Ubuntu 14.04 after numerous attempts at repair both by myself and by Toshiba.

That said, I've only run into one roadblock, and it's that I can't seem to connect to any wireless networks. I suspect it may be an issue with drivers for the laptop's network card as Ubuntu immediately recognized the network card on my desktop when I first installed it. I've played around with the settings a bit but I'm stumped. I'm gonna need this wi-fi working next week when I resume classes so it's not immediately urgent, but it's necessary.

The laptop itself is a Toshiba Satellite C75D-B7260. Specs are as follows:

Quad-Core AMD A6-6310 APU (R4-6310 Graphics)
8GB RAM
750GB HDD
Ubuntu 14.04LTS

Thanks for the help, guys. Glad to be here.

---

### Post by Kaabi on 2015-03-29
Hey there, 

First of all it would be awesome if you could tell us your wifi card model.  To find this, open a terminal and run:
```
lspci | grep "Wireless"
```
and then post the ouptut.

---

### Post by Alexander_Hardge on 2015-03-29
I tried inputting that but it didn't output anything. Just inputting lscpi output a whole list from which I was able to pick out that it's a Broadcom BCM43142. I couldn't hunt down any drivers for it. Where do I go from there?

In case I got it wrong, here's the full output of lspci.

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD]Device 1566
00:01.0 VGA compatible controller: Advanced Micro Devices,Inc. [AMD/ATI] Mullins [Radeon APU A4-6000 with R2 Graphics]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI]Device 9840
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device156b
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family16h Processor Functions 5:1
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family16h Processor Functions 5:1
00:08.0 Encryption controller: Advanced Micro Devices, Inc.[AMD] Device 1537
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD]FCH USB XHCI Controller (rev 11)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD]FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD]FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD]FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBusController (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCHAzalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCHLPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD]Device 1580
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD]Device 1581
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD]Device 1582
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD]Device 1583
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD]Device 1584
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD]Device 1585
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
05:00.0 Network controller: Broadcom Corporation BCM43142802.11b/g/n (rev 01)

06:00.0 Unassigned class [ff00]: Realtek Semiconductor Co.,Ltd. RTS5229 PCI Express Card Reader (rev 01)
```


EDIT: Aaaah, nevermind. I downgraded to 12.04 and it's fine now. Thanks.

---


---
title: "Worrying dmesg on new box."
date: 2016-02-07
forum: General Help
---

### Post by Bucky Ball on 2016-02-07
Hi all. As per the title. This is the end of my dmesg after boot:

```
  3.552879] [B]NVRM: Your system is not currently configured to drive a VGA console
[    3.552881] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[    3.552882] NVRM: requires the use of a text-mode VGA console. Use of other console
[    3.552883] NVRM: drivers including, but not limited to, vesafb, may result in
[    3.552883] NVRM: corruption and stability problems, and is not supported.[/B]
[    3.607438] IPv6: ADDRCONF(NETDEV_UP): wlxe84e060dc5a4: link is not ready
[    3.608929] rtl8192cu: MAC auto ON okay!
[    3.619512] rtl8192cu: Tx queue select: 0x05
[    3.992188] IPv6: ADDRCONF(NETDEV_UP): wlxe84e060dc5a4: link is not ready
[    4.052758] IPv6: ADDRCONF(NETDEV_UP): wlxe84e060dc5a4: link is not ready
[    4.893428] wlxe84e060dc5a4: authenticate with 10:0d:7f:de:92:ba
[    4.908510] wlxe84e060dc5a4: direct probe to 10:0d:7f:de:92:ba (try 1/3)
[    5.110646] wlxe84e060dc5a4: send auth to 10:0d:7f:de:92:ba (try 2/3)
[    5.113231] wlxe84e060dc5a4: authenticated
[    5.114680] wlxe84e060dc5a4: associate with 10:0d:7f:de:92:ba (try 1/3)
[    5.139001] wlxe84e060dc5a4: RX AssocResp from 10:0d:7f:de:92:ba (capab=0x411 status=0 aid=4)
[    5.140234] wlxe84e060dc5a4: associated
[    5.140240] IPv6: ADDRCONF(NETDEV_CHANGE): wlxe84e060dc5a4: link becomes ready

```

Running Xubuntu-core 15.10, installed for about three days, and below are the specs of my new system which I've had running for about the same time.

ASUS Strix GTX 970 (attached to two DVI-D monitors currently and perhaps part of this issue, card using the 352.63 driver)
Gigabyte HD170-HD3
Intel i7 6700
16Gb Kingston Hyperfury-x (from memory, no joke intended)

Any other details you'd like just ask. Maybe this message is easily fixed but because I don't know what it means and how to remedy, worried. Hope someone has some ideas and in the meantime I'll be looking for some. 

Just to note: the machine appears to be running faultlessly (and the DVI-D monitors look better than ever), despite the ominous wording of this message, but now I'm waiting for the sky to fall in! :| :D

* Just noticed in the Nvidia Config Tool in Xvideo Settings that it is currently synced to display Acer X193HQ (DVI-I-1). Beneath that I can select Auto, the monitor it is already synced to, or the other monitor, identical, except it is (DVI-D-0).

---

### Post by kansasnoob on 2016-02-07
I've encountered some nvidia problems in Wily, Xenial, and 14.04.4 test installs:

[http://ubuntuforums.org/showthread.php?t=2311759](http://ubuntuforums.org/showthread.php?t=2311759)

Be sure to jump to comments 3 and 4 for more info.

Running the following command would show you which graphics driver is in use:

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

---

### Post by Bucky Ball on 2016-02-07
Thanks for the input. Well, the driver in use is the propriatary Nvidia 352.63, as stated in first post, installed using Additional Drivers, but maybe you are looking for some other info from that command so here's the output in case it gives some other clue:

```
01:00.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 8508
	Flags: bus master, fast devsel, latency 0, IRQ 130
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, prefetchable) [size=32M]
	I/O ports at e000 [size=128]
	[virtual] Expansion ROM at df000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [250] Latency Tolerance Reporting
	Capabilities: [258] L1 PM Substates
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Capabilities: [900] #19
	Kernel driver in use: nvidia
```

There is a more recent driver at the Nvidia site, but I have read in other places that installing that driver directly from their site can cause issues so haven't gone there. 

I have a heap of work I need to be doing on this machine, it's currently working fine so that's happening, despite this problem, so rather not install the wrong driver and spend half a day figuring out how to get back to work. I'm currently trying to figure this out between trying to fix a couple of other niggles (sudden wireless dropouts, intermittent dead keyboard) and study commitments. :)

---

### Post by matt_symes on 2016-02-07
Hi Bucky Ball

What happens if you switch to a console using the ALT +F1 keys ?

Kind regards

---

### Post by Bucky Ball on 2016-02-07
> **matt_symes said:**
> Hi Bucky Ball

What happens if you switch to a console using the ALT +F1 keys ?



Nothing. You mean contol+alt+F1? Get a console. ;)

---

### Post by matt_symes on 2016-02-07
Hi Bucky Ball

For a sanity check, try all the consoles from F1 to F6.

Do they also exhibit the same problem ?

I suspect they might.

I'm out the house now, on my phone, so i'll post back tonight.

EDIT:

Yep. Ctrl + alt + F1 :)

Kind regards

---

### Post by Bucky Ball on 2016-02-07
Thanks for that. Yep, I get a console fine using ctl+alt+F1 - F6, back home fine with F7. All as per normal there.

I have an odd problem going on with USB keyboards and wireless dongles also. I only mention it in case you might see some relationship to this. I'm going to post a thread about that in the morning if I haven't got it nutted out before bed from my own sifting.

---

### Post by matt_symes on 2016-02-07
Hi Bucky Ball

> **Bucky Ball said:**
> Thanks for that. Yep, I get a console fine using ctl+alt+F1 - F6, back home fine with F7. All as per normal there.

I have an odd problem going on with USB keyboards and wireless dongles also. I only mention it in case you might see some relationship to this. I'm going to post a thread about that in the morning if I haven't got it nutted out before bed from my own sifting.

Oh well. That's my initial thoughts on what the problem may be out the window then.

I can't think of any relation to the USB problems either.

Not sure what to suggest at the moment.

Kind regards

---


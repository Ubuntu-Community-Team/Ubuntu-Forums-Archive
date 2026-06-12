---
title: "No sound on rt286 driver P34W4 gigabyte laptop"
date: 2016-03-30
forum: General Help
---

### Post by Toast2120 on 2016-03-30
OK, so got a new P34W4 gigabyte laptop, yay. No sound, boo. I think I tracked down the launchpad issue here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1413446](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1413446)
It looks sort of like my issue, but I couldn't find anything exactly like me.

Using 15.10, unity desktop, nothing else is out of the ordinary

relevant output of lspci
```
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 0a)
```

output of lspci -vmmk
```
toast@pancake:~$ lspci -vmmk
Slot:	00:00.0
Class:	Host bridge
Vendor:	Intel Corporation
Device:	Broadwell-U Host Bridge - DMI
SVendor:	Gigabyte Technology Co., Ltd
SDevice:	Device a456
Rev:	0a

Slot:	00:01.0
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	Broadwell-U PCI Express x16 Controller
Rev:	0a
Driver:	pcieport

Slot:	00:02.0
Class:	VGA compatible controller
Vendor:	Intel Corporation
Device:	Broadwell-U Integrated Graphics
SVendor:	Gigabyte Technology Co., Ltd
SDevice:	Device a456
Rev:	0a
Driver:	i915

Slot:	00:03.0
Class:	Audio device
Vendor:	Intel Corporation
Device:	Broadwell-U Audio Controller
SVendor:	Gigabyte Technology Co., Ltd
SDevice:	Device a456
Rev:	0a
Driver:	snd_hda_intel

Slot:	00:14.0
Class:	USB controller
Vendor:	Intel Corporation
Device:	9 Series Chipset Family USB xHCI Controller
SVendor:	Gigabyte Technology Co., Ltd
SDevice:	Device a456
ProgIf:	30
Driver:	xhci_hcd

Slot:	00:16.0
Class:	Communication controller
Vendor:	Intel Corporation
Device:	9 Series Chipset Family ME Interface #1
SVendor:	Gigabyte Technology Co., Ltd
SDevice:	Device a456
Driver:	mei_me

Slot:	00:1a.0
Class:	USB controller
Vendor:	Intel Corporation
Device:	9 Series Chipset Family USB EHCI Controller #2
SVendor:	Gigabyte Technology Co., Ltd
SDevice:	Device a456
ProgIf:	20
Driver:	ehci-pci

Slot:	00:1b.0
Class:	Audio device
Vendor:	Intel Corporation
Device:	9 Series Chipset Family HD Audio Controller
SVendor:	Gigabyte Technology Co., Ltd
SDevice:	Device a456
Driver:	snd_hda_intel

Slot:	00:1c.0
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	9 Series Chipset Family PCI Express Root Port 1
Rev:	d0
Driver:	pcieport

Slot:	00:1c.1
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	9 Series Chipset Family PCI Express Root Port 2
Rev:	d0
Driver:	pcieport

Slot:	00:1c.2
Class:	PCI bridge
Vendor:	Intel Corporation
Device:	9 Series Chipset Family PCI Express Root Port 3
Rev:	d0
Driver:	pcieport

Slot:	00:1d.0
Class:	USB controller
Vendor:	Intel Corporation
Device:	9 Series Chipset Family USB EHCI Controller #1
SVendor:	Gigabyte Technology Co., Ltd
SDevice:	Device a456
ProgIf:	20
Driver:	ehci-pci

Slot:	00:1f.0
Class:	ISA bridge
Vendor:	Intel Corporation
Device:	9 Series Chipset Family HM97 LPC Controller
SVendor:	Gigabyte Technology Co., Ltd
SDevice:	Device a456
Driver:	lpc_ich

Slot:	00:1f.2
Class:	SATA controller
Vendor:	Intel Corporation
Device:	9 Series Chipset Family SATA Controller [AHCI Mode]
SVendor:	Gigabyte Technology Co., Ltd
SDevice:	Device a456
ProgIf:	01
Driver:	ahci

Slot:	00:1f.3
Class:	SMBus
Vendor:	Intel Corporation
Device:	9 Series Chipset Family SMBus Controller
SVendor:	Gigabyte Technology Co., Ltd
SDevice:	Device a456

Slot:	01:00.0
Class:	3D controller
Vendor:	NVIDIA Corporation
Device:	GM204M [GeForce GTX 970M]
SVendor:	Gigabyte Technology Co., Ltd
SDevice:	Device a456
Rev:	a1
Driver:	nouveau

Slot:	02:00.0
Class:	Unassigned class [ff00]
Vendor:	Realtek Semiconductor Co., Ltd.
Device:	RTS5227 PCI Express Card Reader
SVendor:	Realtek Semiconductor Co., Ltd.
SDevice:	RTS5227 PCI Express Card Reader
Ph*****:	0
Rev:	01
Driver:	rtsx_pci

Slot:	03:00.0
Class:	Ethernet controller
Vendor:	Realtek Semiconductor Co., Ltd.
Device:	RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
SVendor:	Gigabyte Technology Co., Ltd
SDevice:	Device a456
Rev:	10
Driver:	r8169

Slot:	04:00.0
Class:	Network controller
Vendor:	Intel Corporation
Device:	Wireless 7260
SVendor:	Intel Corporation
SDevice:	Dual Band Wireless-AC 7260
Rev:	bb
Driver:	iwlwifi

toast@pancake:~$ 

```

I have included the snd-soc-rt286 within /etc/modules and nothing changes after several reboots, so I'm not particularly sure where to go next.

---

### Post by Toast2120 on 2016-03-30
[solved] [https://bbs.archlinux.org/viewtopic.php?id=207284](https://bbs.archlinux.org/viewtopic.php?id=207284)

---


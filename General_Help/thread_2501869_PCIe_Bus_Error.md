---
title: "PCIe Bus Error"
date: 2024-10-23
forum: General Help
---

### Post by aachaoshand on 2024-10-23
A few threads seemed to indicate that an error like mine is due to power saving.  I just recently got an HP dock that goes with my HP Zbook Power 16.  I started noticing an entire slew of these error messages and at around the same time, it takes longer to shutdown and reboot.  Not sure if this is related or a coincidence.  

Basic troubleshooting, like disconnecting the dock and powering up does resolve the speed issue.  However, even at idle, I just did another dmesg -T and can see the error keeps repeating.  Another step I just took was disconnecting the HP dock and the error stopped repeating.  At this point, I can establish that something with the "**HP Thunderbolt Dock 120 G4**" is making it generate the errors.  Below is the exact error that repeats over and over in the dmesg.

```
[
Wed Oct 23 18:51:44 2024] pcieport 0000:67:04.0:   device [8086:0b26] error status/mask=00000080/00002000
[Wed Oct 23 18:51:44 2024] pcieport 0000:67:04.0:    [ 7] BadDLLP               
[Wed Oct 23 18:51:44 2024] pcieport 0000:00:04.1: AER: Correctable error message received from 0000:67:04.0
[Wed Oct 23 18:51:44 2024] pcieport 0000:67:04.0: PCIe Bus Error: severity=Correctable, type=Data Link Layer, (Receiver ID)
[Wed Oct 23 18:51:44 2024] pcieport 0000:67:04.0:   device [8086:0b26] error status/mask=00000080/00002000
[Wed Oct 23 18:51:44 2024] pcieport 0000:67:04.0:    [ 7] BadDLLP 

```

Here is the moment I disconnected the Dock USB-C connection to my ZBook 

```
Wed Oct 23 18:48:36 2024] usb 7-1.4.2.3: USB disconnect, device number 7
[Wed Oct 23 18:48:36 2024] usb 7-1.4.3: USB disconnect, device number 5
[Wed Oct 23 18:48:44 2024] audit: type=1107 audit(1729727324.813:229): pid=1300 uid=101 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.DBus.Properties" member="PropertiesChanged" name=":1.14" mask="receive" pid=5078 label="snap.thunderbird.thunderbird" peer_pid=1329 peer_label="unconfined"
                            exe="/usr/bin/dbus-daemon" sauid=101 hostname=? addr=? terminal=?'
[Wed Oct 23 18:49:01 2024] usb 7-1: new high-speed USB device number 8 using xhci_hcd
[Wed Oct 23 18:49:01 2024] thunderbolt 1-0:2.1: new retimer found, vendor=0x1da0 device=0x8833
[Wed Oct 23 18:49:01 2024] usb 7-1: New USB device found, idVendor=1d5c, idProduct=5801, bcdDevice= 1.01
[Wed Oct 23 18:49:01 2024] usb 7-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[Wed Oct 23 18:49:01 2024] usb 7-1: Product: USB2.0 Hub
[Wed Oct 23 18:49:01 2024] usb 7-1: Manufacturer: Fresco Logic, Inc.
[Wed Oct 23 18:49:02 2024] hub 7-1:1.0: USB hub found
[Wed Oct 23 18:49:02 2024] hub 7-1:1.0: 4 ports detected
[Wed Oct 23 18:49:02 2024] thunderbolt 1-2: new device found, vendor=0xf0 device=0x488
[Wed Oct 23 18:49:02 2024] thunderbolt 1-2: HP Thunderbolt Dock G4
[Wed Oct 23 18:49:02 2024] usb 7-1.4: new high-speed USB device number 9 using xhci_hcd
[Wed Oct 23 18:49:02 2024] usb 7-1.4: New USB device found, idVendor=03f0, idProduct=2488, bcdDevice= 6.25
[Wed Oct 23 18:49:02 2024] usb 7-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[Wed Oct 23 18:49:02 2024] usb 7-1.4: Product: USB4206 Smart Hub
[Wed Oct 23 18:49:02 2024] usb 7-1.4: Manufacturer: Microchip
[Wed Oct 23 18:49:02 2024] hub 7-1.4:1.0: USB hub found
[Wed Oct 23 18:49:02 2024] hub 7-1.4:1.0: 5 ports detected
[Wed Oct 23 18:49:03 2024] thunderbolt 1-2:1.1: new retimer found, vendor=0x1da0 device=0x8833
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: pciehp: Slot(0-1): Card present
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: pciehp: Slot(0-1): Link Up
[Wed Oct 23 18:49:03 2024] [drm] DM_MST: starting TM on aconnector: 0000000078e07d6a [id: 138]
[Wed Oct 23 18:49:03 2024] [drm] DM_MST: DP14, 4-lane link detected
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: [8086:0b26] type 01 class 0x060400 PCIe Switch Upstream Port
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: PCI bridge to [bus 00]
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0:   bridge window [io  0x0000-0x0fff]
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0:   bridge window [mem 0x00000000-0x000fffff]
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0:   bridge window [mem 0x00000000-0x000fffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: enabling Extended Tags
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: supports D1 D2
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: 2.000 Gb/s available PCIe bandwidth, limited by 2.5 GT/s PCIe x1 link at 0000:00:04.1 (capable of 31.504 Gb/s with 8.0 GT/s PCIe x4 link)
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: Adding to iommu group 8
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: ASPM: current common clock configuration is inconsistent, reconfiguring
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: bridge configuration invalid ([bus 00-00]), reconfiguring
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: [8086:0b26] type 01 class 0x060400 PCIe Switch Downstream Port
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: PCI bridge to [bus 00]
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0:   bridge window [io  0x0000-0x0fff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0:   bridge window [mem 0x00000000-0x000fffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0:   bridge window [mem 0x00000000-0x000fffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: enabling Extended Tags
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: supports D1 D2
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: Adding to iommu group 8
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: [8086:0b26] type 01 class 0x060400 PCIe Switch Downstream Port
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: PCI bridge to [bus 00]
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0:   bridge window [io  0x0000-0x0fff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0:   bridge window [mem 0x00000000-0x000fffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0:   bridge window [mem 0x00000000-0x000fffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: enabling Extended Tags
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: supports D1 D2
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: Adding to iommu group 8
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: [8086:0b26] type 01 class 0x060400 PCIe Switch Downstream Port
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: PCI bridge to [bus 00]
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0:   bridge window [io  0x0000-0x0fff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0:   bridge window [mem 0x00000000-0x000fffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0:   bridge window [mem 0x00000000-0x000fffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: enabling Extended Tags
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: supports D1 D2
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: Adding to iommu group 8
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: [8086:0b26] type 01 class 0x060400 PCIe Switch Downstream Port
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: PCI bridge to [bus 00]
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0:   bridge window [io  0x0000-0x0fff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0:   bridge window [mem 0x00000000-0x000fffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0:   bridge window [mem 0x00000000-0x000fffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: enabling Extended Tags
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: supports D1 D2
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: Adding to iommu group 8
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: [8086:0b26] type 01 class 0x060400 PCIe Switch Downstream Port
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: PCI bridge to [bus 00]
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0:   bridge window [io  0x0000-0x0fff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0:   bridge window [mem 0x00000000-0x000fffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0:   bridge window [mem 0x00000000-0x000fffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: enabling Extended Tags
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: supports D1 D2
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: Adding to iommu group 8
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: PCI bridge to [bus 67-c5]
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: bridge configuration invalid ([bus 00-00]), reconfiguring
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: bridge configuration invalid ([bus 00-00]), reconfiguring
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: bridge configuration invalid ([bus 00-00]), reconfiguring
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: bridge configuration invalid ([bus 00-00]), reconfiguring
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: bridge configuration invalid ([bus 00-00]), reconfiguring
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: PCI bridge to [bus 68-c5]
[Wed Oct 23 18:49:03 2024] pci_bus 0000:68: busn_res: [bus 68-c5] end is updated to 68
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: PCI bridge to [bus 69-c5]
[Wed Oct 23 18:49:03 2024] pci_bus 0000:69: busn_res: [bus 69-c5] end is updated to 87
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: PCI bridge to [bus 88-c5]
[Wed Oct 23 18:49:03 2024] pci_bus 0000:88: busn_res: [bus 88-c5] end is updated to a6
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: PCI bridge to [bus a7-c5]
[Wed Oct 23 18:49:03 2024] pci_bus 0000:a7: busn_res: [bus a7-c5] end is updated to c4
[Wed Oct 23 18:49:03 2024] pci 0000:c5:00.0: [8086:5502] type 00 class 0x020000 PCIe Endpoint
[Wed Oct 23 18:49:03 2024] pci 0000:c5:00.0: BAR 0 [mem 0x00000000-0x000fffff]
[Wed Oct 23 18:49:03 2024] pci 0000:c5:00.0: BAR 3 [mem 0x00000000-0x00003fff]
[Wed Oct 23 18:49:03 2024] pci 0000:c5:00.0: PME# supported from D0 D3hot D3cold
[Wed Oct 23 18:49:03 2024] pci 0000:c5:00.0: 2.000 Gb/s available PCIe bandwidth, limited by 2.5 GT/s PCIe x1 link at 0000:00:04.1 (capable of 4.000 Gb/s with 5.0 GT/s PCIe x1 link)
[Wed Oct 23 18:49:03 2024] pci 0000:c5:00.0: Adding to iommu group 8
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: PCI bridge to [bus c5]
[Wed Oct 23 18:49:03 2024] pci_bus 0000:c5: busn_res: [bus c5] end is updated to c5
[Wed Oct 23 18:49:03 2024] pci_bus 0000:67: busn_res: [bus 67-c5] end is updated to c5
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: bridge window [mem 0x00100000-0x001fffff 64bit pref] to [bus 69-87] add_size 100000 add_align 100000
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: bridge window [mem 0x00100000-0x001fffff] to [bus 69-87] add_size 100000 add_align 100000
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: bridge window [mem 0x00100000-0x001fffff 64bit pref] to [bus 88-a6] add_size 100000 add_align 100000
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: bridge window [mem 0x00100000-0x001fffff] to [bus 88-a6] add_size 100000 add_align 100000
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: bridge window [mem 0x00100000-0x001fffff 64bit pref] to [bus a7-c4] add_size 100000 add_align 100000
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: bridge window [mem 0x00100000-0x001fffff] to [bus a7-c4] add_size 100000 add_align 100000
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: bridge window [mem 0x00100000-0x005fffff 64bit pref] to [bus 67-c5] add_size 300000 add_align 100000
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: bridge window [mem 0x00100000-0x006fffff] to [bus 67-c5] add_size 300000 add_align 100000
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: bridge window [io  size 0x5000]: can't assign; no space
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: bridge window [io  size 0x5000]: failed to assign
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: bridge window [mem 0x64000000-0x7bffffff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: bridge window [mem 0x1400000000-0x23ffffffff 64bit pref]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: bridge window [io  size 0x5000]: can't assign; no space
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: bridge window [io  size 0x5000]: failed to assign
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: bridge window [mem 0x64000000-0x640fffff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: bridge window [mem 0x1400000000-0x14000fffff 64bit pref]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: bridge window [mem 0x64100000-0x6bffffff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: bridge window [mem 0x1400100000-0x19554fffff 64bit pref]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: bridge window [mem 0x6c000000-0x73efffff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: bridge window [mem 0x1955500000-0x1eaa8fffff 64bit pref]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: bridge window [mem 0x73f00000-0x7bdfffff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: bridge window [mem 0x1eaa900000-0x23ffcfffff 64bit pref]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: bridge window [mem 0x7be00000-0x7bffffff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: bridge window [mem 0x23ffd00000-0x23ffdfffff 64bit pref]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: bridge window [io  size 0x1000]: can't assign; no space
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: bridge window [io  size 0x1000]: failed to assign
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: bridge window [io  size 0x1000]: can't assign; no space
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: bridge window [io  size 0x1000]: failed to assign
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: bridge window [io  size 0x1000]: can't assign; no space
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: bridge window [io  size 0x1000]: failed to assign
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: bridge window [io  size 0x1000]: can't assign; no space
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: bridge window [io  size 0x1000]: failed to assign
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: bridge window [io  size 0x1000]: can't assign; no space
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: bridge window [io  size 0x1000]: failed to assign
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: PCI bridge to [bus 68]
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0:   bridge window [mem 0x64000000-0x640fffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0:   bridge window [mem 0x1400000000-0x14000fffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: PCI bridge to [bus 69-87]
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0:   bridge window [mem 0x64100000-0x6bffffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0:   bridge window [mem 0x1400100000-0x19554fffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: PCI bridge to [bus 88-a6]
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0:   bridge window [mem 0x6c000000-0x73efffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0:   bridge window [mem 0x1955500000-0x1eaa8fffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: PCI bridge to [bus a7-c4]
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0:   bridge window [mem 0x73f00000-0x7bdfffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0:   bridge window [mem 0x1eaa900000-0x23ffcfffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:c5:00.0: BAR 0 [mem 0x7be00000-0x7befffff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:c5:00.0: BAR 3 [mem 0x7bf00000-0x7bf03fff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: PCI bridge to [bus c5]
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0:   bridge window [mem 0x7be00000-0x7bffffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0:   bridge window [mem 0x23ffd00000-0x23ffdfffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: PCI bridge to [bus 67-c5]
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0:   bridge window [mem 0x64000000-0x7bffffff]
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0:   bridge window [mem 0x1400000000-0x23ffffffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: PCI bridge to [bus 66-c5]
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1:   bridge window [mem 0x64000000-0x7bffffff]
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1:   bridge window [mem 0x1400000000-0x23ffffffff 64bit pref]
[Wed Oct 23 18:49:03 2024] PCI: No. 2 try to assign unassigned res
[Wed Oct 23 18:49:03 2024] release child resource [io  0xb000-0xb0ff]
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:01.3: resource 13 [io  0xb000-0xbfff] released
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:01.3: PCI bridge to [bus 02]
[Wed Oct 23 18:49:03 2024] release child resource [io  0xa000-0xa0ff]
[Wed Oct 23 18:49:03 2024] release child resource [io  0xa000-0xa0ff]
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:02.2: resource 13 [io  0xa000-0xafff] released
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:02.2: PCI bridge to [bus 04]
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:03.1: resource 13 [io  0x6000-0x9fff] released
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:03.1: PCI bridge to [bus 06-65]
[Wed Oct 23 18:49:03 2024] release child resource [io  0x1000-0x10ff]
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:08.1: resource 13 [io  0x1000-0x1fff] released
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:08.1: PCI bridge to [bus c6]
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: bridge window [io  0x1000-0x5fff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: bridge window [io  0x1000-0x5fff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: bridge window [io  0x1000-0x1fff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: bridge window [io  0x2000-0x2fff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: bridge window [io  0x3000-0x3fff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: bridge window [io  0x4000-0x4fff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: bridge window [io  0x5000-0x5fff]: assigned
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0: PCI bridge to [bus 68]
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0:   bridge window [io  0x1000-0x1fff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0:   bridge window [mem 0x64000000-0x640fffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:00.0:   bridge window [mem 0x1400000000-0x14000fffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0: PCI bridge to [bus 69-87]
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0:   bridge window [io  0x2000-0x2fff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0:   bridge window [mem 0x64100000-0x6bffffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:01.0:   bridge window [mem 0x1400100000-0x19554fffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0: PCI bridge to [bus 88-a6]
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0:   bridge window [io  0x3000-0x3fff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0:   bridge window [mem 0x6c000000-0x73efffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:02.0:   bridge window [mem 0x1955500000-0x1eaa8fffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0: PCI bridge to [bus a7-c4]
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0:   bridge window [io  0x4000-0x4fff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0:   bridge window [mem 0x73f00000-0x7bdfffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:03.0:   bridge window [mem 0x1eaa900000-0x23ffcfffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0: PCI bridge to [bus c5]
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0:   bridge window [io  0x5000-0x5fff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0:   bridge window [mem 0x7be00000-0x7bffffff]
[Wed Oct 23 18:49:03 2024] pci 0000:67:04.0:   bridge window [mem 0x23ffd00000-0x23ffdfffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0: PCI bridge to [bus 67-c5]
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0:   bridge window [io  0x1000-0x5fff]
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0:   bridge window [mem 0x64000000-0x7bffffff]
[Wed Oct 23 18:49:03 2024] pci 0000:66:00.0:   bridge window [mem 0x1400000000-0x23ffffffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: PCI bridge to [bus 66-c5]
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1:   bridge window [io  0x1000-0x5fff]
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1:   bridge window [mem 0x64000000-0x7bffffff]
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1:   bridge window [mem 0x1400000000-0x23ffffffff 64bit pref]
[Wed Oct 23 18:49:03 2024] pcieport 0000:66:00.0: enabling device (0000 -> 0003)
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:00.0: enabling device (0000 -> 0003)
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:01.0: enabling device (0000 -> 0003)
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:01.0: pciehp: Slot #1 AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+ Interlock- NoCompl+ IbPresDis- LLActRep+
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:02.0: enabling device (0000 -> 0003)
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:02.0: pciehp: Slot #2 AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+ Interlock- NoCompl+ IbPresDis- LLActRep+
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:03.0: enabling device (0000 -> 0003)
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:03.0: pciehp: Slot #3 AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+ Interlock- NoCompl+ IbPresDis- LLActRep+
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0: enabling device (0000 -> 0003)
[Wed Oct 23 18:49:03 2024] igc 0000:c5:00.0: enabling device (0000 -> 0002)
[Wed Oct 23 18:49:03 2024] igc 0000:c5:00.0: PCIe PTM not supported by PCIe bus/controller
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: AER: Correctable error message received from 0000:67:04.0
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0: PCIe Bus Error: severity=Correctable, type=Data Link Layer, (Receiver ID)
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:   device [8086:0b26] error status/mask=00000080/00002000
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:    [ 7] BadDLLP               
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: PME: Spurious native interrupt!
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: PME: Spurious native interrupt!
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] usb 8-1: new SuperSpeed Plus Gen 2x1 USB device number 5 using xhci_hcd
[Wed Oct 23 18:49:03 2024] usb 8-1: New USB device found, idVendor=8087, idProduct=0b40, bcdDevice=12.34
[Wed Oct 23 18:49:03 2024] usb 8-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[Wed Oct 23 18:49:03 2024] usb 8-1: Product: USB3.0 Hub
[Wed Oct 23 18:49:03 2024] usb 8-1: Manufacturer: Intel Corporation.
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] hub 8-1:1.0: USB hub found
[Wed Oct 23 18:49:03 2024] hub 8-1:1.0: 4 ports detected
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] usb 7-1.4.2: new high-speed USB device number 10 using xhci_hcd
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] [drm] DMUB HPD RX IRQ callback: link_index=8
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: AER: Correctable error message received from 0000:67:04.0
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0: PCIe Bus Error: severity=Correctable, type=Data Link Layer, (Receiver ID)
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:   device [8086:0b26] error status/mask=00000080/00002000
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:    [ 7] BadDLLP               
[Wed Oct 23 18:49:03 2024] [drm] Downstream port present 1, type 0
[Wed Oct 23 18:49:03 2024] audit: type=1107 audit(1729727343.930:230): pid=1300 uid=101 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.DBus.Properties" member="PropertiesChanged" name=":1.14" mask="receive" pid=5078 label="snap.thunderbird.thunderbird" peer_pid=1329 peer_label="unconfined"
                            exe="/usr/bin/dbus-daemon" sauid=101 hostname=? addr=? terminal=?'
[Wed Oct 23 18:49:03 2024] usb 7-1.4.2: New USB device found, idVendor=03f0, idProduct=4488, bcdDevice= 1.21
[Wed Oct 23 18:49:03 2024] usb 7-1.4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[Wed Oct 23 18:49:03 2024] usb 7-1.4.2: Product: USB2734
[Wed Oct 23 18:49:03 2024] usb 7-1.4.2: Manufacturer: Microchip Tech
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: AER: Correctable error message received from 0000:67:04.0
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0: PCIe Bus Error: severity=Correctable, type=Data Link Layer, (Receiver ID)
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:   device [8086:0b26] error status/mask=00000080/00002000
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:    [ 7] BadDLLP               
[Wed Oct 23 18:49:03 2024] hub 7-1.4.2:1.0: USB hub found
[Wed Oct 23 18:49:03 2024] hub 7-1.4.2:1.0: 4 ports detected
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: AER: Correctable error message received from 0000:67:04.0
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0: PCIe Bus Error: severity=Correctable, type=Data Link Layer, (Receiver ID)
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:   device [8086:0b26] error status/mask=00000080/00002000
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:    [ 7] BadDLLP               
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: AER: Correctable error message received from 0000:67:04.0
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0: PCIe Bus Error: severity=Correctable, type=Data Link Layer, (Receiver ID)
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:   device [8086:0b26] error status/mask=00000080/00002000
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:    [ 7] BadDLLP               
[Wed Oct 23 18:49:03 2024] usb 7-1.4.3: new full-speed USB device number 11 using xhci_hcd
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: AER: Correctable error message received from 0000:67:04.0
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0: PCIe Bus Error: severity=Correctable, type=Data Link Layer, (Receiver ID)
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:   device [8086:0b26] error status/mask=00000080/00002000
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:    [ 7] BadDLLP               
[Wed Oct 23 18:49:03 2024] audit: type=1107 audit(1729727344.201:231): pid=1300 uid=101 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_signal"  bus="system" path="/org/freedesktop/login1" interface="org.freedesktop.DBus.Properties" member="PropertiesChanged" name=":1.14" mask="receive" pid=5078 label="snap.thunderbird.thunderbird" peer_pid=1329 peer_label="unconfined"
                            exe="/usr/bin/dbus-daemon" sauid=101 hostname=? addr=? terminal=?'
[Wed Oct 23 18:49:03 2024] pcieport 0000:00:04.1: AER: Correctable error message received from 0000:67:04.0
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0: PCIe Bus Error: severity=Correctable, type=Data Link Layer, (Receiver ID)
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:   device [8086:0b26] error status/mask=00000080/00002000
[Wed Oct 23 18:49:03 2024] pcieport 0000:67:04.0:    [ 7] BadDLLP               
[Wed Oct 23 18:49:04 2024] pcieport 0000:00:04.1: AER: Correctable error message received from 0000:67:04.0
[Wed Oct 23 18:49:04 2024] pcieport 0000:67:04.0: PCIe Bus Error: severity=Correctable, type=Data Link Layer, (Receiver ID)

```

lspci -tv output:

```
cactus@cactus-ZBookPower:~$ lspci -tv
-[0000:00]-+-00.0  Advanced Micro Devices, Inc. [AMD] Device 14e8
           +-00.2  Advanced Micro Devices, Inc. [AMD] Device 14e9
           +-01.0  Advanced Micro Devices, Inc. [AMD] Device 14ea
           +-01.2-[01]----00.0  Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983
           +-01.3-[02]----00.0  Realtek Semiconductor Co., Ltd. RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet Controller
           +-02.0  Advanced Micro Devices, Inc. [AMD] Device 14ea
           +-02.1-[03]----00.0  Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader
           +-02.2-[04]----00.0  Realtek Semiconductor Co., Ltd. RTL8852CE PCIe 802.11ax Wireless Network Controller
           +-02.4-[05]----00.0  KIOXIA Corporation NVMe SSD Controller BG5 (DRAM-less)
           +-03.0  Advanced Micro Devices, Inc. [AMD] Device 14ea
           +-03.1-[06-65]--
           +-04.0  Advanced Micro Devices, Inc. [AMD] Device 14ea
           +-04.1-[66-c5]----00.0-[67-c5]--+-00.0-[68]--
           |                               +-01.0-[69-87]--
           |                               +-02.0-[88-a6]--
           |                               +-03.0-[a7-c4]--
           |                               \-04.0-[c5]----00.0  Intel Corporation Ethernet Controller (2) I225-LMvP
           +-08.0  Advanced Micro Devices, Inc. [AMD] Device 14ea
           +-08.1-[c6]--+-00.0  Advanced Micro Devices, Inc. [AMD/ATI] Phoenix3
           |            +-00.1  Advanced Micro Devices, Inc. [AMD/ATI] Rembrandt Radeon High Definition Audio Controller
           |            +-00.2  Advanced Micro Devices, Inc. [AMD] Family 19h (Model 74h) CCP/PSP 3.0 Device
           |            +-00.3  Advanced Micro Devices, Inc. [AMD] Device 15b9
           |            +-00.4  Advanced Micro Devices, Inc. [AMD] Device 15ba
           |            +-00.5  Advanced Micro Devices, Inc. [AMD] ACP/ACP3X/ACP6x Audio Coprocessor
           |            +-00.6  Advanced Micro Devices, Inc. [AMD] Family 17h/19h HD Audio Controller
           |            \-00.7  Advanced Micro Devices, Inc. [AMD] Device 164a
           +-08.2-[c7]--+-00.0  Advanced Micro Devices, Inc. [AMD] Device 14ec
           |            \-00.1  Advanced Micro Devices, Inc. [AMD] AMD IPU Device
           +-08.3-[c8]--+-00.0  Advanced Micro Devices, Inc. [AMD] Device 14ec
           |            +-00.3  Advanced Micro Devices, Inc. [AMD] Device 15c0
           |            +-00.4  Advanced Micro Devices, Inc. [AMD] Device 15c1
           |            +-00.5  Advanced Micro Devices, Inc. [AMD] Pink Sardine USB4/Thunderbolt NHI controller #1
           |            \-00.6  Advanced Micro Devices, Inc. [AMD] Pink Sardine USB4/Thunderbolt NHI controller #2
           +-14.0  Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller
           +-14.3  Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge
           +-18.0  Advanced Micro Devices, Inc. [AMD] Device 14f0
           +-18.1  Advanced Micro Devices, Inc. [AMD] Device 14f1
           +-18.2  Advanced Micro Devices, Inc. [AMD] Device 14f2
           +-18.3  Advanced Micro Devices, Inc. [AMD] Device 14f3
           +-18.4  Advanced Micro Devices, Inc. [AMD] Device 14f4
           +-18.5  Advanced Micro Devices, Inc. [AMD] Device 14f5
           +-18.6  Advanced Micro Devices, Inc. [AMD] Device 14f6
           \-18.7  Advanced Micro Devices, Inc. [AMD] Device 14f7

```

I'm not "new" to linux but I'm also not too savvy on the hardware side of things when it comes to this stuff.  Any help would be greatly appreciated.

---

### Post by aachaoshand on 2024-10-30
Still have the issue, even after tinkering around with thunderbolt drivers...Anyone have any input?

---

### Post by glite on 2024-11-06
Relevant bug report [https://bugzilla.kernel.org/show_bug.cgi?id=218795](https://bugzilla.kernel.org/show_bug.cgi?id=218795)
If system is otherwise stable for you, eg you don't expect any crashes or mentions of Uncorrectable errors, you can try to hide them with pci=noaer.

---


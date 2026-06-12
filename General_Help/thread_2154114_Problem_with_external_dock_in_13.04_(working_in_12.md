---
title: "Problem with external dock in 13.04 (working in 12.10)"
date: 2013-06-13
forum: General Help
---

### Post by PegasoR on 2013-06-13
Hi to all the community :-)

I'm using ubuntu gnome 13.04.
My computer has a PCIe USB3 card with 2 USB3.0 ports. The card works perfectly (I can plug USB3 card readers, USB3 pendrives, etc... hotplugging with no problems).

The problem comes when I plug a external dock for 4 hard disks (this one: [http://www.tweaktown.com/pressrelease/5236/sharkoon_sata_quickport_quattro_for_up_to_four_sata_hard_drives_and_ssds/index.html](http://www.tweaktown.com/pressrelease/5236/sharkoon_sata_quickport_quattro_for_up_to_four_sata_hard_drives_and_ssds/index.html) )
It works if I plug it using a usb2.0 cable, but if I use a usb3.0 cable... the nightmare starts.

Using Ubuntu 12.10 everything worked. 
Since I installed 13.04 it doesn't work (fresh install, not upgrade). If I boot with the device already connected, it works, but if I unplug and plug again (hotplug), my system freezes for 10 seconds, and then the PCIe USB3 card is "disabled".

Here I paste some results, in case they can help.

This are the results when I start the computer with the device unplugged:

-----------------
**lspci:**

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G71 [GeForce 7950 GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
04:00.0 USB controller: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller (rev 02)
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
06:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)

--------------
**lsusb:**

Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 002: ID 0bc2:3010 Seagate RSS LLC 
Bus 002 Device 003: ID 0424:2502 Standard Microsystems Corp. 
Bus 002 Device 005: ID 0bda:0161 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 003: ID 056a:00b5 Wacom Co., Ltd Intuos3 6x11 (PTZ-631W)
Bus 006 Device 002: ID 1ea7:1002  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 0424:2602 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 007: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader

[B]-----------------
-----------------
Now I connect the dock to the PCIe USB3 card, using USB2.0 cable, and one hard disk connected (it works):[/B]

----------------
**lsusb:**

Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 002: ID 0bc2:3010 Seagate RSS LLC 
Bus 002 Device 003: ID 0424:2502 Standard Microsystems Corp. 
Bus 002 Device 005: ID 0bda:0161 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 003: ID 056a:00b5 Wacom Co., Ltd Intuos3 6x11 (PTZ-631W)
Bus 006 Device 002: ID 1ea7:1002  
Bus 008 Device 002: ID 152d:0551 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 0424:2602 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 007: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader

----------------
**dmesg (just the changes after plugging the device)**:

[ 5797.932029] usb 8-2: new high-speed USB device number 2 using xhci_hcd
[ 5797.952916] usb 8-2: New USB device found, idVendor=152d, idProduct=0551
[ 5797.952922] usb 8-2: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[ 5797.952926] usb 8-2: Product: USB to ATA/ATAPI Bridge
[ 5797.952930] usb 8-2: Manufacturer: JMicron
[ 5797.952933] usb 8-2: SerialNumber: DCA2375564FF
[ 5797.956062] scsi11 : usb-storage 8-2:1.0
[ 5798.957979] scsi 11:0:0:0: Direct-Access     WDC WD30 EZRX-00MMMB0          PQ: 0 ANSI: 5
[ 5798.958674] sd 11:0:0:0: Attached scsi generic sg12 type 0
[ 5798.958965] sd 11:0:0:0: [sdk] Very big device. Trying to use READ CAPACITY(16).
[ 5798.959151] sd 11:0:0:0: [sdk] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[ 5798.963266] sd 11:0:0:0: [sdk] Write Protect is off
[ 5798.963272] sd 11:0:0:0: [sdk] Mode Sense: 28 00 00 00
[ 5798.965263] sd 11:0:0:0: [sdk] No Caching mode page present
[ 5798.965268] sd 11:0:0:0: [sdk] Assuming drive cache: write through
[ 5798.965864] sd 11:0:0:0: [sdk] Very big device. Trying to use READ CAPACITY(16).
[ 5798.969105] sd 11:0:0:0: [sdk] No Caching mode page present
[ 5798.969111] sd 11:0:0:0: [sdk] Assuming drive cache: write through
[ 5799.033931]  sdk: sdk1 sdk2
[ 5799.035431] sd 11:0:0:0: [sdk] Very big device. Trying to use READ CAPACITY(16).
[ 5799.038912] sd 11:0:0:0: [sdk] No Caching mode page present
[ 5799.038918] sd 11:0:0:0: [sdk] Assuming drive cache: write through
[ 5799.038922] sd 11:0:0:0: [sdk] Attached SCSI disk
[ 6153.597744] usb 8-2: USB disconnect, device number 2


[B]--------------------
--------------------

Now I plug the device with one hard disk connected, using a USB3.0 cable (the system freezes for about 10 seconds)[/B]

--------------------
**lsusb (there is no sign of the device):** 

Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 002: ID 0bc2:3010 Seagate RSS LLC 
Bus 002 Device 003: ID 0424:2502 Standard Microsystems Corp. 
Bus 002 Device 005: ID 0bda:0161 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 003: ID 056a:00b5 Wacom Co., Ltd Intuos3 6x11 (PTZ-631W)
Bus 006 Device 002: ID 1ea7:1002  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 0424:2602 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 007: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader

-----------------
**lspci (the PCIe usb3 card is still there, but it's not working anymore if I plug anything):**

00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G71 [GeForce 7950 GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 02)
04:00.0 USB controller: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller (rev 02)
06:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
06:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)

-----------------
**dmesg (just the changes since I plug the device):**

[ 6254.332050] usb 8-2: new high-speed USB device number 3 using xhci_hcd
[ 6259.332022] xhci_hcd 0000:04:00.0: Timeout while waiting for address device command
[ 6259.340016] xhci_hcd 0000:04:00.0: Stopped the command ring failed, maybe the host is dead
[ 6259.340016] xhci_hcd 0000:04:00.0: Host not halted after 16000 microseconds.
[ 6259.340016] xhci_hcd 0000:04:00.0: Abort command ring failed
[ 6275.759578] xhci_hcd 0000:04:00.0: HC died; cleaning up
[ 6275.760003] [sched_delayed] sched: RT throttling activated
[ 6280.960024] xhci_hcd 0000:04:00.0: Timeout while waiting for address device command
[ 6280.960031] xhci_hcd 0000:04:00.0: Abort the command ring, but the xHCI is dead.
[ 6281.164068] usb 8-2: device not accepting address 3, error -108
[ 6281.164078] hub 8-0:1.0: cannot disable port 2 (err = -19)
[ 6286.164042] xhci_hcd 0000:04:00.0: Timeout while waiting for a slot
[ 6286.164049] xhci_hcd 0000:04:00.0: Abort the command ring, but the xHCI is dead.
[ 6286.164062] hub 8-0:1.0: cannot reset port 2 (err = -19)
[ 6286.164068] hub 8-0:1.0: cannot disable port 2 (err = -19)
[ 6286.164072] xHCI xhci_free_dev called with unaddressed device
[ 6291.164019] xhci_hcd 0000:04:00.0: Timeout while waiting for a slot
[ 6291.164026] xhci_hcd 0000:04:00.0: Abort the command ring, but the xHCI is dead.
[ 6291.164040] hub 8-0:1.0: cannot reset port 2 (err = -19)
[ 6291.164046] hub 8-0:1.0: cannot disable port 2 (err = -19)
[ 6291.164050] xHCI xhci_free_dev called with unaddressed device
[ 6296.164021] xhci_hcd 0000:04:00.0: Timeout while waiting for a slot
[ 6296.164028] xhci_hcd 0000:04:00.0: Abort the command ring, but the xHCI is dead.
[ 6296.164042] hub 8-0:1.0: cannot reset port 2 (err = -19)
[ 6296.164047] hub 8-0:1.0: cannot disable port 2 (err = -19)
[ 6296.164052] xHCI xhci_free_dev called with unaddressed device
[ 6296.164058] hub 8-0:1.0: unable to enumerate USB device on port 2
[ 6296.164061] hub 8-0:1.0: cannot disable port 2 (err = -19)

[B]---------------------
---------------------

Now I reboot the system, with the device plugged using usb3.0 cable, and one hard disk connected.
Everything works (if I don't unplug it).[/B]

------------------
**lsusb :**

Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 002: ID 0bc2:3010 Seagate RSS LLC 
Bus 002 Device 003: ID 0424:2502 Standard Microsystems Corp. 
Bus 002 Device 005: ID 0bda:0161 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 003: ID 056a:00b5 Wacom Co., Ltd Intuos3 6x11 (PTZ-631W)
Bus 006 Device 002: ID 1ea7:1002  
Bus 009 Device 002: ID 152d:0551 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 0424:2602 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 007: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader

-----------------
**dmesg | grep -i usb:**

[    0.148234] ACPI: bus type usb registered
[    0.148234] usbcore: registered new interface driver usbfs
[    0.148234] usbcore: registered new interface driver hub
[    0.148234] usbcore: registered new device driver usb
[    0.816639] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.816684] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.832036] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.832062] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.832066] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.832070] usb usb1: Product: EHCI Host Controller
[    0.832073] usb usb1: Manufacturer: Linux 3.8.0-23-generic ehci_hcd
[    0.832076] usb usb1: SerialNumber: 0000:00:1a.7
[    0.832208] hub 1-0:1.0: USB hub found
[    0.832349] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.848027] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.848046] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.848050] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.848053] usb usb2: Product: EHCI Host Controller
[    0.848057] usb usb2: Manufacturer: Linux 3.8.0-23-generic ehci_hcd
[    0.848060] usb usb2: SerialNumber: 0000:00:1d.7
[    0.848170] hub 2-0:1.0: USB hub found
[    0.848317] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.848332] uhci_hcd: USB Universal Host Controller Interface driver
[    0.848357] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.848416] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.848419] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.848421] usb usb3: Product: UHCI Host Controller
[    0.848423] usb usb3: Manufacturer: Linux 3.8.0-23-generic uhci_hcd
[    0.848425] usb usb3: SerialNumber: 0000:00:1a.0
[    0.848502] hub 3-0:1.0: USB hub found
[    0.848581] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.848641] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.848643] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.848646] usb usb4: Product: UHCI Host Controller
[    0.848648] usb usb4: Manufacturer: Linux 3.8.0-23-generic uhci_hcd
[    0.848650] usb usb4: SerialNumber: 0000:00:1a.1
[    0.848731] hub 4-0:1.0: USB hub found
[    0.848809] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.848857] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.848860] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.848862] usb usb5: Product: UHCI Host Controller
[    0.848864] usb usb5: Manufacturer: Linux 3.8.0-23-generic uhci_hcd
[    0.848866] usb usb5: SerialNumber: 0000:00:1d.0
[    0.848941] hub 5-0:1.0: USB hub found
[    0.849018] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.849066] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.849068] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.849071] usb usb6: Product: UHCI Host Controller
[    0.849073] usb usb6: Manufacturer: Linux 3.8.0-23-generic uhci_hcd
[    0.849075] usb usb6: SerialNumber: 0000:00:1d.1
[    0.849150] hub 6-0:1.0: USB hub found
[    0.849227] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.849276] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.849279] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.849281] usb usb7: Product: UHCI Host Controller
[    0.849283] usb usb7: Manufacturer: Linux 3.8.0-23-generic uhci_hcd
[    0.849285] usb usb7: SerialNumber: 0000:00:1d.2
[    0.849359] hub 7-0:1.0: USB hub found
[    0.849467] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 8
[    1.131022] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    1.131024] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.131027] usb usb8: Product: xHCI Host Controller
[    1.131029] usb usb8: Manufacturer: Linux 3.8.0-23-generic xhci_hcd
[    1.131031] usb usb8: SerialNumber: 0000:04:00.0
[    1.131123] hub 8-0:1.0: USB hub found
[    1.131195] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 9
[    1.134239] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.134241] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.134244] usb usb9: Product: xHCI Host Controller
[    1.134246] usb usb9: Manufacturer: Linux 3.8.0-23-generic xhci_hcd
[    1.134248] usb usb9: SerialNumber: 0000:04:00.0
[    1.134345] hub 9-0:1.0: USB hub found
[    1.656041] usb 1-3: new high-speed USB device number 4 using ehci-pci
[    1.794514] usb 1-3: New USB device found, idVendor=0bda, idProduct=8187
[    1.794518] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.794522] usb 1-3: Product: RTL8187_Wireless
[    1.794525] usb 1-3: Manufacturer: Manufacturer_Realtek_RTL8187_
[    1.794528] usb 1-3: SerialNumber: 0015AF09F727
[    1.904026] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    2.058703] usb 2-1: New USB device found, idVendor=0bc2, idProduct=3010
[    2.058710] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.058713] usb 2-1: Product: FreeAgent Pro
[    2.058717] usb 2-1: Manufacturer: Seagate
[    2.058720] usb 2-1: SerialNumber:             5QD02W7C
[    2.180112] usb 2-2: new high-speed USB device number 3 using ehci-pci
[    2.312452] usb 2-2: New USB device found, idVendor=0424, idProduct=2502
[    2.312458] usb 2-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.312738] hub 2-2:1.0: USB hub found
[    2.684047] usb 2-5: new high-speed USB device number 5 using ehci-pci
[    2.882701] usb 2-5: New USB device found, idVendor=0bda, idProduct=0161
[    2.882705] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.882709] usb 2-5: Product: USB2.0-CRW
[    2.882712] usb 2-5: Manufacturer: Generic
[    2.882715] usb 2-5: SerialNumber: 20070818000000000
[    3.124030] usb 3-1: new low-speed USB device number 2 using uhci_hcd
[    3.301429] usb 3-1: New USB device found, idVendor=046d, idProduct=c517
[    3.301435] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.301439] usb 3-1: Product: USB Receiver
[    3.301442] usb 3-1: Manufacturer: Logitech
[    3.544160] usb 3-2: new full-speed USB device number 3 using uhci_hcd
[    3.712427] usb 3-2: New USB device found, idVendor=056a, idProduct=00b5
[    3.712434] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.712437] usb 3-2: Product: PTZ-631W
[    3.712441] usb 3-2: Manufacturer: Tablet
[    3.952062] usb 6-2: new full-speed USB device number 2 using uhci_hcd
[    4.128083] usb 6-2: New USB device found, idVendor=1ea7, idProduct=1002
[    4.128090] usb 6-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.128094] usb 6-2: Product: Gaming Mouse
[    4.128097] usb 6-2: Manufacturer: BTL
[    4.496704] usb 9-2: new SuperSpeed USB device number 2 using xhci_hcd
[    4.513544] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[    4.515919] usb 9-2: New USB device found, idVendor=152d, idProduct=0551
[    4.515924] usb 9-2: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[    4.515928] usb 9-2: Product: USB to ATA/ATAPI Bridge
[    4.515931] usb 9-2: Manufacturer: JMicron
[    4.515935] usb 9-2: SerialNumber: DCA2375564FF
[    4.716081] usb 2-2.1: new high-speed USB device number 6 using ehci-pci
[    4.808329] usb 2-2.1: New USB device found, idVendor=0424, idProduct=2602
[    4.808334] usb 2-2.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    4.808605] hub 2-2.1:1.0: USB hub found
[    5.080080] usb 2-2.1.1: new high-speed USB device number 7 using ehci-pci
[    5.258959] usb 2-2.1.1: New USB device found, idVendor=0424, idProduct=2228
[    5.258965] usb 2-2.1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.258969] usb 2-2.1.1: Product: Flash Card Reader
[    5.258972] usb 2-2.1.1: Manufacturer: Generic
[    5.258975] usb 2-2.1.1: SerialNumber: 26020128B005
[   10.932138] Initializing USB Mass Storage driver...
[   10.933648] usb-storage 2-1:1.0: Quirks match for vid 0bc2 pid 3010: 8000
[   10.936417] scsi8 : usb-storage 2-1:1.0
[   10.940812] scsi9 : usb-storage 2-5:1.1
[   10.954055] scsi10 : usb-storage 9-2:1.0
[   10.966609] scsi11 : usb-storage 2-2.1.1:1.0
[   10.966776] usbcore: registered new interface driver usb-storage
[   10.966779] USB Mass Storage support registered.
[   11.051092] usbcore: registered new interface driver usbhid
[   11.051096] usbhid: USB HID core driver
[   11.066227] input: BTL Gaming Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.0/input/input2
[   11.071761] hid-generic 0003:1EA7:1002.0003: input,hiddev0,hidraw0: USB HID v1.10 Mouse [BTL Gaming Mouse] on usb-0000:00:1d.1-2/input0
[   11.076052] input: Wacom Intuos3 6x11 as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input3
[   11.078290] input: BTL Gaming Mouse as /devices/pci0000:00/0000:00:1d.1/usb6/6-2/6-2:1.1/input/input4
[   11.079095] hid-generic 0003:1EA7:1002.0004: input,hidraw1: USB HID v1.11 Keyboard [BTL Gaming Mouse] on usb-0000:00:1d.1-2/input1
[   11.089836] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input5
[   11.090006] logitech 0003:046D:C517.0001: input,hidraw2: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.0-1/input0
[   11.093376] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input6
[   11.093528] logitech 0003:046D:C517.0002: input,hiddev0,hidraw3: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-1/input1
[   11.146836] usbcore: registered new interface driver mceusb
[   11.358682] usbcore: registered new interface driver rtl8187
[   11.684541] usbcore: registered new interface driver wacom
[   28.945389] usb 9-2: reset SuperSpeed USB device number 2 using xhci_hcd
[   28.961645] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.

-----------------
[B]-----------------
The device is mounted and working, but... if I unplug it and plug it again... we are back to the beginning and nothing works (same results as posted before "xhci_hcd 0000:04:00.0: Timeout while waiting for address device command", PCIe card not working anymore, etc, etc...)[/B]



Any help is welcome :-)
Thanks.

---

### Post by gladia2r on 2013-08-12
I'm experiencing a similar issue with my USB3 ports - which appears to be a known issue/bug reported:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/994248](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/994248)

Cheers,

---


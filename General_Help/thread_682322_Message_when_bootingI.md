---
title: "Message when bootingI"
date: 2008-01-29
forum: General Help
---

### Post by rhomp2002 on 2008-01-29
I am getting this message when the O/S is booting and I am not sure if it is software related or hardware related:

 This is displayed and I am not sure what to do to correct it.

usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 8 ports detected
116x: driver isp116x-hcd, 03 Nov 2005
ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
USB Universal Host Controller Interface driver v3.0
ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: UHCI Host Controller
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
uhci_hcd 0000:00:1d.0: irq 20, io base 0x00009000
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: UHCI Host Controller
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
uhci_hcd 0000:00:1d.1: irq 17, io base 0x00009400
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: UHCI Host Controller
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009800
usb usb4: configuration #1 chosen from 1 choice
usb 1-1: new high speed USB device using ehci_hcd and address 2
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: UHCI Host Controller
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000a000
usb usb5: configuration #1 chosen from 1 choice
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 2 ports detected
sl811: driver sl811-hcd, 19 May 2005
Initializing USB Mass Storage driver...
usb 1-1: device descriptor read/64, error -110
usb 1-1: device descriptor read/64, error -110
usb 1-1: new high speed USB device using ehci_hcd and address 3
usb 1-1: device descriptor read/64, error -110
usb 1-1: device descriptor read/64, error -110
usb 1-1: new high speed USB device using ehci_hcd and address 4
usb 1-1: device descriptor read/8, error -110
usb 1-1: device descriptor read/8, error -110
usb 1-1: new high speed USB device using ehci_hcd and address 5
usb 1-1: device descriptor read/8, error -110
usb 1-1: device descriptor read/8, error -110
usb 4-1: new low speed USB device using uhci_hcd and address 2
usb 4-1: configuration #1 chosen from 1 choice
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.

I looked in LinuxQuestions.org and saw something like it but they suggesting blacklisting pegasus. That was tied in with bluetooth but I am not using bluetooth. It just started doing this and I am not sure if it is a software or a hardware issue. It starts off saying it recognizes 8 USB hubs. Then it says it recognizes 2 USB hubs. Kind of confusing which it is doing. What my computer has is 4 USB hubs on the back of the box and 2 on the front of the box. Everything I have hooked up seems to work OK but I am just wondering if this is a problem waiting to happen or not. It is not exclusive to Ubuntu. It happens with all the other Linux distros I have as well (BlueWhite64, Sabayon both full and mini, Debian). It gets the same message in all cases.

Any ideas or suggestions would be appreciated. I am putting this in the other forums as well.

---

### Post by FuturePilot on 2008-01-29
Do you have an external drive or a USB Flash drive or something plugged in? If you do is it mounting?
[Related]("http://www.linuxquestions.org/questions/linux-hardware-18/suse-10.1-usb-hdd-problem-498780/")

---


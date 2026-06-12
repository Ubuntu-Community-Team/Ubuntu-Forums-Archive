---
title: "help! /proc/bus/usb is empty"
date: 2007-11-25
forum: General Help
---

### Post by D-KICK on 2007-11-25
the /proc/bus/usb directory is completely empty on my machine - no devices file - no directories for the single interfaces.
Mouse and Keyboard are working (wireless usb device). 
I found this out because VMware server does not show any usb device.

lsusb looks like this:
Bus 002 Device 004: ID 03f0:0211 Hewlett-Packard
Bus 002 Device 002: ID 046d:c513 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

dmesg | grep -i usb:
[    3.876000] usbcore: registered new interface driver usbfs
[    3.876000] usbcore: registered new interface driver hub
[    3.876000] usbcore: registered new device driver usb
[    3.904000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    7.348000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    7.348000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.348000] usb usb1: configuration #1 chosen from 1 choice
[    7.352000] hub 1-0:1.0: USB hub found
[    7.456000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    7.512000] usb usb2: configuration #1 chosen from 1 choice
[    7.512000] hub 2-0:1.0: USB hub found
[    8.240000] usb 2-4: new full speed USB device using ohci_hcd and address 2
[    8.460000] usb 2-4: configuration #1 chosen from 1 choice
[    8.768000] usb 2-6: new full speed USB device using ohci_hcd and address 3
[    8.984000] usb 2-6: configuration #1 chosen from 1 choice
[   14.756000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 3 vid 0x03F0 pid 0x0211
[   14.756000] usbcore: registered new interface driver usblp
[   14.756000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   14.756000] usbcore: registered new interface driver hiddev
[   14.760000] input: Logitech USB Receiver as /class/input/input1
[   14.760000] input: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-4
[   14.768000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: Fixing up Logitech keyboard report descriptor
[   14.768000] input: Logitech USB Receiver as /class/input/input2
[   14.768000] input,hiddev96: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-4
[   14.768000] usbcore: registered new interface driver usbhid
[   14.768000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   23.840000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: removed
[31004.704000] usb 2-6: USB disconnect, address 3
[31012.532000] usb 2-7: new full speed USB device using ohci_hcd and address 4
[31012.744000] usb 2-7: configuration #1 chosen from 1 choice
[31012.756000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 3 vid 0x03F0 pid 0x0211

I am running Gutsy, Amd64 5200+ on a Asrock ALiveNF5-eSATA2+ (NVIDIA nForce 520).

How can I fix this?

thanks & regards

Peter

---

### Post by tjbonzo on 2007-12-02
I did:
[INDENT]# mount -t usbfs /dev/bus/usb /proc/bus/usb/[/INDENT]
as per: [http://linux.wordpress.com/2006/05/29/running-vmware-workstation-55-on-suse-101/](http://linux.wordpress.com/2006/05/29/running-vmware-workstation-55-on-suse-101/)
And now have /proc/bus/usb populated. Hope that helps.

---

### Post by fjgaude on 2007-12-02
Read through this post to see the normal way to fix this in VMware. It's a Gutsy issue and not one in Feisty:

[http://ubuntuforums.org/showthread.php?t=626118&highlight=vmware](http://ubuntuforums.org/showthread.php?t=626118&highlight=vmware)

---


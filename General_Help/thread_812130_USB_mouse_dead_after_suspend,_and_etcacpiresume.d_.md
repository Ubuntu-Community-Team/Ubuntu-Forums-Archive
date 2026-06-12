---
title: "USB mouse dead after suspend, and /etc/acpi/resume.d scripts not running"
date: 2008-05-29
forum: General Help
---

### Post by mrowth on 2008-05-29
When I suspend the PC to RAM and wake it up again, the mouse cursor almost always sits frozen in the middle of the (main) screen. 

dmesg deluge:

```
[55644.328000] skge eth0: disabling interface
[55644.416000] uhci_hcd 0000:00:10.3: remove, state 4
[55644.416000] usb usb4: USB disconnect, address 1
[55644.416000] uhci_hcd 0000:00:10.3: USB bus 4 deregistered
[55644.416000] ACPI: PCI interrupt for device 0000:00:10.3 disabled
[55644.416000] uhci_hcd 0000:00:10.2: remove, state 4
[55644.416000] usb usb3: USB disconnect, address 1
[55644.416000] uhci_hcd 0000:00:10.2: USB bus 3 deregistered
[55644.416000] ACPI: PCI interrupt for device 0000:00:10.2 disabled
[55644.416000] uhci_hcd 0000:00:10.1: remove, state 4
[55644.416000] usb usb2: USB disconnect, address 1
[55644.416000] uhci_hcd 0000:00:10.1: USB bus 2 deregistered
[55644.416000] ACPI: PCI interrupt for device 0000:00:10.1 disabled
[55644.416000] uhci_hcd 0000:00:10.0: remove, state 1
[55644.416000] usb usb1: USB disconnect, address 1
[55644.416000] usb 1-2: USB disconnect, address 2
[55644.416000] uhci_hcd 0000:00:10.0: USB bus 1 deregistered
[55644.416000] ACPI: PCI interrupt for device 0000:00:10.0 disabled
[55644.480000] ieee1394: Node removed: ID:BUS[0-00:1023]  GUID[00e0180000c88ca1]
[55644.524000] skge eth0: enabling interface
[55645.304000] PM: Preparing system for mem sleep
[55645.304000] Stopping tasks ... done.
[55645.312000] Suspending console(s)
[55645.312000] msp3400 1-0040: chip reset failed
[55645.312000] usb_device usbdev5.1: PM: suspend 0->2, parent usb5 already 2
[55645.312000] usb_endpoint usbdev5.1_ep81: PM: suspend 0->2, parent 5-0:1.0 already 2
[55645.312000] hub 5-0:1.0: PM: suspend 2->2, parent usb5 already 2
[55645.312000] usb_endpoint usbdev5.1_ep00: PM: suspend 0->2, parent usb5 already 2
[55646.208000] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[55646.720000] pnp: Device 00:0d disabled.
[55646.720000] pnp: Device 00:0b disabled.
[55646.720000] pnp: Device 00:0a disabled.
[55646.720000] NVRM: RmPowerManagement: 3
[55647.016000] ACPI: PCI interrupt for device 0000:00:11.5 disabled
[55647.032000] ACPI: PCI interrupt for device 0000:00:10.4 disabled
[55647.048000] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
[55647.064000] skge eth0: disabling interface
[55647.096000] ACPI: PCI interrupt for device 0000:00:09.0 disabled
[55647.128000] Disabling non-boot CPUs ...
[55647.244000] CPU 1 is now offline
[55647.244000] SMP alternatives: switching to UP code
[55647.244000] CPU1 is down
[55647.244000] PM: Entering mem sleep
[55647.244000] Back to C!
[55647.244000] PCI: enabled onboard AC97/MC97 devices
[55647.244000] PM: Finishing wakeup.
[55647.244000] Enabling non-boot CPUs ...
[55647.244000] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware direc
tly.
[55647.256000] SMP alternatives: switching to SMP code
[55647.256000] Booting processor 1/1 eip 3000
[55647.264000] Initializing CPU#1
[55647.344000] Calibrating delay using timer specific routine.. 4805.98 BogoMIPS (lpj=9611972)
[55647.344000] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00
000003
[55647.344000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[55647.344000] CPU: L2 Cache: 1024K (64 bytes/line)
[55647.344000] CPU 1(2) -> Core 1
[55647.344000] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[55647.344000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ stepping 02
[55647.344000] CPU1 is up
[55647.348000] Switched to high resolution mode on CPU 1
[55647.360000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[55647.360000] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 16 (level, low) -> IRQ 16
[55647.376000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[55647.392000] skge eth0: enabling interface
[55647.392000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 18 (level, low) -> IRQ 20
[55647.392000] bttv0: Can't enable device.
[55647.392000] ACPI: PCI Interrupt 0000:00:0d.1[A] -> GSI 18 (level, low) -> IRQ 20
[55647.408000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 19
[55647.408000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 19
[55647.408000] PM: Writing back config space on device 0000:00:10.0 at offset 1 (was 2100017, writing 2100
013)
[55647.408000] PM: Writing back config space on device 0000:00:10.1 at offset 1 (was 2100017, writing 2100
013)
[55647.408000] PM: Writing back config space on device 0000:00:10.2 at offset 1 (was 2100017, writing 2100
013)
[55647.408000] PM: Writing back config space on device 0000:00:10.3 at offset 1 (was 2100017, writing 2100
013)
[55647.424000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 18
[55647.440000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 21
[55647.440000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[55647.440000] PM: Writing back config space on device 0000:00:11.6 at offset 4 (was 1, writing 1001)
[55647.440000] PM: Writing back config space on device 0000:00:11.6 at offset 1 (was 2100000, writing 2100
001)
[55647.440000] NVRM: RmPowerManagement: 4
[55647.788000] pnp: Failed to activate device 00:03.
[55647.788000] pnp: Device 00:0a activated.
[55647.788000] pnp: Device 00:0b activated.
[55647.788000] pnp: Device 00:0d activated.
[55649.132000] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[55655.532000] ACPI Error (dsopcode-0481): Attempt to CreateField of length zero [20070126]
[55655.532000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.IDEC.RATA] (Node df84e
db0), AE_AML_OPERAND_VALUE
[55655.532000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.IDEC.CHN1.DRV0._GTF] (
Node df84ec18), AE_AML_OPERAND_VALUE
[55655.532000] do_drive_get_GTF: Run _GTF error: status = 0x3006
[55655.544000] usb_endpoint usbdev5.1_ep00: PM: resume from 0, parent usb5 still 2
[55655.544000] usb_endpoint usbdev5.1_ep81: PM: resume from 0, parent 5-0:1.0 still 2
[55655.544000] usb_device usbdev5.1: PM: resume from 0, parent usb5 still 2
[55655.544000] Restarting tasks ... <4>msp3400 1-0040: I/O error #0 (write 0x12/0x00)
[55655.560000] done.
[55655.680000] msp3400 1-0040: I/O error #1 (write 0x12/0x00)
[55655.828000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[f9900000-f99007ff]  Max Packet=[20
48]  IR/IT contexts=[4/8]
[55655.836000] msp3400 1-0040: I/O error #2 (write 0x12/0x00)
[55655.852000] USB Universal Host Controller Interface driver v3.0
[55655.852000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 18
[55655.852000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[55655.852000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[55655.852000] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000d400
[55655.852000] usb usb1: configuration #1 chosen from 1 choice
[55655.852000] hub 1-0:1.0: USB hub found
[55655.852000] hub 1-0:1.0: 2 ports detected
[55655.852000] msp3400 1-0040: giving up, resetting chip. Sound will go off, sorry folks :-|

[snipping many, many repetitions of it giving up on mps3400 - I think it's my ancient Hauppauge WinTV that's also dead after resume]

[55655.956000] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 18
[55655.956000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[55655.956000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[55655.956000] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000d800
[55655.956000] usb usb2: configuration #1 chosen from 1 choice
[55655.956000] hub 2-0:1.0: USB hub found
[55655.956000] hub 2-0:1.0: 2 ports detected
[55656.060000] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 18
[55656.060000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[55656.060000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[55656.060000] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000e000
[55656.060000] usb usb3: configuration #1 chosen from 1 choice
[55656.060000] hub 3-0:1.0: USB hub found
[55656.060000] hub 3-0:1.0: 2 ports detected
[55656.164000] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 18
[55656.164000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[55656.164000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[55656.164000] uhci_hcd 0000:00:10.3: irq 18, io base 0x0000e400
[55656.164000] usb usb4: configuration #1 chosen from 1 choice
[55656.164000] hub 4-0:1.0: USB hub found
[55656.164000] hub 4-0:1.0: 2 ports detected
[55656.332000] skge eth0: disabling interface
[55656.404000] skge eth0: enabling interface
[55658.088000] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
```

When I unplug the Logitech USB wheelmouse and plug it back in, it's back to normal. 

My keyboard isn't USB so I don't know if it would be hit by the same problem.

```
[55789.204000] hub 5-0:1.0: over-current change on port 1
[55789.308000] hub 5-0:1.0: over-current change on port 2
[55789.540000] hub 5-0:1.0: over-current change on port 3
[55789.644000] hub 5-0:1.0: over-current change on port 4
[55789.748000] hub 5-0:1.0: over-current change on port 5
[55789.852000] hub 5-0:1.0: over-current change on port 6
[55789.956000] hub 5-0:1.0: over-current change on port 7
[55790.060000] hub 5-0:1.0: over-current change on port 8
[55791.308000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[55791.484000] usb 1-2: configuration #1 chosen from 1 choice
[55791.500000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input9
[55791.500000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0-2
```

("over-current"...?)

Also: there're some scripts in /etc/acpi/resume.d that aren't ever running (same with the other /etc/acpi/....d directories). Shouldn't they? I want to run some commands on resume (hdparm and such) and maybe something to reinitialise the mouse (*speculation*)

Packages I have installed include: acpid, libapm1 (do I need it?), powermgmt-base, powersaved 

Not apmd, though, as APT wants to uninstall powersaved for it - and without powersaved, I lose the console font and correct keymap after every resume! (I have no real idea how it all interconnects, though I thought APM was superseded by ACPI.)

Still on Gutsy, too many additional issues with Hardy.

---

### Post by mrowth on 2008-05-30
:icon_frown:?

---

### Post by mrowth on 2008-06-03
I may be having too many problems at the same time to sufficiently investigate them before asking for help, but I'm starting to wonder if there's some *other* reason that I'm almost always talking to myself only in these forums.

---

### Post by dps77 on 2008-06-19
I also experience this problem.  It probably happens 1 out of every 10 or so "wake ups" from being suspended, the mouse and keyboard are frozen.  It restart using the power button, and I'm good for a while...:confused:

---

### Post by sdennie on 2008-06-19
/etc/acpi/resume.d no longer works in Hardy.  You will instead have to make much more complicated scripts for the ponderously included pm-utils package and put them in /etc/pm/sleep.d.  A basic framework for the script would look like this:

```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    # Do stuff on hibernate or suspend
;;
    thaw|resume)
    # Do stuff on resume
;;
    *)
;;
esac

exit

```

---


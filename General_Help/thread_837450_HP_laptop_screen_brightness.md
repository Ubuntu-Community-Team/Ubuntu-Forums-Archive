---
title: "HP laptop screen brightness"
date: 2008-06-22
forum: General Help
---

### Post by franky_88 on 2008-06-22
Hello everyone,

I don`t know if this is in the right category but I have a really low screen brightness on my HP pavilion laptop. It is running on the AC power and it used to be more bright than it is right now. I checked in th power management and everything seems fine. I read somewhere about some shortcuts for the brightness ( FN+...) what is FN button??


Thank you for your help,

Franck

---

### Post by danwood76 on 2008-06-22
You might be able to set the LCD brightness with the following command:
```

echo LCD_BRIGHTNESS | sudo dd of=/proc/acpi/video/VGA/LCD/brightness

```
Try setting the LCD_BRIGHTNESS to 100, this should be 100% bright.

Normally you can set what the LCD brightness is within power management, obviously if this isnt working the ACPI for you laptops video may not be working correctly.

---

### Post by franky_88 on 2008-06-22
Hello,


I tried the command you gave me and it gave me this: francis@francis-laptop:~$ echo LCD_BRIGHTNESS | sudo dd of=/proc/acpi/video/VGA/LCD/brightness
sudo: unable to resolve host francis-laptop
dd: writing `/proc/acpi/video/VGA/LCD/brightness': Invalid argument
0+1 records in
0+0 records out
0 bytes (0 B) copied, 0.000396162 s, 0.0 kB/s
francis@francis-laptop:~$ 


What should I do next??


Thank you,

Franck

---

### Post by danwood76 on 2008-06-23
It sounds like the ACPI isnt correctly installed for your laptop.
What is the exact spec of your laptop?

Could you post the output of the following command?
It will just list what exact hardware is inside your laptop.
```

sudo lspci -v

```

---

### Post by franky_88 on 2008-06-23
Here you go: 


francis@francis-laptop:~$ sudo lspci -v
sudo: unable to resolve host francis-laptop
[sudo] password for francis: 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: c4000000-c6ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: Hewlett-Packard Company Unknown device 30cc
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at f8404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00007fff
	Memory behind bridge: f4000000-f7ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f3ffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30cc
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00008000-0000bfff
	Memory behind bridge: bc000000-bfffffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000cbffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30cc
	Capabilities: [a0] Power Management version 2

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: f8000000-f80fffff
	Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
	Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 30cc
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f8404c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
	Memory behind bridge: f8100000-f81fffff
	Capabilities: [50] Subsystem: Hewlett-Packard Company Unknown device 30cc

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 219
	I/O ports at 18d8 [size=8]
	I/O ports at 18cc [size=4]
	I/O ports at 18d0 [size=8]
	I/O ports at 18c8 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f8404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] #12 [0010]

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: medium devsel, IRQ 10
	Memory at 88100000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at c4000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
	Subsystem: Intel Corporation Unknown device 1100
	Flags: bus master, fast devsel, latency 0, IRQ 217
	Memory at f4000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint IRQ 0

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, fast devsel, latency 0, IRQ 218
	I/O ports at c000 [size=256]
	Memory at f8000000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 88000000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Vital Product Data
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] Express Endpoint IRQ 0
	Capabilities: [84] Vendor Specific Information

07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at f8100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [dc] Power Management version 2

07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at f8100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at f8100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cc
	Flags: bus master, medium devsel, latency 32, IRQ 11
	Memory at f8101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2

07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

francis@francis-laptop:~$

---

### Post by franky_88 on 2008-06-27
Okay before this problem errupted on my computer I thought I was okay at handling ubuntu and the occasional problems that came along. I solved the problem by simply right-clicking on my upper panel and then click on add to panel and finally on brightness. I just then solved my screen brightness with this icon. 

Thanks to you all for your help even though it could`ve been solved earlier.


Frank

---


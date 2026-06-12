---
title: "same cards don't work"
date: 2007-05-24
forum: General Help
---

### Post by mapelo on 2007-05-24
Hi everyone:

I do not know why this computer does not work: the problem is:

-If card sound is running a sound, then wireless connections stop. (If my song  finished, then wireless works right)
-If wireless connections are active with transfers, then usb does not work (the printer is on usb port).

I thinked that there was an irq conflict, but this solutions does not work:

-Rotate fisicaly the cards into the PCI slots.
-Configure Bios with  Non-PNP, autoconfigure PCI

Anyone can help me?
Thanks

These are some configurations:

Linux alhambra 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

root@mypc:~# cat /proc/interrupts
           CPU0
  0:   18543652    XT-PIC-XT        timer
  1:         10    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  5:       9542    XT-PIC-XT        VIA686A
  6:          2    XT-PIC-XT        floppy
  7:          1    XT-PIC-XT        acpi
  8:          3    XT-PIC-XT        rtc
 10:     929406    XT-PIC-XT        uhci_hcd:usb1, eth0
 11:    1282765    XT-PIC-XT        eth1
 12:    1008295    XT-PIC-XT        i8042, wifi0
 14:     166158    XT-PIC-XT        ide0
 15:       7876    XT-PIC-XT        ide1
NMI:          0
LOC:          0
ERR:          0
MIS:          0


root@mypc:~# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0a.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Intel Corporation 82740 (i740) AGP Graphics Accelerator (rev 21)



root@mycp:~# lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device e212
        Flags: bus master, medium devsel, latency 8
        Memory at d0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [a0] AGP version 2.0
        Capabilities: [c0] Power Management version 2

00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: d4000000-d5ffffff
        Prefetchable memory behind bridge: d6000000-d6ffffff
        Capabilities: [80] Power Management version 2

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
        Subsystem: VIA Technologies, Inc. VT82C686/A PCI to ISA Bridge
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: [c0] Power Management version 2

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at c000 [size=16]
        Capabilities: [c0] Power Management version 2

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at c400 [size=32]
        Capabilities: [80] Power Management version 2

00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device e212
        Flags: medium devsel, IRQ 7
        Capabilities: [68] Power Management version 2

00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device e212
        Flags: medium devsel, IRQ 5
        I/O ports at cc00 [size=256]
        I/O ports at d000 [size=4]
        I/O ports at d400 [size=4]
        Capabilities: [c0] Power Management version 2

00:0a.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
        Subsystem: D-Link System Inc DWL-520 Wireless PCI Adapter
        Flags: bus master, medium devsel, latency 32, IRQ 12
        Memory at d7000000 (32-bit, prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at dc00 [size=256]
        Memory at d7001000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at e000 [size=256]
        Memory at d7002000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

01:00.0 VGA compatible controller: Intel Corporation 82740 (i740) AGP Graphics Accelerator (rev 21) (prog-if 00 [VGA])
        Subsystem: Intel Corporation Intel740 Graphics Accelerator
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 255
        Memory at d6000000 (32-bit, prefetchable) [size=16M]
        Memory at d5000000 (32-bit, non-prefetchable) [size=512K]
        [virtual] Expansion ROM at d4000000 [disabled] [size=256K]
        Capabilities: [d0] AGP version 1.0
        Capabilities: [dc] Power Management version 1

---

### Post by blazercist on 2007-05-24
try passing acpi=off to the kernel at boot.

---

### Post by mapelo on 2007-05-24
Thanks blazercist,

Inserting acpi=off into /boot/grub/menu.lst 
[...]
kernel          /vmlinuz-2.6.20-15-generic root=UUID=5318d189-4830-48a7-83b2-5b9f4884b186 ro quiet splash acpi=off
[...]

and booting the system, still my problems persist.

Manuel Perez.

---

### Post by mapelo on 2007-05-24
But the interrupts changes:

root@mypc:/# cat /proc/interrupts
           CPU0
  0:     100197    XT-PIC-XT        timer
  1:          2    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  5:       1004    XT-PIC-XT        VIA686A
  6:          2    XT-PIC-XT        floppy
  8:          3    XT-PIC-XT        rtc
 10:         27    XT-PIC-XT        uhci_hcd:usb1, eth0
 11:       2539    XT-PIC-XT        eth1
 12:      53097    XT-PIC-XT        wifi0
 14:       6116    XT-PIC-XT        ide0
 15:        182    XT-PIC-XT        ide1

---

### Post by blazercist on 2007-05-24
well yea ofcourse it changes cuz acpi isnt handling it anymore... Hmm I'm stumped I couldve swore it was Acpi/irq issue but now I'm stumped.

---

### Post by blazercist on 2007-05-24
try turning off apic, and if i remember correctly some motherboards also attempt to handle IRQ assignment themselves instead of leaving it to the system look in bios.

---


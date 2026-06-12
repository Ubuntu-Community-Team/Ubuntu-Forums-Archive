---
title: "Edgy does not respond with USB devices"
date: 2007-02-08
forum: General Help
---

### Post by wersdaluv on 2007-02-08
**The Problem**
Kubuntu/Ubuntu Edgy Eft does not respond whenever I plug a USB device (except for my USB mouse which barely worked).

[B]
The Peripherals I tried[/B]
I have a CD-R King (a brand from the Philippines) USB Mouse. Whenever I plugged it after booting my laptop, Edgy does not respond at all. The mouse lights up so I believe it is properly connected. Whenever it is plugged since my laptop is booted, it works but the mouse pointer responds very very slowly.

I tried my EPSON Stylus C43 UX Printer, Canon PIXMA MP150 Printer/Scanner, Kingston DataTraveller USB Flash drive, Memory Card Reader, and Logitech Quickcam Orbit Webcam; but Ubuntu/Kubuntu Edgy Eft did not respond with any of them.

**The Machine**
I have a Joybook R31E laptop running Kubuntu/Ubuntu Edgy Eft. I believe that it should have worked with my Epson Stylus C43UX Printer since there was a driver available in Edgy by default. As for my Canon PIXMA MP150 and my Logitech Quickcam Orbit Webcam, I still need to hunt for drivers so I do not really expect my machine to work with it well. I am dual-booting this with Windows and all my peripherals work with it so I do not think I am having a USB slot problem.

**What I have tried**
I have tried **lsusb** with my Kingston USB Flash Drive Device and my USB mouse plugged  (I just plugged both of them after booting) and the output was
```
user@Laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```
Note: I don't know if this would be a significant information but it took about 30 seconds for Konsole to show the output of the code

Here is the output of lsusb in the case where I plugged my USB mouse before booting and no other USB device is plugged
```

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 15ca:00c3
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

I have noticed that whenever my USB mouse is the only one plugged and it is plugged since before I booted my laptop, that is the only time when I get an lsusb result with "15ca:00c3"



**Notes**
1. To you who is reading this right now, thank you for your time. :)
2. Please tell me what information I need to add. I will edit this post and put the information that you ask for in this post.

**Edit:**
I just tried my USB Mouse again by plugging it before booting laptop. Before Ubuntu Edgy Eft was loaded  the red light under the mouse (since it is an optical mouse) was lighting up, but for some reason, when Ubuntu was loaded, the red light turned of and of course, the mouse did not work

:guitar:

**Update:**
In this thread, someone suggested to me to use boot arguments such as noacpi. That made my USB work but also stopped my wireless LAN as a side effect. Now, I want to figure out a solution that will enable me to run my wireless LAN and my USB card.

---

### Post by wersdaluv on 2007-02-15
I have reported a bug report on this ( [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/83984](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/83984) ).

It is already confirmed but it still is not assigned to anybody.

If any of you know what I can try to solve this please tell me.

I'm desperate. I need to have those USB devices working. I think, that's the last thing I have to do for me to completely switch to Ubuntu.

---

### Post by charl.ie on 2007-02-15
Whats the output of dmesg?

---

### Post by wersdaluv on 2007-02-25
Sorry for the late reply...

here is the output of dmesg...

```

[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001bfef000 (usable)
[17179569.184000]  BIOS-e820: 000000001bff0000 - 000000001bffffc0 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001bffffc0 - 000000001c000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 447MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 114671
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110575 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 OID_00                                ) @ 0x000e6010
[17179569.184000] ACPI: RSDT (v001 INSYDE FACP_000 0x00000100 0000 0x00010200) @ 0x1bffc280
[17179569.184000] ACPI: FADT (v001 INSYDE FACP_000 0x00000100 0000 0x00010200) @ 0x1bfffb00
[17179569.184000] ACPI: MADT (v001 INSYDE APIC_000 0x30303030 0000 0x00010200) @ 0x1bfffb90
[17179569.184000] ACPI: DSDT (v001 INSYDE    PN800 0x00001000 INTL 0x02002036) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3f80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1492.993 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.220000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.220000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.236000] Memory: 444768k/458684k available (1911k kernel code, 13360k reserved, 1073k data, 308k init, 0k highmem)
[17179569.236000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.316000] Calibrating delay using timer specific routine.. 2989.25 BogoMIPS (lpj=5978515)
[17179569.316000] Security Framework v1.0.0 initialized
[17179569.316000] SELinux:  Disabled at boot.
[17179569.316000] Mount-cache hash table entries: 512
[17179569.316000] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.316000] CPU: After vendor identify, caps: afe9fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179569.316000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.316000] CPU: L2 cache: 1024K
[17179569.316000] CPU: After all inits, caps: afe9fbff 00000000 00000000 00000040 00000000 00000000 00000000
[17179569.316000] Checking 'hlt' instruction... OK.
[17179569.332000] SMP alternatives: switching to UP code
[17179569.332000] Freeing SMP alternatives: 16k freed
[17179569.332000] checking if image is initramfs... it is
[17179569.956000] Freeing initrd memory: 5584k freed
[17179569.956000] ACPI: Core revision 20060707
[17179569.956000] ACPI: Looking for DSDT ... not found!
[17179569.968000] CPU0: Intel(R) Celeron(R) M processor         1.50GHz stepping 08
[17179569.968000] Total of 1 processors activated (2989.25 BogoMIPS).
[17179569.968000] ENABLING IO-APIC IRQs
[17179569.968000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.112000] Brought up 1 CPUs
[17179570.112000] migration_cost=0
[17179570.112000] NET: Registered protocol family 16
[17179570.112000] EISA bus registered
[17179570.112000] ACPI: bus type pci registered
[17179570.112000] PCI: PCI BIOS revision 2.10 entry at 0xe9bf4, last bus=1
[17179570.112000] PCI: Using configuration type 1
[17179570.112000] Setting up standard PCI resources
[17179570.116000] ACPI: Interpreter enabled
[17179570.116000] ACPI: Using IOAPIC for interrupt routing
[17179570.116000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.116000] PCI: Probing PCI hardware (bus 00)
[17179570.116000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179570.116000] PCI quirk: region 1000-107f claimed by vt8235 PM
[17179570.116000] PCI quirk: region 1400-140f claimed by vt8235 SMB
[17179570.116000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179570.116000] Boot video device is 0000:01:00.0
[17179570.116000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.136000] ACPI: Embedded Controller [EC0] (gpe 1) interrupt mode.
[17179570.136000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[17179570.136000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 10 11 14 15)
[17179570.136000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[17179570.136000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 14 15)
[17179570.136000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[17179570.136000] ACPI: PCI Interrupt Link [ALKB] (IRQs 23) *11
[17179570.136000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *5, disabled.
[17179570.136000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd29b4), AE_TYPE
[17179570.136000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179570.136000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179570.136000] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *0
[17179570.136000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.136000] pnp: PnP ACPI init
[17179570.144000] pnp: PnP ACPI: found 9 devices
[17179570.144000] PnPBIOS: Disabled by ACPI PNP
[17179570.144000] PCI: Using ACPI for IRQ routing
[17179570.144000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.144000] PCI: Cannot allocate resource region 0 of device 0000:00:06.0
[17179570.144000] pnp: 00:07: ioport range 0x330-0x331 has been reserved
[17179570.144000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[17179570.144000] pnp: 00:07: ioport range 0x1000-0x107f could not be reserved
[17179570.144000] pnp: 00:07: ioport range 0x1400-0x140f has been reserved
[17179570.144000] PCI: Bridge: 0000:00:01.0
[17179570.144000]   IO window: c000-dfff
[17179570.144000]   MEM window: c0000000-cfffffff
[17179570.144000]   PREFETCH window: 90000000-9fffffff
[17179570.144000] PCI: Bus 2, cardbus bridge: 0000:00:09.0
[17179570.144000]   IO window: 00001800-000018ff
[17179570.144000]   IO window: 00001c00-00001cff
[17179570.144000]   PREFETCH window: 20000000-21ffffff
[17179570.144000]   MEM window: 22000000-23ffffff
[17179570.144000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.144000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179570.144000] NET: Registered protocol family 2
[17179570.180000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.180000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.180000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.180000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.180000] TCP reno registered
[17179570.180000] audit: initializing netlink socket (disabled)
[17179570.180000] audit(1172380383.180:1): initialized
[17179570.180000] VFS: Disk quotas dquot_6.5.1
[17179570.180000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.180000] Initializing Cryptographic API
[17179570.180000] io scheduler noop registered
[17179570.180000] io scheduler anticipatory registered
[17179570.180000] io scheduler deadline registered
[17179570.180000] io scheduler cfq registered (default)
[17179570.180000] isapnp: Scanning for PnP cards...
[17179570.532000] isapnp: No Plug & Play device found
[17179570.568000] Real Time Clock Driver v1.12ac
[17179570.568000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.568000] mice: PS/2 mouse device common for all mice
[17179570.568000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.568000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.568000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.568000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.580000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179570.588000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179570.588000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179570.588000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179570.588000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179570.588000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.592000] EISA: Probing bus 0 at eisa.0
[17179570.592000] Cannot allocate resource for EISA slot 1
[17179570.592000] EISA: Detected 0 cards.
[17179570.592000] TCP bic registered
[17179570.592000] NET: Registered protocol family 1
[17179570.592000] NET: Registered protocol family 8
[17179570.592000] NET: Registered protocol family 20
[17179570.592000] Using IPI No-Shortcut mode
[17179570.592000] ACPI: (supports S0 S1 S3 S4 S5)
[17179570.592000] Freeing unused kernel memory: 308k freed
[17179570.616000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.720000] Capability LSM initialized
[17179571.752000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179571.752000] ACPI: Processor [CPU0] (supports 16 throttling states)
[17179571.760000] ACPI: Thermal Zone [TZ0] (66 C)
[17179572.080000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179572.080000] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[17179572.080000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[17179572.080000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179572.080000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 177
[17179572.080000] PCI: Via IRQ fixup for 0000:00:11.1, from 0 to 1
[17179572.080000] VP_IDE: chipset revision 6
[17179572.080000] VP_IDE: not 100% native mode: will probe irqs later
[17179572.080000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179572.080000]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
[17179572.080000]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:DMA, hdd:pio
[17179572.080000] Probing IDE interface ide0...
[17179572.500000] hda: FUJITSU MHV2060AT PL, ATA DISK drive
[17179573.176000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.252000] Probing IDE interface ide1...
[17179574.116000] hdc: PHILIPS CD-RW/DVD-ROM SCB5265, ATAPI CD/DVD-ROM drive
[17179574.788000] ide1 at 0x170-0x177,0x376 on irq 15
[17179574.792000] hda: max request size: 128KiB
[17179574.792000] hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[17179574.800000] hda: cache flushes supported
[17179574.800000]  hda: hda1 hda2 hda3 < hda5 > hda4
[17179574.868000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179574.868000] Uniform CD-ROM driver Revision: 3.20
[17179575.232000] usbcore: registered new driver usbfs
[17179575.232000] usbcore: registered new driver hub
[17179575.236000] USB Universal Host Controller Interface driver v3.0
[17179575.236000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd29b4), AE_TYPE
[17179575.236000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179575.236000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179575.236000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179575.236000] ACPI: Invalid IRQ link routing entry
[17179575.236000] ACPI: Unable to derive IRQ for device 0000:00:10.0
[17179575.236000] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI - using IRQ 11
[17179575.236000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179575.236000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179575.236000] uhci_hcd 0000:00:10.0: irq 11, io base 0x00001200
[17179575.236000] usb usb1: configuration #1 chosen from 1 choice
[17179575.236000] hub 1-0:1.0: USB hub found
[17179575.236000] hub 1-0:1.0: 2 ports detected
[17179575.340000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd29b4), AE_TYPE
[17179575.340000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179575.340000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179575.340000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179575.340000] ACPI: Invalid IRQ link routing entry
[17179575.340000] ACPI: Unable to derive IRQ for device 0000:00:10.1
[17179575.340000] ACPI: PCI Interrupt 0000:00:10.1[B]: no GSI - using IRQ 7
[17179575.340000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179575.340000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179575.340000] uhci_hcd 0000:00:10.1: irq 7, io base 0x00001220
[17179575.340000] usb usb2: configuration #1 chosen from 1 choice
[17179575.340000] hub 2-0:1.0: USB hub found
[17179575.340000] hub 2-0:1.0: 2 ports detected
[17179575.444000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd29b4), AE_TYPE
[17179575.444000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179575.444000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179575.444000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179575.444000] ACPI: Invalid IRQ link routing entry
[17179575.444000] ACPI: Unable to derive IRQ for device 0000:00:10.2
[17179575.444000] ACPI: PCI Interrupt 0000:00:10.2[C]: no GSI - using IRQ 5
[17179575.444000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179575.444000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179575.444000] uhci_hcd 0000:00:10.2: irq 5, io base 0x00001240
[17179575.444000] usb usb3: configuration #1 chosen from 1 choice
[17179575.444000] hub 3-0:1.0: USB hub found
[17179575.444000] hub 3-0:1.0: 2 ports detected
[17179575.556000] PCI: Enabling device 0000:00:10.3 (0000 -> 0002)
[17179575.556000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd29b4), AE_TYPE
[17179575.556000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179575.556000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179575.556000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179575.556000] ACPI: Invalid IRQ link routing entry
[17179575.556000] ACPI: Unable to derive IRQ for device 0000:00:10.3
[17179575.556000] ACPI: PCI Interrupt 0000:00:10.3[D]: no GSI - using IRQ 10
[17179575.556000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179575.556000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179575.556000] ehci_hcd 0000:00:10.3: irq 10, io mem 0x24003000
[17179575.556000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.556000] usb usb4: configuration #1 chosen from 1 choice
[17179575.556000] hub 4-0:1.0: USB hub found
[17179575.556000] hub 4-0:1.0: 6 ports detected
[17179575.684000] Attempting manual resume
[17179575.720000] kjournald starting.  Commit interval 5 seconds
[17179575.720000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.292000] hub 4-0:1.0: over-current change on port 5
[17179576.692000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179579.224000] usb 2-1: configuration #1 chosen from 1 choice
[17179588.572000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179588.572000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 11, using IRQ 23
[17179588.572000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 23
[17179588.572000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKB] -> GSI 23 (level, low) -> IRQ 185
[17179588.572000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 9
[17179588.576000] eth0: VIA Rhine II at 0x1e200, 00:40:d0:84:06:a9, IRQ 185.
[17179588.576000] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[17179588.648000] PCI: Enabling device 0000:00:06.0 (0000 -> 0002)
[17179588.648000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 193
[17179588.648000] rt2500 1.1.0 BETA4 2006/06/18 http://rt2x00.serialmonkey.com
[17179588.648000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179588.744000] irda_init()
[17179588.744000] NET: Registered protocol family 23
[17179588.884000] eth0: link down
[17179588.984000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[17179588.984000] rt2500 EEPROM:  2  2  2  2  2  2  2  2  2  2  2  2  2  2  dBm Maximum
[17179589.004000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.008000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.668000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.840000] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[17179589.848000] agpgart: AGP aperture is 128M @ 0xa0000000
[17179589.928000] input: PC Speaker as /class/input/input1
[17179590.016000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179590.016000] Yenta: CardBus bridge found at 0000:00:09.0 [1071:8666]
[17179590.016000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179590.016000] Yenta: Routing CardBus interrupts to PCI
[17179590.016000] Yenta TI: socket 0000:00:09.0, mfunc 0x01001002, devctl 0x44
[17179590.216000] NET: Registered protocol family 17
[17179590.276000] Yenta: ISA IRQ mask 0x0058, PCI irq 169
[17179590.276000] Socket status: 30000006
[17179590.276000] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
[17179590.276000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 5, using IRQ 22
[17179590.276000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179590.276000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179590.276000] PCI: Via IRQ fixup for 0000:00:11.6, from 5 to 9
[17179590.280000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[17179590.304000] usbcore: registered new driver hiddev
[17179590.384000] ACPI: query EC, OB not full
[17179590.592000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa56eb1, caps: 0x804713/0x0
[17179590.648000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179590.688000] ts: Compaq touchscreen protocol output
[17179590.796000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179590.796000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 9
[17179590.796000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179590.816000] input: USB Optical Mouse as /class/input/input3
[17179590.816000] input: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:10.1-1
[17179590.816000] usbcore: registered new driver usbhid
[17179590.816000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179591.204000] cs: IO port probe 0x100-0x3af: clean.
[17179591.204000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179591.208000] cs: IO port probe 0x820-0x8ff: clean.
[17179591.208000] cs: IO port probe 0xc00-0xcf7: clean.
[17179591.208000] cs: IO port probe 0xa00-0xaff: clean.
[17179591.464000] lp: driver loaded but no devices found
[17179591.524000] Adding 1317288k swap on /dev/disk/by-uuid/f0702c1a-f7ca-4bca-a436-7a346cb46212.  Priority:-1 extents:1 across:1317288k
[17179591.600000] EXT3 FS on hda1, internal journal
[17179592.200000] NET: Registered protocol family 10
[17179592.200000] lo: Disabled Privacy Extensions
[17179592.200000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179592.200000] IPv6 over IPv4 tunneling driver
[17179595.444000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179597.556000] ACPI: AC Adapter [AC] (off-line)
[17179597.720000] ACPI: Battery Slot [BAT0] (battery present)
[17179597.740000] ACPI: Power Button (FF) [PWRF]
[17179597.740000] ACPI: Lid Switch [LID]
[17179597.740000] ACPI: Sleep Button (CM) [SBTN]
[17179597.740000] ACPI: Power Button (CM) [PBTN]
[17179597.852000] ibm_acpi: ec object not found
[17179597.880000] pcc_acpi: loading...
[17179598.028000] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[17179600.876000] [drm] Initialized drm 1.0.1 20051102
[17179601.384000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 209
[17179601.384000] PCI: Via IRQ fixup for 0000:01:00.0, from 11 to 1
[17179601.384000] [drm] Initialized via 2.7.4 20051116 on minor 0
[17179601.436000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179601.436000] agpgart: Device is in legacy mode, falling back to 2.x
[17179601.436000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[17179601.440000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[17179601.776000] uhci_hcd 0000:00:10.1: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[17179602.272000] apm: BIOS not found.
[17179602.356000] ra0: no IPv6 routers present
[17179615.100000] Bluetooth: Core ver 2.8
[17179615.100000] NET: Registered protocol family 31
[17179615.100000] Bluetooth: HCI device and connection manager initialized
[17179615.100000] Bluetooth: HCI socket layer initialized
[17179615.488000] Bluetooth: L2CAP ver 2.8
[17179615.488000] Bluetooth: L2CAP socket layer initialized
[17179615.508000] Bluetooth: RFCOMM socket layer initialized
[17179615.508000] Bluetooth: RFCOMM TTY layer initialized
[17179615.508000] Bluetooth: RFCOMM ver 1.7

```

---

### Post by Koybe on 2007-02-25
Could you try booting with noapic and/or pci=nopaci.

You can have a try without modifying your existing config by pushing 'e' on the grub menu the modify the line with the kernel by pushing again 'e', when you'r finished press 'b' to boot with the option.

---

### Post by wersdaluv on 2007-02-25
> **Koybe said:**
> Could you try booting with noapic and/or pci=nopaci.

You can have a try without modifying your existing config by pushing 'e' on the grub menu the modify the line with the kernel by pushing again 'e', when you'r finished press 'b' to boot with the option.

I'm sorry but I am unfamiliar with that and can hardly relate.

May I know what noapic and pci=noapic are?

I understood the pushing 'e' on the grup menu part, but how do I modify the line with the kernel?

By the way, thank you so much for the reply!

---

### Post by Koybe on 2007-02-25
It deals with the way your kernel is handling you material. I'm not expert enough to tell you more.

What you have to do when grub menu loads :
- Hit 'e', it will show you the configuration for this booting option.
- Move to the kernel line with the arrows. It should look like this : 
kernel          /vmlinuz-2.6.15-28-k7 root=/dev/mapper/vghda6-lvslash ro vga=791 quiet splash
- Hit 'e' once again and add the option to this line :
kernel          /vmlinuz-2.6.15-28-k7 root=/dev/mapper/vghda6-lvslash ro vga=791 quiet splash noapic
- Hit 'enter', it should show you back the whole config with your modification for this boot only
- Hit 'b' to boot using this configuraiton

If it works then you can set it permanently to your /boot/grub/menu.lst but it's better this way for testing purpose.

Here are some parameters dealing with the way it handles hardware... but maybe someone else can give more informations about these :
[B]- noapic 
- nolapic 
- acpi=off 
- pci=noacpi

[/B]

---

### Post by wersdaluv on 2007-02-25
> **Koybe said:**
> It deals with the way your kernel is handling you material. I'm not expert enough to tell you more.

What you have to do when grub menu loads :
- Hit 'e', it will show you the configuration for this booting option.
- Move to the kernel line with the arrows. It should look like this : 
kernel          /vmlinuz-2.6.15-28-k7 root=/dev/mapper/vghda6-lvslash ro vga=791 quiet splash
- Hit 'e' once again and add the option to this line :
kernel          /vmlinuz-2.6.15-28-k7 root=/dev/mapper/vghda6-lvslash ro vga=791 quiet splash noapic
- Hit 'enter', it should show you back the whole config with your modification for this boot only
- Hit 'b' to boot using this configuraiton

If it works then you can set it permanently to your /boot/grub/menu.lst but it's better this way for testing purpose.

Here are some parameters dealing with the way it handles hardware... but maybe someone else can give more informations about these :
[B]- noapic 
- nolapic 
- acpi=off 
- pci=noacpi

[/B]

Oh my gosh! It worked!

You fcking changed my life!

Thank you very much!

Just one thing... if I boot using noapic, I am unable to use my wireless lan. It is disabled. Do you know what I can do to fix this?

---

### Post by Koybe on 2007-02-25
Nice. Don't forget then to change your grub.conf, because what we made will only work for booting once :

```
sudo gedit /boot/grub/menu.lst
```Go to this line :
```
# kopt=root=/dev/mapper/vghda6-lvslash ro 
```And change it to :
```
# kopt=root=/dev/mapper/vghda6-lvslash ro noapic
```Then save and run grub update :
```
sudo update-grub
```This will automaticaly change all the lines and change also for any future kernel upgrade.

Then we get into another problem :( The wireless connection. I'm not very used to this. What is you wirelesse network card? Maybe you another now another module to get it worked.

---

### Post by wersdaluv on 2007-02-25
I do not know what the name of my wireless card is but according to BenQ's site, my laptop has Wireless 802.11b/g.

What I have tried is to enable wireless network device in the "Network Settings" in Kubuntu, but it  doesn't work. My laptop has this LED that indicates if my wireless is on or not. That LED is turned off under noapic so I tried to press Fn+F1 which is designed to turn the wireless on and off.

---

### Post by Koybe on 2007-02-25
I've found this in your launchpad entry :
> Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
        Subsystem: RaLink Unknown device 2560
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 193
        Region 0: Memory at 24000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME- Then if you search this forum for RaLink RT2500 you should find some posts and maybe some help :)

---

### Post by esaym on 2007-02-25
It kinda looks like the usb controller is the problem.  If you have pcmcia slots you might be able to buy a usb card

Edit:
Yea it really looks like the compnay that makes the laptop put a cheesy usb controller in it: [http://www.linuxquestions.org/questions/showthread.php?t=348987](http://www.linuxquestions.org/questions/showthread.php?t=348987) What a shame.

Also try updating your bios and also file a complaint with the laptop manufacture if that doesn't work.

---

### Post by wersdaluv on 2007-02-25
> **esaym said:**
> It kinda looks like the usb controller is the problem.  If you have pcmcia slots you might be able to buy a usb card

Edit:
Yea it really looks like the compnay that makes the laptop put a cheesy usb controller in it: [http://www.linuxquestions.org/questions/showthread.php?t=348987](http://www.linuxquestions.org/questions/showthread.php?t=348987) What a shame.

Also try updating your bios and also file a complaint with the laptop manufacture if that doesn't work.

That's a nice link. So I am not alone here ei?

Guys, how do I boot so that my USB and Wireless LAN will work?

---

### Post by wersdaluv on 2007-02-25
Do you think that using another distro will solve this kind of problem? I've been waiting for PCLinuxOS 2007's final release and am not sure if it will solve my problem.

---

### Post by muguwmp67 on 2007-02-25
Here is a page discussing installation of Ubuntu on a joybook.  It looks like a good reference work for you.

[http://www.cancullet.org/benqjb7000/BenqJB7000_linux.html]("http://www.cancullet.org/benqjb7000/BenqJB7000_linux.html")

---

### Post by wersdaluv on 2007-02-25
I think, the best thing I can do now is to buy a pcmcia USB controller or a pcmcia wireless LAN.

What do you think?

It's just that, it would be frustrating for me to see a pcmcia device considering that I have the built-in devices. Ohhh... I guess I have to do it if this problem really is impossible to fix.

---

### Post by AndyCooll on 2007-02-25
As has been indicated it does look like you have USB controller issue. For I know that your "Kingston DataTraveller USB Flash drive" should work out-of-the-box since I have one too and it "just works".

:cool:

---

### Post by esaym on 2007-02-26
> **wersdaluv said:**
> I think, the best thing I can do now is to buy a pcmcia USB controller or a pcmcia wireless LAN.

What do you think?

It's just that, it would be frustrating for me to see a pcmcia device considering that I have the built-in devices. Ohhh... I guess I have to do it if this problem really is impossible to fix.

You should have a mini-pci slot for your wireless card.  No need to buy a bulky pcmcia card for wireless. [http://www.netgate.com/product_info.php?cPath=26_34&products_id=126](http://www.netgate.com/product_info.php?cPath=26_34&products_id=126)

For some reason I though you had your wireless working though?  What does  ```
lspci
``` say your wireless controller is?

You might also want to try the latest feisty live cd.  Alot has changed with this latest feisty release..

---

### Post by wersdaluv on 2007-02-27
> **esaym said:**
> You should have a mini-pci slot for your wireless card.  No need to buy a bulky pcmcia card for wireless. [http://www.netgate.com/product_info.php?cPath=26_34&products_id=126](http://www.netgate.com/product_info.php?cPath=26_34&products_id=126)

For some reason I though you had your wireless working though?  What does  ```
lspci
``` say your wireless controller is?

You might also want to try the latest feisty live cd.  Alot has changed with this latest feisty release..

Here is my lspci
```
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)

```

> **esaym said:**
> For some reason I though you had your wireless working though?

Wireless works without booting parameters. With booting parameters like noacpi, wireless doesn't work but USB does.

> **esaym said:**
> You might also want to try the latest feisty live cd.  Alot has changed with this latest feisty release..

Just tried Herd 4 and still doesn't work.

---

### Post by dustman on 2007-02-27
I have a similar problem, but the thing is that in my case the USB mouse does not work :| ( I have installed Ubuntu 6.10 Edgy Eft)...well, it works just fine...for about 3 minutes, then it suddenly stops moving :P. If I plug it out and then plug it back in, it won't light! ( I have a Logitech USB Mouse that lights up when it's plugged in) . My mouse worked fine in Suse 9.3, Ubuntu 6.06, Fedora Core 5 and 6, even in PC BSD(which has a major laptop driver issue..:( ) . It's funny because my TouchPad works fine, but my mouse ain't...

Cheers!

---

### Post by wersdaluv on 2007-02-27
> **wersdaluv said:**
> [B]
I have a CD-R King (a brand from the Philippines) USB Mouse. Whenever I plugged it after booting my laptop, Edgy does not respond at all. The mouse lights up so I believe it is properly connected. Whenever it is plugged since my laptop is booted, it works but the mouse pointer responds very very slowly.

> **wersdaluv said:**
> **Edit:**
I just tried my USB Mouse again by plugging it before booting laptop. Before Ubuntu Edgy Eft was loaded  the red light under the mouse (since it is an optical mouse) was lighting up, but for some reason, when Ubuntu was loaded, the red light turned of and of course, the mouse did not work


Before, I have noticed that, whenever I plug my USB mouse since before I boot my computer, it partially worked. Whenever I plug my USB mouse together with another USB device since before I boot my computer, the USB mouse wont work at all. (Those are in the case of having no PCI arguments like **noacpi**)

In Feisty Herd 4, even if I plug my USB mouse together with another peripheral (with no PCI argument), my mouse partially worked (mouse pointer reacted very slowly). 

So there is a difference between Edgy's and Feisty Herd 4's reactions. What do you think does that imply?

---

### Post by HasratUSA on 2007-02-28
> **esaym said:**
> It kinda looks like the usb controller is the problem.  If you have pcmcia slots you might be able to buy a usb card

Edit:
Yea it really looks like the compnay that makes the laptop put a cheesy usb controller in it: [http://www.linuxquestions.org/questions/showthread.php?t=348987](http://www.linuxquestions.org/questions/showthread.php?t=348987) What a shame.

Also try updating your bios and also file a complaint with the laptop manufacture if that doesn't work.

downloading the bios upgrade tool from my manufacturer, which is dell, and using it to upgrade the bios instantly solved all my weird problems with USB devices!

---

### Post by dustman on 2007-02-28
Hi

I solved the USB mouse problem....By chance I installed the newest ATI driver for my graphics card, then I installed Beryl with XGL, and it works perfectly....Dunno why with plain GNOME it didn't work, but this solution worked fine for me :D 


Cheers

---

### Post by wersdaluv on 2007-02-28
> **HasratUSA said:**
> downloading the bios upgrade tool from my manufacturer, which is dell, and using it to upgrade the bios instantly solved all my weird problems with USB devices!

Hmmmm... good idea.

I'll hunt for the BIOS upgrade

---

### Post by wersdaluv on 2007-03-01
Updated my BIOS but usb still didn't work.

---

### Post by dustman on 2007-03-02
Well, I reinstalled Ubuntu and Beryl and the mouse did not work again, so I asked a teacher from my school to solve my USB problem.....he tried for about 2 hours with no success :(....so....I guess I will change my distro....I'm sorry about Ubuntu, cause it's great, but I cannot do almost anything without my mouse. If someone will post an answer for this problem, perhaps I will switch back to Ubuntu, but till then...Good Bye!

---

### Post by HasratUSA on 2007-03-02
> **dustman said:**
> Well, I reinstalled Ubuntu and Beryl and the mouse did not work again, so I asked a teacher from my school to solve my USB problem.....he tried for about 2 hours with no success :(....so....I guess I will change my distro....I'm sorry about Ubuntu, cause it's great, but I cannot do almost anything without my mouse. If someone will post an answer for this problem, perhaps I will switch back to Ubuntu, but till then...Good Bye!

Wait a second! What's the name of your distribution? (edgy? dapper? which one?) what kinda mouse is this? is it an USB or ps/2? do you have a ibm pentium or AMD 64 or AMD 64 dual core? who is your PC's manufacturer?

After installation and when Ubuntu boots up, do you observe that the mouse stalls/hangs frequently? or does the mouse stop working before, during or after the installation? Tell us the complete name of the mouse as well as its manufacturer.

I will try my best to help you out. I have been through similar situation during my first introduction to Ubuntu.

---

### Post by dustman on 2007-03-03
Man, thanks for your intention, but i've searched almost everywhere but I did not find an answer to my problem. I had installed Ubuntu 6.10 Edgy Eft on 32 bit, on my Toshiba Satellite A100-529 notebook. It has a ATI Radeon XPress 200M, and the mouse worked during the install, and even for about 20 seconds after rebooting. My mouse is an optical USB Logitech Mouse ( but i dunno exactly what model....On the mouse is written: "Premium Optical, Wheel Mouse, M/N: M-BT58, P/N: 831116-0000, maybe it helps at something). Then, after 20-30 seconds from the time I rebooted and logged in, it stopped working. The light in the mouse kept on going, but no motion at all. When I plugged out the mouse(so the light turned off) and plugged it back in, the light did not appear again. I did not have any problem with my mouse on Ubuntu  6.06, Fedora Core 5 and 6, PC-BSD(even if it has a big hardware drivers problem), SUSE 9.3. 

This is the second time I have installed Edgy Eft. During the first install, I've noticed that the mouse did not work even during the installation, only for about the same 20-30 seconds. After I logged in, for the same period of time the mouse worked, and then it stalled. After I installed the newest ATI driver for my graphics card, and after I got Beryl working, when I logged to the XGL session the mouse worked perfectly fine( PURE LUCK i guess) , but if I tried to log in just plain GNOME, the mouse stalled again after the same 20-30 seconds. But now I reinstalled Ubuntu and the ATI driver and Beryl and the mouse doesn't work, only for about, I think you already guessed...YES...20-30 seconds from the time the graphic interface gets loaded...I don't know why it does this, and even I tried to find answers, I didn't find one. As I said, I asked a teacher at school to try to solve this problem(i study at a Computer Science University), and he tried, but without any success at all.... I think I'll just wait till Linux will provide better systems without so many issues (especially on notebooks ) . I like Ubuntu, it's great, but I have a lot of work to do for school, and I cannot do everything by just using the keyboard. Anyway, thanks for your post...it kinda grew up my moral. 


Cheers!

Radu

---

### Post by francesco44 on 2007-03-03
I have posted something yesterday about this. Some USB devices definetely do not work under Edgy (a wireless mouse, a USB Key with U3, a little USB HD-4 Go) All these work perfectly under Dapper.

The problems seems important enough, as you can find many messages about that **to justify an update**. Before submitting that as a bug myself I would like to know if somebody from the dev teams has something to say about it.

Of course I will try the advices of the previous messages!

Many thanks to all

---

### Post by HasratUSA on 2007-03-03
> **dustman said:**
> Man, thanks for your intention, but i've searched almost everywhere but I did not find an answer to my problem. I had installed Ubuntu 6.10 Edgy Eft on 32 bit, on my Toshiba Satellite A100-529 notebook. It has a ATI Radeon XPress 200M, and the mouse worked during the install, and even for about 20 seconds after rebooting. My mouse is an optical USB Logitech Mouse ( but i dunno exactly what model....On the mouse is written: "Premium Optical, Wheel Mouse, M/N: M-BT58, P/N: 831116-0000, maybe it helps at something). Then, after 20-30 seconds from the time I rebooted and logged in, it stopped working. The light in the mouse kept on going, but no motion at all. When I plugged out the mouse(so the light turned off) and plugged it back in, the light did not appear again. I did not have any problem with my mouse on Ubuntu  6.06, Fedora Core 5 and 6, PC-BSD(even if it has a big hardware drivers problem), SUSE 9.3. 

This is the second time I have installed Edgy Eft. During the first install, I've noticed that the mouse did not work even during the installation, only for about the same 20-30 seconds. After I logged in, for the same period of time the mouse worked, and then it stalled. After I installed the newest ATI driver for my graphics card, and after I got Beryl working, when I logged to the XGL session the mouse worked perfectly fine( PURE LUCK i guess) , but if I tried to log in just plain GNOME, the mouse stalled again after the same 20-30 seconds. But now I reinstalled Ubuntu and the ATI driver and Beryl and the mouse doesn't work, only for about, I think you already guessed...YES...20-30 seconds from the time the graphic interface gets loaded...I don't know why it does this, and even I tried to find answers, I didn't find one. As I said, I asked a teacher at school to try to solve this problem(i study at a Computer Science University), and he tried, but without any success at all.... I think I'll just wait till Linux will provide better systems without so many issues (especially on notebooks ) . I like Ubuntu, it's great, but I have a lot of work to do for school, and I cannot do everything by just using the keyboard. Anyway, thanks for your post...it kinda grew up my moral. 


Cheers!

Radu

go to toshiba's website and visit their support/update/upgrade/download section and see if they have any update or upgrade files available for your Toshiba Satellite A100-529's bios. if they have, install them ASAP.

also you can find out the current version of your bios and see in toshiba's official website if they have a newer version of it. if they have,  upgrade your bios with your eyes closed.

but remember to always check for these updates for your laptop from toshiba's official sites only.

---

### Post by dustman on 2007-03-04
Thanks for the tip :D! The thing is that I switched back to FC6, cause everything works there. I had loads of trouble getting my LinuxDCPP to work on Ubuntu 6.06, and never succeeded properly :( . I posted on this forum about my problem, but got no response( at that time ). I use LinuxDCPP daily, and I had to have it going; that's why I installed FC6, and it worked great there. I'm not a Linux veteran, so when I tried to install a new Kernel and the newest graphics card drivers, to make XGL work on Fedora, I did something wrong and I lost my dual boot Fedora with Windows XP. So I installed Ubuntu 6.10, but as I said the mouse didn't work, so I reinstalled FC6. I'm not sure that if I make that BIOS upgrade, then the mouse will work, and I am reluctant about this upgrade, because I fear that Windows won't work. Anyway....thanks for your help. I think that I'll wait for a stable release of Feisty Fawn, and give it a try. 

Cheers!

Radu

---

### Post by HasratUSA on 2007-03-04
> **dustman said:**
> Thanks for the tip :D! The thing is that I switched back to FC6, cause everything works there. I had loads of trouble getting my LinuxDCPP to work on Ubuntu 6.06, and never succeeded properly :( . I posted on this forum about my problem, but got no response( at that time ). I use LinuxDCPP daily, and I had to have it going; that's why I installed FC6, and it worked great there. I'm not a Linux veteran, so when I tried to install a new Kernel and the newest graphics card drivers, to make XGL work on Fedora, I did something wrong and I lost my dual boot Fedora with Windows XP. So I installed Ubuntu 6.10, but as I said the mouse didn't work, so I reinstalled FC6. I'm not sure that if I make that BIOS upgrade, then the mouse will work, and I am reluctant about this upgrade, because I fear that Windows won't work. Anyway....thanks for your help. I think that I'll wait for a stable release of Feisty Fawn, and give it a try. 

Cheers!

Radu

After you do the bios/flashbios upgrade, nothing bad would happen to either your computer or its operating systems. Allow me to let you in on something. This 'mouse doesn't work', 'no USB devices work' and etc etc are serious issues undeniably, but every problem has an unique solution as well. 

My newly bought PC is a dell dimension e521 AMD ATHLON 64 bit dual core 3800+ and the M$'s crappy propaganda OS that came with it (sorry I don't remember its name anymore, nor do I want to) worked fine.

When I decided to switch to Ubuntu GNU/Linux, I used the live CD to start the installation and ever since then, after every 4-5 minutes, the mouse stalled. when it stalled, it didn't do anything and just sat there. The light was on but the cursor didn't move. This continued to happen for like 5 days and everytime it crashed, I had to unplug and replug the USB cable.

Then I simply searched in Google for problems related to USB devices in GNU/Linux on Dell Dimension PCs and walla! In Dell's alternative OS's support forum, more than 200 people were complaining about the same issue. Many of them even threatened to sue dell because dell earlier promised to many of these customers that linux-based OSs would run fine if the user chose not to use XP, which came with it by default. 

After confronting huge pressure, Dell finally released a Bios upgrade, the users as well as me did the upgrade and it was all GONE!

[http://linux-blog.org/index.php?/archives/180-Dell-E521,-Linux,-Freezing-USB-Mouse-Problem-Resolved.html](http://linux-blog.org/index.php?/archives/180-Dell-E521,-Linux,-Freezing-USB-Mouse-Problem-Resolved.html)

Anyways I want to wish you goodluck with your quest. Feel free to try doing the upgrade because I can personally assure you that nothing harmful would take place. Even if you have already switched to Fedora Core 6, give it some time, relax, then come back after a day or two and do the upgrade and reinstallation.

However, Feisty is coming in April and it would be really better if you don't touch your box at all for the moment being. I really pray and hope that most of the annoying issues that we have faced in Edgy Edt would be fixed in this upgrade, in which case you wouldn't even need to do the bios upgrade. You better wait a little more

---

### Post by map on 2007-03-13
hope somebody's still looking at this thread since i can 'one-down' the original poster: i found the thread because after doing a reinstall of 6.10 on a lenovo 3000 n100 ['vistastation 1' for reasons too involved to go into here] in hopes of gettng a clean start on trying to get wireless working, i discovered that my usb mouse [and usb keyboard] were no longer working.  that's no longer working, as in they worked on the same system [hardware and software] before the reinstall.

since i didn't want to inflict html on people and can't do italics/bold/underline without figuring out where i turned 'em off, i'll say it again 'loudly': 

USB MOUSE AND USB KEYBOARD DON'T WORK AFTER CLEAN REINSTALL OF 6.10.

they worked only an hour or three before when i used 6.10 to re-burn the iso disc for the reinstallation [don't ask; the house ate the other one], be it noted.

so if anybody sees this and has a solution that doesn't involve bioses, or anything to do with the hardware [other than an easy test for detecting that a bus failed between x p.m. and x+3 p.m.], please let me know by direct netmail, as we called it when we were inventing it, at firstmap [at] yahoo.com, because i find waving ickons [sic] off to right extremely annoying and can't be bothered to waste the time figuring out how to make 'em go away, so i really don't want to have to come back to the forum to learn the answer ... if there is one.

thanks,
and cheers,
map

---

### Post by wersdaluv on 2007-03-18
My problem is solved! All I had to do was to use irqpoll as a boot option! 

:guitar:

---

### Post by sblanzio on 2007-03-29
could you please tell us exactly what you did? thanks!!

---

### Post by sxp on 2007-03-30
I have had a different problem with my Dapper install.  I never had a problem with USB devices - but now all four ports are unrecognised.  Mine is a desktop and has been working with a Canon inkjet, a flash drive, 2 iPods, and a Canon A510.  This morning all of a sudden after a fresh power up, nothing has been working.

---

### Post by HasratUSA on 2007-03-30
what exactly did you do to your system before 'this morning' ?

---

### Post by sxp on 2007-03-31
I had a problem with bringing up X last Monday which is since solved.  But I boted up from recovery and went for kernal 2.6.  could that be a problem?

---

### Post by sxp on 2007-03-31
OK I went into recovery mode at booting and started up using V 2.6.15-28-386.  Shd I try going back to 2.4 V which is where I originally was?

---

### Post by HasratUSA on 2007-03-31
Hmm may be you're not using Edgy. I'm, and my current super-stable ultrafast kernel is 2.6.17-11 and I don't have a single problem with the current set-up. Well I would suggest that you let go of whatever you have (but not before making complete back-up of your important data) and then find for yourself an Edgy eft iso of either Ubuntu or Kubuntu and reinstall it. After installation, edgy would automatically upgrade the kernel to 2.6.17-11 (stable)

Edit: Oh now I realize that you have been using Dapper! Um if you like it, then I don't know what to say. If you don't, you could give Edgy Eft a try. It's gonna stay alive until March 2008 anyways

---

### Post by sxp on 2007-04-01
thanks let me try that route.

---

### Post by mvaranda on 2007-04-02
Works for Toshiba (I got from another link which I can not remember):

# At first, the USB mouse (and presumably other USB devices) didn't work. It locked up and I was left with only the touch pad for moving the pointer around (and I haaate the touch pad). I fixed this by adding the red text to the following line in /boot/grub/menu.lst:

    * kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda7 ro quiet splash [COLOR="Red"]noapic irqpoll pci=routeirq[/COLOR]

(Note that you will likely have to do this each time a new kernel is installed, because the menu.lst file gets overwritten.)

---

### Post by dustman on 2007-04-03
Hi....I had some time ago a similar problem, but managed recently to solve it. My mouse did not work( well, it worked for about 30 seconds and then total silence ) , so I modified the /boot/grub/menu.lst, and added "noapic irqpoll" there at the kernel boot options. It works like a dream.


P.S. Adding just "irqpoll" didn't work for me.

---


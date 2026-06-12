---
title: "laptop heat issues again - CPU never goes to C3 state"
date: 2006-12-16
forum: General Help
---

### Post by fauigerzigerk on 2006-12-16
Hi all,

Once again I'm having troubles with power management. I'm using Ubuntu 6.1 on an Acer TravelMate 8000. The fans keep spinning even though there's no CPU load and frequency scaling works (cpufreq keeps it down at 600 Mhz). I have narrowed down the issue to the fact that the CPU never goes to C-state C3. It always remains in C2 and goes to C1 as needed. This is what cat /proc/acpi/processor/CPU0/power shows:

active state:            C2
max_cstate:              C8
bus master activity:     ffffffff
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010] duration[00000000000000000000]
   *C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[01407088] duration[00000000013249823353]
    C3:                  type[C3] promotion[--] demotion[C2] latency[085] usage[00000000] duration[00000000000000000000]

As you can see C3 is never activated. On Windows the CPU spends almost all the time in C3. If I telinit 1 the system starts to use C3 as it should. I'm suspecting that some driver loaded by gnome prevents the system from going to C3 but I don't know which one it is. Also, I cannot unload the usbcore module for some reason, despite removing all named dependent modules listed by lsmod. There appears to be one unnamed dependency but I can't seem to figure out what that is.

Any help is greately appreciated.

---

### Post by cpu886 on 2006-12-23
I too am having the same problem. My laptop is an HP Pavilion DV5000. The CPU frequency scaling works fine. However, if I run "watch -n 0.1 /proc/acpi/processor/CPU0/power," I get

active state:            C2
max_cstate:              C8
bus master activity:     ddfde140
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00282490]
   *C2:                  type[C2] promotion[C3] demotion[C1] latency[018] usage[03223332]
    C3:                  type[C3] promotion[--] demotion[C2] latency[083] usage[00001611]


As you can see, the system hardly ever uses power state C3, and as a result, my laptop doesn't get as good battery life. I cannot figure out why this is happening. I tried doing removing certain modules with "rmmod," but still, the problem persists. I'm wondering if there is some problem with ACPI. Here's the output of dmesg:


[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000037ea0000 (usable)
[17179569.184000]  BIOS-e820: 0000000037ea0000 - 0000000037eac000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000037eac000 - 0000000037f00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000037f00000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 894MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7c50
[17179569.184000] On node 0 totalpages: 229024
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 224928 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7c20
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x37ea474d
[17179569.184000] ACPI: FADT (v001 HP     Piranha  0x06040000 ATI  0x000f4240) @ 0x37eabe3b
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x37eabeaf
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x37eabf7e
[17179569.184000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x37eabfc4
[17179569.184000] ACPI: DSDT (v001     HP     309B 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 1791.092 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.296000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.296000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.312000] Memory: 897588k/916096k available (1976k kernel code, 17896k reserved, 606k data, 288k init, 0k highmem)
[17179570.312000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.392000] Calibrating delay using timer specific routine.. 3587.52 BogoMIPS (lpj=7175043)
[17179570.392000] Security Framework v1.0.0 initialized
[17179570.392000] SELinux:  Disabled at boot.
[17179570.392000] Mount-cache hash table entries: 512
[17179570.392000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179570.392000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179570.392000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179570.392000] CPU: L2 Cache: 1024K (64 bytes/line)
[17179570.392000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179570.392000] mtrr: v2.0 (20020519)
[17179570.392000] CPU: AMD Turion(tm) 64 Mobile Technology ML-34 stepping 02
[17179570.392000] Enabling fast FPU save and restore... done.
[17179570.392000] Enabling unmasked SIMD FPU exception support... done.
[17179570.392000] Checking 'hlt' instruction... OK.
[17179570.408000] checking if image is initramfs... it is
[17179570.948000] Freeing initrd memory: 6614k freed
[17179570.956000] ACPI: Looking for DSDT ... not found!
[17179571.596000] ENABLING IO-APIC IRQs
[17179571.596000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179571.740000] NET: Registered protocol family 16
[17179571.740000] EISA bus registered
[17179571.740000] ACPI: bus type pci registered
[17179571.740000] PCI: PCI BIOS revision 2.10 entry at 0xfd86c, last bus=8
[17179571.740000] PCI: Using MMCONFIG
[17179571.740000] ACPI: Subsystem revision 20051216
[17179571.740000] ACPI: Interpreter enabled
[17179571.740000] ACPI: Using IOAPIC for interrupt routing
[17179571.740000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.740000] PCI: Probing PCI hardware (bus 00)
[17179571.764000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179571.764000] Boot video device is 0000:01:05.0
[17179571.764000] PCI: Transparent bridge - 0000:00:14.4
[17179571.764000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.764000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[17179571.768000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[17179571.768000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[17179571.768000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[17179571.768000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[17179571.768000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[17179571.768000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[17179571.768000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179571.768000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[17179571.768000] ACPI: Embedded Controller [EC0] (gpe 26) interrupt mode.
[17179571.808000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179571.808000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179571.808000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.808000] pnp: PnP ACPI init
[17179571.832000] pnp: PnP ACPI: found 10 devices
[17179571.832000] PnPBIOS: Disabled by ACPI PNP
[17179571.832000] PCI: Using ACPI for IRQ routing
[17179571.832000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.832000] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[17179571.832000] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
[17179571.856000] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[17179571.856000] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[17179571.856000] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[17179571.856000] pnp: 00:08: ioport range 0x4d6-0x4d6 has been reserved
[17179571.856000] pnp: 00:08: ioport range 0x870-0x87f has been reserved
[17179571.856000] PCI: Bridge: 0000:00:01.0
[17179571.856000]   IO window: 9000-9fff
[17179571.856000]   MEM window: b0100000-b01fffff
[17179571.856000]   PREFETCH window: c0000000-cfffffff
[17179571.856000] PCI: Bridge: 0000:00:05.0
[17179571.856000]   IO window: disabled.
[17179571.856000]   MEM window: disabled.
[17179571.856000]   PREFETCH window: disabled.
[17179571.856000] PCI: Bus 7, cardbus bridge: 0000:06:04.0
[17179571.856000]   IO window: 0000a400-0000a4ff
[17179571.856000]   IO window: 0000a800-0000a8ff
[17179571.856000]   PREFETCH window: 50000000-51ffffff
[17179571.856000]   MEM window: 52000000-53ffffff
[17179571.856000] PCI: Bridge: 0000:00:14.4
[17179571.856000]   IO window: a000-afff
[17179571.856000]   MEM window: b0200000-b02fffff
[17179571.856000]   PREFETCH window: 50000000-51ffffff
[17179571.856000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[17179571.856000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 20 (level, low) -> IRQ 177
[17179571.856000] audit: initializing netlink socket (disabled)
[17179571.856000] audit(1166906907.856:1): initialized
[17179571.856000] VFS: Disk quotas dquot_6.5.1
[17179571.856000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.856000] Initializing Cryptographic API
[17179571.856000] io scheduler noop registered
[17179571.856000] io scheduler anticipatory registered
[17179571.856000] io scheduler deadline registered
[17179571.856000] io scheduler cfq registered
[17179571.856000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[17179571.856000] pcie_portdrv_probe->Dev[5a37:1002] has invalid IRQ. Check vendor BIOS
[17179571.856000] assign_interrupt_mode Found MSI capability
[17179571.856000] Allocate Port Service[pcie00]
[17179571.856000] Allocate Port Service[pcie01]
[17179571.856000] isapnp: Scanning for PnP cards...
[17179572.212000] isapnp: No Plug & Play device found
[17179572.224000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179572.244000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179572.256000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179572.256000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179572.260000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179572.264000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179572.264000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.264000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.268000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 201
[17179572.268000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[17179572.268000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.268000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.268000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.268000] mice: PS/2 mouse device common for all mice
[17179572.272000] EISA: Probing bus 0 at eisa.0
[17179572.272000] Cannot allocate resource for EISA slot 1
[17179572.272000] Cannot allocate resource for EISA slot 8
[17179572.272000] EISA: Detected 0 cards.
[17179572.272000] NET: Registered protocol family 2
[17179572.316000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.316000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.316000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.316000] TCP: Hash tables configured (established 131072 bind 65536)
[17179572.316000] TCP reno registered
[17179572.316000] TCP bic registered
[17179572.316000] NET: Registered protocol family 1
[17179572.316000] NET: Registered protocol family 8
[17179572.316000] NET: Registered protocol family 20
[17179572.316000] Using IPI Shortcut mode
[17179572.316000] ACPI wakeup devices:
[17179572.316000]  LID KBC0 MSE0 ELAN
[17179572.316000] ACPI: (supports S0 S3 S4 S5)
[17179572.316000] Freeing unused kernel memory: 288k freed
[17179572.336000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.356000] vga16fb: initializing
[17179572.356000] vga16fb: mapped to 0xc00a0000
[17179572.444000] Console: switching to colour frame buffer device 80x25
[17179572.444000] fb0: VGA16 VGA frame buffer device
[17179573.472000] Capability LSM initialized
[17179573.596000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179573.596000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179573.608000] ACPI: Thermal Zone [THRM] (0 C)
[17179574.008000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179574.008000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 209
[17179574.008000] ATIIXP: chipset revision 0
[17179574.008000] ATIIXP: not 100% native mode: will probe irqs later
[17179574.008000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[17179574.008000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[17179574.008000] Probing IDE interface ide0...
[17179574.296000] hda: ST9100822A, ATA DISK drive
[17179574.968000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.968000] Probing IDE interface ide1...
[17179575.708000] hdc: HL-DT-ST DVDRAM GSA-4084N, ATAPI CD/DVD-ROM drive
[17179576.044000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.052000] hda: max request size: 1024KiB
[17179576.052000] hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.060000] hda: cache flushes supported
[17179576.060000]  hda: hda1 hda2 hda3 < hda5 hda6 >
[17179576.124000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA
[17179576.124000] Uniform CD-ROM driver Revision: 3.20
[17179576.532000] ieee1394: Initialized config rom entry `ip1394'
[17179576.536000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179576.536000] ACPI: PCI Interrupt 0000:06:04.2[C] -> GSI 23 (level, low) -> IRQ 217
[17179576.568000] usbcore: registered new driver usbfs
[17179576.568000] usbcore: registered new driver hub
[17179576.568000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179576.568000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 225
[17179576.568000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179576.568000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179576.568000] ohci_hcd 0000:00:13.0: irq 225, io mem 0xb0000000
[17179576.588000] hub 1-0:1.0: USB hub found
[17179576.588000] hub 1-0:1.0: 4 ports detected
[17179576.632000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[217]  MMIO=[b0209000-b02097ff]  Max Packet=[2048]
[17179576.692000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 225
[17179576.692000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179576.692000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[17179576.692000] ohci_hcd 0000:00:13.1: irq 225, io mem 0xb0001000
[17179576.700000] hub 2-0:1.0: USB hub found
[17179576.700000] hub 2-0:1.0: 4 ports detected
[17179576.804000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 225
[17179576.804000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179576.804000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[17179576.804000] ehci_hcd 0000:00:13.2: irq 225, io mem 0xb0002000
[17179576.804000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.804000] hub 3-0:1.0: USB hub found
[17179576.804000] hub 3-0:1.0: 8 ports detected
[17179576.964000] Attempting manual resume
[17179576.988000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.996000] kjournald starting.  Commit interval 5 seconds
[17179584.228000] ip_tables: (C) 2000-2002 Netfilter core team
[17179584.304000] Netfilter messages via NETLINK v0.30.
[17179584.304000] ip_conntrack version 2.4 (7157 buckets, 57256 max) - 232 bytes per conntrack
[17179586.620000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.736000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.740000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.260000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 201
[17179587.316000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 201
[17179587.360000] input: PC Speaker as /class/input/input1
[17179587.400000] Real Time Clock Driver v1.12
[17179587.424000] MC'97 0 converters and GPIO not ready (0x1)
[17179587.560000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[17179587.628000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179587.788000] ts: Compaq touchscreen protocol output
[17179587.800000] 8139too Fast Ethernet driver 0.9.27
[17179587.800000] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 22 (level, low) -> IRQ 233
[17179587.800000] eth0: RealTek RTL8139 at 0xf8a32400, 00:0f:b0:fc:10:e2, IRQ 233
[17179587.800000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179587.812000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179587.828000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[17179587.828000] sdhci: Copyright(c) Pierre Ossman
[17179587.828000] ACPI: PCI Interrupt 0000:06:04.4[A] -> GSI 20 (level, low) -> IRQ 177
[17179587.852000] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 20 (level, low) -> IRQ 177
[17179587.852000] Yenta: CardBus bridge found at 0000:06:04.0 [103c:30a4]
[17179587.852000] Yenta: Enabling burst memory read transactions
[17179587.852000] Yenta: Using INTVAL to route CSC interrupts to PCI
[17179587.852000] Yenta: Routing CardBus interrupts to ISA
[17179587.852000] Yenta TI: socket 0000:06:04.0, mfunc 0x00a61b22, devctl 0x64
[17179588.088000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 177
[17179588.088000] Socket status: 30000006
[17179588.088000] Yenta: Raising subordinate bus# of parent bus (#06) from #08 to #0a
[17179588.088000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179588.088000] cs: IO port probe 0xa000-0xafff: clean.
[17179588.088000] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
[17179588.088000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff
[17179588.288000] sdhci: ============== REGISTER DUMP ==============
[17179588.288000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179588.288000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179588.288000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179588.288000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179588.288000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179588.288000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179588.288000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179588.288000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179588.288000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179588.288000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179588.288000] sdhci: ===========================================
[17179588.340000] mmc0: SDHCI at 0xb020a000 irq 177 DMA
[17179588.436000] sdhci: ============== REGISTER DUMP ==============
[17179588.436000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179588.436000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179588.436000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179588.436000] sdhci: Present:  0x00020000 | Host ctl: 0x00000000
[17179588.436000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179588.436000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179588.436000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179588.436000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179588.436000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179588.436000] sdhci: Caps:     0x01821090 | Max curr: 0x00000000
[17179588.436000] sdhci: ===========================================
[17179588.488000] mmc1: SDHCI at 0xb0209c00 irq 177 DMA
[17179588.588000] sdhci: ============== REGISTER DUMP ==============
[17179588.588000] sdhci: Sys addr: 0x00000000 | Version:  0x00008400
[17179588.588000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179588.588000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179588.588000] sdhci: Present:  0x000a0000 | Host ctl: 0x00000000
[17179588.588000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179588.588000] sdhci: Walk up:  0x00000000 | Clock:    0x00000002
[17179588.588000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179588.588000] sdhci: Int enab: 0x11ff00cf | Sig enab: 0x11ff00cf
[17179588.588000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179588.588000] sdhci: Caps:     0x01821898 | Max curr: 0x00000000
[17179588.588000] sdhci: ===========================================
[17179588.636000] mmc2: SDHCI at 0xb0209800 irq 177 DMA
[17179588.816000] eth0: link down
[17179589.188000] cs: IO port probe 0x100-0x3af: clean.
[17179589.188000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179589.192000] cs: IO port probe 0x820-0x8ff: clean.
[17179589.192000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179589.192000] cs: IO port probe 0xa00-0xaff: clean.
[17179589.496000] lp: driver loaded but no devices found
[17179589.544000] SCSI subsystem initialized
[17179589.560000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179589.560000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179589.560000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179589.596000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179589.672000] ndiswrapper: driver bcmwl5a (Broadcom,12/22/2004, 3.100.46.0) loaded
[17179589.672000] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 21 (level, low) -> IRQ 50
[17179589.680000] ndiswrapper: using irq 50
[17179589.964000] NET: Registered protocol family 17
[17179591.040000] wlan0: vendor: ''
[17179591.040000] wlan0: ndiswrapper ethernet device 00:14:a5:79:3a:cc using driver bcmwl5a, 14E4:4318.5.conf
[17179591.040000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179591.112000] Adding 2096440k swap on /dev/hda1.  Priority:-1 extents:1 across:2096440k
[17179591.272000] EXT3 FS on hda2, internal journal
[17179591.456000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179591.456000] md: bitmap version 4.39
[17179591.864000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179592.916000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17179592.916000] hdc: packet command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[17179592.916000] ide: failed opcode was: unknown
[17179592.916000] cdrom: open failed.
[17179599.196000] ACPI: AC Adapter [ACAD] (on-line)
[17179599.240000] ACPI: Battery Slot [BAT1] (battery present)
[17179599.312000] ACPI: Power Button (FF) [PWRF]
[17179599.312000] ACPI: Sleep Button (FF) [SLPF]
[17179599.312000] ACPI: Lid Switch [LID]
[17179599.312000] ACPI: Power Button (CM) [PWRB]
[17179599.412000] ibm_acpi: ec object not found
[17179599.436000] pcc_acpi: loading...
[17179599.468000] wmi_add device=dff6f800
[17179599.468000] calling WQBA
[17179599.512000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179599.884000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[17179599.888000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4 (1450 mV)
[17179599.888000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6 (1400 mV)
[17179599.888000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[17179599.888000] cpu_init done, current fid 0xa, vid 0x2
[17179599.888000] powernow-k8: ph2 null fid transition 0xa
[17179602.120000] ppdev: user-space parallel port driver
[17179603.988000] apm: BIOS not found.
[17179604.284000] [fglrx] Maximum main memory to use for locked dma buffers: 803 MBytes.
[17179604.284000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 201
[17179604.284000] [fglrx] module loaded - fglrx 8.24.8 [Apr 11 2006] on minor 0
[17179605.212000] [fglrx] free  PCIe = 54804480
[17179605.212000] [fglrx] max   PCIe = 54804480
[17179605.212000] [fglrx] free  LFB = 119762944
[17179605.212000] [fglrx] max   LFB = 119762944
[17179605.212000] [fglrx] free  Inv = 134217728
[17179605.212000] [fglrx] max   Inv = 134217728
[17179605.212000] [fglrx] total Inv = 134217728
[17179605.212000] [fglrx] total TIM = 0
[17179605.212000] [fglrx] total FB  = 0
[17179605.212000] [fglrx] total PCIe = 16384
[17179648.400000] Bluetooth: Core ver 2.8
[17179648.400000] NET: Registered protocol family 31
[17179648.400000] Bluetooth: HCI device and connection manager initialized
[17179648.400000] Bluetooth: HCI socket layer initialized
[17179701.268000] DROPPED IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0f:db:2a:d9:9f:08:00 SRC=192.168.1.1 DST=255.255.255.255 LEN=332 TOS=0x00 PREC=0x00 TTL=64 ID=32410 PROTO=UDP SPT=67 DPT=68 LEN=312
[17179704.200000] NET: Registered protocol family 10
[17179704.200000] lo: Disabled Privacy Extensions
[17179704.200000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179704.200000] IPv6 over IPv4 tunneling driver
[17179714.736000] wlan0: no IPv6 routers present
[17179739.076000] wlan0: no IPv6 routers present
[17179857.780000] ndiswrapper: device wlan0 removed
[17179857.808000] ACPI: PCI interrupt for device 0000:06:02.0 disabled
[17179858.256000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179858.292000] ndiswrapper: driver bcmwl5a (Broadcom,12/22/2004, 3.100.46.0) loaded
[17179858.292000] ACPI: PCI Interrupt 0000:06:02.0[A] -> GSI 21 (level, low) -> IRQ 50



Any ideas?

---


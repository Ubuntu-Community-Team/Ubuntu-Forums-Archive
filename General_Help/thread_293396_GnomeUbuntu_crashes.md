---
title: "Gnome/Ubuntu crashes"
date: 2006-11-05
forum: General Help
---

### Post by trondhuso on 2006-11-05
Hi list,

Recently changed from Fedora Core 6 to Ubuntu Dapper so bare with me... 

Anyway. The reason why I did the switch was because my Compaq Evo N160 laptop crached/freezed on the fedora (running with gnome). 
I thought it could be related to the 3com card that I have, but I am not sure. 

As of now I am wondering which logfiles to check to see if the freeze gets registered somewhere. 

best regards,
Trond

---

### Post by trondhuso on 2006-11-06
Okay. So I have researched and found different files to pull out information from. This posting will be long. Hopefully someone will tell me what might be the reason why gnome/x/ubuntu just freezes on me.

Results of cpuinfo.txt:
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 11
model name	: Intel(R) Pentium(R) III Mobile CPU      1000MHz
stepping	: 1
cpu MHz		: 730.985
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips	: 1463.13

/var/log/messages

dmesg (long):
[17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ff60000 (usable)
[17179569.184000]  BIOS-e820: 000000001ff60000 - 000000001ff6fc00 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001ff6fc00 - 000000001ff80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 130912
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126816 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6410
[17179569.184000] ACPI: RSDT (v001 PTLTD  	 RSDT   0x06040000  LTP 0x00000000) @ 0x1ff6a082
[17179569.184000] ACPI: FADT (v001 COMPAQ CPQ2C01  0x06040000 PTL  0x00000001) @ 0x1ff6fb64
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1ff6fbd8
[17179569.184000] ACPI: DSDT (v001 COMPAQ   U22C01 0x06040000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:df800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01401000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 996.798 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.652000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.656000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.684000] Memory: 508212k/523648k available (1976k kernel code, 14804k reserved, 606k data, 288k init, 0k highmem)
[17179571.684000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.764000] Calibrating delay using timer specific routine.. 1995.17 BogoMIPS (lpj=3990358)
[17179571.764000] Security Framework v1.0.0 initialized
[17179571.764000] SELinux:  Disabled at boot.
[17179571.764000] Mount-cache hash table entries: 512
[17179571.764000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.764000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.764000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179571.764000] CPU: L2 cache: 512K
[17179571.764000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179571.764000] mtrr: v2.0 (20020519)
[17179571.764000] CPU: Intel(R) Pentium(R) III Mobile CPU      1000MHz stepping 01
[17179571.764000] Enabling fast FPU save and restore... done.
[17179571.764000] Enabling unmasked SIMD FPU exception support... done.
[17179571.764000] Checking 'hlt' instruction... OK.
[17179571.780000] checking if image is initramfs... it is
[17179573.244000] Freeing initrd memory: 6616k freed
[17179573.268000] ACPI: Looking for DSDT ... not found!
[17179573.268000] ACPI: setting ELCR to 0200 (from 0e20)
[17179573.272000] NET: Registered protocol family 16
[17179573.272000] EISA bus registered
[17179573.272000] ACPI: bus type pci registered
[17179573.276000] PCI: PCI BIOS revision 2.10 entry at 0xfd99b, last bus=2
[17179573.276000] PCI: Using configuration type 1
[17179573.276000] ACPI: Subsystem revision 20051216
[17179573.288000] ACPI: Interpreter enabled
[17179573.288000] ACPI: Using PIC for interrupt routing
[17179573.292000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.292000] PCI: Probing PCI hardware (bus 00)
[17179573.296000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179573.296000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179573.296000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.296000] Boot video device is 0000:01:00.0
[17179573.296000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.296000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.300000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179573.300000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179573.300000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 14 15)
[17179573.300000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 14 15)
[17179573.300000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 14 15) *0, disabled.
[17179573.300000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 14 15)
[17179573.300000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 14 15)
[17179573.304000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 14 15) *0, disabled.
[17179573.304000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 14 15) *0, disabled.
[17179573.304000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 14 15) *0, disabled.
[17179573.308000] ACPI: Embedded Controller [H8] (gpe 29) interrupt mode.
[17179573.312000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.312000] pnp: PnP ACPI init
[17179573.324000] pnp: PnP ACPI: found 11 devices
[17179573.324000] PnPBIOS: Disabled by ACPI PNP
[17179573.324000] PCI: Using ACPI for IRQ routing
[17179573.324000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.324000] pnp: 00:03: ioport range 0x600-0x60f has been reserved
[17179573.324000] PCI: Bridge: 0000:00:01.0
[17179573.324000]   IO window: 2000-2fff
[17179573.324000]   MEM window: d0100000-d01fffff
[17179573.324000]   PREFETCH window: d8000000-dfffffff
[17179573.324000] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[17179573.324000]   IO window: 00003400-000034ff
[17179573.324000]   IO window: 00003800-000038ff
[17179573.328000]   PREFETCH window: 30000000-31ffffff
[17179573.328000]   MEM window: 34000000-35ffffff
[17179573.328000] PCI: Bridge: 0000:00:1e.0
[17179573.328000]   IO window: 3000-3fff
[17179573.328000]   MEM window: d0200000-d02fffff
[17179573.328000]   PREFETCH window: 30000000-31ffffff
[17179573.328000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.688000] **** SET: Misaligned resource pointer: dfec05e2 Type 07 Len 0
[17179573.688000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[17179573.688000] PCI: setting IRQ 10 as level-triggered
[17179573.688000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179573.688000] PCI: Setting latency timer of device 0000:02:06.0 to 64
[17179573.688000] Simple Boot Flag at 0x38 set to 0x1
[17179573.688000] audit: initializing netlink socket (disabled)
[17179573.688000] audit(1162808616.688:1): initialized
[17179573.688000] VFS: Disk quotas dquot_6.5.1
[17179573.688000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.688000] Initializing Cryptographic API
[17179573.688000] io scheduler noop registered
[17179573.688000] io scheduler anticipatory registered
[17179573.688000] io scheduler deadline registered
[17179573.688000] io scheduler cfq registered
[17179573.688000] isapnp: Scanning for PnP cards...
[17179574.044000] isapnp: No Plug & Play device found
[17179574.068000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179574.076000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.076000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.076000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.076000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[17179574.080000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[17179574.080000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.080000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.080000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.080000] mice: PS/2 mouse device common for all mice
[17179574.080000] EISA: Probing bus 0 at eisa.0
[17179574.080000] Cannot allocate resource for EISA slot 1
[17179574.080000] Cannot allocate resource for EISA slot 2
[17179574.080000] Cannot allocate resource for EISA slot 3
[17179574.080000] EISA: Detected 0 cards.
[17179574.080000] NET: Registered protocol family 2
[17179574.104000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.124000] Using IPI Shortcut mode
[17179574.124000] ACPI wakeup devices: 
[17179574.124000]   AC  LID PWRB PCIB CRD0  LAN PS2K PS2M   H8 USB0 USB1 USB2 
[17179574.124000] ACPI: (supports S0 S1 S4 S5)
[17179574.124000] Freeing unused kernel memory: 288k freed
[17179574.208000] vga16fb: initializing
[17179574.208000] vga16fb: mapped to 0xc00a0000
[17179574.324000] Console: switching to colour frame buffer device 80x25
[17179574.324000] fb0: VGA16 VGA frame buffer device
[17179575.392000] Capability LSM initialized
[17179575.528000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.532000] ACPI: Thermal Zone [TZ0] (56 C)
[17179576.172000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[17179576.172000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179576.172000] **** SET: Misaligned resource pointer: df9871c2 Type 07 Len 0
[17179576.172000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179576.172000] PCI: setting IRQ 11 as level-triggered
[17179576.172000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179576.172000] ICH3M: chipset revision 1
[17179576.172000] ICH3M: not 100% native mode: will probe irqs later
[17179576.172000]     ide0: BM-DMA at 0x1800-0x1807, BIOS settings: hda:DMA, hdb:pio
[17179576.172000]     ide1: BM-DMA at 0x1808-0x180f, BIOS settings: hdc:DMA, hdd:pio
[17179576.172000] Probing IDE interface ide0...
[17179576.460000] hda: IC25N020ATDA04-0, ATA DISK drive
[17179577.132000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.148000] Probing IDE interface ide1...
[17179577.884000] hdc: LG DVD-ROM DRN-8080B, ATAPI CD/DVD-ROM drive
[17179578.556000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.572000] hda: max request size: 128KiB
[17179578.584000] hda: 39070080 sectors (20003 MB) w/1806KiB Cache, CHS=38760/16/63, UDMA(100)
[17179578.584000] hda: cache flushes not supported
[17179578.584000]  hda: hda1 hda2 < hda5 >
[17179578.644000] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179578.644000] Uniform CD-ROM driver Revision: 3.20
[17179578.908000] USB Universal Host Controller Interface driver v2.3
[17179578.908000] **** SET: Misaligned resource pointer: dfc084e2 Type 07 Len 0
[17179578.908000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179578.908000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179578.908000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179578.908000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179578.908000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179578.908000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001840
[17179578.908000] hub 1-0:1.0: USB hub found
[17179578.908000] hub 1-0:1.0: 2 ports detected
[17179578.996000] ieee1394: Initialized config rom entry `ip1394'
[17179579.012000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179579.012000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179579.012000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179579.012000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179579.012000] uhci_hcd 0000:00:1d.1: irq 10, io base 0x00001860
[17179579.012000] hub 2-0:1.0: USB hub found
[17179579.012000] hub 2-0:1.0: 2 ports detected
[17179579.116000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179579.116000] **** SET: Misaligned resource pointer: dfdf3c02 Type 07 Len 0
[17179579.116000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
[17179579.116000] PCI: setting IRQ 9 as level-triggered
[17179579.116000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[17179579.168000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[9]  MMIO=[d0201000-d02017ff]  Max Packet=[2048]
[17179579.272000] Attempting manual resume
[17179579.292000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179579.292000] EXT3-fs: write access will be enabled during recovery.
[17179580.440000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00508b702fad0082]
[17179583.416000] EXT3-fs: recovery complete.
[17179583.416000] kjournald starting.  Commit interval 5 seconds
[17179583.420000] EXT3-fs: mounted filesystem with ordered data mode.
[17179599.980000] Linux agpgart interface v0.101 (c) Dave Jones
[17179599.996000] agpgart: Detected an Intel 830M Chipset.
[17179600.008000] agpgart: AGP aperture is 256M @ 0xe0000000
[17179600.356000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179600.364000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179600.456000] hw_random: RNG not detected
[17179601.044000] Real Time Clock Driver v1.12
[17179601.072000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[17179601.072000] **** SET: Misaligned resource pointer: d91fed22 Type 07 Len 0
[17179601.072000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179601.072000] PCI: setting IRQ 5 as level-triggered
[17179601.072000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179601.072000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179601.340000] parport: PnPBIOS parport detected.
[17179601.340000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179601.368000] Floppy drive(s): fd0 is 1.44M
[17179601.388000] intel8x0_measure_ac97_clock: measured 54659 usecs
[17179601.388000] intel8x0: clocking to 48000
[17179601.696000] Synaptics Touchpad, model: 1, fw: 5.5, id: 0x1d56b1, caps: 0x904713/0x4006
[17179601.732000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179601.748000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179601.748000] Yenta: CardBus bridge found at 0000:02:06.0 [0e11:b103]
[17179601.748000] Yenta: Enabling burst memory read transactions
[17179601.748000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179601.748000] Yenta: Routing CardBus interrupts to PCI
[17179601.748000] Yenta TI: socket 0000:02:06.0, mfunc 0x012c1202, devctl 0x64
[17179601.848000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17179601.848000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179601.980000] Yenta: ISA IRQ mask 0x0018, PCI irq 10
[17179601.980000] Socket status: 30000020
[17179601.980000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179601.980000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179601.980000] cs: IO port probe 0x3000-0x3fff: clean.
[17179601.980000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[17179601.980000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179602.016000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[17179602.036000] e100: eth0: e100_probe: addr 0xd0200000, irq 9, MAC addr 00:02:A5:99:EE:A8
[17179602.612000] ts: Compaq touchscreen protocol output
[17179602.688000] pccard: CardBus card inserted into slot 0
[17179602.796000] Loaded prism54 driver, version 1.2
[17179602.796000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[17179602.800000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[17179602.800000] eth1: uploading firmware...
[17179603.072000] cs: IO port probe 0x100-0x3af: clean.
[17179603.072000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179603.072000] cs: IO port probe 0x820-0x8ff: clean.
[17179603.076000] cs: IO port probe 0xc00-0xcf7: clean.
[17179603.076000] cs: IO port probe 0xa00-0xaff: clean.
[17179603.116000] eth1: firmware version: 1.0.4.3
[17179603.116000] eth1: firmware upload complete
[17179603.276000] eth2: resetting device...
[17179603.276000] eth2: uploading firmware...
[17179603.360000] eth2: firmware version: 1.0.4.3
[17179603.360000] eth2: firmware upload complete
[17179603.596000] eth2: interface reset complete
[17179604.236000] NET: Registered protocol family 17
[17179710.772000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179717.568000] [drm] Initialized drm 1.0.1 20051102
[17179717.632000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179717.636000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179720.916000] ppdev: user-space parallel port driver
[17179721.824000] apm: BIOS not found.
[17179728.672000] Bluetooth: Core ver 2.8
[17179728.672000] NET: Registered protocol family 31
[17179728.672000] Bluetooth: HCI device and connection manager initialized
[17179728.672000] Bluetooth: HCI socket layer initialized
[17179728.780000] Bluetooth: L2CAP ver 2.8
[17179728.780000] Bluetooth: L2CAP socket layer initialized
[17179728.788000] Bluetooth: RFCOMM socket layer initialized
[17179728.788000] Bluetooth: RFCOMM TTY layer initialized
[17179728.788000] Bluetooth: RFCOMM ver 1.7

meminfo:
MemTotal:       515364 kB
MemFree:        188112 kB
Buffers:          9344 kB
Cached:         184832 kB
SwapCached:          0 kB
Active:         169500 kB
Inactive:       135388 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       515364 kB
LowFree:        188112 kB
SwapTotal:      827308 kB
SwapFree:       827308 kB
Dirty:             344 kB
Writeback:           0 kB
Mapped:         161216 kB
Slab:            14880 kB
CommitLimit:   1084988 kB
Committed_AS:   456160 kB
PageTables:       1500 kB
VmallocTotal:   507896 kB
VmallocUsed:      4784 kB
VmallocChunk:   502964 kB

/proc/modules
binfmt_misc 12296 1 - Live 0xe0c98000
rfcomm 40216 0 - Live 0xe0cc6000
l2cap 26244 5 rfcomm, Live 0xe0c2b000
bluetooth 50020 4 rfcomm,l2cap, Live 0xe0c8a000
ppdev 9220 0 - Live 0xe0c1e000
radeon 116000 0 - Live 0xe0ca8000
drm 73236 1 radeon, Live 0xe0c77000
speedstep_ich 5260 0 - Live 0xe0c15000
speedstep_lib 4484 1 speedstep_ich, Live 0xe0c12000
cpufreq_userspace 4696 1 - Live 0xe0c0f000
cpufreq_stats 5636 0 - Live 0xe0c0c000
freq_table 4740 2 speedstep_ich,cpufreq_stats, Live 0xe0c09000
cpufreq_powersave 1920 0 - Live 0xe0aee000
cpufreq_ondemand 6428 0 - Live 0xe0c06000
cpufreq_conservative 7332 0 - Live 0xe0c03000
video 16260 0 - Live 0xe0b33000
tc1100_wmi 6916 0 - Live 0xe0b5c000
sony_acpi 5644 0 - Live 0xe0afa000
pcc_acpi 12416 0 - Live 0xe0b44000
hotkey 11556 0 - Live 0xe0b40000
dev_acpi 11140 0 - Live 0xe0b3c000
container 4608 0 - Live 0xe0b21000
button 6672 0 - Live 0xe0ade000
acpi_sbs 19980 0 - Live 0xe0bf9000
battery 9988 1 acpi_sbs, Live 0xe0b38000
ac 5252 1 acpi_sbs, Live 0xe0ae4000
i2c_acpi_ec 5120 1 acpi_sbs, Live 0xe0ae1000
i2c_core 21904 1 i2c_acpi_ec, Live 0xe0b1a000
dm_mod 58936 1 - Live 0xe0be9000
md_mod 72532 0 - Live 0xe0b49000
ipv6 265728 6 - Live 0xe0c35000
sr_mod 16932 0 - Live 0xe0af4000
sbp2 24196 0 - Live 0xe0ae7000
scsi_mod 139496 2 sr_mod,sbp2, Live 0xe0b5f000
lp 11844 0 - Live 0xe09d0000
af_packet 22920 4 - Live 0xe0b13000
prism54 54280 0 - Live 0xe0b24000
joydev 10048 0 - Live 0xe0af0000
tsdev 8000 0 - Live 0xe0a5f000
pcmcia 40508 0 - Live 0xe0b08000
e100 40580 0 - Live 0xe0afd000
mii 5888 1 e100, Live 0xe09fc000
yenta_socket 28428 2 - Live 0xe0ad6000
rsrc_nonstatic 13440 1 yenta_socket, Live 0xe0a5a000
pcmcia_core 42640 3 pcmcia,yenta_socket,rsrc_nonstatic, Live 0xe0aca000
parport_pc 35780 1 - Live 0xe0ac0000
parport 36296 3 ppdev,lp,parport_pc, Live 0xe0a9e000
psmouse 36100 0 - Live 0xe0a94000
snd_intel8x0 33692 3 - Live 0xe0a8a000
rtc 13492 0 - Live 0xe0a4f000
snd_ac97_codec 93216 1 snd_intel8x0, Live 0xe0aa8000
snd_ac97_bus 2304 1 snd_ac97_codec, Live 0xe0937000
serio_raw 7300 0 - Live 0xe09cb000
snd_pcm_oss 53664 0 - Live 0xe0a7b000
snd_mixer_oss 18688 1 snd_pcm_oss, Live 0xe0a49000
snd_pcm 89864 4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss, Live 0xe0a64000
snd_timer 25220 2 snd_pcm, Live 0xe0a41000
snd 55268 10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer, Live 0xe09df000
shpchp 45632 0 - Live 0xe09ef000
pci_hotplug 29236 1 shpchp, Live 0xe09d6000
soundcore 10208 1 snd, Live 0xe09c7000
snd_page_alloc 10632 2 snd_intel8x0,snd_pcm, Live 0xe09bc000
intel_agp 22940 1 - Live 0xe09c0000
agpgart 34888 2 drm,intel_agp, Live 0xe093e000
evdev 9856 1 - Live 0xe093a000
ext3 135816 1 - Live 0xe0994000
jbd 58772 1 ext3, Live 0xe090b000
ide_generic 1536 0 - Live 0xe08f6000
ohci1394 35124 0 - Live 0xe08ec000
ieee1394 299832 2 sbp2,ohci1394, Live 0xe0949000
uhci_hcd 33808 0 - Live 0xe08a4000
usbcore 130820 2 uhci_hcd, Live 0xe08cb000
ide_cd 33028 0 - Live 0xe089a000
cdrom 38560 2 sr_mod,ide_cd, Live 0xe088f000
ide_disk 17664 3 - Live 0xe086c000
piix 11012 1 - Live 0xe087e000
generic 5124 0 - Live 0xe0869000
thermal 13576 0 - Live 0xe0879000
processor 23360 1 thermal, Live 0xe0872000
fan 4868 0 - Live 0xe0866000
capability 5000 0 - Live 0xe0863000
commoncap 7296 1 capability, Live 0xe081e000
vga16fb 13704 1 - Live 0xe0844000
vgastate 10368 1 vga16fb, Live 0xe082c000
fbcon 42784 72 - Live 0xe0838000
tileblit 2816 1 fbcon, Live 0xe0806000
font 8320 1 fbcon, Live 0xe0828000
bitblit 6272 1 fbcon, Live 0xe0821000
softcursor 2304 1 bitblit, Live 0xe081c000

/var/log/messages
Nov  6 09:36:25 localhost kernel: [17179622.768000] apm: BIOS not found.
Nov  6 09:36:17 localhost kernel: [17179602.888000] pccard: CardBus card inserted into slot 0
Nov  6 09:36:17 localhost kernel: [17179602.944000] cs: IO port probe 0x100-0x3af: clean.
Nov  6 09:36:17 localhost kernel: [17179602.948000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Nov  6 09:36:17 localhost kernel: [17179602.948000] cs: IO port probe 0x820-0x8ff: clean.
Nov  6 09:36:17 localhost kernel: [17179602.948000] cs: IO port probe 0xc00-0xcf7: clean.
Nov  6 09:36:17 localhost kernel: [17179602.948000] cs: IO port probe 0xa00-0xaff: clean.
Nov  6 09:36:17 localhost kernel: [17179603.000000] Loaded prism54 driver, version 1.2
Nov  6 09:36:17 localhost kernel: [17179603.000000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Nov  6 09:36:17 localhost kernel: [17179603.000000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10

BR
Trond

---


---
title: "Catching the error message?"
date: 2007-03-01
forum: General Help
---

### Post by Raavea on 2007-03-01
When Iload upmy ystem it gives me an error** just before **the Xubuntu usplash *(is that the word for the thing where it says 'loading so-and-so [ok]'?)*

 I can't see it... My camera phone is too grainy for me to make it out on the recording I did... All I know is that one of the words is remote, I THINK.

 I have put up with it for some time, but the other day my hard-drive went kaput. No bootup, and the loader told me that the hda1 was not detected. It was slow as hells too.

 I thought 'ah crap, I killed another compy' but then I thought 'but hmmm' and tried the LiveCD to do a memtest and boot from hd. Memtest was fine, but the hd spat out the same errors. Well, I decided to reinstall and see if that helped. Voila, all is fine - I wiped the hd completely and installed on top.


 Could this error be what caused my system to die? And how can I catch it? 

 Also, what does  **hw_random: RNG not detected**  mean?

---

### Post by IcemanV9 on 2007-03-01
To see boot up messages, in the terminal, type ...

```
dmesg |more
```

For hw_random: RNG not dectected error, it was trying to load the module hw_random which your box does not have. If err msg annoys you, then you might try this [[COLOR="Orange"]solution[/COLOR]]("http://lists.debian.org/debian-laptop/2004/06/msg00205.html").

---

### Post by Raavea on 2007-03-01
So what does this mean? I am worried that whatever the error is, it's what finally caused my system to stop booting from hd...
```
$ dmesg |more
[17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.
0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 00000000000eee00 (reserved)
[17179569.184000]  BIOS-e820: 00000000000eee00 - 00000000000ef000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000ef40000 (usable)
[17179569.184000]  BIOS-e820: 000000000ef40000 - 000000000ef50000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000ef50000 - 000000000f000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[17179569.184000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 239MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 61248
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 57152 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 TOSHIB                                ) @ 0x000f0180
[17179569.184000] ACPI: RSDT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x0ef40000
[17179569.184000] ACPI: FADT (v002 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x0ef40058
[17179569.184000] ACPI: DBGP (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x0ef400dc
[17179569.184000] ACPI: BOOT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x0ef40030
[17179569.184000] ACPI: DSDT (v001 TOSHIB AFCF7    0x20030326 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xd808
[17179569.184000] Allocating PCI resources starting at 10000000 (gap: 0f000000:efc10000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (011e0000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 1995.298 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.916000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.916000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179571.924000] Memory: 232372k/244992k available (1977k kernel code, 12032k reserved, 605k data, 288k init, 0k highmem)
[17179571.924000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.004000] Calibrating delay using timer specific routine.. 3994.19 BogoMIPS (lpj=7988380)
[17179572.004000] Security Framework v1.0.0 initialized
[17179572.004000] SELinux:  Disabled at boot.
[17179572.004000] Mount-cache hash table entries: 512
[17179572.004000] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.004000] CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179572.004000] CPU: L2 cache: 256K
[17179572.004000] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00004400 00000000 00000000
[17179572.004000] mtrr: v2.0 (20020519)
[17179572.004000] CPU: Intel Mobile Intel(R) Celeron(R) CPU 2.00GHz stepping 09
[17179572.004000] Enabling fast FPU save and restore... done.
[17179572.004000] Enabling unmasked SIMD FPU exception support... done.
[17179572.004000] Checking 'hlt' instruction... OK.
[17179572.020000] checking if image is initramfs... it is
[17179572.704000] Freeing initrd memory: 6617k freed
[17179572.712000] ACPI: Looking for DSDT ... not found!
[17179572.716000] ACPI: setting ELCR to 0200 (from 0e00)
[17179572.716000] NET: Registered protocol family 16
[17179572.716000] EISA bus registered
[17179572.716000] ACPI: bus type pci registered
[17179572.716000] PCI: PCI BIOS revision 2.10 entry at 0xfd317, last bus=3
[17179572.716000] PCI: Using configuration type 1
[17179572.716000] ACPI: Subsystem revision 20051216
[17179572.720000] ACPI: Interpreter enabled
[17179572.720000] ACPI: Using PIC for interrupt routing
[17179572.720000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[17179572.720000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[17179572.720000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[17179572.720000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[17179572.724000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[17179572.724000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[17179572.724000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[17179572.724000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[17179572.724000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.724000] PCI: Probing PCI hardware (bus 00)
[17179572.724000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179572.724000] Boot video device is 0000:00:02.0
[17179572.728000] PCI quirk: region d800-d87f claimed by ICH4 ACPI/GPIO/TCO
[17179572.728000] PCI quirk: region eec0-eeff claimed by ICH4 GPIO
[17179572.728000] PCI: Enabled i801 SMBus device
[17179572.728000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179572.728000] PCI: Transparent bridge - 0000:00:1e.0
[17179572.728000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.728000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179572.732000] ACPI: Power Resource [PFAN] (off)
[17179572.732000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.732000] pnp: PnP ACPI init
[17179572.736000] pnp: PnP ACPI: found 11 devices
[17179572.736000] PnPBIOS: Disabled by ACPI PNP
[17179572.736000] PCI: Using ACPI for IRQ routing
[17179572.736000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.736000] PCI: Cannot allocate resource region 4 of device 0000:00:1d.0
[17179572.744000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179572.744000] PCI: Bus 2, cardbus bridge: 0000:01:0b.0
[17179572.744000]   IO window: 0000c000-0000c0ff
[17179572.744000]   IO window: 0000c400-0000c4ff
[17179572.744000]   PREFETCH window: 18000000-19ffffff
[17179572.744000]   MEM window: 1c000000-1dffffff
[17179572.744000] PCI: Bridge: 0000:00:1e.0
[17179572.744000]   IO window: c000-cfff
[17179572.744000]   MEM window: cff00000-cfffffff
[17179572.744000]   PREFETCH window: 18000000-19ffffff
[17179572.744000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179572.744000] PCI: Enabling device 0000:01:0b.0 (0000 -> 0003)
[17179572.744000] **** SET: Misaligned resource pointer: ce9757c2 Type 07 Len 0
[17179572.744000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179572.744000] PCI: setting IRQ 11 as level-triggered
[17179572.744000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179572.744000] Simple Boot Flag at 0x7c set to 0x1
[17179572.744000] audit: initializing netlink socket (disabled)
[17179572.744000] audit(1172773500.744:1): initialized
[17179572.744000] VFS: Disk quotas dquot_6.5.1
[17179572.744000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.744000] Initializing Cryptographic API
[17179572.744000] io scheduler noop registered
[17179572.744000] io scheduler anticipatory registered
[17179572.744000] io scheduler deadline registered
[17179572.744000] io scheduler cfq registered
[17179572.744000] isapnp: Scanning for PnP cards...
[17179573.100000] isapnp: No Plug & Play device found
[17179573.124000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.136000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.140000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.140000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.140000] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
[17179573.140000] **** SET: Misaligned resource pointer: cec4c3c2 Type 07 Len 0
[17179573.144000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179573.144000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179573.144000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179573.144000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.144000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.144000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.144000] mice: PS/2 mouse device common for all mice
[17179573.144000] EISA: Probing bus 0 at eisa.0
[17179573.144000] Cannot allocate resource for EISA slot 1
[17179573.144000] EISA: Detected 0 cards.
[17179573.144000] NET: Registered protocol family 2
[17179573.172000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.184000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179573.184000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[17179573.184000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[17179573.184000] TCP: Hash tables configured (established 8192 bind 8192)
[17179573.184000] TCP reno registered
[17179573.184000] TCP bic registered
[17179573.184000] NET: Registered protocol family 1
[17179573.184000] NET: Registered protocol family 8
[17179573.184000] NET: Registered protocol family 20
[17179573.184000] Using IPI Shortcut mode
[17179573.184000] ACPI wakeup devices:
[17179573.184000] MPC0 MPC1  LAN VIY0 USB1 USB4 AMDM  LID PWRB
[17179573.184000] ACPI: (supports S0 S3 S4 S5)
[17179573.184000] Freeing unused kernel memory: 288k freed
[17179573.248000] vga16fb: initializing
[17179573.248000] vga16fb: mapped to 0xc00a0000
[17179573.388000] Console: switching to colour frame buffer device 80x25
[17179573.388000] fb0: VGA16 VGA frame buffer device
[17179574.508000] Capability LSM initialized
[17179574.552000] ACPI: Fan [FAN] (off)
[17179574.556000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179574.560000] ACPI: Thermal Zone [THRM] (60 C)
[17179575.400000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179575.400000] **** SET: Misaligned resource pointer: cec523c2 Type 07 Len 0
[17179575.400000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179575.400000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179575.400000] ICH4: chipset revision 3
[17179575.400000] ICH4: not 100% native mode: will probe irqs later
[17179575.400000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
[17179575.400000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:DMA, hdd:pio
[17179575.400000] Probing IDE interface ide0...
[17179575.692000] hda: FUJITSU MHS2030AT, ATA DISK drive
[17179576.528000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.592000] Probing IDE interface ide1...
[17179577.328000] hdc: UJDA740 DVD/CDRW, ATAPI CD/DVD-ROM drive
[17179578.000000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.008000] hda: max request size: 128KiB
[17179578.020000] hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=58140/16/63, UDMA(100)
[17179578.020000] hda: cache flushes supported
[17179578.024000]  hda: hda1 hda2 < hda5 >
[17179578.092000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.092000] Uniform CD-ROM driver Revision: 3.20
[17179578.548000] usbcore: registered new driver usbfs
[17179578.548000] usbcore: registered new driver hub
[17179578.548000] USB Universal Host Controller Interface driver v2.3
[17179578.548000] **** SET: Misaligned resource pointer: cedbf702 Type 07 Len 0
[17179578.552000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[17179578.552000] PCI: setting IRQ 10 as level-triggered
[17179578.552000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179578.552000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179578.552000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179578.552000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179578.552000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018c0
[17179578.552000] hub 1-0:1.0: USB hub found
[17179578.552000] hub 1-0:1.0: 2 ports detected
[17179578.656000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[17179578.656000] **** SET: Misaligned resource pointer: cedbf402 Type 07 Len 0
[17179578.656000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[17179578.656000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[17179578.656000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179578.656000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179578.656000] ehci_hcd 0000:00:1d.7: debug port 1
[17179578.656000] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[17179578.656000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[17179578.656000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x1a080000
[17179578.660000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.660000] hub 2-0:1.0: USB hub found
[17179578.660000] hub 2-0:1.0: 6 ports detected
[17179578.860000] Attempting manual resume
[17179578.888000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.916000] kjournald starting.  Commit interval 5 seconds
[17179579.400000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179621.052000] Linux agpgart interface v0.101 (c) Dave Jones
[17179621.056000] agpgart: Detected an Intel 855 Chipset.
[17179621.056000] agpgart: Detected 16252K stolen memory.
[17179621.064000] agpgart: AGP aperture is 128M @ 0xd8000000
[17179621.548000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179621.580000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179621.832000] input: PC Speaker as /class/input/input1
[17179621.852000] usbcore: registered new driver hiddev
[17179621.880000] input: Microsoft Basic Optical Mouse as /class/input/input2
[17179621.880000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.0-1
[17179621.880000] usbcore: registered new driver usbhid
[17179621.880000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179622.080000] ts: Compaq touchscreen protocol output
[17179622.092000] Real Time Clock Driver v1.12
[17179622.100000] hw_random: RNG not detected
[17179622.164000] **** SET: Misaligned resource pointer: cadf3242 Type 04 Len 42
[17179622.164000] **** SET: Misaligned resource pointer: cadf32c6 Type 01 Len 42
[17179622.168000] pnp: Device 00:08 activated.
[17179622.168000] parport: PnPBIOS parport detected.
[17179622.168000] pnp: Device 00:08 disabled.
[17179622.348000] input: PS/2 Mouse as /class/input/input3
[17179622.356000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0003)
[17179622.356000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179622.356000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179622.408000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[17179622.952000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[17179622.952000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179623.176000] intel8x0_measure_ac97_clock: measured 55344 usecs
[17179623.176000] intel8x0: clocking to 48000
[17179623.180000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179623.180000] Yenta: CardBus bridge found at 0000:01:0b.0 [1179:0001]
[17179623.180000] **** SET: Misaligned resource pointer: c9845902 Type 07 Len 0
[17179623.180000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[17179623.180000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[17179623.204000] e100: eth0: e100_probe: addr 0xcffff000, irq 11, MAC addr 00:08:0D:0D:D4:61
[17179623.308000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[17179623.308000] Socket status: 30000007
[17179623.308000] Yenta: Raising subordinate bus# of parent bus (#01) from #03 to #05
[17179623.308000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[17179623.308000] cs: IO port probe 0xc000-0xcfff: clean.
[17179623.308000] pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xcfffffff
[17179623.308000] pcmcia: parent PCI bridge Memory window: 0x18000000 - 0x19ffffff
[17179624.092000] cs: IO port probe 0x100-0x3af: excluding 0x1e0-0x1e7
[17179624.092000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179624.096000] cs: IO port probe 0x820-0x8ff: clean.
[17179624.096000] cs: IO port probe 0xc00-0xcf7: clean.
[17179624.096000] cs: IO port probe 0xa00-0xaff: clean.
[17179624.156000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[17179624.436000] lp: driver loaded but no devices found
[17179624.508000] Adding 698788k swap on /dev/hda5.  Priority:-1 extents:1 across:698788k
[17179624.652000] EXT3 FS on hda1, internal journal
[17179624.980000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179624.980000] md: bitmap version 4.39
[17179625.292000] NET: Registered protocol family 17
[17179625.692000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179627.148000] cdrom: open failed.
[17179631.884000] NET: Registered protocol family 10
[17179631.884000] lo: Disabled Privacy Extensions
[17179631.884000] IPv6 over IPv4 tunneling driver
[17179635.052000] ACPI: AC Adapter [ADP1] (on-line)
[17179635.056000] ACPI: Battery Slot [BAT1] (battery present)
[17179635.164000] ACPI: Power Button (FF) [PWRF]
[17179635.164000] ACPI: Lid Switch [LID]
[17179635.164000] ACPI: Power Button (CM) [PWRB]
[17179635.296000] ibm_acpi: ec object not found
[17179635.332000] pcc_acpi: loading...
[17179635.412000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[17179635.412000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[17179635.416000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[17179635.416000] toshiba_acpi: ktoshkeyd will check 2 times per second
[17179635.416000] toshiba_acpi: Dropped 0 keys from the queue on startup
[17179635.440000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[17179642.228000] eth0: no IPv6 routers present
[17179649.964000] ppdev: user-space parallel port driver
[17179650.924000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[17179650.924000] apm: overridden by ACPI.
[17179652.464000] Bluetooth: Core ver 2.8
[17179652.464000] NET: Registered protocol family 31
[17179652.464000] Bluetooth: HCI device and connection manager initialized
[17179652.464000] Bluetooth: HCI socket layer initialized
[17179652.612000] Bluetooth: L2CAP ver 2.8
[17179652.612000] Bluetooth: L2CAP socket layer initialized
[17179652.944000] Bluetooth: RFCOMM socket layer initialized
[17179652.944000] Bluetooth: RFCOMM TTY layer initialized
[17179652.944000] Bluetooth: RFCOMM ver 1.7

```

---


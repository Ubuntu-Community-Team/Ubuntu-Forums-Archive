---
title: "HAL Error"
date: 2007-05-31
forum: General Help
---

### Post by macmichael01 on 2007-05-31
Also I am getting a dialog box that pops up when I login stating:

Internal Error
failed to initialize HAL!

ubuntu does not load correctly. i have to go to recovery mode to load ubuntu up.  So I am assuming that it is a hardware thing that is not loading correctly.

Any suggestions?

---

### Post by macmichael01 on 2007-05-31
I really need some help on this issue so you anyone could help that would be great!

---

### Post by phidia on 2007-05-31
Just to start the ball rolling please open a terminal and type lsmod <enter> also type dmesg <enter> and post the results here. Your profile says you are using Edubuntu 5.10 is that correct?

---

### Post by macmichael01 on 2007-05-31
lsmod:

Module                  Size  Used by
sg                     36252  0 
sd_mod                 23428  0 
usb_storage            72256  0 
libusual               17936  1 usb_storage
i915                   24448  2 
drm                    81044  3 i915
ipv6                  268960  8 
lp                     12452  0 
fuse                   46612  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               7940  0 
parport_pc             36388  1 
parport                36936  2 lp,parport_pc
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
pcspkr                  4224  0 
psmouse                38920  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
i2c_i810                6276  0 
i2c_algo_bit            8712  1 i2c_i810
intel_agp              25244  1 
i2c_core               22656  2 i2c_i810,i2c_algo_bit
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
agpgart                35400  3 drm,intel_agp
af_packet              23816  2 
evdev                  11008  1 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  3 
generic                 5124  0 [permanent]
usbhid                 26592  0 
hid                    27392  1 usbhid
piix                   11140  0 [permanent]
floppy                 59524  0 
e1000                 126016  0 
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  4 sg,sd_mod,usb_storage,libata
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

dmesg:

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed May 23 01:46:23 UTC 2007 (Ubuntu 2.6.20-16.28-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 00000000000a0000 end: 00000000000a0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fd71000 end: 000000003fe71000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fe71000 size: 0000000000002000 end: 000000003fe73000 type: 4
[    0.000000] copy_e820_map() start: 000000003fe73000 size: 0000000000021000 end: 000000003fe94000 type: 3
[    0.000000] copy_e820_map() start: 000000003fe94000 size: 000000000006c000 end: 000000003ff00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000010000 end: 00000000fee10000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe71000 (usable)
[    0.000000]  BIOS-e820: 000000003fe71000 - 000000003fe73000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fe73000 - 000000003fe94000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fe94000 - 000000003ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 261745) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261745
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261745
[    0.000000] On node 0 totalpages: 261745
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 252 pages used for memmap
[    0.000000]   HighMem zone: 32117 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000feba0
[    0.000000] ACPI: RSDT (v001 DELL    GX260   0x00000008 ASL  0x00000061) @ 0x000fd4fe
[    0.000000] ACPI: FADT (v001 DELL    GX260   0x00000008 ASL  0x00000061) @ 0x000fd536
[    0.000000] ACPI: SSDT (v001   DELL    st_ex 0x00001000 MSFT 0x0100000d) @ 0xfffded2d
[    0.000000] ACPI: MADT (v001 DELL    GX260   0x00000008 ASL  0x00000061) @ 0x000fd5aa
[    0.000000] ACPI: BOOT (v001 DELL    GX260   0x00000008 ASL  0x00000061) @ 0x000fd616
[    0.000000] ACPI: ASF! (v016 DELL    GX260   0x00000008 ASL  0x00000061) @ 0x000fd63e
[    0.000000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:bed00000)
[    0.000000] Detected 2789.705 MHz processor.
[   11.362991] Built 1 zonelists.  Total pages: 259701
[   11.362997] Kernel command line: root=UUID=2433a726-6942-414d-a65e-ac20b219bd51 ro single
[   11.363161] mapped APIC to ffffd000 (fee00000)
[   11.363164] mapped IOAPIC to ffffc000 (fec00000)
[   11.363169] Enabling fast FPU save and restore... done.
[   11.363172] Enabling unmasked SIMD FPU exception support... done.
[   11.363190] Initializing CPU#0
[   11.363304] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   11.364982] Console: colour VGA+ 80x25
[   11.368595] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   11.369684] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   11.401081] Memory: 1026796k/1046980k available (1992k kernel code, 19476k reserved, 896k data, 328k init, 129476k highmem)
[   11.401169] virtual kernel memory layout:
[   11.401170]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   11.401171]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.401172]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   11.401173]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   11.401174]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   11.401175]       .data : 0xc02f2354 - 0xc03d26d4   ( 896 kB)
[   11.401176]       .text : 0xc0100000 - 0xc02f2354   (1992 kB)
[   11.401563] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.479294] Calibrating delay using timer specific routine.. 5583.83 BogoMIPS (lpj=11167672)
[   11.479445] Security Framework v1.0.0 initialized
[   11.479510] SELinux:  Disabled at boot.
[   11.479578] Mount-cache hash table entries: 512
[   11.479854] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   11.479868] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   11.479950] CPU: L2 cache: 512K
[   11.479998] CPU: Hyper-Threading is disabled
[   11.480046] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00000000 00000000 00000000
[   11.480064] Compat vDSO mapped to ffffe000.
[   11.480118] Remapping vsyscall page to ffffe000
[   11.480182] Checking 'hlt' instruction... OK.
[   11.495543] SMP alternatives: switching to UP code
[   11.496019] Freeing SMP alternatives: 11k freed
[   11.496316] Early unpacking initramfs... done
[   11.776790] ACPI: Core revision 20060707
[   11.778016] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   11.802697] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 07
[   11.802851] Total of 1 processors activated (5583.83 BogoMIPS).
[   11.803038] ENABLING IO-APIC IRQs
[   11.803290] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   11.947281] Brought up 1 CPUs
[   11.947589] Booting paravirtualized kernel on bare hardware
[   11.947718] Time:  0:03:42  Date: 05/01/107
[   11.947806] NET: Registered protocol family 16
[   11.947971] EISA bus registered
[   11.948024] ACPI: bus type pci registered
[   11.949369] PCI: PCI BIOS revision 2.10 entry at 0xfbdeb, last bus=1
[   11.949420] PCI: Using configuration type 1
[   11.949468] Setting up standard PCI resources
[   11.985516] ACPI: Interpreter enabled
[   11.985569] ACPI: Using IOAPIC for interrupt routing
[   11.990102] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.990160] PCI: Probing PCI hardware (bus 00)
[   11.990181] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   11.992409] Boot video device is 0000:00:02.0
[   11.992686] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   11.992687] * this clock source is slow. If you are sure your timer does not have
[   11.992688] * this bug, please use "acpi_pm_good" to disable the workaround
[   11.992904] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   11.992956] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   11.993285] PCI: Transparent bridge - 0000:00:1e.0
[   11.993355] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.127982] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   12.150500] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   12.151663] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   12.152815] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   12.153965] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   12.155133] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   12.156385] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   12.157627] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   12.158850] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
[   12.159441] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.159507] pnp: PnP ACPI init
[   12.192845] pnp: PnP ACPI: found 11 devices
[   12.192898] PnPBIOS: Disabled by ACPI PNP
[   12.193007] PCI: Using ACPI for IRQ routing
[   12.193057] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.197193] NET: Registered protocol family 8
[   12.197243] NET: Registered protocol family 20
[   12.205701] pnp: 00:0a: ioport range 0x800-0x85f could not be reserved
[   12.205755] pnp: 00:0a: ioport range 0xc00-0xc7f has been reserved
[   12.205807] pnp: 00:0a: ioport range 0x860-0x8ff could not be reserved
[   12.206166] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   12.206226] PCI: Bridge: 0000:00:1e.0
[   12.206275]   IO window: e000-efff
[   12.206325]   MEM window: ff800000-ff9fffff
[   12.206375]   PREFETCH window: disabled.
[   12.206437] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   12.206472] NET: Registered protocol family 2
[   12.243311] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   12.243619] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   12.245124] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   12.246125] TCP: Hash tables configured (established 131072 bind 65536)
[   12.246188] TCP reno registered
[   12.255426] checking if image is initramfs... it is
[   12.806207] Freeing initrd memory: 6783k freed
[   12.806573] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[   12.806626] Simple Boot Flag at 0x7a set to 0x1
[   12.806955] audit: initializing netlink socket (disabled)
[   12.807022] audit(1180656222.524:1): initialized
[   12.807201] highmem bounce pool size: 64 pages
[   12.807338] VFS: Disk quotas dquot_6.5.1
[   12.807410] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   12.807532] io scheduler noop registered
[   12.807613] io scheduler anticipatory registered
[   12.807693] io scheduler deadline registered
[   12.807783] io scheduler cfq registered (default)
[   12.808196] isapnp: Scanning for PnP cards...
[   13.162308] isapnp: No Plug & Play device found
[   13.192633] Real Time Clock Driver v1.12ac
[   13.192749] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.192933] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.193892] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   13.194241] mice: PS/2 mouse device common for all mice
[   13.194918] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.195303] input: Macintosh mouse button emulation as /class/input/input0
[   13.195392] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   13.195446] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   13.195764] PNP: PS/2 Controller [PNP0f13:MOU] at 0x60,0x64 irq 12
[   13.195816] PNP: PS/2 controller doesn't have KBD irq; using default 1
[   13.199268] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.199327] serio: i8042 AUX port at 0x60,0x64 irq 12
[   13.199570] EISA: Probing bus 0 at eisa.0
[   13.199654] EISA: Detected 0 cards.
[   13.229812] TCP cubic registered
[   13.229865] NET: Registered protocol family 1
[   13.229940] Using IPI No-Shortcut mode
[   13.230063] ACPI: (supports S0 S1 S3 S4 S5)
[   13.230342]   Magic number: 11:581:50
[   13.231063] Time: tsc clocksource has been installed.
[   13.231128] Freeing unused kernel memory: 328k freed
[   13.435520] Capability LSM initialized
[   13.482068] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   14.085068] usbcore: registered new interface driver usbfs
[   14.085153] usbcore: registered new interface driver hub
[   14.085235] usbcore: registered new device driver usb
[   14.086274] USB Universal Host Controller Interface driver v3.0
[   14.086394] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.086499] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   14.086504] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   14.086730] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   14.086818] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[   14.087042] usb usb1: configuration #1 chosen from 1 choice
[   14.087120] hub 1-0:1.0: USB hub found
[   14.087177] hub 1-0:1.0: 2 ports detected
[   14.146028] SCSI subsystem initialized
[   14.151718] libata version 2.20 loaded.
[   14.166467] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[   14.166526] Copyright (c) 1999-2006 Intel Corporation.
[   14.191150] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   14.191260] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   14.191264] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   14.191336] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   14.191424] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[   14.191576] usb usb2: configuration #1 chosen from 1 choice
[   14.191649] hub 2-0:1.0: USB hub found
[   14.191703] hub 2-0:1.0: 2 ports detected
[   14.253651] Floppy drive(s): fd0 is 1.44M
[   14.285865] FDC 0 is a post-1991 82077
[   14.295131] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   14.295243] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   14.295248] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   14.295321] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   14.295408] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[   14.295563] usb usb3: configuration #1 chosen from 1 choice
[   14.295639] hub 3-0:1.0: USB hub found
[   14.295693] hub 3-0:1.0: 2 ports detected
[   14.401308] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   14.401433] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   14.401437] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   14.401544] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   14.401653] ehci_hcd 0000:00:1d.7: debug port 1
[   14.401706] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   14.401719] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa00800
[   14.405654] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.405811] usb usb4: configuration #1 chosen from 1 choice
[   14.405890] hub 4-0:1.0: USB hub found
[   14.405947] hub 4-0:1.0: 6 ports detected
[   14.508935] ICH4: IDE controller at PCI slot 0000:00:1f.1
[   14.508999] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   14.509055] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   14.509158] ICH4: chipset revision 1
[   14.509206] ICH4: not 100% native mode: will probe irqs later
[   14.509265]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[   14.509403]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[   14.509536] Probing IDE interface ide0...
[   14.795004] hda: WDC WD400BB-75DEA0, ATA DISK drive
[   15.038825] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   15.213240] usb 2-1: configuration #1 chosen from 1 choice
[   15.229391] usbcore: registered new interface driver hiddev
[   15.245457] input: Dell Dell USB Keyboard as /class/input/input1
[   15.245533] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.1-1
[   15.245680] usbcore: registered new interface driver usbhid
[   15.245731] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   15.471868] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   15.472023] Probing IDE interface ide1...
[   15.886857] hdc: LG CD-ROM CRN-8245B, ATAPI CD/DVD-ROM drive
[   16.602855] ide1 at 0x170-0x177,0x376 on irq 15
[   16.605549] ACPI: PCI Interrupt 0000:01:0c.0[A] -> GSI 18 (level, low) -> IRQ 18
[   16.614430] hda: max request size: 128KiB
[   16.877378] e1000: 0000:01:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:0b:db:6a:15:83
[   16.877686] hda: Host Protected Area detected.
[   16.877687]  current capacity is 78125000 sectors (40000 MB)
[   16.877689]  native  capacity is 78165360 sectors (40020 MB)
[   16.880378] hda: Host Protected Area disabled.
[   16.880432] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   16.880622] hda: cache flushes not supported
[   16.880727]  hda: hda1 hda2
[   16.892605] hdc: ATAPI 24X CD-ROM drive, 128kB Cache, UDMA(33)
[   16.892849] Uniform CD-ROM driver Revision: 3.20
[   16.916358] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   17.122932] Attempting manual resume
[   17.122982] swsusp: Resume From Partition 3:1
[   17.122984] PM: Checking swsusp image.
[   17.123157] PM: Resume from disk failed.
[   17.177470] kjournald starting.  Commit interval 5 seconds
[   17.177537] EXT3-fs: mounted filesystem with ordered data mode.
[   28.265376] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[   29.727901] NET: Registered protocol family 17
[   30.030934] Linux agpgart interface v0.102 (c) Dave Jones
[   30.036025] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.038082] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.287214] agpgart: Detected an Intel 845G Chipset.
[   30.287392] agpgart: Detected 892K stolen memory.
[   30.302362] agpgart: AGP aperture is 128M @ 0xe8000000
[   30.307139] intel_rng: FWH not detected
[   30.309020] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   30.328437] iTCO_vendor_support: vendor-support=0
[   30.329690] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   30.329838] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   30.329902] iTCO_wdt: No card detected
[   30.576818] input: PC Speaker as /class/input/input2
[   30.655092] logips2pp: Detected unknown logitech mouse model 1
[   30.695777] parport: PnPBIOS parport detected.
[   30.695883] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   31.003380] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   31.003512] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   31.127728] input: PS/2 Logitech Mouse as /class/input/input3
[   31.324586] intel8x0_measure_ac97_clock: measured 58100 usecs
[   31.324646] intel8x0: clocking to 48000
[   31.514635] fuse init (API version 7.8)
[   31.550241] lp0: using parport0 (interrupt-driven).
[   31.587552] Adding 987956k swap on /dev/disk/by-uuid/cd7290ab-5835-4637-a7d8-f37680dc3faa.  Priority:-1 extents:1 across:987956k
[   31.715759] EXT3 FS on hda2, internal journal
[   50.618420] NET: Registered protocol family 10
[   50.618534] lo: Disabled Privacy Extensions
[   61.384459] eth0: no IPv6 routers present
[  124.629221] [drm] Initialized drm 1.1.0 20060810
[  124.638754] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  124.641043] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  205.636671] eth0: no IPv6 routers present
[  245.459215] usb 4-5: new high speed USB device using ehci_hcd and address 3
[  245.592797] usb 4-5: configuration #1 chosen from 1 choice
[  245.715140] usbcore: registered new interface driver libusual
[  245.722953] Initializing USB Mass Storage driver...
[  245.723086] scsi0 : SCSI emulation for USB Mass Storage devices
[  245.723147] usbcore: registered new interface driver usb-storage
[  245.723151] USB Mass Storage support registered.
[  245.723335] usb-storage: device found at 3
[  245.723337] usb-storage: waiting for device to settle before scanning
[  250.722631] usb-storage: device scan complete
[  250.723498] scsi 0:0:0:0: Direct-Access     JetFlash TS4GJF110        0.00 PQ: 0 ANSI: 2
[  250.763716] SCSI device sda: 8191999 512-byte hdwr sectors (4194 MB)
[  250.764328] sda: Write Protect is off
[  250.764331] sda: Mode Sense: 00 00 00 00
[  250.764333] sda: assuming drive cache: write through
[  250.766457] SCSI device sda: 8191999 512-byte hdwr sectors (4194 MB)
[  250.767077] sda: Write Protect is off
[  250.767079] sda: Mode Sense: 00 00 00 00
[  250.767081] sda: assuming drive cache: write through
[  250.767087]  sda: sda1
[  250.818755] sd 0:0:0:0: Attached scsi removable disk sda
[  250.830710] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1243.522320] usb 4-5: USB disconnect, address 3
[ 1251.541188] usb 4-1: new high speed USB device using ehci_hcd and address 4
[ 1251.675695] usb 4-1: configuration #1 chosen from 1 choice
[ 1251.676231] scsi1 : SCSI emulation for USB Mass Storage devices
[ 1251.676423] usb-storage: device found at 4
[ 1251.676425] usb-storage: waiting for device to settle before scanning
[ 1256.676591] usb-storage: device scan complete
[ 1256.677456] scsi 1:0:0:0: Direct-Access     JetFlash TS4GJF110        0.00 PQ: 0 ANSI: 2
[ 1256.679303] SCSI device sda: 8191999 512-byte hdwr sectors (4194 MB)
[ 1256.680525] sda: Write Protect is off
[ 1256.680531] sda: Mode Sense: 00 00 00 00
[ 1256.680534] sda: assuming drive cache: write through
[ 1256.682802] SCSI device sda: 8191999 512-byte hdwr sectors (4194 MB)
[ 1256.683422] sda: Write Protect is off
[ 1256.683425] sda: Mode Sense: 00 00 00 00
[ 1256.683427] sda: assuming drive cache: write through
[ 1256.683431]  sda: sda1
[ 1256.734805] sd 1:0:0:0: Attached scsi removable disk sda
[ 1256.734861] sd 1:0:0:0: Attached scsi generic sg0 type 0

---

### Post by phidia on 2007-05-31
Sorry maybe I should have asked you to attach the dmesg output as a file or just do dmesg | tail
Are you using the 5.10 edubuntu release and can you get to a GUI i.e does your windowmanager finally start?

---

### Post by macmichael01 on 2007-06-01
sorry for late reply.  I have an Intel graphics card in the dell optiplex gx260 and so I had to use the 915resolution driver config with Xorg.  I have to boot up via recovery mode b/c ubuntu freezes when I try to boot up in regular mode.  Then I load gdm and then when I login I get that message. I am using regular ubuntu not edubuntu. and version 7.04.

---

### Post by mark. on 2007-06-09
i also use ubuntu 7/04 and am having this problem, i cant access removable media :/

---

### Post by theorem_hunter on 2007-06-10
i am having the exact same problems :(

i am using 7.04 64bit, 
CPU: AMD Athlon 64 3000+
Graphics: ATI X700

all was working well with edgy 64bit!!!

```

$ uname -a
Linux aa 2.6.20-16-lowlatency #2 SMP PREEMPT Thu Jun 7 19:03:17 UTC 2007 x86_64 GNU/Linux

```

---

### Post by king20878 on 2007-06-17
I managed to get rid of the error by changing the priority of the dbus service in the Services control panel.  If you right-click on the entry you can edit its properties and change it from 20 to 1 for run-levels 3,4, and 5.  That seems to give it enough time to initialize.

Let me know if this works for anyone else.

---


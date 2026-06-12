---
title: "Random Kernel Panics"
date: 2007-08-10
forum: General Help
---

### Post by hackabusa on 2007-08-10
Ever since I first installed ubuntu on this machine, I've gotten seemingly random kernel panics. No message, no logs. Just the flashing scroll and caps locks. At first, I thought that it may have been a problem with my old wireless card (some shoddy 2wire usb adapter), but when I replaced it, the panics persisted. I've done a little research and found that it could possibly be linked to bad RAM or an overheating video card, so I tested both. Memtest86 reported no errors and my video card temperatures didn't rise significantly under stress. I'm not sure what to do at this point. Here's an lsmod and dmesg

```
Module                  Size  Used by
isofs                  36284  1 
udf                    85252  0 
vmnet                  44596  12 
vmblock                16288  3 
vmmon                 452012  0 
binfmt_misc            12680  1 
nfs                   240876  0 
nfsd                  218992  17 
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
ppdev                  10116  0 
fglrx                 540004  11 
ipv6                  268960  8 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  0 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
dock                   10268  0 
sbs                    15652  0 
battery                10756  0 
button                  8720  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
i2c_ec                  6016  1 sbs
ac                      6020  0 
container               5248  0 
video                  16388  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
af_packet              23816  2 
joydev                 10816  0 
wlan_wep                7936  1 
xpad                    9988  0 
usblp                  14848  0 
quickcam               72356  0 
snd_via82xx            29208  1 
videodev               28160  1 quickcam
v4l2_common            25216  1 videodev
v4l1_compat            15236  1 videodev
snd_usb_audio          79744  0 
snd_usb_lib            17280  1 snd_usb_audio
gameport               16520  1 snd_via82xx
snd_mpu401_uart         9472  1 snd_via82xx
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
usbhid                 26592  0 
hid                    27392  1 usbhid
snd_via82xx_modem      16008  0 
snd_ac97_codec         98464  2 snd_via82xx,snd_via82xx_modem
snd_seq_midi            9600  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_hwdep               9988  1 snd_usb_audio
pcspkr                  4224  0 
snd_rawmidi            25472  3 snd_usb_lib,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                79876  5 snd_via82xx,snd_usb_audio,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
wlan_scan_sta          14976  1 
ath_rate_sample        14080  1 
psmouse                38920  0 
snd_timer              23684  2 snd_seq,snd_pcm
ath_pci                97312  0 
serio_raw               7940  0 
k8temp                  6656  0 
i2c_viapro             10132  0 
i2c_core               22656  2 i2c_ec,i2c_viapro
snd_page_alloc         10888  3 snd_via82xx,snd_via82xx_modem,snd_pcm
amd64_agp              13700  1 
agpgart                35400  2 fglrx,amd64_agp
snd                    54020  16 snd_via82xx,snd_usb_audio,snd_mpu401_uart,snd_seq_oss,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore               8672  1 snd
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
wlan                  204868  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci
tsdev                   8768  0 
evdev                  11008  4 
ide_cd                 32672  1 
cdrom                  37664  1 ide_cd
ata_generic             9092  0 
generic                 5124  0 [permanent]
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
floppy                 59524  0 
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  9 xpad,usblp,quickcam,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd
via82cxxx              10372  0 [permanent]
sata_via               12548  2 
libata                125720  2 ata_generic,sata_via
scsi_mod              142348  3 sg,sd_mod,libata
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

```

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003feb0000 end: 000000003ffb0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003ffb0000 size: 0000000000010000 end: 000000003ffc0000 type: 3
[    0.000000] copy_e820_map() start: 000000003ffc0000 size: 0000000000030000 end: 000000003fff0000 type: 4
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 0000000000010000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff780000 size: 0000000000880000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262064) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262064
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262064
[    0.000000] On node 0 totalpages: 262064
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32433 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v002 ACPIAM                                ) @ 0x000fa880
[    0.000000] ACPI: XSDT (v001 A M I  OEMXSDT  0x11000503 MSFT 0x00000097) @ 0x3ffb0100
[    0.000000] ACPI: FADT (v003 A M I  OEMFACP  0x11000503 MSFT 0x00000097) @ 0x3ffb0290
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x11000503 MSFT 0x00000097) @ 0x3ffb0390
[    0.000000] ACPI: OEMB (v001 A M I  OEMBIOS  0x11000503 MSFT 0x00000097) @ 0x3ffc0040
[    0.000000] ACPI: DSDT (v001  A0277 A0277001 0x00000001 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf780000)
[    0.000000] Detected 1802.438 MHz processor.
[   29.070511] Built 1 zonelists.  Total pages: 260017
[   29.070515] Kernel command line: root=UUID=99f11857-e0de-41ff-988d-2c64c2a851d8 ro quiet splash acpi=force lapic
[   29.070663] mapped APIC to ffffd000 (fee00000)
[   29.070665] mapped IOAPIC to ffffc000 (fec00000)
[   29.070668] Enabling fast FPU save and restore... done.
[   29.070671] Enabling unmasked SIMD FPU exception support... done.
[   29.070677] Initializing CPU#0
[   29.070751] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   29.072286] Console: colour VGA+ 80x25
[   29.072610] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   29.072985] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   29.091956] Memory: 1028056k/1048256k available (1992k kernel code, 19480k reserved, 900k data, 328k init, 130752k highmem)
[   29.091966] virtual kernel memory layout:
[   29.091967]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   29.091969]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   29.091970]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   29.091971]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   29.091972]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   29.091974]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   29.091975]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   29.091978] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   29.170738] Calibrating delay using timer specific routine.. 3609.59 BogoMIPS (lpj=7219187)
[   29.170775] Security Framework v1.0.0 initialized
[   29.170781] SELinux:  Disabled at boot.
[   29.170795] Mount-cache hash table entries: 512
[   29.170913] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   29.170922] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   29.170924] CPU: L2 Cache: 512K (64 bytes/line)
[   29.170927] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   29.170937] Compat vDSO mapped to ffffe000.
[   29.170941] Remapping vsyscall page to ffffe000
[   29.170950] Checking 'hlt' instruction... OK.
[   29.186848] SMP alternatives: switching to UP code
[   29.187025] Freeing SMP alternatives: 11k freed
[   29.187201] Early unpacking initramfs... done
[   29.496382] ACPI: Core revision 20060707
[   29.496786] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   29.498552] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 02
[   29.498571] Total of 1 processors activated (3609.59 BogoMIPS).
[   29.499070] ENABLING IO-APIC IRQs
[   29.499393] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   29.646671] Brought up 1 CPUs
[   29.646879] Booting paravirtualized kernel on bare hardware
[   29.646974] Time:  4:19:11  Date: 07/10/107
[   29.646995] NET: Registered protocol family 16
[   29.647061] EISA bus registered
[   29.647064] ACPI: bus type pci registered
[   29.647653] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   29.647656] PCI: Using configuration type 1
[   29.647657] Setting up standard PCI resources
[   29.656765] ACPI: Interpreter enabled
[   29.656767] ACPI: Using IOAPIC for interrupt routing
[   29.657775] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   29.657780] PCI: Probing PCI hardware (bus 00)
[   29.658725] PCI: enabled onboard AC97/MC97 devices
[   29.658983] Boot video device is 0000:01:00.0
[   29.659082] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   29.675014] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[   29.675260] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[   29.675499] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[   29.675742] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   29.675987] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   29.676228] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   29.676469] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   29.676712] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   29.676819] Linux Plug and Play Support v0.97 (c) Adam Belay
[   29.676827] pnp: PnP ACPI init
[   29.680581] pnp: PnP ACPI: found 13 devices
[   29.680584] PnPBIOS: Disabled by ACPI PNP
[   29.680624] PCI: Using ACPI for IRQ routing
[   29.680626] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.687727] NET: Registered protocol family 8
[   29.687729] NET: Registered protocol family 20
[   29.688416] pnp: 00:08: ioport range 0x680-0x6ff has been reserved
[   29.688419] pnp: 00:08: ioport range 0x290-0x297 has been reserved
[   29.688623] PCI: Bridge: 0000:00:01.0
[   29.688626]   IO window: e000-efff
[   29.688631]   MEM window: fbd00000-fbffffff
[   29.688634]   PREFETCH window: d0000000-faffffff
[   29.688652] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   29.688674] NET: Registered protocol family 2
[   29.726677] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   29.726807] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   29.727562] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   29.727940] TCP: Hash tables configured (established 131072 bind 65536)
[   29.727943] TCP reno registered
[   29.738729] checking if image is initramfs... it is
[   30.345743] Freeing initrd memory: 6787k freed
[   30.346085] audit: initializing netlink socket (disabled)
[   30.346096] audit(1186719551.348:1): initialized
[   30.346148] highmem bounce pool size: 64 pages
[   30.346195] VFS: Disk quotas dquot_6.5.1
[   30.346211] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.346250] io scheduler noop registered
[   30.346252] io scheduler anticipatory registered
[   30.346255] io scheduler deadline registered
[   30.346261] io scheduler cfq registered (default)
[   30.370626] isapnp: Scanning for PnP cards...
[   30.724975] isapnp: No Plug & Play device found
[   30.746243] Real Time Clock Driver v1.12ac
[   30.746280] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.746413] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.746989] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.747145] mice: PS/2 mouse device common for all mice
[   30.747539] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.747706] input: Macintosh mouse button emulation as /class/input/input0
[   30.747731] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   30.747734] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   30.747985] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   30.748377] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.748380] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.748467] EISA: Probing bus 0 at eisa.0
[   30.748475] Cannot allocate resource for EISA slot 1
[   30.748504] EISA: Detected 0 cards.
[   30.778649] TCP cubic registered
[   30.778658] NET: Registered protocol family 1
[   30.778675] Using IPI No-Shortcut mode
[   30.778737] ACPI: (supports S0 S1 S3 S4 S5)
[   30.778775]   Magic number: 3:455:312
[   30.778798]   hash matches device ttyxf
[   30.779074] Freeing unused kernel memory: 328k freed
[   30.782366] Time: tsc clocksource has been installed.
[   30.791650] input: AT Translated Set 2 keyboard as /class/input/input1
[   32.020384] Capability LSM initialized
[   32.059615] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   32.573062] SCSI subsystem initialized
[   32.577268] libata version 2.20 loaded.
[   32.578416] sata_via 0000:00:0f.0: version 2.1
[   32.578439] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 16
[   32.578456] sata_via 0000:00:0f.0: routed to hard irq line 10
[   32.578504] ata1: SATA max UDMA/133 cmd 0x0001c000 ctl 0x0001b802 bmdma 0x0001a800 irq 16
[   32.578530] ata2: SATA max UDMA/133 cmd 0x0001b400 ctl 0x0001b002 bmdma 0x0001a808 irq 16
[   32.578547] scsi0 : sata_via
[   32.596921] usbcore: registered new interface driver usbfs
[   32.596944] usbcore: registered new interface driver hub
[   32.596962] usbcore: registered new device driver usb
[   32.631484] USB Universal Host Controller Interface driver v3.0
[   32.779196] Floppy drive(s): fd0 is 1.44M
[   32.785769] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   32.827779] FDC 0 is a post-1991 82077
[   32.953336] ATA: abnormal status 0x7F on port 0x0001c007
[   32.964940] ATA: abnormal status 0x7F on port 0x0001c007
[   32.974048] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   32.974053] ata1.00: ATA-7: WDC WD1600JS-00NCB1, 10.02E02, max UDMA/133
[   32.974056] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   32.986037] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   32.986041] ata1.00: configured for UDMA/133
[   32.986049] scsi1 : sata_via
[   33.193642] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   33.205236] ATA: abnormal status 0x7F on port 0x0001b407
[   33.205826] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JS-00N 10.0 PQ: 0 ANSI: 5
[   33.206511] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   33.206527] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 16
[   33.206537] VP_IDE: chipset revision 6
[   33.206539] VP_IDE: not 100% native mode: will probe irqs later
[   33.206550] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   33.206558]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
[   33.206570]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[   33.206579] Probing IDE interface ide0...
[   33.223022] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   33.223038] sda: Write Protect is off
[   33.223040] sda: Mode Sense: 00 3a 00 00
[   33.223052] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.223097] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   33.223103] sda: Write Protect is off
[   33.223105] sda: Mode Sense: 00 3a 00 00
[   33.223116] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.223119]  sda: sda1 sda2 < sda5 >
[   33.258440] sd 0:0:0:0: Attached scsi disk sda
[   33.262317] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   33.462620] Attempting manual resume
[   33.462623] swsusp: Resume From Partition 8:5
[   33.462625] PM: Checking swsusp image.
[   33.462815] PM: Resume from disk failed.
[   33.475694] EXT3-fs: INFO: recovery required on readonly filesystem.
[   33.475698] EXT3-fs: write access will be enabled during recovery.
[   33.777478] Probing IDE interface ide1...
[   34.645355] hdc: LITE-ON DVDRW SHW-160P6S, ATAPI CD/DVD-ROM drive
[   35.317613] ide1 at 0x170-0x177,0x376 on irq 15
[   35.334328] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 17
[   35.334340] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   35.334572] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   35.334605] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000c400
[   35.335058] usb usb1: configuration #1 chosen from 1 choice
[   35.335083] hub 1-0:1.0: USB hub found
[   35.335090] hub 1-0:1.0: 2 ports detected
[   35.349100] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   35.349135] Uniform CD-ROM driver Revision: 3.20
[   35.441128] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 17
[   35.441140] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   35.441158] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   35.441183] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000c800
[   35.441262] usb usb2: configuration #1 chosen from 1 choice
[   35.441282] hub 2-0:1.0: USB hub found
[   35.441287] hub 2-0:1.0: 2 ports detected
[   35.545071] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 17
[   35.545081] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   35.545099] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   35.545123] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000d000
[   35.545205] usb usb3: configuration #1 chosen from 1 choice
[   35.545225] hub 3-0:1.0: USB hub found
[   35.545231] hub 3-0:1.0: 2 ports detected
[   35.649049] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 17
[   35.649061] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   35.649079] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   35.649104] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000d400
[   35.649189] usb usb4: configuration #1 chosen from 1 choice
[   35.649212] hub 4-0:1.0: USB hub found
[   35.649218] hub 4-0:1.0: 2 ports detected
[   35.680944] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   35.753125] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 17
[   35.753139] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   35.753163] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   35.753201] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfbc00000
[   35.753209] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   35.753290] usb usb5: configuration #1 chosen from 1 choice
[   35.753312] hub 5-0:1.0: USB hub found
[   35.753318] hub 5-0:1.0: 8 ports detected
[   36.216788] usb 1-1: device not accepting address 2, error -71
[   36.603101] kjournald starting.  Commit interval 5 seconds
[   36.603114] EXT3-fs: sda1: orphan cleanup on readonly fs
[   36.603120] ext3_orphan_cleanup: deleting unreferenced inode 2736132
[   36.603169] EXT3-fs: sda1: 1 orphan inode deleted
[   36.603171] EXT3-fs: recovery complete.
[   36.610490] EXT3-fs: mounted filesystem with ordered data mode.
[   37.776378] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   37.948531] usb 1-1: configuration #1 chosen from 1 choice
[   37.951481] hub 1-1:1.0: USB hub found
[   37.954458] hub 1-1:1.0: 4 ports detected
[   38.304199] usb 1-2: new full speed USB device using uhci_hcd and address 5
[   38.475296] usb 1-2: configuration #1 chosen from 1 choice
[   38.478245] hub 1-2:1.0: USB hub found
[   38.481219] hub 1-2:1.0: 4 ports detected
[   38.817070] usb 1-1.1: new full speed USB device using uhci_hcd and address 6
[   38.965072] usb 1-1.1: configuration #1 chosen from 1 choice
[   38.968032] hub 1-1.1:1.0: USB hub found
[   38.970998] hub 1-1.1:1.0: 2 ports detected
[   39.305849] usb 1-1.2: new full speed USB device using uhci_hcd and address 7
[   39.459832] usb 1-1.2: configuration #1 chosen from 1 choice
[   39.693673] usb 1-2.1: new full speed USB device using uhci_hcd and address 8
[   39.811675] usb 1-2.1: configuration #1 chosen from 1 choice
[   40.045514] usb 1-1.1.1: new full speed USB device using uhci_hcd and address 9
[   40.196547] usb 1-1.1.1: configuration #1 chosen from 1 choice
[   40.433338] usb 1-1.1.2: new full speed USB device using uhci_hcd and address 10
[   40.586329] usb 1-1.1.2: configuration #1 chosen from 1 choice
[   45.673059] ath_hal: module license 'Proprietary' taints kernel.
[   45.673617] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   46.434730] wlan: 0.8.4.2 (0.9.3.1)
[   46.459917] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.461439] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.583942] Linux agpgart interface v0.102 (c) Dave Jones
[   46.585130] agpgart: Detected AGP bridge 0
[   46.592180] agpgart: AGP aperture is 256M @ 0xc0000000
[   46.704037] ath_pci: 0.9.4.5 (0.9.3.1)
[   46.704089] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 18 (level, low) -> IRQ 18
[   47.349399] ath_rate_sample: 1.2 (0.9.3.1)
[   47.349602] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   47.349607] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   47.349616] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   47.349620] wifi0: mac 7.8 phy 4.5 radio 5.6
[   47.349624] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   47.349626] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   47.349628] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   47.349630] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   47.349632] wifi0: Use hw queue 8 for CAB traffic
[   47.349656] wifi0: Use hw queue 9 for beacons
[   47.369351] wifi0: Atheros 5212: mem=0xfba00000, irq=18
[   47.801996] input: PC Speaker as /class/input/input2
[   48.044214] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   48.044223] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 19
[   48.112092] usbcore: registered new interface driver hiddev
[   48.218667] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   48.234864] Linux video capture interface: v2.00
[   48.268900] input: HID 19fa:8d91 as /class/input/input4
[   48.268930] input: USB HID v1.10 Joystick [HID 19fa:8d91] on usb-0000:00:10.0-2.1
[   48.268954] usbcore: registered new interface driver snd-usb-audio
[   48.291595] input: HID 19fa:8d91 as /class/input/input5
[   48.291644] input: USB HID v1.10 Joystick [HID 19fa:8d91] on usb-0000:00:10.0-2.1
[   48.291663] usbcore: registered new interface driver usbhid
[   48.291666] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   48.391749] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[   48.391755] quickcam: Kernel:2.6.20-16-generic bus:1 class:FF subclass:FF vendor:046D product:0850
[   48.405731] quickcam: Sensor VV6410 detected
[   48.407775] quickcam: Registered device: /dev/video0
[   48.407803] usbcore: registered new interface driver xpad
[   48.407807] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   48.408251] usbcore: registered new interface driver quickcam
[   48.529720] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 10 if 0 alt 0 proto 2 vid 0x043D pid 0x00FF
[   48.529732] usbcore: registered new interface driver usblp
[   48.529735] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   48.797233] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   49.301278] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   49.301285] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   49.301406] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 19
[   49.301543] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   49.709662] NET: Registered protocol family 17
[   49.963578] fuse init (API version 7.8)
[   50.022932] lp: driver loaded but no devices found
[   50.055556] Adding 3028212k swap on /dev/disk/by-uuid/32ba4f77-ca28-4152-b0e4-507654093d85.  Priority:-1 extents:1 across:3028212k
[   50.197368] EXT3 FS on sda1, internal journal
[   52.093869] input: Power Button (FF) as /class/input/input6
[   52.097295] ACPI: Power Button (FF) [PWRF]
[   52.131264] input: Power Button (CM) as /class/input/input7
[   52.134707] ACPI: Power Button (CM) [PWRB]
[   52.168807] input: Sleep Button (CM) as /class/input/input8
[   52.172232] ACPI: Sleep Button (CM) [SLPB]
[   52.238552] Using specific hotkey driver
[   52.254304] ibm_acpi: ec object not found
[   52.282186] No dock devices found.
[   52.349542] pcc_acpi: loading...
[   52.544421] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[   52.546706] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   53.863365] NET: Registered protocol family 10
[   53.863438] lo: Disabled Privacy Extensions
[   59.734751] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[   59.734989] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   59.988846] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   60.117553] ppdev: user-space parallel port driver
[   62.954600] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   62.954605] apm: overridden by ACPI.
[   63.398349] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   63.398357] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   63.398361] [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of chipset)
[   63.398959] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   63.399131] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   63.399344] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   63.399509] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[   63.405200] [fglrx] total      GART = 268435456
[   63.405206] [fglrx] free       GART = 252440576
[   63.405208] [fglrx] max single GART = 252440576
[   63.405210] [fglrx] total      LFB  = 134217728
[   63.405212] [fglrx] free       LFB  = 116387840
[   63.405214] [fglrx] max single LFB  = 116387840
[   63.405216] [fglrx] total      Inv  = 134217728
[   63.405218] [fglrx] free       Inv  = 134217728
[   63.405220] [fglrx] max single Inv  = 134217728
[   63.405222] [fglrx] total      TIM  = 0
[   64.084062] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   64.221164] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   64.221563] NFSD: starting 90-second grace period
[   64.740711] ath0: no IPv6 routers present
[   66.733797] /dev/vmmon[5245]: VMCI: Driver initialized.
[   66.735918] /dev/vmmon[5245]: Module vmmon: registered with major=10 minor=165
[   66.736163] /dev/vmmon[5245]: Module vmmon: initialized
[   67.709657] /dev/vmnet: open called by PID 5294 (vmnet-bridge)
[   67.709895] /dev/vmnet: hub 0 does not exist, allocating memory.
[   67.710052] /dev/vmnet: port on hub 0 successfully opened
[   67.710194] bridge-eth0: peer interface eth0 not found, will wait for it to come up
[   67.710346] bridge-eth0: attached
[   67.953277] /dev/vmnet: open called by PID 5310 (vmnet-dhcpd)
[   67.953446] /dev/vmnet: hub 1 does not exist, allocating memory.
[   67.953594] /dev/vmnet: port on hub 1 successfully opened
[   67.977815] /dev/vmnet: open called by PID 5321 (vmnet-dhcpd)
[   67.977988] /dev/vmnet: hub 2 does not exist, allocating memory.
[   67.978158] /dev/vmnet: port on hub 2 successfully opened
[   67.993753] /dev/vmnet: open called by PID 5326 (vmnet-natd)
[   67.993969] /dev/vmnet: port on hub 2 successfully opened
[   78.083048] /dev/vmnet: open called by PID 5525 (vmnet-netifup)
[   78.083133] /dev/vmnet: port on hub 1 successfully opened
[   78.085389] /dev/vmnet: open called by PID 5526 (vmnet-netifup)
[   78.085470] /dev/vmnet: port on hub 2 successfully opened
[   88.106102] vmnet1: no IPv6 routers present
[   88.366028] vmnet2: no IPv6 routers present

```

Thanks in advance, and I hope that I'm posting this in the right forum.

---

### Post by hackabusa on 2007-08-10
Please help someone. This problem isn't going to fix itself.

---


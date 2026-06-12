---
title: "AGPGART not enabling AGP in Feisty"
date: 2007-08-23
forum: General Help
---

### Post by Mole Nerd on 2007-08-23
I installed the restricted drivers via System->Administration->Restricted Drivers Manager.  After installation, AGP did not work, so I set: 'Option "NvAGP" "2"', which was recommended in these forums.  AGP also did not work, with 'Option "NvAGP" "1"'.

The next thing I did was edit "/etc/modprobe.d/blacklist" to blacklist the following in different combinations, which was also recommended in these forums:
blacklist i2c_ec
blacklist i2c_viapro
blacklist i2c_core 
blacklist nvidia_agp
blacklist amd64_agp

AGP still does not work.

I rebooted, AGP still does not work.

The following should help you understand the problem:

```
/proc/driver/nvidia/version
NVRM version: NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
GCC version:  gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
```

```
/proc/driver/nvidia/cards/0
Model: 		 GeForce FX 5200
IRQ:   		 20
Video BIOS: 	 04.34.20.87.00
Card Type: 	 AGP
DMA Size: 	 32 bits
DMA Mask: 	 0xffffffff/proc/driver/nvidia/agp/card
Fast Writes: 	 Supported
SBA: 		 Supported
AGP Rates: 	 8x 4x 
Registers: 	 0x1f000e1b:0x00000000
```

```
/proc/driver/nvidia/agp/host-bridge
Host Bridge: 	 PCI device 1106:0282
Fast Writes: 	 Supported
SBA: 		 Supported
AGP Rates: 	 8x 4x 
Registers: 	 0x1f000a1b:0x00000000
```

```
/proc/driver/nvidia/agp/status
Status: 	 Disabled

AGP initialization failed, please check the ouput  
of the 'dmesg' command and/or your system log file 
for additional information on this problem. 
```

```
/proc/driver/nvidia/registry
VideoMemoryTypeOverride: 1
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
SoftEDIDs: 1
Mobile: 4294967295
ResmanDebugLevel: 4294967295
FlatPanelMode: 0
DevicesConnected: 0
RmLogonRC: 1
VbiosFromROM: 0
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UseCPA: 4294967295
DetectPrimaryVga: 1
SaveVBios: 0
EnableBrightnessControl: 0
PanelPWMFrequency: 1018
PanelBrightnessLimits: 65280
RMEdgeIntrCheck: 1
```

```
/proc/modules
snd_rtctimer 4384 1 - Live 0xf8e30000
binfmt_misc 12680 1 - Live 0xf8e2b000
rfcomm 40856 0 - Live 0xf8e5b000
l2cap 25856 5 rfcomm, Live 0xf8e34000
bluetooth 55908 4 rfcomm,l2cap, Live 0xf8e3e000
ppdev 10116 0 - Live 0xf8d29000
cpufreq_userspace 5408 0 - Live 0xf8d30000
cpufreq_stats 7360 0 - Live 0xf8d2d000
cpufreq_powersave 2688 0 - Live 0xf88c9000
cpufreq_ondemand 9228 0 - Live 0xf8d1b000
freq_table 5792 2 cpufreq_stats,cpufreq_ondemand, Live 0xf8d26000
cpufreq_conservative 8200 0 - Live 0xf8d22000
tc1100_wmi 8068 0 - Live 0xf8d1f000
pcc_acpi 13184 0 - Live 0xf8d11000
dev_acpi 12292 0 - Live 0xf8d16000
sony_acpi 6284 0 - Live 0xf8ab5000
video 16388 0 - Live 0xf8d06000
sbs 15652 0 - Live 0xf8d0c000
i2c_ec 6016 1 sbs, Live 0xf8ab8000
dock 10268 0 - Live 0xf8d02000
button 8720 0 - Live 0xf8cfe000
battery 10756 0 - Live 0xf88f9000
container 5248 0 - Live 0xf8ab2000
ac 6020 0 - Live 0xf8a95000
asus_acpi 17308 0 - Live 0xf8cf8000
backlight 7040 1 asus_acpi, Live 0xf8a12000
af_packet 23816 0 - Live 0xf8cf1000
lp 12452 0 - Live 0xf8aa5000
snd_via82xx 29208 1 - Live 0xf8abc000
gameport 16520 1 snd_via82xx, Live 0xf8aac000
nvidia 4713780 22 - Live 0xf9068000 (P)
snd_mpu401_uart 9472 1 snd_via82xx, Live 0xf8a1f000
ide_cd 32672 0 - Live 0xf8a36000
usbhid 26592 0 - Live 0xf8a8d000
cdrom 37664 1 ide_cd, Live 0xf8a9a000
snd_via82xx_modem 16008 0 - Live 0xf8a31000
hid 27392 1 usbhid, Live 0xf8a85000
snd_seq_dummy 4740 0 - Live 0xf898f000
snd_seq_oss 32896 0 - Live 0xf8a60000
agpgart 35400 1 nvidia, Live 0xf8a56000
psmouse 38920 0 - Live 0xf8a4b000
snd_ac97_codec 98464 2 snd_via82xx,snd_via82xx_modem, Live 0xf8a6b000
ac97_bus 3200 1 snd_ac97_codec, Live 0xf8878000
snd_pcm_oss 44544 0 - Live 0xf8a3f000
snd_mixer_oss 17408 1 snd_pcm_oss, Live 0xf8a19000
snd_seq_midi 9600 0 - Live 0xf898b000
snd_rawmidi 25472 2 snd_mpu401_uart,snd_seq_midi, Live 0xf89c6000
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi, Live 0xf8987000
snd_seq 52592 7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xf8a23000
i2c_core 22656 2 i2c_ec,nvidia, Live 0xf89bf000
serio_raw 7940 0 - Live 0xf8959000
snd_seq_device 9100 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xf8907000
parport_pc 36388 1 - Live 0xf89b5000
parport 36936 3 ppdev,lp,parport_pc, Live 0xf8994000
k8temp 6656 0 - Live 0xf8904000
snd_pcm 79876 4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss, Live 0xf89a0000
snd_timer 23684 3 snd_rtctimer,snd_seq,snd_pcm, Live 0xf8980000
pcspkr 4224 0 - Live 0xf8901000
ata_generic 9092 0 - Live 0xf88fd000
snd_page_alloc 10888 3 snd_via82xx,snd_via82xx_modem,snd_pcm, Live 0xf887a000
snd 54020 15 snd_via82xx,snd_mpu401_uart,snd_via82xx_modem,snd_seq_oss,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm,snd_timer, Live 0xf894a000
soundcore 8672 1 snd, Live 0xf88eb000
shpchp 34324 0 - Live 0xf8940000
pci_hotplug 32576 1 shpchp, Live 0xf8937000
ipv6 268960 10 - Live 0xf89cf000
evdev 11008 4 - Live 0xf88d7000
tsdev 8768 0 - Live 0xf88c5000
ext3 133128 1 - Live 0xf895e000
jbd 59816 1 ext3, Live 0xf8927000
mbcache 9604 1 ext3, Live 0xf88d3000
sg 36252 0 - Live 0xf891d000
sd_mod 23428 3 - Live 0xf88e4000
via82cxxx 10372 0 [permanent], Live 0xf8824000
floppy 59524 0 - Live 0xf890d000
ehci_hcd 34188 0 - Live 0xf88ef000
via_rhine 25608 0 - Live 0xf88dc000
mii 6528 1 via_rhine, Live 0xf88c2000
uhci_hcd 25360 0 - Live 0xf88cb000
usbcore 134280 4 usbhid,ehci_hcd,uhci_hcd, Live 0xf8856000
generic 5124 0 [permanent], Live 0xf8849000
sata_via 12548 2 - Live 0xf8851000
libata 125720 2 ata_generic,sata_via, Live 0xf88a2000
scsi_mod 142348 3 sg,sd_mod,libata, Live 0xf887e000
thermal 14856 0 - Live 0xf884c000
processor 31048 1 thermal, Live 0xf8831000
fan 5636 0 - Live 0xf882e000
fbcon 42656 0 - Live 0xf883a000
tileblit 3584 1 fbcon, Live 0xf882c000
font 9216 1 fbcon, Live 0xf8828000
bitblit 6912 1 fbcon, Live 0xf881f000
softcursor 3200 1 bitblit, Live 0xf8822000
vesafb 9220 0 - Live 0xf8804000
capability 5896 0 - Live 0xf881c000
commoncap 8192 1 capability, Live 0xf8819000
```

```
/usr/bin/lspci -d "10de:*" -v -xxx

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA])
	Subsystem: Giga-byte Technology Unknown device 3419
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 20
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at faf00000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 3.0
```

```
Scanning kernel log files for NVRM messages:

  /var/log/messages:
Aug 23 07:40:18 mayumi-desktop kernel: [54498.395273] NVRM: not using NVAGP, an AGPGART backend is loaded!
Aug 23 16:20:02 mayumi-desktop kernel: [85674.905833] NVRM: not using NVAGP, an AGPGART backend is loaded!
Aug 23 17:09:10 mayumi-desktop kernel: [   50.461165] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
Aug 23 17:20:32 mayumi-desktop kernel: [  137.147974] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
Aug 23 17:57:21 mayumi-desktop kernel: [   48.205141] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
Aug 23 18:04:24 mayumi-desktop kernel: [   50.311769] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
Aug 23 18:19:36 mayumi-desktop kernel: [   49.082508] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
Aug 23 18:28:16 mayumi-desktop kernel: [   50.189582] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
```

```
dmesg:

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
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000fab00
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x09000530 MSFT 0x00000097) @ 0x3ffb0000
[    0.000000] ACPI: FADT (v001 A M I  OEMFACP  0x09000530 MSFT 0x00000097) @ 0x3ffb0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x09000530 MSFT 0x00000097) @ 0x3ffb0390
[    0.000000] ACPI: OEMB (v001 A M I  OEMBIOS  0x09000530 MSFT 0x00000097) @ 0x3ffc0040
[    0.000000] ACPI: DSDT (v001  A0232 A0232008 0x00000008 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bf780000)
[    0.000000] Detected 1602.280 MHz processor.
[   18.807315] Built 1 zonelists.  Total pages: 260017
[   18.807319] Kernel command line: root=UUID=cdd15960-a8c4-4621-9405-891686ceed7e ro quiet splash
[   18.807477] mapped APIC to ffffd000 (fee00000)
[   18.807480] mapped IOAPIC to ffffc000 (fec00000)
[   18.807484] Enabling fast FPU save and restore... done.
[   18.807487] Enabling unmasked SIMD FPU exception support... done.
[   18.807495] Initializing CPU#0
[   18.807571] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   18.809053] Console: colour VGA+ 80x25
[   18.809604] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.810535] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.836358] Memory: 1028056k/1048256k available (1992k kernel code, 19444k reserved, 900k data, 328k init, 130752k highmem)
[   18.836370] virtual kernel memory layout:
[   18.836372]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   18.836373]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.836375]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   18.836376]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   18.836378]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   18.836379]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   18.836381]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   18.836384] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.915556] Calibrating delay using timer specific routine.. 3208.28 BogoMIPS (lpj=6416575)
[   18.915605] Security Framework v1.0.0 initialized
[   18.915614] SELinux:  Disabled at boot.
[   18.915631] Mount-cache hash table entries: 512
[   18.915788] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[   18.915797] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   18.915800] CPU: L2 Cache: 128K (64 bytes/line)
[   18.915804] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[   18.915816] Compat vDSO mapped to ffffe000.
[   18.915820] Remapping vsyscall page to ffffe000
[   18.915831] Checking 'hlt' instruction... OK.
[   18.931700] SMP alternatives: switching to UP code
[   18.931979] Freeing SMP alternatives: 11k freed
[   18.932243] Early unpacking initramfs... done
[   19.280362] ACPI: Core revision 20060707
[   19.280854] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   19.282758] CPU0: AMD Sempron(tm) Processor 2600+ stepping 02
[   19.282781] Total of 1 processors activated (3208.28 BogoMIPS).
[   19.283283] ENABLING IO-APIC IRQs
[   19.283614] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   19.427483] Brought up 1 CPUs
[   19.427753] Booting paravirtualized kernel on bare hardware
[   19.427861] Time: 23:27:38  Date: 07/23/107
[   19.427899] NET: Registered protocol family 16
[   19.428003] EISA bus registered
[   19.428008] ACPI: bus type pci registered
[   19.428716] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   19.428718] PCI: Using configuration type 1
[   19.428720] Setting up standard PCI resources
[   19.440437] ACPI: Interpreter enabled
[   19.440444] ACPI: Using IOAPIC for interrupt routing
[   19.441626] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.441634] PCI: Probing PCI hardware (bus 00)
[   19.442417] PCI: enabled onboard AC97/MC97 devices
[   19.442684] Boot video device is 0000:01:00.0
[   19.442727] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.460488] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[   19.460758] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[   19.461022] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[   19.461286] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   19.461559] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   19.461823] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   19.462086] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   19.462356] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[   19.462480] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.462492] pnp: PnP ACPI init
[   19.466711] pnp: PnP ACPI: found 13 devices
[   19.466718] PnPBIOS: Disabled by ACPI PNP
[   19.466780] PCI: Using ACPI for IRQ routing
[   19.466783] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.471345] NET: Registered protocol family 8
[   19.471347] NET: Registered protocol family 20
[   19.472057] pnp: 00:08: ioport range 0x290-0x297 has been reserved
[   19.472335] PCI: Bridge: 0000:00:01.0
[   19.472337]   IO window: disabled.
[   19.472342]   MEM window: faf00000-fbffffff
[   19.472345]   PREFETCH window: f0000000-f9ffffff
[   19.472365] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   19.472403] NET: Registered protocol family 2
[   19.511515] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.511725] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   19.513019] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   19.513682] TCP: Hash tables configured (established 131072 bind 65536)
[   19.513687] TCP reno registered
[   19.523575] checking if image is initramfs... it is
[   20.210433] Freeing initrd memory: 6751k freed
[   20.210874] audit: initializing netlink socket (disabled)
[   20.210889] audit(1187911658.480:1): initialized
[   20.210953] highmem bounce pool size: 64 pages
[   20.211037] VFS: Disk quotas dquot_6.5.1
[   20.211061] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.211118] io scheduler noop registered
[   20.211121] io scheduler anticipatory registered
[   20.211123] io scheduler deadline registered
[   20.211137] io scheduler cfq registered (default)
[   28.210051] 0000:00:10.4 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   28.210439] isapnp: Scanning for PnP cards...
[   28.564291] isapnp: No Plug & Play device found
[   28.605459] Real Time Clock Driver v1.12ac
[   28.605503] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.605616] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.606697] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.607005] mice: PS/2 mouse device common for all mice
[   28.607466] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.607718] input: Macintosh mouse button emulation as /class/input/input0
[   28.607750] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   28.607754] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   28.608019] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   28.608022] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   28.608437] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.608443] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.608558] EISA: Probing bus 0 at eisa.0
[   28.608568] Cannot allocate resource for EISA slot 1
[   28.608595] EISA: Detected 0 cards.
[   28.638698] TCP cubic registered
[   28.638709] NET: Registered protocol family 1
[   28.638735] Using IPI No-Shortcut mode
[   28.638840] ACPI: (supports S0 S1 S3 S4 S5)
[   28.638884]   Magic number: 3:109:505
[   28.638888]   hash matches device i8042
[   28.639329] Freeing unused kernel memory: 328k freed
[   28.641370] Time: tsc clocksource has been installed.
[   28.662083] input: AT Translated Set 2 keyboard as /class/input/input1
[   29.943649] Capability LSM initialized
[   30.745953] SCSI subsystem initialized
[   30.751028] libata version 2.20 loaded.
[   30.752434] sata_via 0000:00:0f.0: version 2.1
[   30.752459] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 16
[   30.752478] sata_via 0000:00:0f.0: routed to hard irq line 10
[   30.752530] ata1: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e402 bmdma 0x0001d400 irq 16
[   30.752554] ata2: SATA max UDMA/133 cmd 0x0001e000 ctl 0x0001d802 bmdma 0x0001d408 irq 16
[   30.752573] scsi0 : sata_via
[   30.763999] usbcore: registered new interface driver usbfs
[   30.764021] usbcore: registered new interface driver hub
[   30.764043] usbcore: registered new device driver usb
[   30.831122] USB Universal Host Controller Interface driver v3.0
[   30.841919] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   30.953646] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   30.968686] Floppy drive(s): fd0 is 1.44M
[   31.045920] FDC 0 is a post-1991 82077
[   31.120240] ATA: abnormal status 0x7F on port 0x0001e807
[   31.130836] ATA: abnormal status 0x7F on port 0x0001e807
[   31.137845] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   31.137849] ata1.00: ATA-7: WDC WD800JD-19LSA0, 06.01D06, max UDMA/133
[   31.137852] ata1.00: 156301488 sectors, multi 16: LBA48 
[   31.145847] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[   31.145850] ata1.00: configured for UDMA/133
[   31.145861] scsi1 : sata_via
[   31.349543] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   31.360181] ATA: abnormal status 0x7F on port 0x0001e007
[   31.360313] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JD-19LS 06.0 PQ: 0 ANSI: 5
[   31.362338] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   31.362359] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 16
[   31.362372] VP_IDE: chipset revision 6
[   31.362374] VP_IDE: not 100% native mode: will probe irqs later
[   31.362385] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   31.362394]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   31.362406]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[   31.362413] Probing IDE interface ide0...
[   31.384213] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   31.384243] sda: Write Protect is off
[   31.384246] sda: Mode Sense: 00 3a 00 00
[   31.384259] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.384316] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   31.384325] sda: Write Protect is off
[   31.384327] sda: Mode Sense: 00 3a 00 00
[   31.384339] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.384342]  sda: sda1 sda2 < sda5 >
[   31.436241] sd 0:0:0:0: Attached scsi disk sda
[   31.441353] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   31.645283] Attempting manual resume
[   31.645287] swsusp: Resume From Partition 8:5
[   31.645289] PM: Checking swsusp image.
[   31.645478] PM: Resume from disk failed.
[   31.695856] kjournald starting.  Commit interval 5 seconds
[   31.695870] EXT3-fs: mounted filesystem with ordered data mode.
[   32.225494] hda: LITE-ON DVDRW SHW-160P6S, ATAPI CD/DVD-ROM drive
[   32.897863] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   32.910362] Probing IDE interface ide1...
[   33.477446] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 17
[   33.477461] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   33.477707] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   33.477742] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000b800
[   33.477866] usb usb1: configuration #1 chosen from 1 choice
[   33.477891] hub 1-0:1.0: USB hub found
[   33.477898] hub 1-0:1.0: 2 ports detected
[   33.581325] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 17
[   33.581338] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   33.581363] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   33.581387] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000c000
[   33.581476] usb usb2: configuration #1 chosen from 1 choice
[   33.581502] hub 2-0:1.0: USB hub found
[   33.581509] hub 2-0:1.0: 2 ports detected
[   33.685273] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 17
[   33.685286] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   33.685308] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   33.685331] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000c400
[   33.685423] usb usb3: configuration #1 chosen from 1 choice
[   33.685446] hub 3-0:1.0: USB hub found
[   33.685453] hub 3-0:1.0: 2 ports detected
[   33.789268] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 17
[   33.789281] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   33.789303] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   33.789328] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000c800
[   33.789422] usb usb4: configuration #1 chosen from 1 choice
[   33.789446] hub 4-0:1.0: USB hub found
[   33.789453] hub 4-0:1.0: 2 ports detected
[   33.893484] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 18
[   33.893578] eth0: VIA Rhine II at 0x1b000, 00:15:f2:3f:4d:69, IRQ 18.
[   33.894292] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[   33.894468] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 17
[   33.894480] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   33.894515] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   33.894564] ehci_hcd 0000:00:10.4: irq 17, io mem 0xfad00000
[   33.894571] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.894662] usb usb5: configuration #1 chosen from 1 choice
[   33.894687] hub 5-0:1.0: USB hub found
[   33.894697] hub 5-0:1.0: 8 ports detected
[   33.949127] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   35.332910] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   35.507963] usb 1-2: configuration #1 chosen from 1 choice
[   44.573097] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   45.188671] NET: Registered protocol family 10
[   45.188769] lo: Disabled Privacy Extensions
[   46.905326] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.039764] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.341627] input: PC Speaker as /class/input/input2
[   47.734772] parport: PnPBIOS parport detected.
[   47.734879] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   48.187495] Linux agpgart interface v0.102 (c) Dave Jones
[   48.360650] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   48.360662] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 19
[   48.479736] usbcore: registered new interface driver hiddev
[   48.514480] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[   48.514490] Uniform CD-ROM driver Revision: 3.20
[   48.600696] nvidia: module license 'NVIDIA' taints kernel.
[   48.870869] input: Logitech USB Optical Mouse as /class/input/input3
[   48.870959] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:10.0-2
[   48.870976] usbcore: registered new interface driver usbhid
[   48.870982] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   49.118729] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   49.622851] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   49.622860] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   49.623018] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 19
[   49.623155] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   50.137771] codec_read: codec 0 is not valid [0xfe0000]
[   50.144770] codec_read: codec 0 is not valid [0xfe0000]
[   50.151806] codec_read: codec 0 is not valid [0xfe0000]
[   50.158803] codec_read: codec 0 is not valid [0xfe0000]
[   50.189277] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   50.189582] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   50.414287] lp0: using parport0 (interrupt-driven).
[   50.457989] Adding 3028212k swap on /dev/disk/by-uuid/9d45de11-f1b9-4a3e-9e53-a7fd8d54f259.  Priority:-1 extents:1 across:3028212k
[   50.531377] EXT3 FS on sda1, internal journal
[   52.181594] NET: Registered protocol family 17
[   55.981608] eth0: no IPv6 routers present
[   56.736676] input: Power Button (FF) as /class/input/input4
[   56.741931] ACPI: Power Button (FF) [PWRF]
[   56.783567] input: Power Button (CM) as /class/input/input5
[   56.788798] ACPI: Power Button (CM) [PWRB]
[   56.830175] input: Sleep Button (CM) as /class/input/input6
[   56.835370] ACPI: Sleep Button (CM) [SLPB]
[   56.861834] Using specific hotkey driver
[   56.901975] No dock devices found.
[   56.957218] ibm_acpi: ec object not found
[   57.120070] pcc_acpi: loading...
[   57.506970] powernow-k8: Power state transitions not supported
[   61.773960] ppdev: user-space parallel port driver
[   62.995049] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   62.995055] apm: overridden by ACPI.
[   63.757255] Bluetooth: Core ver 2.11
[   63.757316] NET: Registered protocol family 31
[   63.757318] Bluetooth: HCI device and connection manager initialized
[   63.757322] Bluetooth: HCI socket layer initialized
[   63.782075] Bluetooth: L2CAP ver 2.8
[   63.782080] Bluetooth: L2CAP socket layer initialized
[   63.919812] Bluetooth: RFCOMM socket layer initialized
[   63.919826] Bluetooth: RFCOMM TTY layer initialized
[   63.919829] Bluetooth: RFCOMM ver 1.8
```

---

### Post by MoLE on 2007-09-02
Which motherboard do you have?  Can you get a GUI display at all?

---


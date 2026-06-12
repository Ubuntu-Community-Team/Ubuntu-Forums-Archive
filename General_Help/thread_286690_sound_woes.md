---
title: "sound woes"
date: 2006-10-28
forum: General Help
---

### Post by arashf on 2006-10-28
I'm having a fairly frustrating sound problem. I'm on edgy and my sound was working perfectly until I started playing with some bios settings (namely pnp support and acpi/apic.) After a bit of fooling around, I managed to break my sound. I returned everything to their original settings and still have no sound. Everything looks okay, but I get no sound out of my speakers (and yea, I checked that it's not the speakers...)

Here's the output of aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 [SB0240]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 [SB0240]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 [SB0240]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 [SB0240]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I also went through the majority of [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Background_.2F_Notes_.2F_Warnings](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Background_.2F_Notes_.2F_Warnings)
and wasn't able to figure anything out.

---

### Post by arashf on 2006-10-28
bump... i can provide more outputs:

> arashf@arash:~$ lsmod | grep snd
snd_emu10k1_synth       8960  0 
snd_emux_synth         39296  1 snd_emu10k1_synth
snd_seq_virmidi         8576  1 snd_emux_synth
snd_seq_midi_emul       8192  1 snd_emux_synth
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                59120  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           128288  2 snd_emu10k1_synth
snd_rawmidi            27264  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         97696  1 snd_emu10k1
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          9868  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25348  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            6016  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10756  2 snd_emux_synth,snd_emu10k1
snd                    58372  15 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
soundcore              11232  1 snd


> arashf@arash:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80f6
        Flags: bus master, fast devsel, latency 0
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fe800000-fe8fffff
        Prefetchable memory behind bridge: bff00000-dfefffff

00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fe900000-fe9fffff

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at eec0 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at ef00 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at ef20 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at ef40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at febff800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fea00000-feafffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at fc00 [size=16]
        Memory at 50000000 (32-bit, non-prefetchable) [size=1K]

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASUSTeK Computer Inc. P4P800 SE Mainboard
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 5
        I/O ports at efe0 [size=8]
        I/O ports at efac [size=4]
        I/O ports at efa0 [size=8]
        I/O ports at efa8 [size=4]
        I/O ports at ef90 [size=16]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. P4P800 Mainboard
        Flags: medium devsel, IRQ 11
        I/O ports at 0400 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 4f72
        Flags: bus master, stepping, 66MHz, medium devsel, latency 255
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at b000 [size=256]
        Memory at fe8f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at fe8c0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)
        Subsystem: ATI Technologies Inc Unknown device 4f73
        Flags: bus master, stepping, 66MHz, medium devsel, latency 64
        Memory at c8000000 (32-bit, prefetchable) [size=128M]
        Memory at fe8e0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller (LOM)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80f7
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 5
        Memory at fe9e0000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at cf80 [size=32]
        Capabilities: <access denied>

03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. A8V Deluxe
        Flags: bus master, medium devsel, latency 64, IRQ 10
        Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
        I/O ports at dc00 [size=128]
        Capabilities: <access denied>

03:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs SB0240 Audigy 2 Platinum 6.1
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at df00 [size=64]
        Capabilities: <access denied>

03:0c.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
        Subsystem: Creative Labs SB Audigy MIDI/Game Port
        Flags: bus master, medium devsel, latency 64
        I/O ports at dfe0 [size=8]
        Capabilities: <access denied>

03:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10 [OHCI])
        Subsystem: Creative Labs SB Audigy FireWire Port
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at feaff000 (32-bit, non-prefetchable) [size=2K]
        Memory at feaf8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


> arashf@arash:~$ cat /proc/asound/modules
 0 snd_emu10k1


> arashf@arash:~$ dmesg | grep snd


> arashf@arash:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ff30000 (usable)
[17179569.184000]  BIOS-e820: 000000003ff30000 - 000000003ff40000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ff40000 - 000000003fff0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 261936
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32560 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] Intel MultiProcessor Specification v1.1
[17179569.184000]     Virtual Wire compatibility mode.
[17179569.184000] OEM ID: ASUSTek  Product ID:  APIC at: 0xFEE00000
[17179569.184000] Processor #0 15:2 APIC version 20
[17179569.184000] I/O APIC #2 Version 32 at 0xFEC00000.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Processors: 1
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=9716be10-5ab7-407c-b1e1-31467a8d869f ro quiet splash linux acpi=off noapic nolapic
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2999.148 MHz processor.
[   19.902297] Using tsc for high-res timesource
[   19.903208] Console: colour VGA+ 80x25
[   19.903610] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   19.903997] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   19.926623] Memory: 1027600k/1047744k available (1910k kernel code, 19480k reserved, 1070k data, 308k init, 130240k highmem)
[   19.926627] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.006097] Calibrating delay using timer specific routine.. 6005.83 BogoMIPS (lpj=12011668)
[   20.006133] Security Framework v1.0.0 initialized
[   20.006141] SELinux:  Disabled at boot.
[   20.006153] Mount-cache hash table entries: 512
[   20.006290] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   20.006299] CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   20.006309] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   20.006311] CPU: L2 cache: 512K
[   20.006313] CPU: Hyper-Threading is disabled
[   20.006315] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[   20.006334] Checking 'hlt' instruction... OK.
[   20.022143] SMP alternatives: switching to UP code
[   20.022314] Freeing SMP alternatives: 16k freed
[   20.022431] checking if image is initramfs... it is
[   20.525619] Freeing initrd memory: 6704k freed
[   20.525624] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   20.525658] Total of 1 processors activated (6005.83 BogoMIPS).
[   20.633282] Brought up 1 CPUs
[   20.633296] migration_cost=0
[   20.633585] NET: Registered protocol family 16
[   20.633613] EISA bus registered
[   20.633689] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[   20.633695] PCI: Using configuration type 1
[   20.633697] Setting up standard PCI resources
[   20.641216] ACPI: Interpreter disabled.
[   20.641219] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.641228] pnp: PnP ACPI: disabled
[   20.641232] PnPBIOS: Scanning system for PnP BIOS support...
[   20.641244] PnPBIOS: Found PnP BIOS installation structure at 0xc00f5230
[   20.641247] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x5e1a, dseg 0xf0000
[   20.641769] PNPBIOS fault.. attempting recovery.
[   20.641810] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
[   20.641848] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[   20.641887] PnPBIOS: Check with your vendor for an updated BIOS
[   20.641923] PnPBIOS: get_dev_node: unexpected status 0x37
[   20.641960] PnPBIOS: 12 nodes reported by PnP BIOS; 12 recorded by driver
[   20.642001] PCI: Probing PCI hardware
[   20.642005] PCI: Probing PCI hardware (bus 00)
[   20.642501] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   20.642505] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   20.642555] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[   20.642724] Boot video device is 0000:01:00.0
[   20.643234] PCI: Transparent bridge - 0000:00:1e.0
[   20.643965] PCI: Using IRQ router PIIX/ICH [8086/24d0] at 0000:00:1f.0
[   20.643989] PCI: Found IRQ 5 for device 0000:00:1f.1
[   20.643998] PCI: Sharing IRQ 5 with 0000:00:1d.2
[   20.644007] PCI: Sharing IRQ 5 with 0000:00:1f.2
[   20.644014] PCI: Sharing IRQ 5 with 0000:02:01.0
[   20.650155] PCI: Bridge: 0000:00:01.0
[   20.650159]   IO window: b000-bfff
[   20.650163]   MEM window: fe800000-fe8fffff
[   20.650167]   PREFETCH window: bff00000-dfefffff
[   20.650171] PCI: Bridge: 0000:00:03.0
[   20.650174]   IO window: c000-cfff
[   20.650178]   MEM window: fe900000-fe9fffff
[   20.650181]   PREFETCH window: disabled.
[   20.650186] PCI: Bridge: 0000:00:1e.0
[   20.650189]   IO window: d000-dfff
[   20.650194]   MEM window: fea00000-feafffff
[   20.650197]   PREFETCH window: disabled.
[   20.650219] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.650239] NET: Registered protocol family 2
[   20.681210] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.681354] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.681903] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   20.682378] TCP: Hash tables configured (established 131072 bind 65536)
[   20.682381] TCP reno registered
[   20.683071] audit: initializing netlink socket (disabled)
[   20.683084] audit(1162025999.864:1): initialized
[   20.683173] highmem bounce pool size: 64 pages
[   20.683226] VFS: Disk quotas dquot_6.5.1
[   20.683244] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.683287] Initializing Cryptographic API
[   20.683292] io scheduler noop registered
[   20.683296] io scheduler anticipatory registered
[   20.683301] io scheduler deadline registered
[   20.683314] io scheduler cfq registered (default)
[   28.669989] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   28.670305] isapnp: Scanning for PnP cards...
[   29.027986] isapnp: No Plug & Play device found
[   29.048244] Real Time Clock Driver v1.12ac
[   29.048307] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.048416] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.048561] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.049104] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.049345] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   29.049607] mice: PS/2 mouse device common for all mice
[   29.050572] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.050759] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.050763] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.050978] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[   29.050981] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   29.052953] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.053167] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.053635] EISA: Probing bus 0 at eisa.0
[   29.053673] EISA: Detected 0 cards.
[   29.053895] TCP bic registered
[   29.053902] NET: Registered protocol family 1
[   29.053908] NET: Registered protocol family 8
[   29.053910] NET: Registered protocol family 20
[   29.053930] Using IPI No-Shortcut mode
[   29.054154] Freeing unused kernel memory: 308k freed
[   30.756021] Capability LSM initialized
[   34.925864] ICH5: IDE controller at PCI slot 0000:00:1f.1
[   34.925873] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   34.925881] PCI: Found IRQ 5 for device 0000:00:1f.1
[   34.925891] PCI: Sharing IRQ 5 with 0000:00:1d.2
[   34.925900] PCI: Sharing IRQ 5 with 0000:00:1f.2
[   34.925907] PCI: Sharing IRQ 5 with 0000:02:01.0
[   34.925920] ICH5: chipset revision 2
[   34.925922] ICH5: not 100% native mode: will probe irqs later
[   34.925931]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:DMA
[   34.925944]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[   34.925954] Probing IDE interface ide0...
[   35.836103] hdb: WDC WD1600JB-00GVA0, ATA DISK drive
[   35.953732] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   35.953904] Probing IDE interface ide1...
[   37.314035] hdc: PLEXTOR DVDR PX-708A, ATAPI CD/DVD-ROM drive
[   37.905162] ide1 at 0x170-0x177,0x376 on irq 15
[   38.024998] hdb: max request size: 512KiB
[   38.032798] hdb: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63, UDMA(33)
[   38.034755] hdb: cache flushes supported
[   38.034792]  hdb: hdb1
[   38.155703] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   38.155713] Uniform CD-ROM driver Revision: 3.20
[   38.617788] SCSI subsystem initialized
[   38.620578] libata version 1.20 loaded.
[   38.622107] ata_piix 0000:00:1f.2: version 1.05
[   38.622124] PCI: Found IRQ 5 for device 0000:00:1f.2
[   38.622133] PCI: Sharing IRQ 5 with 0000:00:1d.2
[   38.622142] PCI: Sharing IRQ 5 with 0000:00:1f.1
[   38.622150] PCI: Sharing IRQ 5 with 0000:02:01.0
[   38.622167] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   38.622210] ata1: SATA max UDMA/133 cmd 0xEFE0 ctl 0xEFAE bmdma 0xEF90 irq 5
[   38.622229] ata2: SATA max UDMA/133 cmd 0xEFA0 ctl 0xEFAA bmdma 0xEF98 irq 5
[   38.784373] ata1: dev 0 cfg 49:2f00 82:74eb 83:7f63 84:4003 85:74e9 86:3c43 87:4003 88:207f
[   38.784378] ata1: dev 0 ATA-6, max UDMA/133, 145226112 sectors: LBA48
[   38.792031] ata1: dev 0 configured for UDMA/133
[   38.792034] scsi0 : ata_piix
[   39.039685] ata2: dev 0 cfg 49:2f00 82:7c6b 83:7f09 84:4003 85:7c69 86:3e01 87:4003 88:207f
[   39.039689] ata2: dev 0 ATA-7, max UDMA/133, 490234752 sectors: LBA48
[   39.047673] ata2: dev 0 configured for UDMA/133
[   39.047676] scsi1 : ata_piix
[   39.047863]   Vendor: ATA       Model: WDC WD740GD-00FL  Rev: 27.0
[   39.047878]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   39.048126]   Vendor: ATA       Model: Maxtor 6Y250M0    Rev: YAR5
[   39.048141]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   39.059038] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[   39.059051] sda: Write Protect is off
[   39.059054] sda: Mode Sense: 00 3a 00 00
[   39.059072] SCSI device sda: drive cache: write back
[   39.059125] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[   39.059135] sda: Write Protect is off
[   39.059137] sda: Mode Sense: 00 3a 00 00
[   39.059154] SCSI device sda: drive cache: write back
[   39.059160]  sda: sda1 sda2 < sda5 >
[   39.087286] sd 0:0:0:0: Attached scsi disk sda
[   39.203511] SCSI device sdb: 490234752 512-byte hdwr sectors (251000 MB)
[   39.207204] sdb: Write Protect is off
[   39.207208] sdb: Mode Sense: 00 3a 00 00
[   39.211218] SCSI device sdb: drive cache: write back
[   39.211834] SCSI device sdb: 490234752 512-byte hdwr sectors (251000 MB)
[   39.211885] sdb: Write Protect is off
[   39.211888] sdb: Mode Sense: 00 3a 00 00
[   39.212402] SCSI device sdb: drive cache: write back
[   39.212405]  sdb: [LDM] sdb1
[   39.508531] sd 1:0:0:0: Attached scsi disk sdb
[   40.228757] usbcore: registered new driver usbfs
[   40.228776] usbcore: registered new driver hub
[   40.229486] USB Universal Host Controller Interface driver v3.0
[   40.229532] PCI: Found IRQ 11 for device 0000:00:1d.0
[   40.229544] PCI: Sharing IRQ 11 with 0000:00:1d.3
[   40.229571] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   40.229574] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   40.229683] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   40.229706] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000eec0
[   40.229788] usb usb1: configuration #1 chosen from 1 choice
[   40.229811] hub 1-0:1.0: USB hub found
[   40.229818] hub 1-0:1.0: 2 ports detected
[   40.270897] ieee1394: Initialized config rom entry `ip1394'
[   40.393829] PCI: Found IRQ 5 for device 0000:00:1d.1
[   40.393866] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   40.393870] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   40.393970] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   40.393992] uhci_hcd 0000:00:1d.1: irq 5, io base 0x0000ef00
[   40.394145] usb usb2: configuration #1 chosen from 1 choice
[   40.394243] hub 2-0:1.0: USB hub found
[   40.394251] hub 2-0:1.0: 2 ports detected
[   40.497594] PCI: Found IRQ 5 for device 0000:00:1d.2
[   40.497611] PCI: Sharing IRQ 5 with 0000:00:1f.1
[   40.497614] PCI: Sharing IRQ 5 with 0000:00:1f.2
[   40.497620] PCI: Sharing IRQ 5 with 0000:02:01.0
[   40.497632] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   40.497635] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   40.497732] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   40.497752] uhci_hcd 0000:00:1d.2: irq 5, io base 0x0000ef20
[   40.497903] usb usb3: configuration #1 chosen from 1 choice
[   40.498005] hub 3-0:1.0: USB hub found
[   40.498012] hub 3-0:1.0: 2 ports detected
[   40.601452] PCI: Found IRQ 11 for device 0000:00:1d.3
[   40.601459] PCI: Sharing IRQ 11 with 0000:00:1d.0
[   40.601486] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   40.601490] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   40.601586] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   40.601605] uhci_hcd 0000:00:1d.3: irq 11, io base 0x0000ef40
[   40.601752] usb usb4: configuration #1 chosen from 1 choice
[   40.601854] hub 4-0:1.0: USB hub found
[   40.601862] hub 4-0:1.0: 2 ports detected
[   40.633264] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   40.705401] PCI: Found IRQ 10 for device 0000:00:1d.7
[   40.705437] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   40.705441] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   40.705557] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   40.705589] ehci_hcd 0000:00:1d.7: debug port 1
[   40.705595] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   40.705603] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xfebff800
[   40.709478] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   40.709619] usb usb5: configuration #1 chosen from 1 choice
[   40.709725] hub 5-0:1.0: USB hub found
[   40.709733] hub 5-0:1.0: 8 ports detected
[   40.813177] PCI: Found IRQ 10 for device 0000:03:03.0
[   40.813203] PCI: Sharing IRQ 10 with 0000:03:0c.0
[   40.875342] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   40.882409] PCI: Found IRQ 11 for device 0000:03:0c.2
[   40.932236] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   41.017459] kjournald starting.  Commit interval 5 seconds
[   41.017470] EXT3-fs: mounted filesystem with ordered data mode.
[   41.160527] usb 1-2: device not accepting address 2, error -71
[   42.079247] usb 5-5: new high speed USB device using ehci_hcd and address 4
[   42.151280] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800005061eb]
[   42.278006] usb 5-5: configuration #1 chosen from 1 choice
[   42.422873] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[00023c010103431a]
[   42.514636] usb 1-2: new low speed USB device using uhci_hcd and address 4
[   42.737701] usb 1-2: configuration #1 chosen from 1 choice
[   42.977988] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   43.155578] usb 2-2: configuration #1 chosen from 1 choice
[   48.679406] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   48.743748] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.904167] hw_random hardware driver 1.0.0 loaded
[   49.271646] Linux agpgart interface v0.101 (c) Dave Jones
[   49.350454] agpgart: Detected an Intel i875 Chipset.
[   49.355075] agpgart: AGP aperture is 128M @ 0xe8000000
[   49.475763] Intel(R) PRO/1000 Network Driver - version 7.1.9-k4
[   49.475767] Copyright (c) 1999-2006 Intel Corporation.
[   49.475814] PCI: Found IRQ 5 for device 0000:02:01.0
[   49.475823] PCI: Sharing IRQ 5 with 0000:00:1d.2
[   49.475832] PCI: Sharing IRQ 5 with 0000:00:1f.1
[   49.475835] PCI: Sharing IRQ 5 with 0000:00:1f.2
[   49.475853] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   49.573270] input: PC Speaker as /class/input/input0
[   49.628518] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:0e:a6:2e:93:cf
[   49.770257] Floppy drive(s): fd0 is 1.44M
[   49.833397] FDC 0 is a post-1991 82077
[   49.869662] usbcore: registered new driver hiddev
[   49.900094] input: Microsoft Corporation Microsoft &#65533; Laser Mouse 6000 as /class/input/input1
[   49.900149] input: USB HID v1.11 Mouse [Microsoft Corporation Microsoft &#65533; Laser Mouse 6000] on usb-0000:00:1d.0-2
[   49.906246] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   49.922052] gameport: EMU10K1 is pci0000:03:0c.1/gameport0, io 0xdfe0, speed 1217kHz
[   49.925606] input: Logitech USB Receiver as /class/input/input2
[   49.925642] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   50.049006] input: Logitech USB Receiver as /class/input/input3
[   50.049241] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   50.049252] usbcore: registered new driver usbhid
[   50.049256] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   50.208655] PCI: Found IRQ 10 for device 0000:03:0c.0
[   50.208679] PCI: Sharing IRQ 10 with 0000:03:03.0
[   50.211694] Installing spdif_bug patch: Audigy 2 [SB0240]
[   50.330836] usbcore: registered new driver libusual
[   50.349373] ts: Compaq touchscreen protocol output
[   50.383391] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   50.384937] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   50.464111] Initializing USB Mass Storage driver...
[   50.464182] scsi2 : SCSI emulation for USB Mass Storage devices
[   50.655086] usbcore: registered new driver usb-storage
[   50.655091] USB Mass Storage support registered.
[   50.655096] usb-storage: device found at 4
[   50.655097] usb-storage: waiting for device to settle before scanning
[   50.996601] parport0: PC-style at 0x378 (0x778) [PCSPP,TRISTATE,EPP]
[   50.997178] parport0: irq 7 detected
[   51.092868] lp0: using parport0 (polling).
[   51.117373] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   51.117378] ieee1394: sbp2: Try serialize_io=0 for better performance
[   51.174920] Adding 2971984k swap on /dev/disk/by-uuid/234640eb-83b8-4f26-b6a9-72df779fc57b.  Priority:-1 extents:1 across:2971984k
[   51.234938] EXT3 FS on sda1, internal journal
[   51.368987] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   51.368991] md: bitmap version 4.39
[   51.454525] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[   51.526869] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[   53.497375] NET: Registered protocol family 17
[   53.626922] NET: Registered protocol family 10
[   53.627014] lo: Disabled Privacy Extensions
[   53.627375] IPv6 over IPv4 tunneling driver
[   55.649864] usb-storage: device scan complete
[   55.653481]   Vendor: IN-WIN    Model: iAPP  HS-CF       Rev: 1.95
[   55.653497]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   55.656595]   Vendor: IN-WIN    Model: iAPP  HS-MS       Rev: 1.95
[   55.656610]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   55.659714]   Vendor: IN-WIN    Model: iAPP  HS-SM       Rev: 1.95
[   55.659729]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   55.662585]   Vendor: IN-WIN    Model: iAPP  HS-SD/MMC   Rev: 1.95
[   55.662599]   Type:   Direct-Access                      ANSI SCSI revision: 00
[   55.672131] sd 2:0:0:0: Attached scsi removable disk sdc
[   55.672170] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   55.682087] sd 2:0:0:1: Attached scsi removable disk sdd
[   55.682127] sd 2:0:0:1: Attached scsi generic sg3 type 0
[   55.696142] sd 2:0:0:2: Attached scsi removable disk sde
[   55.696184] sd 2:0:0:2: Attached scsi generic sg4 type 0
[   55.808067] usb 5-5: reset high speed USB device using ehci_hcd and address 4
[   56.020909] sd 2:0:0:3: Attached scsi removable disk sdf
[   56.020956] sd 2:0:0:3: Attached scsi generic sg5 type 0
[   60.159573] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   60.161887] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   60.162171] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[   60.466500] PCI: No IRQ known for interrupt pin A of device 0000:01:00.0. Please try using pci=biosirq.
[   63.232589] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   63.232597] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   63.232601] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
[   63.233456] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   63.233473] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   63.233515] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   63.233550] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
[   63.241328] [fglrx] total      GART = 134217728
[   63.241335] [fglrx] free       GART = 118222848
[   63.241337] [fglrx] max single GART = 118222848
[   63.241339] [fglrx] total      LFB  = 126873600
[   63.241341] [fglrx] free       LFB  = 116387840
[   63.241343] [fglrx] max single LFB  = 116387840
[   63.241344] [fglrx] total      Inv  = 0
[   63.241346] [fglrx] free       Inv  = 0
[   63.241347] [fglrx] max single Inv  = 0
[   63.241349] [fglrx] total      TIM  = 0
[   63.728994] eth0: no IPv6 routers present
[   64.131489] apm: BIOS not found.


---


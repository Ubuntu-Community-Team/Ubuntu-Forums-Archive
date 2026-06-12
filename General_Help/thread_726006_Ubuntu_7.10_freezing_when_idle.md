---
title: "Ubuntu 7.10 freezing when idle?"
date: 2008-03-16
forum: General Help
---

### Post by FIONEX on 2008-03-16
Hi,
When I leave my desktop to idle over night, I wake up in the morning and find it on the login screen.  Then I try to move the mouse and it just locks up and I would have to hold the power button to turn it off.  I've been having this issue with my new desktop, but it doesn't happen with my old desktop or laptop.

My desktop specs:
Intel C2D 6550
Crucial 2 GB DDR2 @ 1066 MHz
Asus Radeon HD2600 XT vid card
Gigabyte P35-DS3L motherboard

This log file shows that the kernel restarts at 7:34, but I didn't wake up until 8:41.  What do you think the problem is?

```

Mar 16 03:29:39 fionex-d kernel: [ 5113.373863] general protection fault: 0000 [#1]
Mar 16 03:29:39 fionex-d kernel: [ 5113.373866] SMP 
Mar 16 03:29:39 fionex-d kernel: [ 5113.373868] Modules linked in: af_packet binfmt_misc ipv6 ppdev sbs dock button ac video container battery coretemp it87 hwmon_vid i2c_isa i2c_core lp snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event fglrx(P) snd_seq parport_pc snd_timer snd_seq_device pcspkr parport shpchp snd soundcore snd_page_alloc intel_agp agpgart pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_generic usbhid hid floppy r8169 pata_jmicron ata_piix libata scsi_mod uhci_hcd ehci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 03:29:39 fionex-d kernel: [ 5113.373904] CPU:    0
Mar 16 03:29:39 fionex-d kernel: [ 5113.373904] EIP:    0060:[do_mmap_pgoff+518/2000]    Tainted: P       VLI
Mar 16 03:29:39 fionex-d kernel: [ 5113.373905] EFLAGS: 00010286   (2.6.22-14-generic #1)
Mar 16 03:29:39 fionex-d kernel: [ 5113.373910] EIP is at do_mmap_pgoff+0x206/0x7d0
Mar 16 03:29:39 fionex-d kernel: [ 5113.373912] eax: df95a400   ebx: efc341c0   ecx: f0759b58   edx: dfaa40f0
Mar 16 03:29:39 fionex-d kernel: [ 5113.373914] esi: 00001000   edi: dfaaddf0   ebp: 00000000   esp: edb9df3c
Mar 16 03:29:39 fionex-d kernel: [ 5113.373915] ds: 0000   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Mar 16 03:29:39 fionex-d kernel: [ 5113.373918] Process dhclient-script (pid: 6778, ti=edb9c000 task=dff494c0 task.ti=edb9c000)
Mar 16 03:29:39 fionex-d kernel: [ 5113.373919] Stack: 00000001 47ca13f3 00000000 0031a068 00000000 00000071 f7e4d900 00000000 
Mar 16 03:29:39 fionex-d kernel: [ 5113.373924]        dfaaddf0 c0183f3e 0031a068 b7fd4000 00000001 00000001 00000001 00000000 
Mar 16 03:29:39 fionex-d kernel: [ 5113.373929]        00000000 efc341f4 fffffff7 00000001 00000000 c01087fb 00000001 00000001 
Mar 16 03:29:39 fionex-d kernel: [ 5113.373933] Call Trace:
Mar 16 03:29:39 fionex-d kernel: [ 5113.373939]  [sys_fstat64+30/48] sys_fstat64+0x1e/0x30
Mar 16 03:29:39 fionex-d kernel: [ 5113.373945]  [sys_mmap2+187/208] sys_mmap2+0xbb/0xd0
Mar 16 03:29:39 fionex-d kernel: [ 5113.373951]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 03:29:39 fionex-d kernel: [ 5113.373956]  [clip_ioctl+928/1296] clip_ioctl+0x3a0/0x510
Mar 16 03:29:39 fionex-d kernel: [ 5113.373962]  =======================
Mar 16 03:29:39 fionex-d kernel: [ 5113.373963] Code: 8b 7c 24 24 f6 87 3c 01 00 00 04 74 0e 8b 44 24 1c f6 40 1c 02 0f 85 08 01 00 00 8b 54 24 24 8b 82 98 00 00 00 b6 40 30 40 74 1f <0f> b7 42 6a 25 08 04 00 00 3d 00 04 00 00 75 0f 89 d0 e8 23 01 
Mar 16 03:29:39 fionex-d kernel: [ 5113.373986] EIP: [do_mmap_pgoff+518/2000] do_mmap_pgoff+0x206/0x7d0 SS:ESP 0068:edb9df3c
Mar 16 07:34:05 fionex-d kernel: Inspecting /boot/System.map-2.6.22-14-generic
Mar 16 07:34:05 fionex-d kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Mar 16 07:34:05 fionex-d kernel: Symbols match kernel version 2.6.22.
Mar 16 07:34:05 fionex-d kernel: No module symbols loaded - kernel modules not enabled. 
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 16 07:34:05 fionex-d kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Mar 16 07:34:05 fionex-d kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Mar 16 07:34:05 fionex-d kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar 16 07:34:05 fionex-d kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Mar 16 07:34:05 fionex-d kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Mar 16 07:34:05 fionex-d kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Mar 16 07:34:05 fionex-d kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Mar 16 07:34:05 fionex-d kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Mar 16 07:34:05 fionex-d kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] 1150MB HIGHMEM available.
Mar 16 07:34:05 fionex-d kernel: [    0.000000] 896MB LOWMEM available.
Mar 16 07:34:05 fionex-d kernel: [    0.000000] found SMP MP-table at 000f5180
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Entering add_active_range(0, 0, 524000) 0 entries of 256 used
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Zone PFN ranges:
Mar 16 07:34:05 fionex-d kernel: [    0.000000]   DMA             0 ->     4096
Mar 16 07:34:05 fionex-d kernel: [    0.000000]   Normal       4096 ->   229376
Mar 16 07:34:05 fionex-d kernel: [    0.000000]   HighMem    229376 ->   524000
Mar 16 07:34:05 fionex-d kernel: [    0.000000] early_node_map[1] active PFN ranges
Mar 16 07:34:05 fionex-d kernel: [    0.000000]     0:        0 ->   524000
Mar 16 07:34:05 fionex-d kernel: [    0.000000] On node 0 totalpages: 524000
Mar 16 07:34:05 fionex-d kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Mar 16 07:34:05 fionex-d kernel: [    0.000000]   DMA zone: 0 pages reserved
Mar 16 07:34:05 fionex-d kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Mar 16 07:34:05 fionex-d kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Mar 16 07:34:05 fionex-d kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Mar 16 07:34:05 fionex-d kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Mar 16 07:34:05 fionex-d kernel: [    0.000000]   HighMem zone: 292323 pages, LIFO batch:31
Mar 16 07:34:05 fionex-d kernel: [    0.000000] DMI 2.4 present.
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6B40 checksum 0
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: RSDP 000F6B40, 0014 (r0 GBT   )
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: RSDT 7FEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: DSDT 7FEE3180, 4B25 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: FACS 7FEE0000, 0040
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: HPET 7FEE7E00, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: MCFG 7FEE7E80, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: APIC 7FEE7D00, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: SSDT 7FEE7F00, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: SSDT 7FEE8390, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Processor #0 6:15 APIC version 20
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Processor #1 6:15 APIC version 20
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Mar 16 07:34:05 fionex-d kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar 16 07:34:05 fionex-d kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Built 1 zonelists.  Total pages: 519907
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Kernel command line: root=UUID=95f8170d-5d4a-4fb3-b80c-a74bbc119ae5 ro quiet splash
Mar 16 07:34:05 fionex-d kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Initializing CPU#0
Mar 16 07:34:05 fionex-d kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 16 07:34:05 fionex-d kernel: [    0.000000] Detected 2333.523 MHz processor.
Mar 16 07:34:05 fionex-d kernel: [   28.218398] Console: colour VGA+ 80x25
Mar 16 07:34:05 fionex-d kernel: [   28.218558] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 16 07:34:05 fionex-d kernel: [   28.218753] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 16 07:34:05 fionex-d kernel: [   28.281023] Memory: 2066592k/2096000k available (2015k kernel code, 28184k reserved, 915k data, 364k init, 1178496k highmem)
Mar 16 07:34:05 fionex-d kernel: [   28.281029] virtual kernel memory layout:
Mar 16 07:34:05 fionex-d kernel: [   28.281030]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Mar 16 07:34:05 fionex-d kernel: [   28.281031]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Mar 16 07:34:05 fionex-d kernel: [   28.281032]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Mar 16 07:34:05 fionex-d kernel: [   28.281033]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Mar 16 07:34:05 fionex-d kernel: [   28.281034]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Mar 16 07:34:05 fionex-d kernel: [   28.281034]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
Mar 16 07:34:05 fionex-d kernel: [   28.281035]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
Mar 16 07:34:05 fionex-d kernel: [   28.281037] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Mar 16 07:34:05 fionex-d kernel: [   28.281062] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Mar 16 07:34:05 fionex-d kernel: [   28.281164] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Mar 16 07:34:05 fionex-d kernel: [   28.281168] hpet0: 4 64-bit timers, 14318180 Hz
Mar 16 07:34:05 fionex-d kernel: [   28.362021] Calibrating delay using timer specific routine.. 4669.84 BogoMIPS (lpj=9339687)
Mar 16 07:34:05 fionex-d kernel: [   28.362036] Security Framework v1.0.0 initialized
Mar 16 07:34:05 fionex-d kernel: [   28.362040] SELinux:  Disabled at boot.
Mar 16 07:34:05 fionex-d kernel: [   28.362048] Mount-cache hash table entries: 512
Mar 16 07:34:05 fionex-d kernel: [   28.362128] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3fd 00000000 00000001
Mar 16 07:34:05 fionex-d kernel: [   28.362133] monitor/mwait feature present.
Mar 16 07:34:05 fionex-d kernel: [   28.362134] using mwait in idle threads.
Mar 16 07:34:05 fionex-d kernel: [   28.362137] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 16 07:34:05 fionex-d kernel: [   28.362139] CPU: L2 cache: 4096K
Mar 16 07:34:05 fionex-d kernel: [   28.362141] CPU: Physical Processor ID: 0
Mar 16 07:34:05 fionex-d kernel: [   28.362142] CPU: Processor Core ID: 0
Mar 16 07:34:05 fionex-d kernel: [   28.362144] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3fd 00000000 00000001
Mar 16 07:34:05 fionex-d kernel: [   28.362150] Compat vDSO mapped to ffffe000.
Mar 16 07:34:05 fionex-d kernel: [   28.362158] Checking 'hlt' instruction... OK.
Mar 16 07:34:05 fionex-d kernel: [   28.378067] SMP alternatives: switching to UP code
Mar 16 07:34:05 fionex-d kernel: [   28.378366] Early unpacking initramfs... done
Mar 16 07:34:05 fionex-d kernel: [   28.610689] ACPI: Core revision 20070126
Mar 16 07:34:05 fionex-d kernel: [   28.610720] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Mar 16 07:34:05 fionex-d kernel: [   28.613075] CPU0: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz stepping 0b
Mar 16 07:34:05 fionex-d kernel: [   28.613088] SMP alternatives: switching to SMP code
Mar 16 07:34:05 fionex-d kernel: [   28.613133] Booting processor 1/1 eip 3000
Mar 16 07:34:05 fionex-d kernel: [   28.623391] Initializing CPU#1
Mar 16 07:34:05 fionex-d kernel: [   28.701351] Calibrating delay using timer specific routine.. 4666.64 BogoMIPS (lpj=9333298)
Mar 16 07:34:05 fionex-d kernel: [   28.701355] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3fd 00000000 00000001
Mar 16 07:34:05 fionex-d kernel: [   28.701359] monitor/mwait feature present.
Mar 16 07:34:05 fionex-d kernel: [   28.701361] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 16 07:34:05 fionex-d kernel: [   28.701362] CPU: L2 cache: 4096K
Mar 16 07:34:05 fionex-d kernel: [   28.701364] CPU: Physical Processor ID: 0
Mar 16 07:34:05 fionex-d kernel: [   28.701365] CPU: Processor Core ID: 1
Mar 16 07:34:05 fionex-d kernel: [   28.701366] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3fd 00000000 00000001
Mar 16 07:34:05 fionex-d kernel: [   28.701966] CPU1: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz stepping 0b
Mar 16 07:34:05 fionex-d kernel: [   28.701981] Total of 2 processors activated (9336.49 BogoMIPS).
Mar 16 07:34:05 fionex-d kernel: [   28.702116] ENABLING IO-APIC IRQs
Mar 16 07:34:05 fionex-d kernel: [   28.702274] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 16 07:34:05 fionex-d kernel: [   28.849120] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar 16 07:34:05 fionex-d kernel: [   28.869093] Brought up 2 CPUs
Mar 16 07:34:05 fionex-d kernel: [   28.914201] migration_cost=11
Mar 16 07:34:05 fionex-d kernel: [   28.914288] Booting paravirtualized kernel on bare hardware
Mar 16 07:34:05 fionex-d kernel: [   28.914334] Time:  7:33:52  Date: 02/16/108
Mar 16 07:34:05 fionex-d kernel: [   28.914346] NET: Registered protocol family 16
Mar 16 07:34:05 fionex-d kernel: [   28.914401] EISA bus registered
Mar 16 07:34:05 fionex-d kernel: [   28.914404] ACPI: bus type pci registered
Mar 16 07:34:05 fionex-d kernel: [   28.920089] PCI: PCI BIOS revision 3.00 entry at 0xfb1c0, last bus=5
Mar 16 07:34:05 fionex-d kernel: [   28.920090] PCI: Using configuration type 1
Mar 16 07:34:05 fionex-d kernel: [   28.920092] Setting up standard PCI resources
Mar 16 07:34:05 fionex-d kernel: [   28.921379] ACPI: EC: Look up EC in DSDT
Mar 16 07:34:05 fionex-d kernel: [   28.924500] ACPI: Interpreter enabled
Mar 16 07:34:05 fionex-d kernel: [   28.924504] ACPI: (supports S0 S3 S4 S5)
Mar 16 07:34:05 fionex-d kernel: [   28.924517] ACPI: Using IOAPIC for interrupt routing
Mar 16 07:34:05 fionex-d kernel: [   28.928964] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 16 07:34:05 fionex-d kernel: [   28.928981] PCI: Probing PCI hardware (bus 00)
Mar 16 07:34:05 fionex-d kernel: [   28.930102] PCI: Transparent bridge - 0000:00:1e.0
Mar 16 07:34:05 fionex-d kernel: [   28.930150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 16 07:34:05 fionex-d kernel: [   28.930254] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Mar 16 07:34:05 fionex-d kernel: [   28.930311] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
Mar 16 07:34:05 fionex-d kernel: [   28.930368] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
Mar 16 07:34:05 fionex-d kernel: [   28.930426] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Mar 16 07:34:05 fionex-d kernel: [   28.942546] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Mar 16 07:34:05 fionex-d kernel: [   28.942622] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Mar 16 07:34:05 fionex-d kernel: [   28.942696] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Mar 16 07:34:05 fionex-d kernel: [   28.942770] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Mar 16 07:34:05 fionex-d kernel: [   28.942848] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Mar 16 07:34:05 fionex-d kernel: [   28.942923] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Mar 16 07:34:05 fionex-d kernel: [   28.942997] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
Mar 16 07:34:05 fionex-d kernel: [   28.943070] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Mar 16 07:34:05 fionex-d kernel: [   28.943145] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar 16 07:34:05 fionex-d kernel: [   28.943152] pnp: PnP ACPI init
Mar 16 07:34:05 fionex-d kernel: [   28.943158] ACPI: bus type pnp registered
Mar 16 07:34:05 fionex-d kernel: [   28.945212] pnp: PnP ACPI: found 15 devices
Mar 16 07:34:05 fionex-d kernel: [   28.945213] ACPI: ACPI bus type pnp unregistered
Mar 16 07:34:05 fionex-d kernel: [   28.945217] PnPBIOS: Disabled by ACPI PNP
Mar 16 07:34:05 fionex-d kernel: [   28.945251] PCI: Using ACPI for IRQ routing
Mar 16 07:34:05 fionex-d kernel: [   28.945253] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Mar 16 07:34:05 fionex-d kernel: [   28.975185] NET: Registered protocol family 8
Mar 16 07:34:05 fionex-d kernel: [   28.975186] NET: Registered protocol family 20
Mar 16 07:34:05 fionex-d kernel: [   28.975225] pnp: 00:0b: ioport range 0x400-0x4bf has been reserved
Mar 16 07:34:05 fionex-d kernel: [   28.975229] pnp: 00:0c: iomem range 0xf0000000-0xf3ffffff could not be reserved
Mar 16 07:34:05 fionex-d kernel: [   28.975233] pnp: 00:0d: iomem range 0xf0000-0xf3fff could not be reserved
Mar 16 07:34:05 fionex-d kernel: [   28.975235] pnp: 00:0d: iomem range 0xf4000-0xf7fff could not be reserved
Mar 16 07:34:05 fionex-d kernel: [   28.975237] pnp: 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
Mar 16 07:34:05 fionex-d kernel: [   28.975238] pnp: 00:0d: iomem range 0xfc000-0xfffff could not be reserved
Mar 16 07:34:05 fionex-d kernel: [   28.976814] Time: tsc clocksource has been installed.
Mar 16 07:34:05 fionex-d kernel: [   28.976821] Switched to high resolution mode on CPU 0
Mar 16 07:34:05 fionex-d kernel: [   28.976878] Switched to high resolution mode on CPU 1
Mar 16 07:34:05 fionex-d kernel: [   29.005378] PCI: Bridge: 0000:00:01.0
Mar 16 07:34:05 fionex-d kernel: [   29.005380]   IO window: b000-bfff
Mar 16 07:34:05 fionex-d kernel: [   29.005383]   MEM window: f4000000-f5ffffff
Mar 16 07:34:05 fionex-d kernel: [   29.005385]   PREFETCH window: e0000000-efffffff
Mar 16 07:34:05 fionex-d kernel: [   29.005387] PCI: Bridge: 0000:00:1c.0
Mar 16 07:34:05 fionex-d kernel: [   29.005389]   IO window: 9000-9fff
Mar 16 07:34:05 fionex-d kernel: [   29.005392]   MEM window: disabled.
Mar 16 07:34:05 fionex-d kernel: [   29.005395]   PREFETCH window: disabled.
Mar 16 07:34:05 fionex-d kernel: [   29.005398] PCI: Bridge: 0000:00:1c.3
Mar 16 07:34:05 fionex-d kernel: [   29.005400]   IO window: c000-cfff
Mar 16 07:34:05 fionex-d kernel: [   29.005404]   MEM window: f6000000-f6ffffff
Mar 16 07:34:05 fionex-d kernel: [   29.005406]   PREFETCH window: disabled.
Mar 16 07:34:05 fionex-d kernel: [   29.005410] PCI: Bridge: 0000:00:1c.4
Mar 16 07:34:05 fionex-d kernel: [   29.005412]   IO window: d000-dfff
Mar 16 07:34:05 fionex-d kernel: [   29.005415]   MEM window: f7000000-f8ffffff
Mar 16 07:34:05 fionex-d kernel: [   29.005418]   PREFETCH window: 80000000-800fffff
Mar 16 07:34:05 fionex-d kernel: [   29.005422] PCI: Bridge: 0000:00:1e.0
Mar 16 07:34:05 fionex-d kernel: [   29.005423]   IO window: a000-afff
Mar 16 07:34:05 fionex-d kernel: [   29.005427]   MEM window: disabled.
Mar 16 07:34:05 fionex-d kernel: [   29.005429]   PREFETCH window: disabled.
Mar 16 07:34:05 fionex-d kernel: [   29.005439] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 16 07:34:05 fionex-d kernel: [   29.005443] PCI: Setting latency timer of device 0000:00:01.0 to 64
Mar 16 07:34:05 fionex-d kernel: [   29.005455] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 16 07:34:05 fionex-d kernel: [   29.005459] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Mar 16 07:34:05 fionex-d kernel: [   29.005472] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Mar 16 07:34:05 fionex-d kernel: [   29.005476] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Mar 16 07:34:05 fionex-d kernel: [   29.005488] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
Mar 16 07:34:05 fionex-d kernel: [   29.005492] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Mar 16 07:34:05 fionex-d kernel: [   29.005500] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Mar 16 07:34:05 fionex-d kernel: [   29.005507] NET: Registered protocol family 2
Mar 16 07:34:05 fionex-d kernel: [   29.056658] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 16 07:34:05 fionex-d kernel: [   29.056691] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Mar 16 07:34:05 fionex-d kernel: [   29.057136] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 16 07:34:05 fionex-d kernel: [   29.057281] TCP: Hash tables configured (established 131072 bind 65536)
Mar 16 07:34:05 fionex-d kernel: [   29.057283] TCP reno registered
Mar 16 07:34:05 fionex-d kernel: [   29.072701] checking if image is initramfs... it is
Mar 16 07:34:05 fionex-d kernel: [   29.532163] Freeing initrd memory: 7061k freed
Mar 16 07:34:05 fionex-d kernel: [   29.532527] audit: initializing netlink socket (disabled)
Mar 16 07:34:05 fionex-d kernel: [   29.532536] audit(1205652832.072:1): initialized
Mar 16 07:34:05 fionex-d kernel: [   29.532596] highmem bounce pool size: 64 pages
Mar 16 07:34:05 fionex-d kernel: [   29.533822] VFS: Disk quotas dquot_6.5.1
Mar 16 07:34:05 fionex-d kernel: [   29.533854] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 16 07:34:05 fionex-d kernel: [   29.533914] io scheduler noop registered
Mar 16 07:34:05 fionex-d kernel: [   29.533915] io scheduler anticipatory registered
Mar 16 07:34:05 fionex-d kernel: [   29.533917] io scheduler deadline registered
Mar 16 07:34:05 fionex-d kernel: [   29.533926] io scheduler cfq registered (default)
Mar 16 07:34:05 fionex-d kernel: [   29.534029] Boot video device is 0000:01:00.0
Mar 16 07:34:05 fionex-d kernel: [   29.534080] PCI: Setting latency timer of device 0000:00:01.0 to 64
Mar 16 07:34:05 fionex-d kernel: [   29.534105] assign_interrupt_mode Found MSI capability
Mar 16 07:34:05 fionex-d kernel: [   29.534107] Allocate Port Service[0000:00:01.0:pcie00]
Mar 16 07:34:05 fionex-d kernel: [   29.534158] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Mar 16 07:34:05 fionex-d kernel: [   29.534189] assign_interrupt_mode Found MSI capability
Mar 16 07:34:05 fionex-d kernel: [   29.534190] Allocate Port Service[0000:00:1c.0:pcie00]
Mar 16 07:34:05 fionex-d kernel: [   29.534210] Allocate Port Service[0000:00:1c.0:pcie02]
Mar 16 07:34:05 fionex-d kernel: [   29.534265] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Mar 16 07:34:05 fionex-d kernel: [   29.534296] assign_interrupt_mode Found MSI capability
Mar 16 07:34:05 fionex-d kernel: [   29.534298] Allocate Port Service[0000:00:1c.3:pcie00]
Mar 16 07:34:05 fionex-d kernel: [   29.534319] Allocate Port Service[0000:00:1c.3:pcie02]
Mar 16 07:34:05 fionex-d kernel: [   29.534374] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Mar 16 07:34:05 fionex-d kernel: [   29.534405] assign_interrupt_mode Found MSI capability
Mar 16 07:34:05 fionex-d kernel: [   29.534407] Allocate Port Service[0000:00:1c.4:pcie00]
Mar 16 07:34:05 fionex-d kernel: [   29.534427] Allocate Port Service[0000:00:1c.4:pcie02]
Mar 16 07:34:05 fionex-d kernel: [   29.534521] isapnp: Scanning for PnP cards...
Mar 16 07:34:05 fionex-d kernel: [   29.886610] isapnp: No Plug & Play device found
Mar 16 07:34:05 fionex-d kernel: [   29.899825] Real Time Clock Driver v1.12ac
Mar 16 07:34:05 fionex-d kernel: [   29.899938] hpet_resources: 0xfed00000 is busy
Mar 16 07:34:05 fionex-d kernel: [   29.899965] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Mar 16 07:34:05 fionex-d kernel: [   29.900045] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 16 07:34:05 fionex-d kernel: [   29.900446] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 16 07:34:05 fionex-d kernel: [   29.900890] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Mar 16 07:34:05 fionex-d kernel: [   29.901025] input: Macintosh mouse button emulation as /class/input/input0
Mar 16 07:34:05 fionex-d kernel: [   29.901075] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Mar 16 07:34:05 fionex-d kernel: [   29.901077] PNP: PS/2 controller doesn't have AUX irq; using default 12
Mar 16 07:34:05 fionex-d kernel: [   29.903418] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 16 07:34:05 fionex-d kernel: [   29.903484] mice: PS/2 mouse device common for all mice
Mar 16 07:34:05 fionex-d kernel: [   29.903544] EISA: Probing bus 0 at eisa.0
Mar 16 07:34:05 fionex-d kernel: [   29.903567] EISA: Detected 0 cards.
Mar 16 07:34:05 fionex-d kernel: [   29.903676] TCP cubic registered
Mar 16 07:34:05 fionex-d kernel: [   29.903685] NET: Registered protocol family 1
Mar 16 07:34:05 fionex-d kernel: [   29.903697] Using IPI No-Shortcut mode
Mar 16 07:34:05 fionex-d kernel: [   29.903802]   Magic number: 0:951:571
Mar 16 07:34:05 fionex-d kernel: [   29.903819]   hash matches device ptyb3
Mar 16 07:34:05 fionex-d kernel: [   29.903953] Freeing unused kernel memory: 364k freed
Mar 16 07:34:05 fionex-d kernel: [   29.922994] input: AT Translated Set 2 keyboard as /class/input/input1
Mar 16 07:34:05 fionex-d kernel: [   31.036063] AppArmor: AppArmor initialized<5>audit(1205652833.572:2):  type=1505 info="AppArmor initialized" pid=1249
Mar 16 07:34:05 fionex-d kernel: [   31.040074] fuse init (API version 7.8)
Mar 16 07:34:05 fionex-d kernel: [   31.043056] Failure registering capabilities with primary security module.
Mar 16 07:34:05 fionex-d kernel: [   31.070076] ACPI: Processor [CPU0] (supports 8 throttling states)
Mar 16 07:34:05 fionex-d kernel: [   31.070160] ACPI: SSDT 7FEE8300, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
Mar 16 07:34:05 fionex-d kernel: [   31.070242] ACPI: Processor [CPU1] (supports 8 throttling states)
Mar 16 07:34:05 fionex-d kernel: [   31.070249] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Mar 16 07:34:05 fionex-d kernel: [   31.070256] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Mar 16 07:34:05 fionex-d kernel: [   31.331230] usbcore: registered new interface driver usbfs
Mar 16 07:34:05 fionex-d kernel: [   31.331245] usbcore: registered new interface driver hub
Mar 16 07:34:05 fionex-d kernel: [   31.336342] usbcore: registered new device driver usb
Mar 16 07:34:05 fionex-d kernel: [   31.336856] USB Universal Host Controller Interface driver v3.0
Mar 16 07:34:05 fionex-d kernel: [   31.336895] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 16 07:34:05 fionex-d kernel: [   31.336902] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Mar 16 07:34:05 fionex-d kernel: [   31.336905] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Mar 16 07:34:05 fionex-d kernel: [   31.336989] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Mar 16 07:34:05 fionex-d kernel: [   31.337013] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e100
Mar 16 07:34:05 fionex-d kernel: [   31.337083] usb usb1: configuration #1 chosen from 1 choice
Mar 16 07:34:05 fionex-d kernel: [   31.337100] hub 1-0:1.0: USB hub found
Mar 16 07:34:05 fionex-d kernel: [   31.337104] hub 1-0:1.0: 2 ports detected
Mar 16 07:34:05 fionex-d kernel: [   31.373714] SCSI subsystem initialized
Mar 16 07:34:05 fionex-d kernel: [   31.377046] libata version 2.21 loaded.
Mar 16 07:34:05 fionex-d kernel: [   31.436233] Floppy drive(s): fd0 is 1.44M
Mar 16 07:34:05 fionex-d kernel: [   31.440150] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
Mar 16 07:34:05 fionex-d kernel: [   31.440157] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Mar 16 07:34:05 fionex-d kernel: [   31.440160] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Mar 16 07:34:05 fionex-d kernel: [   31.440175] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Mar 16 07:34:05 fionex-d kernel: [   31.440197] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000e200
Mar 16 07:34:05 fionex-d kernel: [   31.440259] usb usb2: configuration #1 chosen from 1 choice
Mar 16 07:34:05 fionex-d kernel: [   31.440278] hub 2-0:1.0: USB hub found
Mar 16 07:34:05 fionex-d kernel: [   31.440281] hub 2-0:1.0: 2 ports detected
Mar 16 07:34:05 fionex-d kernel: [   31.458777] FDC 0 is a post-1991 82077
Mar 16 07:34:05 fionex-d kernel: [   31.543948] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 19
Mar 16 07:34:05 fionex-d kernel: [   31.543955] PCI: Setting latency timer of device 0000:00:1a.2 to 64
Mar 16 07:34:05 fionex-d kernel: [   31.543958] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Mar 16 07:34:05 fionex-d kernel: [   31.543974] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
Mar 16 07:34:05 fionex-d kernel: [   31.543996] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000e000
Mar 16 07:34:05 fionex-d kernel: [   31.544066] usb usb3: configuration #1 chosen from 1 choice
Mar 16 07:34:05 fionex-d kernel: [   31.544082] hub 3-0:1.0: USB hub found
Mar 16 07:34:05 fionex-d kernel: [   31.544086] hub 3-0:1.0: 2 ports detected
Mar 16 07:34:05 fionex-d kernel: [   31.647721] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Mar 16 07:34:05 fionex-d kernel: [   31.647727] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Mar 16 07:34:05 fionex-d kernel: [   31.647730] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar 16 07:34:05 fionex-d kernel: [   31.647745] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
Mar 16 07:34:05 fionex-d kernel: [   31.647766] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000e300
Mar 16 07:34:05 fionex-d kernel: [   31.647831] usb usb4: configuration #1 chosen from 1 choice
Mar 16 07:34:05 fionex-d kernel: [   31.647854] hub 4-0:1.0: USB hub found
Mar 16 07:34:05 fionex-d kernel: [   31.647857] hub 4-0:1.0: 2 ports detected
Mar 16 07:34:05 fionex-d kernel: [   31.751515] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Mar 16 07:34:05 fionex-d kernel: [   31.751521] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Mar 16 07:34:05 fionex-d kernel: [   31.751523] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar 16 07:34:05 fionex-d kernel: [   31.751538] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
Mar 16 07:34:05 fionex-d kernel: [   31.751559] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e400
Mar 16 07:34:05 fionex-d kernel: [   31.751627] usb usb5: configuration #1 chosen from 1 choice
Mar 16 07:34:05 fionex-d kernel: [   31.751650] hub 5-0:1.0: USB hub found
Mar 16 07:34:05 fionex-d kernel: [   31.751653] hub 5-0:1.0: 2 ports detected
Mar 16 07:34:05 fionex-d kernel: [   31.783397] usb 2-1: new low speed USB device using uhci_hcd and address 2
Mar 16 07:34:05 fionex-d kernel: [   31.855312] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Mar 16 07:34:05 fionex-d kernel: [   31.855318] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Mar 16 07:34:05 fionex-d kernel: [   31.855321] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar 16 07:34:05 fionex-d kernel: [   31.855336] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
Mar 16 07:34:05 fionex-d kernel: [   31.855355] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000e500
Mar 16 07:34:05 fionex-d kernel: [   31.855423] usb usb6: configuration #1 chosen from 1 choice
Mar 16 07:34:05 fionex-d kernel: [   31.855448] hub 6-0:1.0: USB hub found
Mar 16 07:34:05 fionex-d kernel: [   31.855451] hub 6-0:1.0: 2 ports detected
Mar 16 07:34:05 fionex-d kernel: [   31.959250] usb 2-1: configuration #1 chosen from 1 choice
Mar 16 07:34:05 fionex-d kernel: [   31.960389] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 19
Mar 16 07:34:05 fionex-d kernel: [   31.960397] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Mar 16 07:34:05 fionex-d kernel: [   31.960400] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Mar 16 07:34:05 fionex-d kernel: [   31.960417] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
Mar 16 07:34:05 fionex-d kernel: [   31.960438] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Mar 16 07:34:05 fionex-d kernel: [   31.960442] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf9004000
Mar 16 07:34:05 fionex-d kernel: [   31.964309] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 16 07:34:05 fionex-d kernel: [   31.964358] usb usb7: configuration #1 chosen from 1 choice
Mar 16 07:34:05 fionex-d kernel: [   31.964375] hub 7-0:1.0: USB hub found
Mar 16 07:34:05 fionex-d kernel: [   31.964379] hub 7-0:1.0: 6 ports detected
Mar 16 07:34:05 fionex-d kernel: [   31.994092] usbcore: registered new interface driver hiddev
Mar 16 07:34:05 fionex-d kernel: [   32.013106] usbcore: registered new interface driver usbhid
Mar 16 07:34:05 fionex-d kernel: [   32.013109] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Mar 16 07:34:05 fionex-d kernel: [   32.046915] usb 2-1: USB disconnect, address 2
Mar 16 07:34:05 fionex-d kernel: [   32.066945] r8169 Gigabit Ethernet driver 2.2LK loaded
Mar 16 07:34:05 fionex-d kernel: [   32.066970] ACPI: PCI Interrupt 0000:00:1d.7[A] -> <6>ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 16 07:34:05 fionex-d kernel: [   32.066974] GSI 23 (level, low) -> IRQ 20
Mar 16 07:34:05 fionex-d kernel: [   32.066982] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Mar 16 07:34:05 fionex-d kernel: [   32.066986] PCI: Setting latency timer of device 0000:04:00.0 to 64
Mar 16 07:34:05 fionex-d kernel: [   32.066988] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar 16 07:34:05 fionex-d kernel: [   32.067005] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
Mar 16 07:34:05 fionex-d kernel: [   32.067033] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Mar 16 07:34:05 fionex-d kernel: [   32.067037] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf9005000
Mar 16 07:34:05 fionex-d kernel: [   32.067160] eth0: RTL8168b/8111b at 0xf8874000, 00:1d:7d:ab:24:6f, XID 38000000 IRQ 16
Mar 16 07:34:05 fionex-d kernel: [   32.070913] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 16 07:34:05 fionex-d kernel: [   32.070963] usb usb8: configuration #1 chosen from 1 choice
Mar 16 07:34:05 fionex-d kernel: [   32.070979] hub 8-0:1.0: USB hub found
Mar 16 07:34:05 fionex-d kernel: [   32.070983] hub 8-0:1.0: 6 ports detected
Mar 16 07:34:05 fionex-d kernel: [   32.174717] ata_piix 0000:00:1f.2: version 2.11
Mar 16 07:34:05 fionex-d kernel: [   32.174723] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Mar 16 07:34:05 fionex-d kernel: [   32.174738] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
Mar 16 07:34:05 fionex-d kernel: [   32.174757] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Mar 16 07:34:05 fionex-d kernel: [   32.174979] scsi0 : ata_piix
Mar 16 07:34:05 fionex-d kernel: [   32.175089] scsi1 : ata_piix
Mar 16 07:34:05 fionex-d kernel: [   32.175159] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
Mar 16 07:34:05 fionex-d kernel: [   32.175161] ata2: SATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
Mar 16 07:34:05 fionex-d kernel: [   32.339053] ata1.00: Host Protected Area detected:
Mar 16 07:34:05 fionex-d kernel: [   32.339055] ^Icurrent size: 488395055 sectors
Mar 16 07:34:05 fionex-d kernel: [   32.339056] ^Inative size: 488397168 sectors
Mar 16 07:34:05 fionex-d kernel: [   32.339248] ata1.00: native size increased to 488397168 sectors
Mar 16 07:34:05 fionex-d kernel: [   32.339251] ata1.00: ATA-8: WDC WD2500AAKS-00VSA0, 01.01B01, max UDMA/133
Mar 16 07:34:05 fionex-d kernel: [   32.339254] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar 16 07:34:05 fionex-d kernel: [   32.355003] ata1.00: configured for UDMA/133
Mar 16 07:34:05 fionex-d kernel: [   32.520627] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500AAKS-0 01.0 PQ: 0 ANSI: 5
Mar 16 07:34:05 fionex-d kernel: [   32.520665] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
Mar 16 07:34:05 fionex-d kernel: [   32.520680] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 17
Mar 16 07:34:05 fionex-d kernel: [   32.520698] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Mar 16 07:34:05 fionex-d kernel: [   32.520718] scsi2 : ata_piix
Mar 16 07:34:05 fionex-d kernel: [   32.520741] scsi3 : ata_piix
Mar 16 07:34:05 fionex-d kernel: [   32.520805] ata3: SATA max UDMA/133 cmd 0x0001e700 ctl 0x0001e802 bmdma 0x0001eb00 irq 17
Mar 16 07:34:05 fionex-d kernel: [   32.520808] ata4: SATA max UDMA/133 cmd 0x0001e900 ctl 0x0001ea02 bmdma 0x0001eb08 irq 17
Mar 16 07:34:05 fionex-d kernel: [   32.789454] usb 2-1: new low speed USB device using uhci_hcd and address 3
Mar 16 07:34:05 fionex-d kernel: [   32.848985] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
Mar 16 07:34:05 fionex-d kernel: [   32.849007] PCI: Setting latency timer of device 0000:03:00.0 to 64
Mar 16 07:34:05 fionex-d kernel: [   32.849066] scsi4 : pata_jmicron
Mar 16 07:34:05 fionex-d kernel: [   32.849460] scsi5 : pata_jmicron
Mar 16 07:34:05 fionex-d kernel: [   32.849524] ata5: PATA max UDMA/100 cmd 0x0001c000 ctl 0x0001c102 bmdma 0x0001c400 irq 17
Mar 16 07:34:05 fionex-d kernel: [   32.849527] ata6: PATA max UDMA/100 cmd 0x0001c200 ctl 0x0001c302 bmdma 0x0001c408 irq 17
Mar 16 07:34:05 fionex-d kernel: [   32.965286] usb 2-1: configuration #1 chosen from 1 choice
Mar 16 07:34:05 fionex-d kernel: [   32.981333] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
Mar 16 07:34:05 fionex-d kernel: [   32.981347] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.1-1
Mar 16 07:34:05 fionex-d kernel: [   33.169283] ata5.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.02, max UDMA/66
Mar 16 07:34:05 fionex-d kernel: [   33.340951] ata5.00: configured for UDMA/66
Mar 16 07:34:05 fionex-d kernel: [   33.497655] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.02 PQ: 0 ANSI: 5
Mar 16 07:34:05 fionex-d kernel: [   33.504165] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Mar 16 07:34:05 fionex-d kernel: [   33.504173] sd 0:0:0:0: [sda] Write Protect is off
Mar 16 07:34:05 fionex-d kernel: [   33.504175] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 16 07:34:05 fionex-d kernel: [   33.504185] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 16 07:34:05 fionex-d kernel: [   33.504213] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Mar 16 07:34:05 fionex-d kernel: [   33.504219] sd 0:0:0:0: [sda] Write Protect is off
Mar 16 07:34:05 fionex-d kernel: [   33.504220] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 16 07:34:05 fionex-d kernel: [   33.504230] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 16 07:34:05 fionex-d kernel: [   33.504232]  sda: sda1 sda2 < sda5 sda6 sda7 >
Mar 16 07:34:05 fionex-d kernel: [   33.541126] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 16 07:34:05 fionex-d kernel: [   33.543841] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar 16 07:34:05 fionex-d kernel: [   33.543853] sr 4:0:0:0: Attached scsi generic sg1 type 5
Mar 16 07:34:05 fionex-d kernel: [   33.555963] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 16 07:34:05 fionex-d kernel: [   33.555966] Uniform CD-ROM driver Revision: 3.20
Mar 16 07:34:05 fionex-d kernel: [   33.556071] sr 4:0:0:0: Attached scsi CD-ROM sr0
Mar 16 07:34:05 fionex-d kernel: [   33.776081] Attempting manual resume
Mar 16 07:34:05 fionex-d kernel: [   33.776083] swsusp: Resume From Partition 8:6
Mar 16 07:34:05 fionex-d kernel: [   33.776084] PM: Checking swsusp image.
Mar 16 07:34:05 fionex-d kernel: [   33.776215] PM: Resume from disk failed.
Mar 16 07:34:05 fionex-d kernel: [   33.783776] EXT3-fs: INFO: recovery required on readonly filesystem.
Mar 16 07:34:05 fionex-d kernel: [   33.783778] EXT3-fs: write access will be enabled during recovery.
Mar 16 07:34:05 fionex-d kernel: [   36.145752] kjournald starting.  Commit interval 5 seconds
Mar 16 07:34:05 fionex-d kernel: [   36.145758] EXT3-fs: sda7: orphan cleanup on readonly fs
Mar 16 07:34:05 fionex-d kernel: [   36.145763] ext3_orphan_cleanup: deleting unreferenced inode 5056484
Mar 16 07:34:05 fionex-d kernel: [   36.145785] EXT3-fs: sda7: 1 orphan inode deleted
Mar 16 07:34:05 fionex-d kernel: [   36.145786] EXT3-fs: recovery complete.
Mar 16 07:34:05 fionex-d kernel: [   36.147988] EXT3-fs: mounted filesystem with ordered data mode.
Mar 16 07:34:05 fionex-d kernel: [   40.210154] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 16 07:34:05 fionex-d kernel: [   40.216035] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 16 07:34:05 fionex-d kernel: [   40.510888] Linux agpgart interface v0.102 (c) Dave Jones
Mar 16 07:34:05 fionex-d kernel: [   40.523696] parport_pc 00:09: reported by Plug and Play ACPI
Mar 16 07:34:05 fionex-d kernel: [   40.523737] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Mar 16 07:34:05 fionex-d kernel: [   40.543134] input: PC Speaker as /class/input/input3
Mar 16 07:34:05 fionex-d kernel: [   40.623117] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Mar 16 07:34:05 fionex-d kernel: [   40.637106] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
Mar 16 07:34:05 fionex-d kernel: [   40.637130] [fglrx] ASYNCIO init succeed!
Mar 16 07:34:05 fionex-d kernel: [   40.638583] [fglrx] PAT is enabled successfully!
Mar 16 07:34:05 fionex-d kernel: [   40.639092] [fglrx] module loaded - fglrx 8.45.5 [Feb  1 2008] on minor 0
Mar 16 07:34:05 fionex-d kernel: [   40.797673] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
Mar 16 07:34:05 fionex-d kernel: [   40.797686] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Mar 16 07:34:05 fionex-d kernel: [   41.169228] lp0: using parport0 (interrupt-driven).
Mar 16 07:34:05 fionex-d kernel: [   41.191240] it87: Found IT8718F chip at 0x290, revision 4
Mar 16 07:34:05 fionex-d kernel: [   41.191247] it87: in3 is VCC (+5V)
Mar 16 07:34:05 fionex-d kernel: [   41.203803] coretemp coretemp.0: Using undocumented features, absolute temperature might be wrong!
Mar 16 07:34:05 fionex-d kernel: [   41.203825] coretemp coretemp.1: Using undocumented features, absolute temperature might be wrong!
Mar 16 07:34:05 fionex-d kernel: [   41.233684] Adding 2104472k swap on /dev/sda6.  Priority:-1 extents:1 across:2104472k
Mar 16 07:34:05 fionex-d kernel: [   41.527091] EXT3 FS on sda7, internal journal
Mar 16 07:34:05 fionex-d kernel: [   42.562812] input: Power Button (FF) as /class/input/input4
Mar 16 07:34:05 fionex-d kernel: [   42.562825] ACPI: Power Button (FF) [PWRF]
Mar 16 07:34:05 fionex-d kernel: [   42.562850] input: Power Button (CM) as /class/input/input5
Mar 16 07:34:05 fionex-d kernel: [   42.562861] ACPI: Power Button (CM) [PWRB]
Mar 16 07:34:05 fionex-d kernel: [   42.591640] No dock devices found.
Mar 16 07:34:05 fionex-d kernel: [   43.011867] ppdev: user-space parallel port driver
Mar 16 07:34:06 fionex-d kernel: [   43.228517] NET: Registered protocol family 10
Mar 16 07:34:06 fionex-d kernel: [   43.228574] lo: Disabled Privacy Extensions
Mar 16 07:34:06 fionex-d kernel: [   43.243665] r8169: eth1: link up
Mar 16 07:34:06 fionex-d kernel: [   43.243672] r8169: eth1: link up
Mar 16 07:34:06 fionex-d kernel: [   43.307351] audit(1205667245.836:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5017 profile="/usr/sbin/cupsd"
Mar 16 07:34:07 fionex-d kernel: [   45.095675] Failure registering capabilities with primary security module.
Mar 16 07:34:09 fionex-d kernel: [   46.966829] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 16 07:34:10 fionex-d kernel: [   47.812391] [fglrx] Reserve Block - 0 offset =  0Xfffc000 length = 0X4000
Mar 16 07:34:10 fionex-d kernel: [   47.812395] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Mar 16 07:34:10 fionex-d kernel: [   47.812398] [fglrx] Reserve Block - 2 offset =  0Xff7b000 length = 0X80000
Mar 16 07:34:10 fionex-d kernel: [   47.954052] [fglrx] interrupt source 20008000 successfully enabled
Mar 16 07:34:10 fionex-d kernel: [   47.954055] [fglrx] enable ID = 0x00000006
Mar 16 07:34:10 fionex-d kernel: [   47.954221] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Mar 16 07:34:10 fionex-d kernel: [   47.954359] [fglrx] interrupt source 10000000 successfully enabled
Mar 16 07:34:10 fionex-d kernel: [   47.954361] [fglrx] enable ID = 0x00000008
Mar 16 07:34:10 fionex-d kernel: [   47.954502] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Mar 16 07:34:10 fionex-d kernel: [   47.962833] [fglrx] interrupt source 60000001 successfully enabled
Mar 16 07:34:10 fionex-d kernel: [   47.962835] [fglrx] enable ID = 0x00000009
Mar 16 07:34:10 fionex-d kernel: [   47.962980] [fglrx] Receive enable interrupt message with irqEnableMask: 60000001
Mar 16 07:34:10 fionex-d kernel: [   47.963112] [fglrx] interrupt source 00000040 successfully enabled
Mar 16 07:34:10 fionex-d kernel: [   47.963114] [fglrx] enable ID = 0x0000000A
Mar 16 07:34:10 fionex-d kernel: [   47.963255] [fglrx] Receive enable interrupt message with irqEnableMask: 00000040
Mar 16 07:34:10 fionex-d kernel: [   47.977144] [fglrx] interrupt source ff00002c successfully enabled
Mar 16 07:34:10 fionex-d kernel: [   47.977146] [fglrx] enable ID = 0x0000000B
Mar 16 07:34:10 fionex-d kernel: [   47.977288] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002c
Mar 16 07:34:10 fionex-d kernel: [   47.977419] [fglrx] interrupt source ff00002d successfully enabled
Mar 16 07:34:10 fionex-d kernel: [   47.977420] [fglrx] enable ID = 0x0000000C
Mar 16 07:34:10 fionex-d kernel: [   47.977562] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002d
Mar 16 07:34:10 fionex-d kernel: [   47.977690] [fglrx] interrupt source 20000400 successfully enabled
Mar 16 07:34:10 fionex-d kernel: [   47.977692] [fglrx] enable ID = 0x0000000D
Mar 16 07:34:10 fionex-d kernel: [   47.977833] [fglrx] Receive enable interrupt message with irqEnableMask: 20000400
Mar 16 07:34:12 fionex-d kernel: [   49.598803] NET: Registered protocol family 17
Mar 16 07:34:29 fionex-d kernel: [   66.751145] eth1: no IPv6 routers present
Mar 16 08:22:11 fionex-d kernel: [ 2922.426976] general protection fault: 0000 [#1]
Mar 16 08:22:11 fionex-d kernel: [ 2922.426979] SMP 
Mar 16 08:22:11 fionex-d kernel: [ 2922.426981] Modules linked in: af_packet binfmt_misc ipv6 ppdev sbs dock button ac video container battery coretemp it87 hwmon_vid i2c_isa i2c_core lp snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer fglrx(P) snd_seq_device pcspkr parport_pc parport intel_agp agpgart snd soundcore snd_page_alloc shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_generic usbhid hid floppy ata_piix r8169 pata_jmicron libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 08:22:11 fionex-d kernel: [ 2922.427017] CPU:    1
Mar 16 08:22:11 fionex-d kernel: [ 2922.427018] EIP:    0060:[do_mmap_pgoff+518/2000]    Tainted: P       VLI
Mar 16 08:22:11 fionex-d kernel: [ 2922.427019] EFLAGS: 00010246   (2.6.22-14-generic #1)
Mar 16 08:22:11 fionex-d kernel: [ 2922.427024] EIP is at do_mmap_pgoff+0x206/0x7d0
Mar 16 08:22:11 fionex-d kernel: [ 2922.427025] eax: dfc5e600   ebx: f39d9c40   ecx: f3358000   edx: f3fd40f0
Mar 16 08:22:11 fionex-d kernel: [ 2922.427027] esi: 00001000   edi: f3fd0df0   ebp: 00000000   esp: ec913f3c
Mar 16 08:22:11 fionex-d kernel: [ 2922.427029] ds: 0000   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Mar 16 08:22:11 fionex-d kernel: [ 2922.427032] Process dhclient-script (pid: 5899, ti=ec912000 task=f3604a60 task.ti=ec912000)
Mar 16 08:22:11 fionex-d kernel: [ 2922.427033] Stack: 00000001 47ca13f3 00000000 0031a068 00000000 00000071 dfc4c180 00000000 
Mar 16 08:22:11 fionex-d kernel: [ 2922.427038]        f3fd0df0 c0183f3e 0031a068 b7f1e000 00000001 00000001 00000001 00000000 
Mar 16 08:22:11 fionex-d kernel: [ 2922.427043]        00000000 f39d9c74 fffffff7 00000001 00000000 c01087fb 00000001 00000001 
Mar 16 08:22:11 fionex-d kernel: [ 2922.427047] Call Trace:
Mar 16 08:22:11 fionex-d kernel: [ 2922.427053]  [sys_fstat64+30/48] sys_fstat64+0x1e/0x30
Mar 16 08:22:11 fionex-d kernel: [ 2922.427060]  [sys_mmap2+187/208] sys_mmap2+0xbb/0xd0
Mar 16 08:22:11 fionex-d kernel: [ 2922.427066]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 08:22:11 fionex-d kernel: [ 2922.427072]  [clip_ioctl+928/1296] clip_ioctl+0x3a0/0x510
Mar 16 08:22:11 fionex-d kernel: [ 2922.427078]  =======================
Mar 16 08:22:11 fionex-d kernel: [ 2922.427079] Code: 8b 7c 24 24 f6 87 3c 01 00 00 04 74 0e 8b 44 24 1c f6 40 1c 02 0f 85 08 01 00 00 8b 54 24 24 8b 82 98 00 00 00 b6 40 30 40 74 1f <0f> b7 42 6a 25 08 04 00 00 3d 00 04 00 00 75 0f 89 d0 e8 23 01 
Mar 16 08:22:11 fionex-d kernel: [ 2922.427102] EIP: [do_mmap_pgoff+518/2000] do_mmap_pgoff+0x206/0x7d0 SS:ESP 0068:ec913f3c
Mar 16 08:39:13 fionex-d kernel: [ 3942.356081] general protection fault: 0000 [#2]
Mar 16 08:39:13 fionex-d kernel: [ 3942.356084] SMP 
Mar 16 08:39:13 fionex-d kernel: [ 3942.356086] Modules linked in: af_packet binfmt_misc ipv6 ppdev sbs dock button ac video container battery coretemp it87 hwmon_vid i2c_isa i2c_core lp snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer fglrx(P) snd_seq_device pcspkr parport_pc parport intel_agp agpgart snd soundcore snd_page_alloc shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_generic usbhid hid floppy ata_piix r8169 pata_jmicron libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 08:39:13 fionex-d kernel: [ 3942.356122] CPU:    0
Mar 16 08:39:13 fionex-d kernel: [ 3942.356122] EIP:    0060:[do_mmap_pgoff+518/2000]    Tainted: P       VLI
Mar 16 08:39:13 fionex-d kernel: [ 3942.356123] EFLAGS: 00010206   (2.6.22-14-generic #1)
Mar 16 08:39:13 fionex-d kernel: [ 3942.356128] EIP is at do_mmap_pgoff+0x206/0x7d0
Mar 16 08:39:13 fionex-d kernel: [ 3942.356130] eax: dfc5e600   ebx: f3431540   ecx: f3717370   edx: f3fd40f0
Mar 16 08:39:13 fionex-d kernel: [ 3942.356132] esi: 00001000   edi: f3fd0df0   ebp: 00000000   esp: f36d1f3c
Mar 16 08:39:13 fionex-d kernel: [ 3942.356134] ds: 0000   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Mar 16 08:39:13 fionex-d kernel: [ 3942.356136] Process gdm (pid: 5524, ti=f36d0000 task=f367b9f0 task.ti=f36d0000)
Mar 16 08:39:13 fionex-d kernel: [ 3942.356138] Stack: 00000001 47ca13f3 00000000 0031a068 00000000 00000075 f336ce40 00000000 
Mar 16 08:39:13 fionex-d kernel: [ 3942.356142]        f3fd0df0 c0183f3e 0031a068 b73d3000 00000001 00000005 00000001 00000000 
Mar 16 08:39:13 fionex-d kernel: [ 3942.356147]        00000000 f3431574 fffffff7 00000001 00000000 c01087fb 00000001 00000001 
Mar 16 08:39:13 fionex-d kernel: [ 3942.356151] Call Trace:
Mar 16 08:39:13 fionex-d kernel: [ 3942.356157]  [sys_fstat64+30/48] sys_fstat64+0x1e/0x30
Mar 16 08:39:13 fionex-d kernel: [ 3942.356164]  [sys_mmap2+187/208] sys_mmap2+0xbb/0xd0
Mar 16 08:39:13 fionex-d kernel: [ 3942.356170]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 08:39:13 fionex-d kernel: [ 3942.356176]  [clip_ioctl+928/1296] clip_ioctl+0x3a0/0x510
Mar 16 08:39:13 fionex-d kernel: [ 3942.356181]  =======================
Mar 16 08:39:13 fionex-d kernel: [ 3942.356182] Code: 8b 7c 24 24 f6 87 3c 01 00 00 04 74 0e 8b 44 24 1c f6 40 1c 02 0f 85 08 01 00 00 8b 54 24 24 8b 82 98 00 00 00 b6 40 30 40 74 1f <0f> b7 42 6a 25 08 04 00 00 3d 00 04 00 00 75 0f 89 d0 e8 23 01 
Mar 16 08:39:13 fionex-d kernel: [ 3942.356205] EIP: [do_mmap_pgoff+518/2000] do_mmap_pgoff+0x206/0x7d0 SS:ESP 0068:f36d1f3c
Mar 16 08:39:23 fionex-d kernel: [ 3952.656438] general protection fault: 0000 [#3]
Mar 16 08:39:23 fionex-d kernel: [ 3952.656441] SMP 
Mar 16 08:39:23 fionex-d kernel: [ 3952.656443] Modules linked in: af_packet binfmt_misc ipv6 ppdev sbs dock button ac video container battery coretemp it87 hwmon_vid i2c_isa i2c_core lp snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer fglrx(P) snd_seq_device pcspkr parport_pc parport intel_agp agpgart snd soundcore snd_page_alloc shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_generic usbhid hid floppy ata_piix r8169 pata_jmicron libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 08:39:23 fionex-d kernel: [ 3952.656479] CPU:    1
Mar 16 08:39:23 fionex-d kernel: [ 3952.656479] EIP:    0060:[do_mmap_pgoff+518/2000]    Tainted: P       VLI
Mar 16 08:39:23 fionex-d kernel: [ 3952.656480] EFLAGS: 00010282   (2.6.22-14-generic #1)
Mar 16 08:39:23 fionex-d kernel: [ 3952.656485] EIP is at do_mmap_pgoff+0x206/0x7d0
Mar 16 08:39:23 fionex-d kernel: [ 3952.656487] eax: df8e3a00   ebx: f3121540   ecx: f36bb240   edx: f3364070
Mar 16 08:39:23 fionex-d kernel: [ 3952.656489] esi: 00060000   edi: f3364570   ebp: 00000000   esp: f3065ee8
Mar 16 08:39:23 fionex-d kernel: [ 3952.656491] ds: 0000   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Mar 16 08:39:23 fionex-d kernel: [ 3952.656493] Process gdmgreeter (pid: 5699, ti=f3064000 task=c23c8000 task.ti=f3064000)
Mar 16 08:39:23 fionex-d kernel: [ 3952.656495] Stack: 00000001 f3364570 000081ff f3364510 c01781a4 00000077 f36bb240 00060000 
Mar 16 08:39:23 fionex-d kernel: [ 3952.656500]        f3364570 00000282 c01792bf b6934000 00000060 00000007 f3348c08 c01819ff 
Mar 16 08:39:23 fionex-d kernel: [ 3952.656505]        00001000 f33cf7e0 f3348c08 f3ef52a8 c03b7da0 c01cb793 00000003 00000001 
Mar 16 08:39:23 fionex-d kernel: [ 3952.656510] Call Trace:
Mar 16 08:39:23 fionex-d kernel: [ 3952.656514]  [shmem_get_inode+164/432] shmem_get_inode+0xa4/0x1b0
Mar 16 08:39:23 fionex-d kernel: [ 3952.656520]  [shmem_file_setup+223/432] shmem_file_setup+0xdf/0x1b0
Mar 16 08:39:23 fionex-d kernel: [ 3952.656524]  [get_empty_filp+111/352] get_empty_filp+0x6f/0x160
Mar 16 08:39:23 fionex-d kernel: [ 3952.656529]  [do_shmat+595/992] do_shmat+0x253/0x3e0
Mar 16 08:39:23 fionex-d kernel: [ 3952.656538]  [sys_ipc+323/608] sys_ipc+0x143/0x260
Mar 16 08:39:23 fionex-d kernel: [ 3952.656543]  [do_page_fault+0/1680] do_page_fault+0x0/0x690
Mar 16 08:39:23 fionex-d kernel: [ 3952.656548]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 08:39:23 fionex-d kernel: [ 3952.656556]  =======================
Mar 16 08:39:23 fionex-d kernel: [ 3952.656557] Code: 8b 7c 24 24 f6 87 3c 01 00 00 04 74 0e 8b 44 24 1c f6 40 1c 02 0f 85 08 01 00 00 8b 54 24 24 8b 82 98 00 00 00 b6 40 30 40 74 1f <0f> b7 42 6a 25 08 04 00 00 3d 00 04 00 00 75 0f 89 d0 e8 23 01 
Mar 16 08:39:23 fionex-d kernel: [ 3952.656579] EIP: [do_mmap_pgoff+518/2000] do_mmap_pgoff+0x206/0x7d0 SS:ESP 0068:f3065ee8
Mar 16 08:39:57 fionex-d kernel: [ 3986.400747] [fglrx] interrupt source 20000400 successfully disabled!
Mar 16 08:39:57 fionex-d kernel: [ 3986.400751] [fglrx] enable ID = 0x00000000
Mar 16 08:39:57 fionex-d kernel: [ 3986.400754] [fglrx] Receive disable interrupt message with irqEnableMask: 20000400; dwIRQEnableId: 0000000d
Mar 16 08:39:57 fionex-d kernel: [ 3986.400762] [fglrx] interrupt source ff00002d successfully disabled!
Mar 16 08:39:57 fionex-d kernel: [ 3986.400764] [fglrx] enable ID = 0x00000000
Mar 16 08:39:57 fionex-d kernel: [ 3986.400766] [fglrx] Receive disable interrupt message with irqEnableMask: ff00002d; dwIRQEnableId: 0000000c
Mar 16 08:39:57 fionex-d kernel: [ 3986.400771] [fglrx] interrupt source ff00002c successfully disabled!
Mar 16 08:39:57 fionex-d kernel: [ 3986.400773] [fglrx] enable ID = 0x00000000
Mar 16 08:39:57 fionex-d kernel: [ 3986.400776] [fglrx] Receive disable interrupt message with irqEnableMask: ff00002c; dwIRQEnableId: 0000000b
Mar 16 08:39:57 fionex-d kernel: [ 3986.400782] [fglrx] interrupt source 00000040 successfully disabled!
Mar 16 08:39:57 fionex-d kernel: [ 3986.400783] [fglrx] enable ID = 0x00000000
Mar 16 08:39:57 fionex-d kernel: [ 3986.400786] [fglrx] Receive disable interrupt message with irqEnableMask: 00000040; dwIRQEnableId: 0000000a
Mar 16 08:39:57 fionex-d kernel: [ 3986.400793] [fglrx] interrupt source 60000001 successfully disabled!
Mar 16 08:39:57 fionex-d kernel: [ 3986.400795] [fglrx] enable ID = 0x00000000
Mar 16 08:39:57 fionex-d kernel: [ 3986.400798] [fglrx] Receive disable interrupt message with irqEnableMask: 60000001; dwIRQEnableId: 00000009
Mar 16 08:39:57 fionex-d kernel: [ 3986.400805] [fglrx] interrupt source 10000000 successfully disabled!
Mar 16 08:39:57 fionex-d kernel: [ 3986.400807] [fglrx] enable ID = 0x00000000
Mar 16 08:39:57 fionex-d kernel: [ 3986.400809] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000008
Mar 16 08:39:57 fionex-d kernel: [ 3986.400817] [fglrx] interrupt source 20008000 successfully disabled!
Mar 16 08:39:57 fionex-d kernel: [ 3986.400819] [fglrx] enable ID = 0x00000000
Mar 16 08:39:57 fionex-d kernel: [ 3986.400821] [fglrx] Receive disable interrupt message with irqEnableMask: 20008000; dwIRQEnableId: 00000006
Mar 16 08:39:57 fionex-d kernel: [ 3986.678432] general protection fault: 0000 [#4]
Mar 16 08:39:57 fionex-d kernel: [ 3986.678433] SMP 
Mar 16 08:39:57 fionex-d kernel: [ 3986.678435] Modules linked in: af_packet binfmt_misc ipv6 ppdev sbs dock button ac video container battery coretemp it87 hwmon_vid i2c_isa i2c_core lp snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer fglrx(P) snd_seq_device pcspkr parport_pc parport intel_agp agpgart snd soundcore snd_page_alloc shpchp pci_hotplug evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_generic usbhid hid floppy ata_piix r8169 pata_jmicron libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
Mar 16 08:39:57 fionex-d kernel: [ 3986.678471] CPU:    1
Mar 16 08:39:57 fionex-d kernel: [ 3986.678472] EIP:    0060:[do_mmap_pgoff+518/2000]    Tainted: P       VLI
Mar 16 08:39:57 fionex-d kernel: [ 3986.678473] EFLAGS: 00013202   (2.6.22-14-generic #1)
Mar 16 08:39:57 fionex-d kernel: [ 3986.678478] EIP is at do_mmap_pgoff+0x206/0x7d0
Mar 16 08:39:57 fionex-d kernel: [ 3986.678480] eax: df85fc00   ebx: f36941c0   ecx: ec922900   edx: c2204010
Mar 16 08:39:57 fionex-d kernel: [ 3986.678482] esi: 00010000   edi: c2208210   ebp: 000000a0   esp: f36ddf3c
Mar 16 08:39:57 fionex-d kernel: [ 3986.678484] ds: 00a0   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Mar 16 08:39:57 fionex-d kernel: [ 3986.678486] Process Xorg (pid: 5531, ti=f36dc000 task=c210a000 task.ti=f36dc000)
Mar 16 08:39:57 fionex-d kernel: [ 3986.678488] Stack: 00000001 f36ddf90 00000101 00000001 00000000 00000073 ec922900 c21538f0 
Mar 16 08:39:57 fionex-d kernel: [ 3986.678493]        c2208210 00000000 00000000 b6f70000 00000010 00000003 00000000 00003287 
Mar 16 08:39:57 fionex-d kernel: [ 3986.678497]        c017ea1e f36941f4 fffffff7 00000001 000000a0 c01087fb 00000003 00000001 
Mar 16 08:39:57 fionex-d kernel: [ 3986.678502] Call Trace:
Mar 16 08:39:57 fionex-d kernel: [ 3986.678508]  [fd_install+30/80] fd_install+0x1e/0x50
Mar 16 08:39:57 fionex-d kernel: [ 3986.678514]  [sys_mmap2+187/208] sys_mmap2+0xbb/0xd0
Mar 16 08:39:57 fionex-d kernel: [ 3986.678520]  [sysenter_past_esp+107/169] sysenter_past_esp+0x6b/0xa9
Mar 16 08:39:57 fionex-d kernel: [ 3986.678527]  =======================
Mar 16 08:39:57 fionex-d kernel: [ 3986.678528] Code: 8b 7c 24 24 f6 87 3c 01 00 00 04 74 0e 8b 44 24 1c f6 40 1c 02 0f 85 08 01 00 00 8b 54 24 24 8b 82 98 00 00 00 b6 40 30 40 74 1f <0f> b7 42 6a 25 08 04 00 00 3d 00 04 00 00 75 0f 89 d0 e8 23 01 
Mar 16 08:39:57 fionex-d kernel: [ 3986.678551] EIP: [do_mmap_pgoff+518/2000] do_mmap_pgoff+0x206/0x7d0 SS:ESP 0068:f36ddf3c
Mar 16 08:41:23 fionex-d kernel: Inspecting /boot/System.map-2.6.22-14-generic
Mar 16 08:41:23 fionex-d kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Mar 16 08:41:23 fionex-d kernel: Symbols match kernel version 2.6.22.
Mar 16 08:41:23 fionex-d kernel: No module symbols loaded - kernel modules not enabled. 
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 16 08:41:23 fionex-d kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Mar 16 08:41:23 fionex-d kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Mar 16 08:41:23 fionex-d kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar 16 08:41:23 fionex-d kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Mar 16 08:41:23 fionex-d kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Mar 16 08:41:23 fionex-d kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Mar 16 08:41:23 fionex-d kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Mar 16 08:41:23 fionex-d kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Mar 16 08:41:23 fionex-d kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] 1150MB HIGHMEM available.
Mar 16 08:41:23 fionex-d kernel: [    0.000000] 896MB LOWMEM available.
Mar 16 08:41:23 fionex-d kernel: [    0.000000] found SMP MP-table at 000f5180
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Entering add_active_range(0, 0, 524000) 0 entries of 256 used
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Zone PFN ranges:
Mar 16 08:41:23 fionex-d kernel: [    0.000000]   DMA             0 ->     4096
Mar 16 08:41:23 fionex-d kernel: [    0.000000]   Normal       4096 ->   229376
Mar 16 08:41:23 fionex-d kernel: [    0.000000]   HighMem    229376 ->   524000
Mar 16 08:41:23 fionex-d kernel: [    0.000000] early_node_map[1] active PFN ranges
Mar 16 08:41:23 fionex-d kernel: [    0.000000]     0:        0 ->   524000
Mar 16 08:41:23 fionex-d kernel: [    0.000000] On node 0 totalpages: 524000
Mar 16 08:41:23 fionex-d kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Mar 16 08:41:23 fionex-d kernel: [    0.000000]   DMA zone: 0 pages reserved
Mar 16 08:41:23 fionex-d kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Mar 16 08:41:23 fionex-d kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Mar 16 08:41:23 fionex-d kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Mar 16 08:41:23 fionex-d kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Mar 16 08:41:23 fionex-d kernel: [    0.000000]   HighMem zone: 292323 pages, LIFO batch:31
Mar 16 08:41:23 fionex-d kernel: [    0.000000] DMI 2.4 present.
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6B40 checksum 0
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: RSDP 000F6B40, 0014 (r0 GBT   )
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: RSDT 7FEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: DSDT 7FEE3180, 4B25 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: FACS 7FEE0000, 0040
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: HPET 7FEE7E00, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: MCFG 7FEE7E80, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: APIC 7FEE7D00, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: SSDT 7FEE7F00, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: SSDT 7FEE8390, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Processor #0 6:15 APIC version 20
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Processor #1 6:15 APIC version 20
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Mar 16 08:41:23 fionex-d kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: IRQ0 used by override.
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: IRQ2 used by override.
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: IRQ9 used by override.
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar 16 08:41:23 fionex-d kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Built 1 zonelists.  Total pages: 519907
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Kernel command line: root=UUID=95f8170d-5d4a-4fb3-b80c-a74bbc119ae5 ro quiet splash
Mar 16 08:41:23 fionex-d kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Enabling fast FPU save and restore... done.
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Initializing CPU#0
Mar 16 08:41:23 fionex-d kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 16 08:41:23 fionex-d kernel: [    0.000000] Detected 2333.422 MHz processor.
Mar 16 08:41:23 fionex-d kernel: [   21.349457] Console: colour VGA+ 80x25
Mar 16 08:41:23 fionex-d kernel: [   21.349614] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 16 08:41:23 fionex-d kernel: [   21.349810] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 16 08:41:23 fionex-d kernel: [   21.412086] Memory: 2066592k/2096000k available (2015k kernel code, 28184k reserved, 915k data, 364k init, 1178496k highmem)
Mar 16 08:41:23 fionex-d kernel: [   21.412093] virtual kernel memory layout:
Mar 16 08:41:23 fionex-d kernel: [   21.412093]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Mar 16 08:41:23 fionex-d kernel: [   21.412094]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Mar 16 08:41:23 fionex-d kernel: [   21.412095]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Mar 16 08:41:23 fionex-d kernel: [   21.412096]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Mar 16 08:41:23 fionex-d kernel: [   21.412097]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Mar 16 08:41:23 fionex-d kernel: [   21.412098]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
Mar 16 08:41:23 fionex-d kernel: [   21.412098]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
Mar 16 08:41:23 fionex-d kernel: [   21.412100] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Mar 16 08:41:23 fionex-d kernel: [   21.412125] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Mar 16 08:41:23 fionex-d kernel: [   21.412228] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Mar 16 08:41:23 fionex-d kernel: [   21.412232] hpet0: 4 64-bit timers, 14318180 Hz
Mar 16 08:41:23 fionex-d kernel: [   21.493085] Calibrating delay using timer specific routine.. 4669.84 BogoMIPS (lpj=9339696)
Mar 16 08:41:23 fionex-d kernel: [   21.493100] Security Framework v1.0.0 initialized
Mar 16 08:41:23 fionex-d kernel: [   21.493104] SELinux:  Disabled at boot.
Mar 16 08:41:23 fionex-d kernel: [   21.493113] Mount-cache hash table entries: 512
Mar 16 08:41:23 fionex-d kernel: [   21.493192] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3fd 00000000 00000001
Mar 16 08:41:23 fionex-d kernel: [   21.493197] monitor/mwait feature present.
Mar 16 08:41:23 fionex-d kernel: [   21.493198] using mwait in idle threads.
Mar 16 08:41:23 fionex-d kernel: [   21.493201] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 16 08:41:23 fionex-d kernel: [   21.493203] CPU: L2 cache: 4096K
Mar 16 08:41:23 fionex-d kernel: [   21.493205] CPU: Physical Processor ID: 0
Mar 16 08:41:23 fionex-d kernel: [   21.493206] CPU: Processor Core ID: 0
Mar 16 08:41:23 fionex-d kernel: [   21.493207] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3fd 00000000 00000001
Mar 16 08:41:23 fionex-d kernel: [   21.493214] Compat vDSO mapped to ffffe000.
Mar 16 08:41:23 fionex-d kernel: [   21.493222] Checking 'hlt' instruction... OK.
Mar 16 08:41:23 fionex-d kernel: [   21.509131] SMP alternatives: switching to UP code
Mar 16 08:41:23 fionex-d kernel: [   21.509429] Early unpacking initramfs... done
Mar 16 08:41:23 fionex-d kernel: [   21.741753] ACPI: Core revision 20070126
Mar 16 08:41:23 fionex-d kernel: [   21.741784] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Mar 16 08:41:23 fionex-d kernel: [   21.744112] CPU0: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz stepping 0b
Mar 16 08:41:23 fionex-d kernel: [   21.744125] SMP alternatives: switching to SMP code
Mar 16 08:41:23 fionex-d kernel: [   21.744169] Booting processor 1/1 eip 3000
Mar 16 08:41:23 fionex-d kernel: [   21.754427] Initializing CPU#1
Mar 16 08:41:23 fionex-d kernel: [   21.832415] Calibrating delay using timer specific routine.. 4666.66 BogoMIPS (lpj=9333332)
Mar 16 08:41:23 fionex-d kernel: [   21.832419] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3fd 00000000 00000001
Mar 16 08:41:23 fionex-d kernel: [   21.832423] monitor/mwait feature present.
Mar 16 08:41:23 fionex-d kernel: [   21.832425] CPU: L1 I cache: 32K, L1 D cache: 32K
Mar 16 08:41:23 fionex-d kernel: [   21.832426] CPU: L2 cache: 4096K
Mar 16 08:41:23 fionex-d kernel: [   21.832428] CPU: Physical Processor ID: 0
Mar 16 08:41:23 fionex-d kernel: [   21.832429] CPU: Processor Core ID: 1
Mar 16 08:41:23 fionex-d kernel: [   21.832430] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3fd 00000000 00000001
Mar 16 08:41:23 fionex-d kernel: [   21.833004] CPU1: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz stepping 0b
Mar 16 08:41:23 fionex-d kernel: [   21.833018] Total of 2 processors activated (9336.51 BogoMIPS).
Mar 16 08:41:23 fionex-d kernel: [   21.833154] ENABLING IO-APIC IRQs
Mar 16 08:41:23 fionex-d kernel: [   21.833312] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 16 08:41:23 fionex-d kernel: [   21.980183] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Mar 16 08:41:23 fionex-d kernel: [   22.000156] Brought up 2 CPUs
Mar 16 08:41:23 fionex-d kernel: [   22.073236] migration_cost=16
Mar 16 08:41:23 fionex-d kernel: [   22.073323] Booting paravirtualized kernel on bare hardware
Mar 16 08:41:23 fionex-d kernel: [   22.073369] Time:  8:41:13  Date: 02/16/108
Mar 16 08:41:23 fionex-d kernel: [   22.073382] NET: Registered protocol family 16
Mar 16 08:41:23 fionex-d kernel: [   22.073436] EISA bus registered
Mar 16 08:41:23 fionex-d kernel: [   22.073439] ACPI: bus type pci registered
Mar 16 08:41:23 fionex-d kernel: [   22.079123] PCI: PCI BIOS revision 3.00 entry at 0xfb1c0, last bus=5
Mar 16 08:41:23 fionex-d kernel: [   22.079124] PCI: Using configuration type 1
Mar 16 08:41:23 fionex-d kernel: [   22.079125] Setting up standard PCI resources
Mar 16 08:41:23 fionex-d kernel: [   22.080413] ACPI: EC: Look up EC in DSDT
Mar 16 08:41:23 fionex-d kernel: [   22.083534] ACPI: Interpreter enabled
Mar 16 08:41:23 fionex-d kernel: [   22.083538] ACPI: (supports S0 S3 S4 S5)
Mar 16 08:41:23 fionex-d kernel: [   22.083550] ACPI: Using IOAPIC for interrupt routing
Mar 16 08:41:23 fionex-d kernel: [   22.088002] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 16 08:41:23 fionex-d kernel: [   22.088018] PCI: Probing PCI hardware (bus 00)
Mar 16 08:41:23 fionex-d kernel: [   22.089139] PCI: Transparent bridge - 0000:00:1e.0
Mar 16 08:41:23 fionex-d kernel: [   22.089187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Mar 16 08:41:23 fionex-d kernel: [   22.089291] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Mar 16 08:41:23 fionex-d kernel: [   22.089348] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
Mar 16 08:41:23 fionex-d kernel: [   22.089405] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
Mar 16 08:41:23 fionex-d kernel: [   22.089462] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Mar 16 08:41:23 fionex-d kernel: [   22.101572] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Mar 16 08:41:23 fionex-d kernel: [   22.101648] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Mar 16 08:41:23 fionex-d kernel: [   22.101722] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Mar 16 08:41:23 fionex-d kernel: [   22.101796] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Mar 16 08:41:23 fionex-d kernel: [   22.101875] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Mar 16 08:41:23 fionex-d kernel: [   22.101949] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Mar 16 08:41:23 fionex-d kernel: [   22.102023] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
Mar 16 08:41:23 fionex-d kernel: [   22.102097] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Mar 16 08:41:23 fionex-d kernel: [   22.102172] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar 16 08:41:23 fionex-d kernel: [   22.102179] pnp: PnP ACPI init
Mar 16 08:41:23 fionex-d kernel: [   22.102185] ACPI: bus type pnp registered
Mar 16 08:41:23 fionex-d kernel: [   22.104240] pnp: PnP ACPI: found 15 devices
Mar 16 08:41:23 fionex-d kernel: [   22.104241] ACPI: ACPI bus type pnp unregistered
Mar 16 08:41:23 fionex-d kernel: [   22.104245] PnPBIOS: Disabled by ACPI PNP
Mar 16 08:41:23 fionex-d kernel: [   22.104280] PCI: Using ACPI for IRQ routing
Mar 16 08:41:23 fionex-d kernel: [   22.104281] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Mar 16 08:41:23 fionex-d kernel: [   22.134214] NET: Registered protocol family 8
Mar 16 08:41:23 fionex-d kernel: [   22.134215] NET: Registered protocol family 20
Mar 16 08:41:23 fionex-d kernel: [   22.134254] pnp: 00:0b: ioport range 0x400-0x4bf has been reserved
Mar 16 08:41:23 fionex-d kernel: [   22.134258] pnp: 00:0c: iomem range 0xf0000000-0xf3ffffff could not be reserved
Mar 16 08:41:23 fionex-d kernel: [   22.134262] pnp: 00:0d: iomem range 0xf0000-0xf3fff could not be reserved
Mar 16 08:41:23 fionex-d kernel: [   22.134264] pnp: 00:0d: iomem range 0xf4000-0xf7fff could not be reserved
Mar 16 08:41:23 fionex-d kernel: [   22.134266] pnp: 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
Mar 16 08:41:23 fionex-d kernel: [   22.134268] pnp: 00:0d: iomem range 0xfc000-0xfffff could not be reserved
Mar 16 08:41:23 fionex-d kernel: [   22.135823] Time: tsc clocksource has been installed.
Mar 16 08:41:23 fionex-d kernel: [   22.135829] Switched to high resolution mode on CPU 0
Mar 16 08:41:23 fionex-d kernel: [   22.135886] Switched to high resolution mode on CPU 1
Mar 16 08:41:23 fionex-d kernel: [   22.164406] PCI: Bridge: 0000:00:01.0
Mar 16 08:41:23 fionex-d kernel: [   22.164407]   IO window: b000-bfff
Mar 16 08:41:23 fionex-d kernel: [   22.164410]   MEM window: f4000000-f5ffffff
Mar 16 08:41:23 fionex-d kernel: [   22.164413]   PREFETCH window: e0000000-efffffff
Mar 16 08:41:23 fionex-d kernel: [   22.164415] PCI: Bridge: 0000:00:1c.0
Mar 16 08:41:23 fionex-d kernel: [   22.164417]   IO window: 9000-9fff
Mar 16 08:41:23 fionex-d kernel: [   22.164420]   MEM window: disabled.
Mar 16 08:41:23 fionex-d kernel: [   22.164423]   PREFETCH window: disabled.
Mar 16 08:41:23 fionex-d kernel: [   22.164426] PCI: Bridge: 0000:00:1c.3
Mar 16 08:41:23 fionex-d kernel: [   22.164428]   IO window: c000-cfff
Mar 16 08:41:23 fionex-d kernel: [   22.164432]   MEM window: f6000000-f6ffffff
Mar 16 08:41:23 fionex-d kernel: [   22.164434]   PREFETCH window: disabled.
Mar 16 08:41:23 fionex-d kernel: [   22.164438] PCI: Bridge: 0000:00:1c.4
Mar 16 08:41:23 fionex-d kernel: [   22.164440]   IO window: d000-dfff
Mar 16 08:41:23 fionex-d kernel: [   22.164443]   MEM window: f7000000-f8ffffff
Mar 16 08:41:23 fionex-d kernel: [   22.164446]   PREFETCH window: 80000000-800fffff
Mar 16 08:41:23 fionex-d kernel: [   22.164450] PCI: Bridge: 0000:00:1e.0
Mar 16 08:41:23 fionex-d kernel: [   22.164452]   IO window: a000-afff
Mar 16 08:41:23 fionex-d kernel: [   22.164455]   MEM window: disabled.
Mar 16 08:41:23 fionex-d kernel: [   22.164458]   PREFETCH window: disabled.
Mar 16 08:41:23 fionex-d kernel: [   22.164468] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 16 08:41:23 fionex-d kernel: [   22.164471] PCI: Setting latency timer of device 0000:00:01.0 to 64
Mar 16 08:41:23 fionex-d kernel: [   22.164484] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 16 08:41:23 fionex-d kernel: [   22.164488] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Mar 16 08:41:23 fionex-d kernel: [   22.164501] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Mar 16 08:41:23 fionex-d kernel: [   22.164505] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Mar 16 08:41:23 fionex-d kernel: [   22.164517] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
Mar 16 08:41:23 fionex-d kernel: [   22.164521] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Mar 16 08:41:23 fionex-d kernel: [   22.164529] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Mar 16 08:41:23 fionex-d kernel: [   22.164536] NET: Registered protocol family 2
Mar 16 08:41:23 fionex-d kernel: [   22.215661] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 16 08:41:23 fionex-d kernel: [   22.215694] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Mar 16 08:41:23 fionex-d kernel: [   22.216138] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 16 08:41:23 fionex-d kernel: [   22.216283] TCP: Hash tables configured (established 131072 bind 65536)
Mar 16 08:41:23 fionex-d kernel: [   22.216285] TCP reno registered
Mar 16 08:41:23 fionex-d kernel: [   22.231704] checking if image is initramfs... it is
Mar 16 08:41:23 fionex-d kernel: [   22.691134] Freeing initrd memory: 7061k freed
Mar 16 08:41:23 fionex-d kernel: [   22.691498] audit: initializing netlink socket (disabled)
Mar 16 08:41:23 fionex-d kernel: [   22.691507] audit(1205656873.100:1): initialized
Mar 16 08:41:23 fionex-d kernel: [   22.691566] highmem bounce pool size: 64 pages
Mar 16 08:41:23 fionex-d kernel: [   22.692794] VFS: Disk quotas dquot_6.5.1
Mar 16 08:41:23 fionex-d kernel: [   22.692825] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 16 08:41:23 fionex-d kernel: [   22.692885] io scheduler noop registered
Mar 16 08:41:23 fionex-d kernel: [   22.692886] io scheduler anticipatory registered
Mar 16 08:41:23 fionex-d kernel: [   22.692888] io scheduler deadline registered
Mar 16 08:41:23 fionex-d kernel: [   22.692897] io scheduler cfq registered (default)
Mar 16 08:41:23 fionex-d kernel: [   22.693000] Boot video device is 0000:01:00.0
Mar 16 08:41:23 fionex-d kernel: [   22.693053] PCI: Setting latency timer of device 0000:00:01.0 to 64
Mar 16 08:41:23 fionex-d kernel: [   22.693077] assign_interrupt_mode Found MSI capability
Mar 16 08:41:23 fionex-d kernel: [   22.693079] Allocate Port Service[0000:00:01.0:pcie00]
Mar 16 08:41:23 fionex-d kernel: [   22.693130] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Mar 16 08:41:23 fionex-d kernel: [   22.693161] assign_interrupt_mode Found MSI capability
Mar 16 08:41:23 fionex-d kernel: [   22.693163] Allocate Port Service[0000:00:1c.0:pcie00]
Mar 16 08:41:23 fionex-d kernel: [   22.693182] Allocate Port Service[0000:00:1c.0:pcie02]
Mar 16 08:41:23 fionex-d kernel: [   22.693238] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Mar 16 08:41:23 fionex-d kernel: [   22.693269] assign_interrupt_mode Found MSI capability
Mar 16 08:41:23 fionex-d kernel: [   22.693270] Allocate Port Service[0000:00:1c.3:pcie00]
Mar 16 08:41:23 fionex-d kernel: [   22.693291] Allocate Port Service[0000:00:1c.3:pcie02]
Mar 16 08:41:23 fionex-d kernel: [   22.693347] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Mar 16 08:41:23 fionex-d kernel: [   22.693378] assign_interrupt_mode Found MSI capability
Mar 16 08:41:23 fionex-d kernel: [   22.693379] Allocate Port Service[0000:00:1c.4:pcie00]
Mar 16 08:41:23 fionex-d kernel: [   22.693400] Allocate Port Service[0000:00:1c.4:pcie02]
Mar 16 08:41:23 fionex-d kernel: [   22.693494] isapnp: Scanning for PnP cards...
Mar 16 08:41:23 fionex-d kernel: [   23.045587] isapnp: No Plug & Play device found
Mar 16 08:41:23 fionex-d kernel: [   23.058796] Real Time Clock Driver v1.12ac
Mar 16 08:41:23 fionex-d kernel: [   23.058910] hpet_resources: 0xfed00000 is busy
Mar 16 08:41:23 fionex-d kernel: [   23.058937] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Mar 16 08:41:23 fionex-d kernel: [   23.059017] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 16 08:41:23 fionex-d kernel: [   23.059417] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 16 08:41:23 fionex-d kernel: [   23.059858] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Mar 16 08:41:23 fionex-d kernel: [   23.059992] input: Macintosh mouse button emulation as /class/input/input0
Mar 16 08:41:23 fionex-d kernel: [   23.060043] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Mar 16 08:41:23 fionex-d kernel: [   23.060045] PNP: PS/2 controller doesn't have AUX irq; using default 12
Mar 16 08:41:23 fionex-d kernel: [   23.062437] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 16 08:41:23 fionex-d kernel: [   23.062502] mice: PS/2 mouse device common for all mice
Mar 16 08:41:23 fionex-d kernel: [   23.062562] EISA: Probing bus 0 at eisa.0
Mar 16 08:41:23 fionex-d kernel: [   23.062585] EISA: Detected 0 cards.
Mar 16 08:41:23 fionex-d kernel: [   23.062695] TCP cubic registered
Mar 16 08:41:23 fionex-d kernel: [   23.062704] NET: Registered protocol family 1
Mar 16 08:41:23 fionex-d kernel: [   23.062717] Using IPI No-Shortcut mode
Mar 16 08:41:23 fionex-d kernel: [   23.062821]   Magic number: 0:163:675
Mar 16 08:41:23 fionex-d kernel: [   23.062860]   hash matches device vtcon0
Mar 16 08:41:23 fionex-d kernel: [   23.062968] Freeing unused kernel memory: 364k freed
Mar 16 08:41:23 fionex-d kernel: [   23.081959] input: AT Translated Set 2 keyboard as /class/input/input1
Mar 16 08:41:23 fionex-d kernel: [   24.195607] AppArmor: AppArmor initialized<5>audit(1205656874.600:2):  type=1505 info="AppArmor initialized" pid=1249
Mar 16 08:41:23 fionex-d kernel: [   24.199635] fuse init (API version 7.8)
Mar 16 08:41:23 fionex-d kernel: [   24.202608] Failure registering capabilities with primary security module.
Mar 16 08:41:23 fionex-d kernel: [   24.228967] ACPI: Processor [CPU0] (supports 8 throttling states)
Mar 16 08:41:23 fionex-d kernel: [   24.229047] ACPI: SSDT 7FEE8300, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
Mar 16 08:41:23 fionex-d kernel: [   24.229131] ACPI: Processor [CPU1] (supports 8 throttling states)
Mar 16 08:41:23 fionex-d kernel: [   24.229138] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Mar 16 08:41:23 fionex-d kernel: [   24.229145] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
Mar 16 08:41:23 fionex-d kernel: [   24.492456] usbcore: registered new interface driver usbfs
Mar 16 08:41:23 fionex-d kernel: [   24.492474] usbcore: registered new interface driver hub
Mar 16 08:41:23 fionex-d kernel: [   24.492486] usbcore: registered new device driver usb
Mar 16 08:41:23 fionex-d kernel: [   24.494776] USB Universal Host Controller Interface driver v3.0
Mar 16 08:41:23 fionex-d kernel: [   24.494816] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 16 08:41:23 fionex-d kernel: [   24.494824] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Mar 16 08:41:23 fionex-d kernel: [   24.494826] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Mar 16 08:41:23 fionex-d kernel: [   24.494911] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Mar 16 08:41:23 fionex-d kernel: [   24.494933] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e100
Mar 16 08:41:23 fionex-d kernel: [   24.495003] usb usb1: configuration #1 chosen from 1 choice
Mar 16 08:41:23 fionex-d kernel: [   24.495020] hub 1-0:1.0: USB hub found
Mar 16 08:41:23 fionex-d kernel: [   24.495024] hub 1-0:1.0: 2 ports detected
Mar 16 08:41:23 fionex-d kernel: [   24.563878] SCSI subsystem initialized
Mar 16 08:41:23 fionex-d kernel: [   24.567223] libata version 2.21 loaded.
Mar 16 08:41:23 fionex-d kernel: [   24.595066] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
Mar 16 08:41:23 fionex-d kernel: [   24.595075] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Mar 16 08:41:23 fionex-d kernel: [   24.595078] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Mar 16 08:41:23 fionex-d kernel: [   24.595093] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Mar 16 08:41:23 fionex-d kernel: [   24.595115] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000e200
Mar 16 08:41:23 fionex-d kernel: [   24.595179] usb usb2: configuration #1 chosen from 1 choice
Mar 16 08:41:23 fionex-d kernel: [   24.595195] hub 2-0:1.0: USB hub found
Mar 16 08:41:23 fionex-d kernel: [   24.595199] hub 2-0:1.0: 2 ports detected
Mar 16 08:41:23 fionex-d kernel: [   24.609252] Floppy drive(s): fd0 is 1.44M
Mar 16 08:41:23 fionex-d kernel: [   24.626522] FDC 0 is a post-1991 82077
Mar 16 08:41:23 fionex-d kernel: [   24.698856] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 19
Mar 16 08:41:23 fionex-d kernel: [   24.698864] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Mar 16 08:41:23 fionex-d kernel: [   24.698868] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Mar 16 08:41:23 fionex-d kernel: [   24.698887] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
Mar 16 08:41:23 fionex-d kernel: [   24.698909] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Mar 16 08:41:23 fionex-d kernel: [   24.698916] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf9004000
Mar 16 08:41:23 fionex-d kernel: [   24.702790] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 16 08:41:23 fionex-d kernel: [   24.702838] usb usb3: configuration #1 chosen from 1 choice
Mar 16 08:41:23 fionex-d kernel: [   24.702855] hub 3-0:1.0: USB hub found
Mar 16 08:41:23 fionex-d kernel: [   24.702858] hub 3-0:1.0: 6 ports detected
Mar 16 08:41:23 fionex-d kernel: [   24.806595] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Mar 16 08:41:23 fionex-d kernel: [   24.806601] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Mar 16 08:41:23 fionex-d kernel: [   24.806604] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Mar 16 08:41:23 fionex-d kernel: [   24.806618] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
Mar 16 08:41:23 fionex-d kernel: [   24.806638] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Mar 16 08:41:23 fionex-d kernel: [   24.806643] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf9005000
Mar 16 08:41:23 fionex-d kernel: [   24.810520] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 16 08:41:23 fionex-d kernel: [   24.810569] usb usb4: configuration #1 chosen from 1 choice
Mar 16 08:41:23 fionex-d kernel: [   24.810587] hub 4-0:1.0: USB hub found
Mar 16 08:41:23 fionex-d kernel: [   24.810590] hub 4-0:1.0: 6 ports detected
Mar 16 08:41:23 fionex-d kernel: [   24.914448] ata_piix 0000:00:1f.2: version 2.11
Mar 16 08:41:23 fionex-d kernel: [   24.914452] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Mar 16 08:41:23 fionex-d kernel: [   24.914466] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
Mar 16 08:41:23 fionex-d kernel: [   24.914485] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Mar 16 08:41:23 fionex-d kernel: [   24.914538] scsi0 : ata_piix
Mar 16 08:41:23 fionex-d kernel: [   24.914561] scsi1 : ata_piix
Mar 16 08:41:23 fionex-d kernel: [   24.914628] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
Mar 16 08:41:23 fionex-d kernel: [   24.914631] ata2: SATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
Mar 16 08:41:23 fionex-d kernel: [   25.078566] ata1.00: Host Protected Area detected:
Mar 16 08:41:23 fionex-d kernel: [   25.078567] ^Icurrent size: 488395055 sectors
Mar 16 08:41:23 fionex-d kernel: [   25.078568] ^Inative size: 488397168 sectors
Mar 16 08:41:23 fionex-d kernel: [   25.078759] ata1.00: native size increased to 488397168 sectors
Mar 16 08:41:23 fionex-d kernel: [   25.078763] ata1.00: ATA-8: WDC WD2500AAKS-00VSA0, 01.01B01, max UDMA/133
Mar 16 08:41:23 fionex-d kernel: [   25.078765] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Mar 16 08:41:23 fionex-d kernel: [   25.094521] ata1.00: configured for UDMA/133
Mar 16 08:41:23 fionex-d kernel: [   25.260299] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500AAKS-0 01.0 PQ: 0 ANSI: 5
Mar 16 08:41:23 fionex-d kernel: [   25.260339] ata_piix 0000:00:1f.5: MAP [ P0 P2 P1 P3 ]
Mar 16 08:41:23 fionex-d kernel: [   25.260353] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 17
Mar 16 08:41:23 fionex-d kernel: [   25.260371] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Mar 16 08:41:23 fionex-d kernel: [   25.260392] scsi2 : ata_piix
Mar 16 08:41:23 fionex-d kernel: [   25.260413] scsi3 : ata_piix
Mar 16 08:41:23 fionex-d kernel: [   25.260476] ata3: SATA max UDMA/133 cmd 0x0001e700 ctl 0x0001e802 bmdma 0x0001eb00 irq 17
Mar 16 08:41:23 fionex-d kernel: [   25.260478] ata4: SATA max UDMA/133 cmd 0x0001e900 ctl 0x0001ea02 bmdma 0x0001eb08 irq 17
Mar 16 08:41:23 fionex-d kernel: [   25.441297] usb 2-1: new low speed USB device using uhci_hcd and address 2
Mar 16 08:41:23 fionex-d kernel: [   25.587579] r8169 Gigabit Ethernet driver 2.2LK loaded
Mar 16 08:41:23 fionex-d kernel: [   25.587596] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 16 08:41:23 fionex-d kernel: [   25.587608] PCI: Setting latency timer of device 0000:04:00.0 to 64
Mar 16 08:41:23 fionex-d kernel: [   25.587776] eth0: RTL8168b/8111b at 0xf884a000, 00:1d:7d:ab:24:6f, XID 38000000 IRQ 16
Mar 16 08:41:23 fionex-d kernel: [   25.589406] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
Mar 16 08:41:23 fionex-d kernel: [   25.589428] PCI: Setting latency timer of device 0000:03:00.0 to 64
Mar 16 08:41:23 fionex-d kernel: [   25.589453] scsi4 : pata_jmicron
Mar 16 08:41:23 fionex-d kernel: [   25.589574] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 19
Mar 16 08:41:23 fionex-d kernel: [   25.589580] PCI: Setting latency timer of device 0000:00:1a.2 to 64
Mar 16 08:41:23 fionex-d kernel: [   25.589582] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Mar 16 08:41:23 fionex-d kernel: [   25.589600] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Mar 16 08:41:23 fionex-d kernel: [   25.589619] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000e000
Mar 16 08:41:23 fionex-d kernel: [   25.589683] usb usb5: configuration #1 chosen from 1 choice
Mar 16 08:41:23 fionex-d kernel: [   25.589704] hub 5-0:1.0: USB hub found
Mar 16 08:41:23 fionex-d kernel: [   25.589707] hub 5-0:1.0: 2 ports detected
Mar 16 08:41:23 fionex-d kernel: [   25.589815] scsi5 : pata_jmicron
Mar 16 08:41:23 fionex-d kernel: [   25.589880] ata5: PATA max UDMA/100 cmd 0x0001c000 ctl 0x0001c102 bmdma 0x0001c400 irq 17
Mar 16 08:41:23 fionex-d kernel: [   25.589883] ata6: PATA max UDMA/100 cmd 0x0001c200 ctl 0x0001c302 bmdma 0x0001c408 irq 17
Mar 16 08:41:23 fionex-d kernel: [   25.592792] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Mar 16 08:41:23 fionex-d kernel: [   25.592800] sd 0:0:0:0: [sda] Write Protect is off
Mar 16 08:41:23 fionex-d kernel: [   25.592801] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 16 08:41:23 fionex-d kernel: [   25.592811] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 16 08:41:23 fionex-d kernel: [   25.592839] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Mar 16 08:41:23 fionex-d kernel: [   25.592845] sd 0:0:0:0: [sda] Write Protect is off
Mar 16 08:41:23 fionex-d kernel: [   25.592847] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Mar 16 08:41:23 fionex-d kernel: [   25.592856] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 16 08:41:23 fionex-d kernel: [   25.592859]  sda: sda1 sda2 < sda5<6>usb 2-1: configuration #1 chosen from 1 choice
Mar 16 08:41:23 fionex-d kernel: [   25.624414]  sda6 sda7 >
Mar 16 08:41:23 fionex-d kernel: [   25.632986] sd 0:0:0:0: [sda] Attached SCSI disk
Mar 16 08:41:23 fionex-d kernel: [   25.635481] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar 16 08:41:23 fionex-d kernel: [   25.908937] ata5.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.02, max UDMA/66
Mar 16 08:41:23 fionex-d kernel: [   25.928971] Attempting manual resume
Mar 16 08:41:23 fionex-d kernel: [   25.928974] swsusp: Resume From Partition 8:6
Mar 16 08:41:23 fionex-d kernel: [   25.928975] PM: Checking swsusp image.
Mar 16 08:41:23 fionex-d kernel: [   25.929122] PM: Resume from disk failed.
Mar 16 08:41:23 fionex-d kernel: [   25.935603] EXT3-fs: INFO: recovery required on readonly filesystem.
Mar 16 08:41:23 fionex-d kernel: [   25.935605] EXT3-fs: write access will be enabled during recovery.
Mar 16 08:41:23 fionex-d kernel: [   26.080680] ata5.00: configured for UDMA/66
Mar 16 08:41:23 fionex-d kernel: [   26.125943] kjournald starting.  Commit interval 5 seconds
Mar 16 08:41:23 fionex-d kernel: [   26.125950] EXT3-fs: recovery complete.
Mar 16 08:41:23 fionex-d kernel: [   26.126320] EXT3-fs: mounted filesystem with ordered data mode.
Mar 16 08:41:23 fionex-d kernel: [   26.237184] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.02 PQ: 0 ANSI: 5
Mar 16 08:41:23 fionex-d kernel: [   26.237228] scsi 4:0:0:0: Attached scsi generic sg1 type 5
Mar 16 08:41:23 fionex-d kernel: [   26.237352] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Mar 16 08:41:23 fionex-d kernel: [   26.237360] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Mar 16 08:41:23 fionex-d kernel: [   26.237363] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Mar 16 08:41:23 fionex-d kernel: [   26.237380] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Mar 16 08:41:23 fionex-d kernel: [   26.237401] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000e300
Mar 16 08:41:23 fionex-d kernel: [   26.237468] usb usb6: configuration #1 chosen from 1 choice
Mar 16 08:41:23 fionex-d kernel: [   26.237485] hub 6-0:1.0: USB hub found
Mar 16 08:41:23 fionex-d kernel: [   26.237488] hub 6-0:1.0: 2 ports detected
Mar 16 08:41:23 fionex-d kernel: [   26.343572] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Mar 16 08:41:23 fionex-d kernel: [   26.343578] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Mar 16 08:41:23 fionex-d kernel: [   26.343581] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Mar 16 08:41:23 fionex-d kernel: [   26.343595] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Mar 16 08:41:23 fionex-d kernel: [   26.343614] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e400
Mar 16 08:41:23 fionex-d kernel: [   26.343682] usb usb7: configuration #1 chosen from 1 choice
Mar 16 08:41:23 fionex-d kernel: [   26.343708] hub 7-0:1.0: USB hub found
Mar 16 08:41:23 fionex-d kernel: [   26.343711] hub 7-0:1.0: 2 ports detected
Mar 16 08:41:23 fionex-d kernel: [   26.447384] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Mar 16 08:41:23 fionex-d kernel: [   26.447390] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Mar 16 08:41:23 fionex-d kernel: [   26.447393] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Mar 16 08:41:23 fionex-d kernel: [   26.447408] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Mar 16 08:41:23 fionex-d kernel: [   26.447428] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000e500
Mar 16 08:41:23 fionex-d kernel: [   26.447502] usb usb8: configuration #1 chosen from 1 choice
Mar 16 08:41:23 fionex-d kernel: [   26.447518] hub 8-0:1.0: USB hub found
Mar 16 08:41:23 fionex-d kernel: [   26.447521] hub 8-0:1.0: 2 ports detected
Mar 16 08:41:23 fionex-d kernel: [   30.212742] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 16 08:41:23 fionex-d kernel: [   30.234245] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 16 08:41:23 fionex-d kernel: [   30.330638] Linux agpgart interface v0.102 (c) Dave Jones
Mar 16 08:41:23 fionex-d kernel: [   30.530528] input: PC Speaker as /class/input/input2
Mar 16 08:41:23 fionex-d kernel: [   30.553474] parport_pc 00:09: reported by Plug and Play ACPI
Mar 16 08:41:23 fionex-d kernel: [   30.553514] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Mar 16 08:41:23 fionex-d kernel: [   30.608533] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Mar 16 08:41:23 fionex-d kernel: [   30.608536] Uniform CD-ROM driver Revision: 3.20
Mar 16 08:41:23 fionex-d kernel: [   30.608572] sr 4:0:0:0: Attached scsi CD-ROM sr0
Mar 16 08:41:23 fionex-d kernel: [   30.652197] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Mar 16 08:41:23 fionex-d kernel: [   30.665851] [fglrx] Maximum main memory to use for locked dma buffers: 1898 MBytes.
Mar 16 08:41:23 fionex-d kernel: [   30.665875] [fglrx] ASYNCIO init succeed!
Mar 16 08:41:23 fionex-d kernel: [   30.667336] [fglrx] PAT is enabled successfully!
Mar 16 08:41:23 fionex-d kernel: [   30.667348] [fglrx] module loaded - fglrx 8.45.5 [Feb  1 2008] on minor 0
Mar 16 08:41:23 fionex-d kernel: [   30.669554] usbcore: registered new interface driver hiddev
Mar 16 08:41:23 fionex-d kernel: [   30.682447] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
Mar 16 08:41:23 fionex-d kernel: [   30.682625] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.1-1
Mar 16 08:41:23 fionex-d kernel: [   30.682637] usbcore: registered new interface driver usbhid
Mar 16 08:41:23 fionex-d kernel: [   30.682639] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Mar 16 08:41:23 fionex-d kernel: [   30.834657] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
Mar 16 08:41:23 fionex-d kernel: [   30.834684] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Mar 16 08:41:23 fionex-d kernel: [   31.188582] lp0: using parport0 (interrupt-driven).
Mar 16 08:41:23 fionex-d kernel: [   31.211943] it87: Found IT8718F chip at 0x290, revision 4
Mar 16 08:41:23 fionex-d kernel: [   31.211949] it87: in3 is VCC (+5V)
Mar 16 08:41:23 fionex-d kernel: [   31.216210] coretemp coretemp.0: Using undocumented features, absolute temperature might be wrong!
Mar 16 08:41:23 fionex-d kernel: [   31.216231] coretemp coretemp.1: Using undocumented features, absolute temperature might be wrong!
Mar 16 08:41:23 fionex-d kernel: [   31.246651] Adding 2104472k swap on /dev/sda6.  Priority:-1 extents:1 across:2104472k
Mar 16 08:41:23 fionex-d kernel: [   31.665598] EXT3 FS on sda7, internal journal
Mar 16 08:41:23 fionex-d kernel: [   32.669953] input: Power Button (FF) as /class/input/input4
Mar 16 08:41:23 fionex-d kernel: [   32.669967] ACPI: Power Button (FF) [PWRF]
Mar 16 08:41:23 fionex-d kernel: [   32.669992] input: Power Button (CM) as /class/input/input5
Mar 16 08:41:23 fionex-d kernel: [   32.670002] ACPI: Power Button (CM) [PWRB]
Mar 16 08:41:23 fionex-d kernel: [   32.680442] No dock devices found.
Mar 16 08:41:24 fionex-d kernel: [   33.130756] ppdev: user-space parallel port driver
Mar 16 08:41:24 fionex-d kernel: [   33.348838] NET: Registered protocol family 10
Mar 16 08:41:24 fionex-d kernel: [   33.348896] lo: Disabled Privacy Extensions
Mar 16 08:41:24 fionex-d kernel: [   33.360966] r8169: eth1: link up
Mar 16 08:41:24 fionex-d kernel: [   33.360973] r8169: eth1: link up
Mar 16 08:41:24 fionex-d kernel: [   33.419306] audit(1205671283.983:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4875 profile="/usr/sbin/cupsd"
Mar 16 08:41:26 fionex-d kernel: [   35.184001] Failure registering capabilities with primary security module.
Mar 16 08:41:27 fionex-d kernel: [   37.029137] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Mar 16 08:41:28 fionex-d kernel: [   37.877580] [fglrx] Reserve Block - 0 offset =  0Xfffc000 length = 0X4000
Mar 16 08:41:28 fionex-d kernel: [   37.877584] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Mar 16 08:41:28 fionex-d kernel: [   37.877586] [fglrx] Reserve Block - 2 offset =  0Xff7b000 length = 0X80000
Mar 16 08:41:28 fionex-d kernel: [   38.033005] [fglrx] interrupt source 20008000 successfully enabled
Mar 16 08:41:28 fionex-d kernel: [   38.033009] [fglrx] enable ID = 0x00000006
Mar 16 08:41:28 fionex-d kernel: [   38.033014] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Mar 16 08:41:28 fionex-d kernel: [   38.033050] [fglrx] interrupt source 10000000 successfully enabled
Mar 16 08:41:28 fionex-d kernel: [   38.033052] [fglrx] enable ID = 0x00000008
Mar 16 08:41:28 fionex-d kernel: [   38.033055] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
Mar 16 08:41:28 fionex-d kernel: [   38.041787] [fglrx] interrupt source 60000001 successfully enabled
Mar 16 08:41:28 fionex-d kernel: [   38.041790] [fglrx] enable ID = 0x00000009
Mar 16 08:41:28 fionex-d kernel: [   38.041793] [fglrx] Receive enable interrupt message with irqEnableMask: 60000001
Mar 16 08:41:28 fionex-d kernel: [   38.041825] [fglrx] interrupt source 00000040 successfully enabled
Mar 16 08:41:28 fionex-d kernel: [   38.041827] [fglrx] enable ID = 0x0000000A
Mar 16 08:41:28 fionex-d kernel: [   38.041829] [fglrx] Receive enable interrupt message with irqEnableMask: 00000040
Mar 16 08:41:28 fionex-d kernel: [   38.042507] [fglrx] interrupt source ff00002c successfully enabled
Mar 16 08:41:28 fionex-d kernel: [   38.042509] [fglrx] enable ID = 0x0000000B
Mar 16 08:41:28 fionex-d kernel: [   38.042512] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002c
Mar 16 08:41:28 fionex-d kernel: [   38.042542] [fglrx] interrupt source ff00002d successfully enabled
Mar 16 08:41:28 fionex-d kernel: [   38.042543] [fglrx] enable ID = 0x0000000C
Mar 16 08:41:28 fionex-d kernel: [   38.042546] [fglrx] Receive enable interrupt message with irqEnableMask: ff00002d
Mar 16 08:41:28 fionex-d kernel: [   38.042573] [fglrx] interrupt source 20000400 successfully enabled
Mar 16 08:41:28 fionex-d kernel: [   38.042575] [fglrx] enable ID = 0x0000000D
Mar 16 08:41:28 fionex-d kernel: [   38.042577] [fglrx] Receive enable interrupt message with irqEnableMask: 20000400
Mar 16 08:41:30 fionex-d kernel: [   39.311084] NET: Registered protocol family 17
Mar 16 08:41:41 fionex-d kernel: [   50.722784] eth1: no IPv6 routers present

```

---

### Post by FIONEX on 2008-03-16
I want to add that my system runs a little too cold.  Less than 22 degrees celcius when I'm using it, and about 16 when it's idle.  My basement is relatively cold and the PC is well ventilated.  Other than that, I'm running the ATI drivers from AMD.com

---


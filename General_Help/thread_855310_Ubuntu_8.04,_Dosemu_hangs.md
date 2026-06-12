---
title: "Ubuntu 8.04, Dosemu hangs"
date: 2008-07-10
forum: General Help
---

### Post by wrgt on 2008-07-10
My apologies if I posted in the wrong section. 

I am using Ubuntu 8.04 on a Pentium III 800mhz with 512mb ram. This computer is connected to a small office network where two more computers are connected.

The program that this computer always use is Dosemu to emulate a clipper-based program database. It is able to access the files from the server for a certain time until it freezes. The system also freezes. The hard drive LED lights up constantly. I couldn't use ctrl+alt+del, ctrl+alt+f1 to f7 or ctrl+alt+backspace. It goes back to normal after resetting, then Dosemu would freeze again eventually.

CPU temperature after resetting is at 43 degrees Celsius. Memory has already been tested and passed by Memtest86 program. I also changed the hard drive just in case the first was failing.

But the computer would not freeze when I use Dosemu and the clipper-based program without connecting to the network. The network might be the culprit but I have another computer with a similar Fedora 8 setup that works fine.

Please help. I'm new to Linux and I don't know what's wrong. Thanks.

---

### Post by danwood76 on 2008-07-10
It could be a dying network card in the PC.

I had all sorts of issues with a PC I was trying to install ubuntu on a while ago and it turned out that it had a faulty net card, it would work fine for 30 minutes or so but then it would crash when the network card warmed up.
Luckily I had a spare motherboard lying around that fixed the issue.

If you have a spare board or net card lying around I would try that first.

---

### Post by wrgt on 2008-07-10
unfortunately i don't have a spare network card. maybe i could buy a new one since they're not that expensive. 

how come when i downloaded ubuntu updates for a few hours it didn't freeze?

---

### Post by danwood76 on 2008-07-11
Downloading updates you are only going down stream, it could be that the upstream is causing the issue.
Of course it may not be the net card at all.

After it does a hard freeze have a look in the syslogs to see if there were any kernel errors before it crashed.

---

### Post by wrgt on 2008-07-11
where can i find the syslogs?

---

### Post by wrgt on 2008-07-14
i found the text file kernel.log. can i email it to you?

---

### Post by wrgt on 2008-07-15
```
Jul 10 16:44:58 linuxws2 kernel: Inspecting /boot/System.map-2.6.24-19-generic 
Jul 10 16:44:58 linuxws2 kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic. 
Jul 10 16:44:58 linuxws2 kernel: Symbols match kernel version 2.6.24. 
Jul 10 16:44:58 linuxws2 kernel: Loaded 15751 symbols from 82 modules. 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Initializing cgroup subsys cpuset 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Initializing cgroup subsys cpu 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] BIOS-provided physical RAM map: 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fffc000 (usable) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]  BIOS-e820: 000000001fffc000 - 000000001ffff000 (ACPI data) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] 0MB HIGHMEM available. 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] 511MB LOWMEM available. 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Entering add_active_range(0, 0, 131068) 0 entries of 256 used 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Zone PFN ranges: 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]   DMA             0 ->     4096 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]   Normal       4096 ->   131068 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]   HighMem    131068 ->   131068 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Movable zone start PFN for each node 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] early_node_map[1] active PFN ranges 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]     0:        0 ->   131068 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] On node 0 totalpages: 131068 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]   DMA zone: 32 pages used for memmap 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]   DMA zone: 0 pages reserved 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]   Normal zone: 991 pages used for memmap 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]   Normal zone: 125981 pages, LIFO batch:31 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]   HighMem zone: 0 pages used for memmap 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000]   Movable zone: 0 pages used for memmap 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] DMI 2.3 present. 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6900 checksum 0 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] ACPI: RSDP 000F6900, 0014 (r0 ASUS  ) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] ACPI: RSDT 1FFFC000, 002C (r1 ASUS   CUV4X_C  30303031 MSFT 31313031) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] ACPI: FACP 1FFFC080, 0074 (r1 ASUS   CUV4X_C  30303031 MSFT 31313031) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] ACPI: DSDT 1FFFC100, 2804 (r1   ASUS CUV4X_C      1000 MSFT  100000B) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] ACPI: FACS 1FFFF000, 0040 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] ACPI: BOOT 1FFFC040, 0028 (r1 ASUS   CUV4X_C  30303031 MSFT 31313031) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xe408 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130045 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Kernel command line: root=UUID=c9b12533-f599-4f1e-979f-4462ac6562fa ro quiet splash 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic" 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] mapped APIC to ffffb000 (0140d000) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Enabling fast FPU save and restore... done. 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done. 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Initializing CPU#0 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes) 
Jul 10 16:44:59 linuxws2 kernel: [    0.000000] Detected 803.680 MHz processor. 
Jul 10 16:44:59 linuxws2 kernel: [   25.407819] Console: colour VGA+ 80x25 
Jul 10 16:44:59 linuxws2 kernel: [   25.407831] console [tty0] enabled 
Jul 10 16:44:59 linuxws2 kernel: [   25.408410] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes) 
Jul 10 16:44:59 linuxws2 kernel: [   25.409512] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes) 
Jul 10 16:44:59 linuxws2 kernel: [   25.460835] Memory: 507780k/524272k available (2177k kernel code, 15960k reserved, 1006k data, 368k init, 0k highmem) 
Jul 10 16:44:59 linuxws2 kernel: [   25.460857] virtual kernel memory layout: 
Jul 10 16:44:59 linuxws2 kernel: [   25.460860]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB) 
Jul 10 16:44:59 linuxws2 kernel: [   25.460863]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB) 
Jul 10 16:44:59 linuxws2 kernel: [   25.460867]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB) 
Jul 10 16:44:59 linuxws2 kernel: [   25.460870]     lowmem  : 0xc0000000 - 0xdfffc000   ( 511 MB) 
Jul 10 16:44:59 linuxws2 kernel: [   25.460874]       .init : 0xc0421000 - 0xc047d000   ( 368 kB) 
Jul 10 16:44:59 linuxws2 kernel: [   25.460877]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB) 
Jul 10 16:44:59 linuxws2 kernel: [   25.460880]       .text : 0xc0100000 - 0xc0320434   (2177 kB) 
Jul 10 16:44:59 linuxws2 kernel: [   25.460889] Checking if this processor honours the WP bit even in supervisor mode... Ok. 
Jul 10 16:44:59 linuxws2 kernel: [   25.460969] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1 
Jul 10 16:44:59 linuxws2 kernel: [   25.540995] Calibrating delay using timer specific routine.. 1609.50 BogoMIPS (lpj=3219018) 
Jul 10 16:44:59 linuxws2 kernel: [   25.541053] Security Framework initialized 
Jul 10 16:44:59 linuxws2 kernel: [   25.541070] SELinux:  Disabled at boot. 
Jul 10 16:44:59 linuxws2 kernel: [   25.541101] AppArmor: AppArmor initialized 
Jul 10 16:44:59 linuxws2 kernel: [   25.541111] Failure registering capabilities with primary security module. 
Jul 10 16:44:59 linuxws2 kernel: [   25.541131] Mount-cache hash table entries: 512 
Jul 10 16:44:59 linuxws2 kernel: [   25.541385] Initializing cgroup subsys ns 
Jul 10 16:44:59 linuxws2 kernel: [   25.541395] Initializing cgroup subsys cpuacct 
Jul 10 16:44:59 linuxws2 kernel: [   25.541413] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000 
Jul 10 16:44:59 linuxws2 kernel: [   25.541439] CPU: L1 I cache: 16K, L1 D cache: 16K 
Jul 10 16:44:59 linuxws2 kernel: [   25.541446] CPU: L2 cache: 256K 
Jul 10 16:44:59 linuxws2 kernel: [   25.541453] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000 00000000 
Jul 10 16:44:59 linuxws2 kernel: [   25.541475] Compat vDSO mapped to ffffe000. 
Jul 10 16:44:59 linuxws2 kernel: [   25.541506] Checking 'hlt' instruction... OK. 
Jul 10 16:44:59 linuxws2 kernel: [   25.557570] SMP alternatives: switching to UP code 
Jul 10 16:44:59 linuxws2 kernel: [   25.560748] Freeing SMP alternatives: 11k freed 
Jul 10 16:44:59 linuxws2 kernel: [   25.561101] Early unpacking initramfs... done 
Jul 10 16:44:59 linuxws2 kernel: [   26.419815] ACPI: Core revision 20070126 
Jul 10 16:44:59 linuxws2 kernel: [   26.420022] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found. 
Jul 10 16:44:59 linuxws2 kernel: [   26.423078] ACPI: setting ELCR to 0200 (from 0c00) 
Jul 10 16:44:59 linuxws2 kernel: [   26.423365] CPU0: Intel Pentium III (Coppermine) stepping 06 
Jul 10 16:44:59 linuxws2 kernel: [   26.423380] SMP motherboard not detected. 
Jul 10 16:44:59 linuxws2 kernel: [   26.423387] Local APIC not detected. Using dummy APIC emulation. 
Jul 10 16:44:59 linuxws2 kernel: [   26.423511] Brought up 1 CPUs 
Jul 10 16:44:59 linuxws2 kernel: [   26.423556] CPU0 attaching sched-domain: 
Jul 10 16:44:59 linuxws2 kernel: [   26.423564]  domain 0: span 01 
Jul 10 16:44:59 linuxws2 kernel: [   26.423568]   groups: 01 
Jul 10 16:44:59 linuxws2 kernel: [   26.424072] net_namespace: 64 bytes 
Jul 10 16:44:59 linuxws2 kernel: [   26.424095] Booting paravirtualized kernel on bare hardware 
Jul 10 16:44:59 linuxws2 kernel: [   26.425575] Time:  8:44:15  Date: 07/10/08 
Jul 10 16:44:59 linuxws2 kernel: [   26.425653] NET: Registered protocol family 16 
Jul 10 16:44:59 linuxws2 kernel: [   26.426221] EISA bus registered 
Jul 10 16:44:59 linuxws2 kernel: [   26.426254] ACPI: bus type pci registered 
Jul 10 16:44:59 linuxws2 kernel: [   26.427554] PCI: PCI BIOS revision 2.10 entry at 0xf0d10, last bus=1 
Jul 10 16:44:59 linuxws2 kernel: [   26.427562] PCI: Using configuration type 1 
Jul 10 16:44:59 linuxws2 kernel: [   26.427596] Setting up standard PCI resources 
Jul 10 16:44:59 linuxws2 kernel: [   26.436319] ACPI: EC: Look up EC in DSDT 
Jul 10 16:44:59 linuxws2 kernel: [   26.441406] ACPI: Interpreter enabled 
Jul 10 16:44:59 linuxws2 kernel: [   26.441416] ACPI: (supports S0 S1 S4 S5) 
Jul 10 16:44:59 linuxws2 kernel: [   26.441448] ACPI: Using PIC for interrupt routing 
Jul 10 16:44:59 linuxws2 kernel: [   26.457786] ACPI: PCI Root Bridge [PCI0] (0000:00) 
Jul 10 16:44:59 linuxws2 kernel: [   26.458221] PCI quirk: region e400-e4ff claimed by vt82c586 ACPI 
Jul 10 16:44:59 linuxws2 kernel: [   26.458230] PCI quirk: region e800-e80f claimed by vt82c686 SMB 
Jul 10 16:44:59 linuxws2 kernel: [   26.458544] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
Jul 10 16:44:59 linuxws2 kernel: [   26.458990] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT] 
Jul 10 16:44:59 linuxws2 kernel: [   26.503517] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15) 
Jul 10 16:44:59 linuxws2 kernel: [   26.503704] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
Jul 10 16:44:59 linuxws2 kernel: [   26.503887] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15) 
Jul 10 16:44:59 linuxws2 kernel: [   26.504069] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled. 
Jul 10 16:44:59 linuxws2 kernel: [   26.504355] Linux Plug and Play Support v0.97 (c) Adam Belay 
Jul 10 16:44:59 linuxws2 kernel: [   26.504440] pnp: PnP ACPI init 
Jul 10 16:44:59 linuxws2 kernel: [   26.504463] ACPI: bus type pnp registered 
Jul 10 16:44:59 linuxws2 kernel: [   26.510815] pnp: PnP ACPI: found 14 devices 
Jul 10 16:44:59 linuxws2 kernel: [   26.510824] ACPI: ACPI bus type pnp unregistered 
Jul 10 16:44:59 linuxws2 kernel: [   26.510836] PnPBIOS: Disabled by ACPI PNP 
Jul 10 16:44:59 linuxws2 kernel: [   26.511484] PCI: Using ACPI for IRQ routing 
Jul 10 16:44:59 linuxws2 kernel: [   26.511493] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
Jul 10 16:44:59 linuxws2 kernel: [   26.524908] NET: Registered protocol family 8 
Jul 10 16:44:59 linuxws2 kernel: [   26.524915] NET: Registered protocol family 20 
Jul 10 16:44:59 linuxws2 kernel: [   26.525107] AppArmor: AppArmor Filesystem Enabled 
Jul 10 16:44:59 linuxws2 kernel: [   26.528855] Time: tsc clocksource has been installed. 
Jul 10 16:44:59 linuxws2 kernel: [   26.536967] system 00:00: iomem range 0x0-0x9ffff could not be reserved 
Jul 10 16:44:59 linuxws2 kernel: [   26.536976] system 00:00: iomem range 0xf0000-0xfffff could not be reserved 
Jul 10 16:44:59 linuxws2 kernel: [   26.536985] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved 
Jul 10 16:44:59 linuxws2 kernel: [   26.536993] system 00:00: iomem range 0xfffe0000-0xffffffff could not be reserved 
Jul 10 16:44:59 linuxws2 kernel: [   26.537014] system 00:02: ioport range 0x3f0-0x3f1 has been reserved 
Jul 10 16:44:59 linuxws2 kernel: [   26.537022] system 00:02: ioport range 0x4d0-0x4d1 has been reserved 
Jul 10 16:44:59 linuxws2 kernel: [   26.537041] system 00:03: ioport range 0xe400-0xe47f has been reserved 
Jul 10 16:44:59 linuxws2 kernel: [   26.537049] system 00:03: ioport range 0xe800-0xe80f has been reserved 
Jul 10 16:44:59 linuxws2 kernel: [   26.568183] PCI: Bridge: 0000:00:01.0 
Jul 10 16:44:59 linuxws2 kernel: [   26.568190]   IO window: disabled. 
Jul 10 16:44:59 linuxws2 kernel: [   26.568199]   MEM window: ee000000-ef5fffff 
Jul 10 16:44:59 linuxws2 kernel: [   26.568205]   PREFETCH window: ef700000-fbffffff 
Jul 10 16:44:59 linuxws2 kernel: [   26.568241] PCI: Setting latency timer of device 0000:00:01.0 to 64 
Jul 10 16:44:59 linuxws2 kernel: [   26.568274] NET: Registered protocol family 2 
Jul 10 16:44:59 linuxws2 kernel: [   26.605045] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
Jul 10 16:44:59 linuxws2 kernel: [   26.605647] TCP established hash table entries: 16384 (order: 5, 131072 bytes) 
Jul 10 16:44:59 linuxws2 kernel: [   26.606020] TCP bind hash table entries: 16384 (order: 5, 131072 bytes) 
Jul 10 16:44:59 linuxws2 kernel: [   26.606546] TCP: Hash tables configured (established 16384 bind 16384) 
Jul 10 16:44:59 linuxws2 kernel: [   26.606555] TCP reno registered 
Jul 10 16:44:59 linuxws2 kernel: [   26.617279] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0 
Jul 10 16:44:59 linuxws2 kernel: [   27.350985]  it is 
Jul 10 16:44:59 linuxws2 kernel: [   28.232906] Freeing initrd memory: 7319k freed 
Jul 10 16:44:59 linuxws2 kernel: [   28.233432] Simple Boot Flag at 0x3a set to 0x1 
Jul 10 16:44:59 linuxws2 kernel: [   28.234362] audit: initializing netlink socket (disabled) 
Jul 10 16:44:59 linuxws2 kernel: [   28.234397] audit(1215679456.776:1): initialized 
Jul 10 16:44:59 linuxws2 kernel: [   28.240366] VFS: Disk quotas dquot_6.5.1 
Jul 10 16:44:59 linuxws2 kernel: [   28.240676] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
Jul 10 16:44:59 linuxws2 kernel: [   28.241099] io scheduler noop registered 
Jul 10 16:44:59 linuxws2 kernel: [   28.241107] io scheduler anticipatory registered 
Jul 10 16:44:59 linuxws2 kernel: [   28.241112] io scheduler deadline registered 
Jul 10 16:44:59 linuxws2 kernel: [   28.241155] io scheduler cfq registered (default) 
Jul 10 16:44:59 linuxws2 kernel: [   28.241186] PCI: VIA PCI bridge detected. Disabling DAC. 
Jul 10 16:44:59 linuxws2 kernel: [   28.241194] PCI: Disabling Via external APIC routing 
Jul 10 16:44:59 linuxws2 kernel: [   28.241249] Boot video device is 0000:01:00.0 
Jul 10 16:44:59 linuxws2 kernel: [   28.241975] isapnp: Scanning for PnP cards... 
Jul 10 16:44:59 linuxws2 kernel: [   28.596386] isapnp: No Plug & Play device found 
Jul 10 16:44:59 linuxws2 kernel: [   28.686617] Real Time Clock Driver v1.12ac 
Jul 10 16:44:59 linuxws2 kernel: [   28.686844] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
Jul 10 16:44:59 linuxws2 kernel: [   28.687098] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
Jul 10 16:44:59 linuxws2 kernel: [   28.687473] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
Jul 10 16:44:59 linuxws2 kernel: [   28.689006] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A 
Jul 10 16:44:59 linuxws2 kernel: [   28.689643] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A 
Jul 10 16:44:59 linuxws2 kernel: [   28.691682] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
Jul 10 16:44:59 linuxws2 kernel: [   28.691864] input: Macintosh mouse button emulation as /devices/virtual/input/input0 
Jul 10 16:44:59 linuxws2 kernel: [   28.692146] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
Jul 10 16:44:59 linuxws2 kernel: [   28.692710] serio: i8042 KBD port at 0x60,0x64 irq 1 
Jul 10 16:44:59 linuxws2 kernel: [   28.692723] serio: i8042 AUX port at 0x60,0x64 irq 12 
Jul 10 16:44:59 linuxws2 kernel: [   28.696890] mice: PS/2 mouse device common for all mice 
Jul 10 16:44:59 linuxws2 kernel: [   28.697200] EISA: Probing bus 0 at eisa.0 
Jul 10 16:44:59 linuxws2 kernel: [   28.697261] EISA: Detected 0 cards. 
Jul 10 16:44:59 linuxws2 kernel: [   28.697269] cpuidle: using governor ladder 
Jul 10 16:44:59 linuxws2 kernel: [   28.697274] cpuidle: using governor menu 
Jul 10 16:44:59 linuxws2 kernel: [   28.697687] NET: Registered protocol family 1 
Jul 10 16:44:59 linuxws2 kernel: [   28.697766] Using IPI No-Shortcut mode 
Jul 10 16:44:59 linuxws2 kernel: [   28.697837] registered taskstats version 1 
Jul 10 16:44:59 linuxws2 kernel: [   28.698038]   Magic number: 0:288:725 
Jul 10 16:44:59 linuxws2 kernel: [   28.698239]   hash matches device 0000:01:00.0 
Jul 10 16:44:59 linuxws2 kernel: [   28.698263] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
Jul 10 16:44:59 linuxws2 kernel: [   28.698269] EDD information not available. 
Jul 10 16:44:59 linuxws2 kernel: [   28.698934] Freeing unused kernel memory: 368k freed 
Jul 10 16:44:59 linuxws2 kernel: [   28.717032] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1 
Jul 10 16:44:59 linuxws2 kernel: [   30.293627] fuse init (API version 7.9) 
Jul 10 16:44:59 linuxws2 kernel: [   30.356967] ACPI: CPU0 (power states: C1[C1] C2[C2]) 
Jul 10 16:44:59 linuxws2 kernel: [   30.356983] ACPI: Processor [CPU0] (supports 16 throttling states) 
Jul 10 16:44:59 linuxws2 kernel: [   31.284336] SCSI subsystem initialized 
Jul 10 16:44:59 linuxws2 kernel: [   31.368245] usbcore: registered new interface driver usbfs 
Jul 10 16:44:59 linuxws2 kernel: [   31.368307] usbcore: registered new interface driver hub 
Jul 10 16:44:59 linuxws2 kernel: [   31.400138] usbcore: registered new device driver usb 
Jul 10 16:44:59 linuxws2 kernel: [   31.584768] USB Universal Host Controller Interface driver v3.0 
Jul 10 16:44:59 linuxws2 kernel: [   31.585663] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10 
Jul 10 16:44:59 linuxws2 kernel: [   31.585672] PCI: setting IRQ 10 as level-triggered 
Jul 10 16:44:59 linuxws2 kernel: [   31.585681] ACPI: PCI Interrupt 0000:00:04.2[D] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10 
Jul 10 16:44:59 linuxws2 kernel: [   31.585705] uhci_hcd 0000:00:04.2: UHCI Host Controller 
Jul 10 16:44:59 linuxws2 kernel: [   31.586202] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1 
Jul 10 16:44:59 linuxws2 kernel: [   31.586244] uhci_hcd 0000:00:04.2: irq 10, io base 0x0000d400 
Jul 10 16:44:59 linuxws2 kernel: [   31.586590] usb usb1: configuration #1 chosen from 1 choice 
Jul 10 16:44:59 linuxws2 kernel: [   31.586659] hub 1-0:1.0: USB hub found 
Jul 10 16:44:59 linuxws2 kernel: [   31.586676] hub 1-0:1.0: 2 ports detected 
Jul 10 16:44:59 linuxws2 kernel: [   31.636050] libata version 3.00 loaded. 
Jul 10 16:44:59 linuxws2 kernel: [   31.688292] ACPI: PCI Interrupt 0000:00:04.3[D] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10 
Jul 10 16:44:59 linuxws2 kernel: [   31.688321] uhci_hcd 0000:00:04.3: UHCI Host Controller 
Jul 10 16:44:59 linuxws2 kernel: [   31.688378] uhci_hcd 0000:00:04.3: new USB bus registered, assigned bus number 2 
Jul 10 16:44:59 linuxws2 kernel: [   31.688418] uhci_hcd 0000:00:04.3: irq 10, io base 0x0000d000 
Jul 10 16:44:59 linuxws2 kernel: [   31.688704] usb usb2: configuration #1 chosen from 1 choice 
Jul 10 16:44:59 linuxws2 kernel: [   31.688765] hub 2-0:1.0: USB hub found 
Jul 10 16:44:59 linuxws2 kernel: [   31.688781] hub 2-0:1.0: 2 ports detected 
Jul 10 16:44:59 linuxws2 kernel: [   31.793353] pata_via 0000:00:04.1: version 0.3.3 
Jul 10 16:44:59 linuxws2 kernel: [   31.812000] scsi0 : pata_via 
Jul 10 16:44:59 linuxws2 kernel: [   31.843994] scsi1 : pata_via 
Jul 10 16:44:59 linuxws2 kernel: [   31.844409] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (000000006) is beyond end of object [20070126] 
Jul 10 16:44:59 linuxws2 kernel: [   31.844431] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0._GTM] (Node ddcc3a08), AE_AML_PACKAGE_LIMIT 
Jul 10 16:44:59 linuxws2 kernel: [   31.844501] ata1: ACPI get timing mode failed (AE 0x300d) 
Jul 10 16:44:59 linuxws2 kernel: [   31.844739] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (00000000A) is beyond end of object [20070126] 
Jul 10 16:44:59 linuxws2 kernel: [   31.844758] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.CHN1._GTM] (Node ddcc3af8), AE_AML_PACKAGE_LIMIT 
Jul 10 16:44:59 linuxws2 kernel: [   31.844804] ata2: ACPI get timing mode failed (AE 0x300d) 
Jul 10 16:44:59 linuxws2 kernel: [   31.844818] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xd800 irq 14 
Jul 10 16:44:59 linuxws2 kernel: [   31.844826] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xd808 irq 15 
Jul 10 16:44:59 linuxws2 kernel: [   32.008524] ata1.00: native sectors (39102335) is smaller than sectors (39102336) 
Jul 10 16:44:59 linuxws2 kernel: [   32.008541] ata1.00: ATA-4: ST320413A, 3.35, max UDMA/100 
Jul 10 16:44:59 linuxws2 kernel: [   32.008548] ata1.00: 39102336 sectors, multi 16: LBA 
Jul 10 16:44:59 linuxws2 kernel: [   32.016649] ata1.00: configured for UDMA/66 
Jul 10 16:44:59 linuxws2 kernel: [   32.052887] 8139too Fast Ethernet driver 0.9.28 
Jul 10 16:44:59 linuxws2 kernel: [   32.352070] Floppy drive(s): fd0 is 1.44M 
Jul 10 16:44:59 linuxws2 kernel: [   32.371832] FDC 0 is a post-1991 82077 
Jul 10 16:44:59 linuxws2 kernel: [   32.496495] ata2.01: ATAPI: LTN526D, 9S03, max UDMA/33 
Jul 10 16:44:59 linuxws2 kernel: [   32.660296] ata2.01: configured for UDMA/33 
Jul 10 16:44:59 linuxws2 kernel: [   32.660610] scsi 0:0:0:0: Direct-Access     ATA      ST320413A        3.35 PQ: 0 ANSI: 5 
Jul 10 16:44:59 linuxws2 kernel: [   32.661153] scsi 1:0:1:0: CD-ROM            LITEON   CD-ROM LTN526D   9S03 PQ: 0 ANSI: 5 
Jul 10 16:44:59 linuxws2 kernel: [   32.669955] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10 
Jul 10 16:44:59 linuxws2 kernel: [   32.670795] eth0: RealTek RTL8139 at 0xb400, 00:50:bf:70:f2:c4, IRQ 10 
Jul 10 16:44:59 linuxws2 kernel: [   32.670802] eth0:  Identified 8139 chip type 'RTL-8139C' 
Jul 10 16:44:59 linuxws2 kernel: [   32.693263] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004) 
Jul 10 16:44:59 linuxws2 kernel: [   33.852501] Driver 'sd' needs updating - please use bus_type methods 
Jul 10 16:44:59 linuxws2 kernel: [   33.857744] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB) 
Jul 10 16:44:59 linuxws2 kernel: [   33.857785] sd 0:0:0:0: [sda] Write Protect is off 
Jul 10 16:44:59 linuxws2 kernel: [   33.857793] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
Jul 10 16:44:59 linuxws2 kernel: [   33.857847] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
Jul 10 16:44:59 linuxws2 kernel: [   33.857978] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB) 
Jul 10 16:44:59 linuxws2 kernel: [   33.858009] sd 0:0:0:0: [sda] Write Protect is off 
Jul 10 16:44:59 linuxws2 kernel: [   33.858016] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
Jul 10 16:44:59 linuxws2 kernel: [   33.858068] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
Jul 10 16:44:59 linuxws2 kernel: [   33.858080]  sda:<4>Driver 'sr' needs updating - please use bus_type methods 
Jul 10 16:44:59 linuxws2 kernel: [   33.888796]  sda1 sda2 < sda5 > 
Jul 10 16:44:59 linuxws2 kernel: [   33.921330] sd 0:0:0:0: [sda] Attached SCSI disk 
Jul 10 16:44:59 linuxws2 kernel: [   33.941506] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray 
Jul 10 16:44:59 linuxws2 kernel: [   33.941519] Uniform CD-ROM driver Revision: 3.20 
Jul 10 16:44:59 linuxws2 kernel: [   33.941657] sr 1:0:1:0: Attached scsi CD-ROM sr0 
Jul 10 16:44:59 linuxws2 kernel: [   33.952969] sd 0:0:0:0: Attached scsi generic sg0 type 0 
Jul 10 16:44:59 linuxws2 kernel: [   33.953023] sr 1:0:1:0: Attached scsi generic sg1 type 5 
Jul 10 16:44:59 linuxws2 kernel: [   34.910657] Attempting manual resume 
Jul 10 16:44:59 linuxws2 kernel: [   34.910667] swsusp: Resume From Partition 8:5 
Jul 10 16:44:59 linuxws2 kernel: [   34.910672] PM: Checking swsusp image. 
Jul 10 16:44:59 linuxws2 kernel: [   34.922205] PM: Resume from disk failed. 
Jul 10 16:44:59 linuxws2 kernel: [   35.021405] kjournald starting.  Commit interval 5 seconds 
Jul 10 16:44:59 linuxws2 kernel: [   35.021437] EXT3-fs: mounted filesystem with ordered data mode. 
Jul 10 16:44:59 linuxws2 kernel: [   52.756702] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
Jul 10 16:44:59 linuxws2 kernel: [   52.839819] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
Jul 10 16:44:59 linuxws2 kernel: [   52.916689] Linux agpgart interface v0.102 
Jul 10 16:44:59 linuxws2 kernel: [   53.074608] parport_pc: VIA 686A/8231 detected 
Jul 10 16:44:59 linuxws2 kernel: [   53.074618] parport_pc: probing current configuration 
Jul 10 16:44:59 linuxws2 kernel: [   53.074642] parport_pc: Current parallel port base: 0x378 
Jul 10 16:44:59 linuxws2 kernel: [   53.074743] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP] 
Jul 10 16:44:59 linuxws2 kernel: [   53.158859] parport_pc: VIA parallel port: io=0x378, irq=7 
Jul 10 16:44:59 linuxws2 kernel: [   53.201065] agpgart: Detected VIA Apollo Pro 133 chipset 
Jul 10 16:44:59 linuxws2 kernel: [   53.203773] agpgart: AGP aperture is 32M @ 0xfc000000 
Jul 10 16:44:59 linuxws2 kernel: [   53.288576] via686a 0000:00:04.4: base address not set - upgrade BIOS or use force_addr=0xaddr 
Jul 10 16:44:59 linuxws2 kernel: [   53.792958] input: PC Speaker as /devices/platform/pcspkr/input/input2 
Jul 10 16:44:59 linuxws2 kernel: [   55.208516] input: Power Button (FF) as /devices/virtual/input/input3 
Jul 10 16:44:59 linuxws2 kernel: [   55.220131] ACPI: Power Button (FF) [PWRF] 
Jul 10 16:44:59 linuxws2 kernel: [   55.220431] input: Power Button (CM) as /devices/virtual/input/input4 
Jul 10 16:44:59 linuxws2 kernel: [   55.232106] ACPI: Power Button (CM) [PWRB] 
Jul 10 16:44:59 linuxws2 kernel: [   55.296278] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1 
Jul 10 16:44:59 linuxws2 kernel: [   58.263034] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input5 
Jul 10 16:44:59 linuxws2 kernel: [   60.431701] NET: Registered protocol family 10 
Jul 10 16:44:59 linuxws2 kernel: [   60.432361] lo: Disabled Privacy Extensions 
Jul 10 16:44:59 linuxws2 kernel: [   60.633211] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11 
Jul 10 16:44:59 linuxws2 kernel: [   60.633223] PCI: setting IRQ 11 as level-triggered 
Jul 10 16:44:59 linuxws2 kernel: [   60.633232] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11 
Jul 10 16:44:59 linuxws2 kernel: [   64.346632] lp0: using parport0 (interrupt-driven). 
Jul 10 16:44:59 linuxws2 kernel: [   64.482787] Adding 859436k swap on /dev/sda5.  Priority:-1 extents:1 across:859436k 
Jul 10 16:44:59 linuxws2 kernel: [   65.132842] EXT3 FS on sda1, internal journal 
Jul 10 16:44:59 linuxws2 kernel: [   67.216709] ip_tables: (C) 2000-2006 Netfilter Core Team 
Jul 10 16:44:59 linuxws2 kernel: [   68.454900] No dock devices found. 
Jul 10 16:44:59 linuxws2 kernel: [   70.713544] eth0: no IPv6 routers present 
Jul 10 16:44:59 linuxws2 kernel: [   70.988123] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac) 
Jul 10 16:44:59 linuxws2 kernel: [   70.988137] apm: overridden by ACPI. 

```

here's a portion of my kernel log file. the crash occurred on July 10, at around 17:30:00. 

my computer specs are:
Pentium III 800mhz
Asus CUV4X-C motherboard
1 IDE 20gb hard drive
1 IDE CD-Rom
1 PCI lan card
1 PCI sound card (don't need this)
1 AGP GeForce 400MX 64mb
no internet connection in the office. I bring the computer home to download updates and install programs.

---

### Post by wrgt on 2008-08-30
danwood76, I bought a new lan card as you suggested, observed the system for one month, and it seems to be stable (knock wood). Thank you for your help.

---


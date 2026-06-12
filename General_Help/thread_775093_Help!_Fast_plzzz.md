---
title: "Help! Fast plzzz"
date: 2008-04-29
forum: General Help
---

### Post by Lostatsea3 on 2008-04-29
So I just installed Ubuntu from a live cd.... and I've got some big problems. 

1) No wireless! My wireless switch won't turn on... its just stays orange. I can't get it to work in Ubuntu settings

2) Vistaa! I can't boot vista anymore? Someone please tell me how because its not working. I hit escape when ubuntu was booting to go to the list of boot choices and vista isn't there!!! what happpened? I desperately still need vista on this comp!

Thanks!

---

### Post by GavinZac on 2008-04-29
> **Lostatsea3 said:**
> So I just installed Ubuntu from a live cd.... and I've got some big problems. 

1) No wireless! My wireless switch won't turn on... its just stays orange. I can't get it to work in Ubuntu settings
You need to tell us more about it. What kind of wireless it is, etc.

> 2) Vistaa! I can't boot vista anymore? Someone please tell me how because its not working. I hit escape when ubuntu was booting to go to the list of boot choices and vista isn't there!!! what happpened? I desperately still need vista on this comp!
Well it sounds like you removed vista completely. Please use gparted to find out what partitions you have on your computer.

---

### Post by Lostatsea3 on 2008-04-29
Wireless = Netgear router. Metrocast. HP computer. Theres a little slide to turn wireless on and off but it always stays off...


RE: Gparted - I made a new partition before installing... and I did the automatic choice to install. Why would it have installed over vista??? Oh man... any way to get vista back if I did? What about all the files that were on the computer?? are they gone??

---

### Post by natrixgli on 2008-04-29
Here's what you need to do:

1) See if drivers for your wireless can be installed via the hardware drivers utility in System > Administration. You will need to connect to your router with a cable to do this.

2) If this fails to work, find out what kind of wireless card is IN your laptop by running the command "dmesg" in a terminal. Post the result here.

3) As for Vista, or the lack thereof, you need to find out if the partition for Vista exists. In a terminal, run "parted" and type "print" - this will display a list of partitions on the drive. Post the results.

4) If we find Vista's partition is unharmed, you can add it as an option to the boot menu. 


-n8

---

### Post by GavinZac on 2008-04-29
There is a program called "hardinfo". Can you install this and find out the exact details of your wireless card? There are so many different kinds, we will really need to know exactly which it is to help you perfectly.

It will only have installed over Vista if you've told it to; otherwise it would have given a link for "Vista/Longhorn" in your Grub menu. If you check for certain what partitions you have left, you can tell if its gone or not.

The files you had in Vista might be gone. You can get them back, but it is very difficult. It would be using the same techniques the police use to find deleted evidence on criminal's computers.

---

### Post by Lostatsea3 on 2008-04-29
1) Only thing coming up in hardware utilities is my nvidia. 

2)How do you start terminal? I'm really new to ubuntu. 

3)" "

4) How?


Gavin - Sounds like what he told me to do... but your method needs a program. How would you add vista to the GRUB menu

---

### Post by Lostatsea3 on 2008-04-29
Found Terminal.... retrying

---

### Post by Lostatsea3 on 2008-04-29
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503682
[    0.000000] Kernel command line: root=UUID=eadf307d-e38f-4625-8e42-ff3ef17b7313 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1808.260 MHz processor.
[   51.148636] spurious 8259A interrupt: IRQ7.
[   51.151782] Console: colour VGA+ 80x25
[   51.151786] console [tty0] enabled
[   51.152117] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   51.152535] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   51.241494] Memory: 2000752k/2030592k available (2157k kernel code, 28532k reserved, 998k data, 364k init, 1113088k highmem)
[   51.241503] virtual kernel memory layout:
[   51.241504]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   51.241505]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   51.241507]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   51.241508]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   51.241509]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   51.241510]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   51.241511]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   51.241514] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   51.241552] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   51.241702] hpet clockevent registered
[   51.321662] Calibrating delay using timer specific routine.. 3619.72 BogoMIPS (lpj=7239454)
[   51.321685] Security Framework initialized
[   51.321691] SELinux:  Disabled at boot.
[   51.321706] AppArmor: AppArmor initialized
[   51.321710] Failure registering capabilities with primary security module.
[   51.321719] Mount-cache hash table entries: 512
[   51.321835] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   51.321844] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   51.321847] CPU: L2 Cache: 512K (64 bytes/line)
[   51.321850] CPU 0(2) -> Core 0
[   51.321852] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f 00000000
[   51.321862] Compat vDSO mapped to ffffe000.
[   51.321872] Checking 'hlt' instruction... OK.
[   51.337930] SMP alternatives: switching to UP code
[   51.339138] Early unpacking initramfs... done
[   51.691209] ACPI: Core revision 20070126
[   51.691288] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   51.901224] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   51.901241] SMP alternatives: switching to SMP code
[   51.901722] Booting processor 1/1 eip 3000
[   51.912046] Initializing CPU#1
[   51.989535] Calibrating delay using timer specific routine.. 3616.49 BogoMIPS (lpj=7232999)
[   51.989542] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f 00000000
[   51.989548] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   51.989551] CPU: L2 Cache: 512K (64 bytes/line)
[   51.989553] CPU 1(2) -> Core 1
[   51.989555] AMD C1E detected late. 	Force timer broadcast.
[   51.989556] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f 00000000
[   51.989484] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   51.989500] Total of 2 processors activated (7236.22 BogoMIPS).
[   51.989802] ENABLING IO-APIC IRQs
[   51.990035] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   52.029858] Brought up 2 CPUs
[   52.029913] CPU0 attaching sched-domain:
[   52.029916]  domain 0: span 03
[   52.029918]   groups: 01 02
[   52.029921] CPU1 attaching sched-domain:
[   52.029923]  domain 0: span 03
[   52.029925]   groups: 02 01
[   52.030119] net_namespace: 64 bytes
[   52.030127] Booting paravirtualized kernel on bare hardware
[   52.030605] Time: 21:05:30  Date: 04/29/08
[   52.030631] NET: Registered protocol family 16
[   52.030804] EISA bus registered
[   52.030808] ACPI: bus type pci registered
[   52.046371] PCI: BIOS BUG #81[49435000] found
[   52.046416] PCI: Using configuration type 1
[   52.046418] Setting up standard PCI resources
[   52.048064] ACPI: EC: Look up EC in DSDT
[   52.049910] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   52.050146] ACPI: Interpreter enabled
[   52.050149] ACPI: (supports S0 S3 S4 S5)
[   52.050160] ACPI: Using IOAPIC for interrupt routing
[   52.051031] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   52.057057] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   52.057061] ACPI: EC: driver started in interrupt mode
[   52.057113] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   52.058378] PCI: Transparent bridge - 0000:00:10.0
[   52.058394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   52.058484] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   52.058510] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   52.058540] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   52.091917] ACPI: PCI Interrupt Link [LNK1] (IRQs 5) *0, disabled.
[   52.092110] ACPI: PCI Interrupt Link [LNK2] (IRQs 7) *11
[   52.092300] ACPI: PCI Interrupt Link [LNK3] (IRQs 10) *11
[   52.092488] ACPI: PCI Interrupt Link [LNK4] (IRQs 11) *0, disabled.
[   52.092678] ACPI: PCI Interrupt Link [LK1E] (IRQs 16) *0, disabled.
[   52.092867] ACPI: PCI Interrupt Link [LK2E] (IRQs 17) *0, disabled.
[   52.093056] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *11
[   52.093246] ACPI: PCI Interrupt Link [LK4E] (IRQs 19) *0, disabled.
[   52.093435] ACPI: PCI Interrupt Link [LSMB] (IRQs *10)
[   52.093624] ACPI: PCI Interrupt Link [LPMU] (IRQs 11) *10
[   52.093826] ACPI: PCI Interrupt Link [LUS0] (IRQs 22) *11
[   52.094016] ACPI: PCI Interrupt Link [LUS2] (IRQs 22) *7
[   52.094206] ACPI: PCI Interrupt Link [LMAC] (IRQs 20) *10
[   52.094397] ACPI: PCI Interrupt Link [LAZA] (IRQs 21) *0, disabled.
[   52.094587] ACPI: PCI Interrupt Link [LACI] (IRQs 21) *0, disabled.
[   52.094778] ACPI: PCI Interrupt Link [LMCI] (IRQs 21) *0, disabled.
[   52.094969] ACPI: PCI Interrupt Link [LPID] (IRQs 21) *0, disabled.
[   52.095167] ACPI: PCI Interrupt Link [LTID] (IRQs 23) *5
[   52.095357] ACPI: PCI Interrupt Link [LSI1] (IRQs 20) *10
[   52.095492] Linux Plug and Play Support v0.97 (c) Adam Belay
[   52.095519] pnp: PnP ACPI init
[   52.095526] ACPI: bus type pnp registered
[   52.098610] pnp: PnP ACPI: found 13 devices
[   52.098613] ACPI: ACPI bus type pnp unregistered
[   52.098617] PnPBIOS: Disabled by ACPI PNP
[   52.098855] PCI: Using ACPI for IRQ routing
[   52.098858] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   52.113957] NET: Registered protocol family 8
[   52.113960] NET: Registered protocol family 20
[   52.113996] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   52.114000] hpet0: 3 32-bit timers, 25000000 Hz
[   52.115043] AppArmor: AppArmor Filesystem Enabled
[   52.117717] Time: hpet clocksource has been installed.
[   52.117721] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   52.117724] Could not switch to high resolution mode on CPU 0
[   52.121949] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   52.121953] Could not switch to high resolution mode on CPU 1
[   52.129980] system 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[   52.129988] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[   52.129991] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   52.129995] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[   52.129998] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[   52.130004] system 00:03: iomem range 0xe0000000-0xefffffff could not be reserved
[   52.130010] system 00:04: ioport range 0x1000-0x107f has been reserved
[   52.130012] system 00:04: ioport range 0x1080-0x10ff has been reserved
[   52.130015] system 00:04: ioport range 0x1400-0x147f has been reserved
[   52.130018] system 00:04: ioport range 0x1480-0x14ff has been reserved
[   52.130021] system 00:04: ioport range 0x1800-0x187f has been reserved
[   52.130023] system 00:04: ioport range 0x1880-0x18ff has been reserved
[   52.130026] system 00:04: ioport range 0x2000-0x203f has been reserved
[   52.130031] system 00:05: ioport range 0x360-0x361 has been reserved
[   52.130034] system 00:05: ioport range 0x380-0x383 has been reserved
[   52.130037] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[   52.160456] PCI: Bridge: 0000:00:02.0
[   52.160458]   IO window: 4000-4fff
[   52.160462]   MEM window: b4000000-b5ffffff
[   52.160464]   PREFETCH window: d0000000-d01fffff
[   52.160467] PCI: Bridge: 0000:00:03.0
[   52.160468]   IO window: disabled.
[   52.160471]   MEM window: b6000000-b7ffffff
[   52.160473]   PREFETCH window: disabled.
[   52.160476] PCI: Bridge: 0000:00:10.0
[   52.160477]   IO window: disabled.
[   52.160481]   MEM window: b8000000-b80fffff
[   52.160483]   PREFETCH window: disabled.
[   52.160496] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   52.160503] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   52.160510] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   52.160522] NET: Registered protocol family 2
[   52.197978] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   52.198248] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   52.199078] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   52.199516] TCP: Hash tables configured (established 131072 bind 65536)
[   52.199519] TCP reno registered
[   52.214050] checking if image is initramfs... it is
[   52.897238] Freeing initrd memory: 7692k freed
[   52.897346] Simple Boot Flag at 0x36 set to 0x1
[   52.898001] audit: initializing netlink socket (disabled)
[   52.898014] audit(1209503130.460:1): initialized
[   52.898193] highmem bounce pool size: 64 pages
[   52.900069] VFS: Disk quotas dquot_6.5.1
[   52.900138] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   52.900265] io scheduler noop registered
[   52.900267] io scheduler anticipatory registered
[   52.900269] io scheduler deadline registered
[   52.900279] io scheduler cfq registered (default)
[   52.900294] Boot video device is 0000:00:05.0
[   53.121545] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   53.121568] assign_interrupt_mode Found MSI capability
[   53.121588] Allocate Port Service[0000:00:02.0:pcie00]
[   53.121651] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   53.121673] assign_interrupt_mode Found MSI capability
[   53.121688] Allocate Port Service[0000:00:03.0:pcie00]
[   53.121912] isapnp: Scanning for PnP cards...
[   53.474457] isapnp: No Plug & Play device found
[   53.502099] Real Time Clock Driver v1.12ac
[   53.502292] hpet_resources: 0xfed00000 is busy
[   53.502343] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   53.503496] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   53.503562] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   53.503656] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   53.520960] serio: i8042 KBD port at 0x60,0x64 irq 1
[   53.520967] serio: i8042 AUX port at 0x60,0x64 irq 12
[   53.533252] mice: PS/2 mouse device common for all mice
[   53.533375] EISA: Probing bus 0 at eisa.0
[   53.533380] Cannot allocate resource for EISA slot 1
[   53.533383] Cannot allocate resource for EISA slot 2
[   53.533385] Cannot allocate resource for EISA slot 3
[   53.533387] Cannot allocate resource for EISA slot 4
[   53.533401] EISA: Detected 0 cards.
[   53.533403] cpuidle: using governor ladder
[   53.533406] cpuidle: using governor menu
[   53.533497] NET: Registered protocol family 1
[   53.533523] Using IPI No-Shortcut mode
[   53.533557] registered taskstats version 1
[   53.533684]   Magic number: 4:907:96
[   53.533859] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   53.533861] EDD information not available.
[   53.534095] Freeing unused kernel memory: 364k freed
[   53.546022] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   54.814596] fuse init (API version 7.9)
[   54.840584] ACPI: Thermal Zone [THRM] (62 C)
[   55.348332] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   55.348344] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK4E] -> GSI 19 (level, high) -> IRQ 16
[   55.348354] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   55.382263] usbcore: registered new interface driver usbfs
[   55.382286] usbcore: registered new interface driver hub
[   55.395124] usbcore: registered new device driver usb
[   55.407516] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   55.408697] WARNING: at /build/buildd/linux-2.6.24/drivers/ssb/main.c:883 ssb_tmslow_reject_bitmask()
[   55.408702] Pid: 1568, comm: modprobe Not tainted 2.6.24-16-generic #1
[   55.408706]  [<f884d87b>] ssb_tmslow_reject_bitmask+0x4b/0x60 [ssb]
[   55.408717]  [<f884e161>] ssb_device_is_enabled+0x11/0x40 [ssb]
[   55.408725]  [<f88502d9>] ssb_pcicore_init+0x19/0x60 [ssb]
[   55.408732]  [<f884d6a3>] ssb_attach_queued_buses+0xd3/0x260 [ssb]
[   55.408739]  [<f884f72f>] ssb_pci_xtal+0x17f/0x230 [ssb]
[   55.408746]  [<f884dc36>] ssb_bus_register+0x156/0x1d0 [ssb]
[   55.408753]  [<f884ef90>] ssb_pci_get_invariants+0x0/0x2c0 [ssb]
[   55.408763]  [<f884dd2a>] ssb_bus_pcibus_register+0x2a/0x60 [ssb]
[   55.408769]  [<c02206e4>] pci_set_master+0x54/0x60
[   55.408776]  [<f884f94c>] ssb_pcihost_probe+0x6c/0xb0 [ssb]
[   55.408783]  [<c0222696>] pci_device_probe+0x56/0x80
[   55.408787]  [<c027d988>] driver_probe_device+0x88/0x190
[   55.408791]  [<c02113f0>] kobject_uevent_env+0xf0/0x3d0
[   55.408796]  [<c027dbfe>] __driver_attach+0x9e/0xa0
[   55.408799]  [<c027cdbb>] bus_for_each_dev+0x3b/0x60
[   55.408803]  [<c027d806>] driver_attach+0x16/0x20
[   55.408806]  [<c027db60>] __driver_attach+0x0/0xa0
[   55.408810]  [<c027d13a>] bus_add_driver+0x8a/0x1e0
[   55.408814]  [<c0222846>] __pci_register_driver+0x56/0x90
[   55.408818]  [<f883104a>] ssb_modinit+0x4a/0x80 [ssb]
[   55.408824]  [<c0145537>] blocking_notifier_call_chain+0x17/0x20
[   55.408829]  [<c01506b6>] sys_init_module+0x126/0x19c0
[   55.408837]  [<c027d330>] bus_register+0x0/0x230
[   55.408842]  [<c0104442>] syscall_call+0x7/0xb
[   55.408846]  =======================
[   55.408898] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   55.409271] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[   55.409281] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 22 (level, high) -> IRQ 17
[   55.409293] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   55.409296] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   55.409575] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   55.409594] ohci_hcd 0000:00:0b.0: irq 17, io mem 0xb0004000
[   55.466068] usb usb1: configuration #1 chosen from 1 choice
[   55.466092] hub 1-0:1.0: USB hub found
[   55.466102] hub 1-0:1.0: 8 ports detected
[   55.487955] SCSI subsystem initialized
[   55.515974] libata version 3.00 loaded.
[   55.568377] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   55.568736] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   55.568747] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 20 (level, high) -> IRQ 18
[   55.568754] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   55.871744] usb 1-4: new full speed USB device using ohci_hcd and address 2
[   56.084730] usb 1-4: configuration #1 chosen from 1 choice
[   56.092298] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:1b:24:4e:dc:db
[   56.092304] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[   56.092440] sata_nv 0000:00:0e.0: version 3.5
[   56.092459] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   56.092479] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[   56.092496] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 5 (level, high) -> IRQ 5
[   56.093038] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 23
[   56.093049] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 23 (level, high) -> IRQ 19
[   56.093091] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   56.093160] scsi0 : sata_nv
[   56.093204] scsi1 : sata_nv
[   56.093331] ata1: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 19
[   56.093335] ata2: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 19
[   56.144245] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[b8000000-b80007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   56.567580] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   56.579753] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC7BP, max UDMA/100
[   56.579756] ata1.00: 312581808 sectors, multi 16: LBA48 
[   56.599744] ata1.00: configured for UDMA/100
[   56.911381] ata2: SATA link down (SStatus 0 SControl 300)
[   56.922033] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[   56.924840] pata_amd 0000:00:0d.0: version 0.3.10
[   56.924894] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   56.926864] scsi2 : pata_amd
[   56.927102] scsi3 : pata_amd
[   56.927682] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[   56.927685] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[   57.259624] ata3.00: ATAPI: MATSHITADVD-RAM UJ-851S, 1.50, max MWDMA2
[   57.431336] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b0089b82500]
[   57.443481] ata3.00: configured for MWDMA2
[   57.443518] ata4: port disabled. ignoring.
[   57.445368] scsi 2:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-851S  1.50 PQ: 0 ANSI: 5
[   57.446929] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   57.446933] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 22 (level, high) -> IRQ 17
[   57.446944] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   57.446947] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   57.446973] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   57.447007] ehci_hcd 0000:00:0b.1: debug port 1
[   57.447011] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   57.447018] ehci_hcd 0000:00:0b.1: irq 17, io mem 0xb0005000
[   57.446843] usb 1-4: USB disconnect, address 2
[   57.455094] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   57.455222] usb usb2: configuration #1 chosen from 1 choice
[   57.455245] hub 2-0:1.0: USB hub found
[   57.455256] hub 2-0:1.0: 8 ports detected
[   57.576312] Driver 'sd' needs updating - please use bus_type methods
[   57.577276] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   57.577288] sd 0:0:0:0: [sda] Write Protect is off
[   57.577291] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   57.577307] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   57.577352] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   57.577361] sd 0:0:0:0: [sda] Write Protect is off
[   57.577363] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   57.577377] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   57.577380]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   57.814668] usb 2-4: new high speed USB device using ehci_hcd and address 2
[   57.968987] usb 2-4: configuration #1 chosen from 1 choice
[   58.000882]  sda1 sda2 < sda5 >
[   58.025704] sd 0:0:0:0: [sda] Attached SCSI disk
[   58.032689] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   58.032710] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   58.032868] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   58.032874] Uniform CD-ROM driver Revision: 3.20
[   58.032929] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   58.295514] Attempting manual resume
[   58.295519] swsusp: Resume From Partition 8:5
[   58.295521] PM: Checking swsusp image.
[   58.295711] PM: Resume from disk failed.
[   58.344339] kjournald starting.  Commit interval 5 seconds
[   58.344573] EXT3-fs: mounted filesystem with ordered data mode.
[   65.151837] input: Power Button (FF) as /devices/virtual/input/input2
[   65.174745] ACPI: Power Button (FF) [PWRF]
[   65.174834] input: Power Button (CM) as /devices/virtual/input/input3
[   65.206715] ACPI: Power Button (CM) [PWRB]
[   65.206794] input: Sleep Button (CM) as /devices/virtual/input/input4
[   65.238690] ACPI: Sleep Button (CM) [SLPB]
[   65.238830] input: Lid Switch as /devices/virtual/input/input5
[   65.239366] ACPI: Lid Switch [LID]
[   65.240872] ACPI: AC Adapter [ACAD] (on-line)
[   65.978830] ACPI: Battery Slot [BAT0] (battery present)
[   65.978919] ACPI: WMI-Acer: Mapper loaded
[   65.981097] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input6
[   66.014498] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   66.016027] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:26/LNXVIDEO:01/input/input7
[   66.042482] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   66.617941] Linux agpgart interface v0.102
[   66.683138] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   66.734288] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   66.780956] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   66.780985] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   67.027893] ricoh-mmc: Ricoh MMC Controller disabling driver
[   67.027897] ricoh-mmc: Copyright(c) Philip Langdale
[   67.027938] ricoh-mmc: Ricoh MMC controller found at 0000:07:05.2 [1180:0843] (rev 1)
[   67.027948] ricoh-mmc: Controller is now disabled.
[   67.045776] sdhci: Secure Digital Host Controller Interface driver
[   67.045780] sdhci: Copyright(c) Pierre Ossman
[   67.045824] sdhci: SDHCI controller found at 0000:07:05.1 [1180:0822] (rev 19)
[   67.046156] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[   67.046167] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 7 (level, high) -> IRQ 7
[   67.046181] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   67.046226] mmc0: SDHCI at 0xb8000800 irq 7 DMA
[   67.389609] Linux video capture interface: v2.00
[   67.491044] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   67.508952] usbcore: registered new interface driver uvcvideo
[   67.508957] USB Video Class driver (v0.1.0)
[   67.741486] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   67.925136] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   67.925147] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 21 (level, high) -> IRQ 20
[   67.925174] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   68.350320] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   68.414171] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   69.310886] lp: driver loaded but no devices found
[   69.455897] Adding 5887780k swap on /dev/sda5.  Priority:-1 extents:1 across:5887780k
[   70.008676] EXT3 FS on sda1, internal journal
[   71.294703] ip_tables: (C) 2000-2006 Netfilter Core Team
[   71.768554] No dock devices found.
[   72.097803] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (2 cpu cores) (version 2.20.00)
[   72.097628] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x12
[   72.097633] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   72.097635] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   72.768927] apm: BIOS not found.
[   72.921761] ppdev: user-space parallel port driver
[   73.022663] audit(1209503150.818:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5201 profile="/usr/sbin/cupsd" namespace="default"
[   74.138466] eth0: no link during initialization.
[   74.193148] Bluetooth: Core ver 2.11
[   74.193227] NET: Registered protocol family 31
[   74.193229] Bluetooth: HCI device and connection manager initialized
[   74.193233] Bluetooth: HCI socket layer initialized
[   74.204446] Bluetooth: L2CAP ver 2.9
[   74.204451] Bluetooth: L2CAP socket layer initialized
[   74.233755] Bluetooth: RFCOMM socket layer initialized
[   74.233769] Bluetooth: RFCOMM TTY layer initialized
[   74.233771] Bluetooth: RFCOMM ver 1.8
[   74.278761] Clocksource tsc unstable (delta = -277803269 ns)
[  293.915658] NET: Registered protocol family 10
[  293.915887] lo: Disabled Privacy Extensions
[  293.916484] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  298.235089] CPU0 attaching NULL sched-domain.
[  298.235099] CPU1 attaching NULL sched-domain.
[  298.252173] CPU0 attaching sched-domain:
[  298.252178]  domain 0: span 03
[  298.252181]   groups: 01 02
[  298.252186] CPU1 attaching sched-domain:
[  298.252188]  domain 0: span 03
[  298.252190]   groups: 02 01
[  575.097463] CPU0 attaching NULL sched-domain.
[  575.097470] CPU1 attaching NULL sched-domain.
[  575.111492] CPU0 attaching sched-domain:
[  575.111496]  domain 0: span 03
[  575.111498]   groups: 01 02
[  575.111502]   domain 1: span 03
[  575.111503]    groups: 03
[  575.111506] CPU1 attaching sched-domain:
[  575.111508]  domain 0: span 03
[  575.111509]   groups: 02 01
[  575.111512]   domain 1: span 03
[  575.111514]    groups: 03
[  628.578413] eth0: link up.
[  628.579640] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  629.566083] NET: Registered protocol family 17
[  638.832194] eth0: no IPv6 routers present
cody@cody-laptop:~$

---

### Post by Lostatsea3 on 2008-04-29
Ok.. there's that. 
 
How do I run parted? I typed it into terminal and it said watch out you're not a super user

---

### Post by Lostatsea3 on 2008-04-29
Btw... thanks for all your help. I really appreciate it! 

I'm starting to really like Ubuntu! now if I could just get wifi

---

### Post by natrixgli on 2008-04-29
Ok, I see nothing re: wireless. 

As for parted, the warning means that you can't make any changes (which is ok) but once you run parted you should be able to type 'print' to get a list of partitions on your drive. 

More info about the laptop - what HP model is it?

Cheers,

-n8

---


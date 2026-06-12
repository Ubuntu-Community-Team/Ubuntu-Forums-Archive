---
title: "PLZ HELP! updated to fiesty, now it won't boot up :("
date: 2007-04-20
forum: General Help
---

### Post by pdrift on 2007-04-20
PLZ HELP! i updated to fiesty thru update manager, everything went smoothly until it was time to reboot.When i try to boot, it shows the Ubuntu splash screen then it just goes blank except for the mouse icon. what can i do? i don't want to lose my data thats why i updated instead of doing a full install with fiesty. man i had edgy running like a champ. please someone help!

---

### Post by bobonthenet on 2007-04-20
I'm having the exact same problem.  I log in then I get a black screen with only the curser then white screen and only the curser works.  Once I get to the white screen my computer is pretty much done, the curser works but thats it.  I'm not very good with ubuntu I'm still somewhat of a noob so I really need some help.

---

### Post by Dave54 on 2007-04-20
Have you tried booting up in a failsafe mode?

I can see 2 ways of doing this.

1: before ubuntu starts booting up, you get a grub message. Hit escape to go into the menu and pick a different boot option.

2: at the login screen, click options > sessions, and pick a different option.

---

### Post by matigol on 2007-04-20
Can you edit your fstab ?

---

### Post by pdrift on 2007-04-20
no, i can't do anything. it doesn't even get to the log-in screen.
when i boot up, i see the ubuntu screen then the screen goes
blank and then nothing. just the cursor for the mouse.
it doesn't make it to the login screen. sorry i am fairly new to ubuntu
i am learning how to fix things as they happen. i was runnung edgy
i learned how to compile programs and get dependencies and stuff
but i don't know much more than that. i don't know what fstab is.
any ideas. does it sound like i need to do a full install?
and can i retrieve my data if i use the live cd to boot up and then copy my files 
over to an external hard drive from the internal drive?
i hope i can get up and running soon because those 3-d desktops
look amazing.my earlier post was from my cellphone. now i'm on another
windoze pc.

---

### Post by skip27 on 2007-04-20
Hi pdrift,

We'll need to know exactly what your kernel is saying so we can identify the problem. Where is it crashing? Does it enter X? Two things:

1) Boot in recovery mode. You will NOT see a splash screen and the kernel will be outputting information verbosely. Are there any problems? If it does crash at this point, what kind of error message does it give you? Perhaps save a copy of /var/log/messages and post it? Could you output the contents of 'dmesg' to a file and post that as well? You can access these files if you boot up Ubuntu through a LiveCD. Mount the drive containing your Ubuntu installation and you'll have access to the entire drive.

2) If it does get past booting and goes into X, it's likely not a startup issue (unless its something subtle, like a driver/module problem). What does your /var/log/Xorg.0.log say? Do you have an Xorg.20.log too? Make sure that your /etc/X11/xorg.conf file is loading the correct video driver! Try using the 'vesa' driver instead of 'nvidia' or whatever it was you were using. If this solves it, you'll need to recompile the driver for your video card (highly recommended) or you could download another one through synaptic via the restricted modules package.

---

### Post by Dave54 on 2007-04-20
How to boot in recovery mode:

Turn on your computer. **Before** Ubuntu begins to start up, you will see a quick message saying something like:
> GRUB loading
Hit "ESC" to enter the GRUB menu.
There will be a three second timer. Before that time runs out, you have to hit Escape. You will be brought to a menu. Use the up and down keys to select an option that says "recovery mode" and hit enter.

---

### Post by VileTimes on 2007-04-20
I'm having this exact same problem after upgrading to Feisty from Edgy via "sudo aptitude dist-upgrade", very frustrating considering I had everything set up perfectly in Edgy. Feisty freezes at:

```

* Running local boot scripts (/etc/rc.local) [ok]

```

Here

This is was a Edgy Server install following teaks in this [guide by Kmandla]("http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/").

Here is my /var/log/messages:

```

Apr 20 22:33:02 server syslogd 1.4.1#20ubuntu4: restart.
Apr 20 22:33:02 server kernel: Inspecting /boot/System.map-2.6.20-15-server
Apr 20 22:33:02 server kernel: Loaded 25134 symbols from /boot/System.map-2.6.20-15-server.
Apr 20 22:33:02 server kernel: Symbols match kernel version 2.6.20.
Apr 20 22:33:02 server kernel: No module symbols loaded - kernel modules not enabled. 
Apr 20 22:33:02 server kernel: [    0.000000] Linux version 2.6.20-15-server (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:41:34 UTC 2007 (Ubuntu 2.6.20-15.27-server)
Apr 20 22:33:02 server kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 20 22:33:02 server kernel: [    0.000000] sanitize start
Apr 20 22:33:02 server kernel: [    0.000000] sanitize end
Apr 20 22:33:02 server kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
Apr 20 22:33:02 server kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 20 22:33:02 server kernel: [    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
Apr 20 22:33:02 server kernel: [    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
Apr 20 22:33:02 server kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fef0000 end: 000000001fff0000 type: 1
Apr 20 22:33:02 server kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 20 22:33:02 server kernel: [    0.000000] copy_e820_map() start: 000000001fff0000 size: 0000000000003000 end: 000000001fff3000 type: 4
Apr 20 22:33:02 server kernel: [    0.000000] copy_e820_map() start: 000000001fff3000 size: 000000000000d000 end: 0000000020000000 type: 3
Apr 20 22:33:02 server kernel: [    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
Apr 20 22:33:02 server kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr 20 22:33:02 server kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr 20 22:33:02 server kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Apr 20 22:33:02 server kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
Apr 20 22:33:02 server kernel: [    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
Apr 20 22:33:02 server kernel: [    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
Apr 20 22:33:02 server kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Apr 20 22:33:02 server kernel: [    0.000000] 0MB HIGHMEM available.
Apr 20 22:33:02 server kernel: [    0.000000] 511MB LOWMEM available.
Apr 20 22:33:02 server kernel: [    0.000000] found SMP MP-table at 000f66c0
Apr 20 22:33:03 server kernel: [    0.000000] Zone PFN ranges:
Apr 20 22:33:03 server kernel: [    0.000000]   DMA             0 ->     4096
Apr 20 22:33:03 server kernel: [    0.000000]   Normal       4096 ->   131056
Apr 20 22:33:03 server kernel: [    0.000000]   HighMem    131056 ->   131056
Apr 20 22:33:03 server kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 20 22:33:03 server kernel: [    0.000000]     0:        0 ->   131056
Apr 20 22:33:03 server kernel: [    0.000000] DMI 2.2 present.
Apr 20 22:33:03 server kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Apr 20 22:33:03 server kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 20 22:33:03 server kernel: [    0.000000] Processor #0 6:4 APIC version 16
Apr 20 22:33:03 server kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 20 22:33:03 server kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Apr 20 22:33:03 server kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 20 22:33:03 server kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
Apr 20 22:33:03 server kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 20 22:33:03 server kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 20 22:33:03 server kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
Apr 20 22:33:03 server kernel: [    0.000000] Detected 799.705 MHz processor.
Apr 20 22:33:03 server kernel: [   28.738255] Built 1 zonelists.  Total pages: 130033
Apr 20 22:33:03 server kernel: [   28.738264] Kernel command line: root=UUID=9fa610e4-4d1f-4a9a-b110-75a826973a62 ro rootflags=data=writeback elevator=cfq
Apr 20 22:33:03 server kernel: [   28.738703] Enabling fast FPU save and restore... done.
Apr 20 22:33:03 server kernel: [   28.738728] Initializing CPU#0
Apr 20 22:33:03 server kernel: [   28.738858] PID hash table entries: 2048 (order: 11, 8192 bytes)
Apr 20 22:33:03 server kernel: [   28.740304] Console: colour VGA+ 80x25
Apr 20 22:33:03 server kernel: [   28.743697] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 20 22:33:03 server kernel: [   28.744406] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 20 22:33:03 server kernel: [   28.780643] Memory: 508828k/524224k available (2020k kernel code, 14868k reserved, 893k data, 328k init, 0k highmem)
Apr 20 22:33:03 server kernel: [   28.780745] virtual kernel memory layout:
Apr 20 22:33:03 server kernel: [   28.780748]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 20 22:33:03 server kernel: [   28.780751]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 20 22:33:03 server kernel: [   28.780755]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Apr 20 22:33:03 server kernel: [   28.780758]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
Apr 20 22:33:03 server kernel: [   28.780762]       .init : 0xc03df000 - 0xc0431000   ( 328 kB)
Apr 20 22:33:03 server kernel: [   28.780765]       .data : 0xc02f9114 - 0xc03d8754   ( 893 kB)
Apr 20 22:33:03 server kernel: [   28.780769]       .text : 0xc0100000 - 0xc02f9114   (2020 kB)
Apr 20 22:33:03 server kernel: [   28.781217] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 20 22:33:03 server kernel: [   28.928778] Calibrating delay using timer specific routine.. 1600.88 BogoMIPS (lpj=8004408)
Apr 20 22:33:03 server kernel: [   28.928988] Security Framework v1.0.0 initialized
Apr 20 22:33:03 server kernel: [   28.929057] SELinux:  Disabled at boot.
Apr 20 22:33:03 server kernel: [   28.929147] Mount-cache hash table entries: 512
Apr 20 22:33:03 server kernel: [   28.929537] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Apr 20 22:33:03 server kernel: [   28.929604] CPU: L2 Cache: 256K (64 bytes/line)
Apr 20 22:33:03 server kernel: [   28.929688] Compat vDSO mapped to ffffe000.
Apr 20 22:33:03 server kernel: [   28.929754] Remapping vsyscall page to ffffe000
Apr 20 22:33:03 server kernel: [   28.929828] Checking 'hlt' instruction... OK.
Apr 20 22:33:03 server kernel: [   28.968874] SMP alternatives: switching to UP code
Apr 20 22:33:03 server kernel: [   28.969422] Freeing SMP alternatives: 11k freed
Apr 20 22:33:03 server kernel: [   28.969987] Early unpacking initramfs... done
Apr 20 22:33:03 server kernel: [   29.675196] ACPI: Core revision 20060707
Apr 20 22:33:03 server kernel: [   29.682528] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 20 22:33:03 server kernel: [   29.686901] CPU0: AMD Athlon(tm) processor stepping 02
Apr 20 22:33:03 server kernel: [   29.687081] Total of 1 processors activated (1600.88 BogoMIPS).
Apr 20 22:33:03 server kernel: [   29.687913] ENABLING IO-APIC IRQs
Apr 20 22:33:03 server kernel: [   29.688324] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 20 22:33:03 server kernel: [   29.908430] Brought up 1 CPUs
Apr 20 22:33:03 server kernel: [   29.909095] Booting paravirtualized kernel on bare hardware
Apr 20 22:33:03 server kernel: [   29.909294] Time:  2:32:40  Date: 03/21/107
Apr 20 22:33:03 server kernel: [   29.909424] NET: Registered protocol family 16
Apr 20 22:33:03 server kernel: [   29.909709] EISA bus registered
Apr 20 22:33:03 server kernel: [   29.909771] ACPI: bus type pci registered
Apr 20 22:33:03 server kernel: [   29.942872] PCI: PCI BIOS revision 2.10 entry at 0xfb590, last bus=1
Apr 20 22:33:03 server kernel: [   29.942934] PCI: Using configuration type 1
Apr 20 22:33:03 server kernel: [   29.942991] Setting up standard PCI resources
Apr 20 22:33:03 server kernel: [   29.960533] ACPI: Interpreter enabled
Apr 20 22:33:03 server kernel: [   29.960603] ACPI: Using IOAPIC for interrupt routing
Apr 20 22:33:03 server kernel: [   29.961990] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 20 22:33:03 server kernel: [   29.962238] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Apr 20 22:33:03 server kernel: [   29.962911] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
Apr 20 22:33:03 server kernel: [   29.962978] PCI quirk: region 5000-500f claimed by vt82c686 SMB
Apr 20 22:33:03 server kernel: [   29.986854] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
Apr 20 22:33:03 server kernel: [   29.988042] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Apr 20 22:33:03 server kernel: [   29.989377] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Apr 20 22:33:03 server kernel: [   29.990684] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
Apr 20 22:33:03 server kernel: [   29.995880] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 20 22:33:03 server kernel: [   29.995964] pnp: PnP ACPI init
Apr 20 22:33:03 server kernel: [   30.001773] pnp: PnP ACPI: found 13 devices
Apr 20 22:33:03 server kernel: [   30.001842] PnPBIOS: Disabled by ACPI PNP
Apr 20 22:33:03 server kernel: [   30.002037] PCI: Using ACPI for IRQ routing
Apr 20 22:33:03 server kernel: [   30.002100] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 20 22:33:03 server kernel: [   30.025380] NET: Registered protocol family 8
Apr 20 22:33:03 server kernel: [   30.025441] NET: Registered protocol family 20
Apr 20 22:33:03 server kernel: [   30.025515] NetLabel: Initializing
Apr 20 22:33:03 server kernel: [   30.025570] NetLabel:  domain hash size = 128
Apr 20 22:33:03 server kernel: [   30.025627] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 20 22:33:03 server kernel: [   30.025716] NetLabel:  unlabeled traffic allowed by default
Apr 20 22:33:03 server kernel: [   30.027141] PCI: Bridge: 0000:00:01.0
Apr 20 22:33:03 server kernel: [   30.027201]   IO window: disabled.
Apr 20 22:33:03 server kernel: [   30.027262]   MEM window: dc000000-ddffffff
Apr 20 22:33:03 server kernel: [   30.027322]   PREFETCH window: d4000000-dbffffff
Apr 20 22:33:03 server kernel: [   30.027458] NET: Registered protocol family 2
Apr 20 22:33:03 server kernel: [   30.098436] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Apr 20 22:33:03 server kernel: [   30.098707] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Apr 20 22:33:03 server kernel: [   30.099347] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Apr 20 22:33:03 server kernel: [   30.099703] TCP: Hash tables configured (established 16384 bind 8192)
Apr 20 22:33:03 server kernel: [   30.099767] TCP reno registered
Apr 20 22:33:03 server kernel: [   30.128497] checking if image is initramfs... it is
Apr 20 22:33:03 server kernel: [   31.474946] Freeing initrd memory: 6645k freed
Apr 20 22:33:03 server kernel: [   31.476140] audit: initializing netlink socket (disabled)
Apr 20 22:33:03 server kernel: [   31.476228] audit(1177122762.590:1): initialized
Apr 20 22:33:03 server kernel: [   31.476518] VFS: Disk quotas dquot_6.5.1
Apr 20 22:33:03 server kernel: [   31.476618] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 20 22:33:03 server kernel: [   31.476792] io scheduler noop registered
Apr 20 22:33:03 server kernel: [   31.476891] io scheduler anticipatory registered
Apr 20 22:33:03 server kernel: [   31.476988] io scheduler deadline registered
Apr 20 22:33:03 server kernel: [   31.477098] io scheduler cfq registered (default)
Apr 20 22:33:03 server kernel: [   31.477261] Applying VIA southbridge workaround.
Apr 20 22:33:03 server kernel: [   31.477324] PCI: Enabling Via external APIC routing
Apr 20 22:33:03 server kernel: [   31.477899] isapnp: Scanning for PnP cards...
Apr 20 22:33:03 server kernel: [   31.835221] isapnp: No Plug & Play device found
Apr 20 22:33:03 server kernel: [   31.901083] Real Time Clock Driver v1.12ac
Apr 20 22:33:03 server kernel: [   31.901258] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 20 22:33:03 server kernel: [   31.901559] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 20 22:33:03 server kernel: [   31.902032] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 20 22:33:03 server kernel: [   31.903405] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 20 22:33:03 server kernel: [   31.904093] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 20 22:33:03 server kernel: [   31.904720] mice: PS/2 mouse device common for all mice
Apr 20 22:33:03 server kernel: [   31.906160] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 20 22:33:03 server kernel: [   31.906807] input: Macintosh mouse button emulation as /class/input/input0
Apr 20 22:33:03 server kernel: [   31.906950] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 20 22:33:03 server kernel: [   31.907018] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 20 22:33:03 server kernel: [   31.907706] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 20 22:33:03 server kernel: [   31.908221] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 20 22:33:03 server kernel: [   31.908288] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 20 22:33:03 server kernel: [   31.908610] EISA: Probing bus 0 at eisa.0
Apr 20 22:33:03 server kernel: [   31.908707] Cannot allocate resource for EISA slot 4
Apr 20 22:33:03 server kernel: [   31.908769] Cannot allocate resource for EISA slot 5
Apr 20 22:33:03 server kernel: [   31.908829] Cannot allocate resource for EISA slot 6
Apr 20 22:33:03 server kernel: [   31.908904] EISA: Detected 0 cards.
Apr 20 22:33:03 server kernel: [   31.939393] TCP cubic registered
Apr 20 22:33:03 server kernel: [   31.939464] NET: Registered protocol family 1
Apr 20 22:33:03 server kernel: [   31.939569] Using IPI No-Shortcut mode
Apr 20 22:33:03 server kernel: [   31.939836] ACPI: (supports S0 S1 S4 S5)
Apr 20 22:33:03 server kernel: [   31.940188]   Magic number: 3:252:511
Apr 20 22:33:03 server kernel: [   31.941394] Freeing unused kernel memory: 328k freed
Apr 20 22:33:03 server kernel: [   31.947379] Time: tsc clocksource has been installed.
Apr 20 22:33:03 server kernel: [   31.954117] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 20 22:33:03 server kernel: [   32.326292] Capability LSM initialized
Apr 20 22:33:03 server kernel: [   33.607387] usbcore: registered new interface driver usbfs
Apr 20 22:33:03 server kernel: [   33.607528] usbcore: registered new interface driver hub
Apr 20 22:33:03 server kernel: [   33.607639] usbcore: registered new device driver usb
Apr 20 22:33:03 server kernel: [   33.609981] USB Universal Host Controller Interface driver v3.0
Apr 20 22:33:03 server kernel: [   33.611292] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Apr 20 22:33:03 server kernel: [   33.611371] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr 20 22:33:03 server kernel: [   33.611533] PCI: VIA VLink IRQ fixup for 0000:00:07.2, from 10 to 11
Apr 20 22:33:03 server kernel: [   33.611628] uhci_hcd 0000:00:07.2: UHCI Host Controller
Apr 20 22:33:03 server kernel: [   33.612806] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
Apr 20 22:33:03 server kernel: [   33.612922] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000d400
Apr 20 22:33:03 server kernel: [   33.613266] usb usb1: configuration #1 chosen from 1 choice
Apr 20 22:33:03 server kernel: [   33.613386] hub 1-0:1.0: USB hub found
Apr 20 22:33:03 server kernel: [   33.613461] hub 1-0:1.0: 2 ports detected
Apr 20 22:33:03 server kernel: [   33.726619] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Apr 20 22:33:03 server kernel: [   33.726792] PCI: VIA VLink IRQ fixup for 0000:00:07.3, from 10 to 11
Apr 20 22:33:03 server kernel: [   33.726888] uhci_hcd 0000:00:07.3: UHCI Host Controller
Apr 20 22:33:03 server kernel: [   33.726994] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
Apr 20 22:33:03 server kernel: [   33.727096] uhci_hcd 0000:00:07.3: irq 11, io base 0x0000d800
Apr 20 22:33:03 server kernel: [   33.727395] usb usb2: configuration #1 chosen from 1 choice
Apr 20 22:33:03 server kernel: [   33.727518] hub 2-0:1.0: USB hub found
Apr 20 22:33:03 server kernel: [   33.727592] hub 2-0:1.0: 2 ports detected
Apr 20 22:33:03 server kernel: [   33.779522] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
Apr 20 22:33:03 server kernel: [   33.850011] VP_IDE: IDE controller at PCI slot 0000:00:07.1
Apr 20 22:33:03 server kernel: [   33.850119] VP_IDE: chipset revision 6
Apr 20 22:33:03 server kernel: [   33.850177] VP_IDE: not 100%% native mode: will probe irqs later
Apr 20 22:33:03 server kernel: [   33.850254] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
Apr 20 22:33:03 server kernel: [   33.850336]     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:DMA, hdb:pio
Apr 20 22:33:03 server kernel: [   33.850501]     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:DMA, hdd:pio
Apr 20 22:33:03 server kernel: [   33.917161] Floppy drive(s): fd0 is 1.44M
Apr 20 22:33:03 server kernel: [   33.968083] FDC 0 is a post-1991 82077
Apr 20 22:33:03 server kernel: [   34.306114] hda: ST3200822A, ATA DISK drive
Apr 20 22:33:03 server kernel: [   34.795837] hdb: HL-DT-ST GCE-8525B, ATAPI CD/DVD-ROM drive
Apr 20 22:33:03 server kernel: [   34.856681] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Apr 20 22:33:03 server kernel: [   35.785305] hdc: MATSHITADVD-ROM SR-8586, ATAPI CD/DVD-ROM drive
Apr 20 22:33:03 server kernel: [   36.145354] ide1 at 0x170-0x177,0x376 on irq 15
Apr 20 22:33:03 server kernel: [   36.161583] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 19 (level, low) -> IRQ 16
Apr 20 22:33:03 server kernel: [   36.165870] eth0: VIA Rhine II at 0x1ec00, 00:50:ba:64:a6:49, IRQ 16.
Apr 20 22:33:03 server kernel: [   36.166883] eth0: MII PHY found at address 8, status 0x782d advertising 01e1 Link 45e1.
Apr 20 22:33:03 server kernel: [   36.168817] SCSI subsystem initialized
Apr 20 22:33:03 server kernel: [   36.226662] hdb: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Apr 20 22:33:03 server kernel: [   36.227021] Uniform CD-ROM driver Revision: 3.20
Apr 20 22:33:03 server kernel: [   36.243073] hda: max request size: 512KiB
Apr 20 22:33:03 server kernel: [   36.243194] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
Apr 20 22:33:03 server kernel: [   36.243706] hda: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63
Apr 20 22:33:03 server kernel: [   36.244124] hda: cache flushes supported
Apr 20 22:33:03 server kernel: [   36.244278]  hda: hda1 hda2 hda3 < hda5 > hda4
Apr 20 22:33:03 server kernel: [   36.626097] Attempting manual resume
Apr 20 22:33:03 server kernel: [   36.672803] kjournald starting.  Commit interval 5 seconds
Apr 20 22:33:03 server kernel: [   36.672899] EXT3-fs: mounted filesystem with writeback data mode.
Apr 20 22:33:03 server kernel: [   44.175454] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Apr 20 22:33:03 server kernel: [   45.270712] NET: Registered protocol family 17
Apr 20 22:33:03 server kernel: [   46.815746] Linux agpgart interface v0.102 (c) Dave Jones
Apr 20 22:33:03 server kernel: [   47.012063] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
Apr 20 22:33:03 server kernel: [   47.018805] agpgart: AGP aperture is 64M @ 0xd0000000
Apr 20 22:33:03 server kernel: [   47.060403] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
Apr 20 22:33:03 server kernel: [   47.148898] parport_pc: VIA parallel port: io=0x378, irq=7
Apr 20 22:33:03 server kernel: [   47.223060] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 20 22:33:03 server kernel: [   47.241883] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 20 22:33:03 server kernel: [   48.546278] input: PC Speaker as /class/input/input2
Apr 20 22:33:03 server kernel: [   48.859182] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
Apr 20 22:33:03 server kernel: [   48.859273] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
Apr 20 22:33:03 server kernel: [   48.859434] PCI: VIA VLink IRQ fixup for 0000:00:07.5, from 11 to 10
Apr 20 22:33:03 server kernel: [   49.125527] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
Apr 20 22:33:03 server kernel: [   49.591284] lp0: using parport0 (interrupt-driven).
Apr 20 22:33:03 server kernel: [   49.658736] Adding 248968k swap on /dev/disk/by-uuid/6b4cb9b1-eb05-481a-8252-b616e4b00642.  Priority:-1 extents:1 across:248968k
Apr 20 22:33:03 server kernel: [   49.670746] EXT3 FS on hda2, internal journal
Apr 20 22:33:03 server kernel: [   49.992805] NET: Registered protocol family 10
Apr 20 22:33:03 server kernel: [   49.993096] lo: Disabled Privacy Extensions
Apr 20 22:33:03 server kernel: [   50.192823] kjournald starting.  Commit interval 5 seconds
Apr 20 22:33:03 server kernel: [   50.193258] EXT3 FS on hda4, internal journal
Apr 20 22:33:03 server kernel: [   50.193270] EXT3-fs: mounted filesystem with writeback data mode.
Apr 20 22:36:06 server exiting on signal 15

```

This is what I get with a dmesg:

```

[    0.000000] Linux version 2.6.20-15-server (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:41:34 UTC 2007 (Ubuntu 2.6.20-15.27-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fef0000 end: 000000001fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fff0000 size: 0000000000003000 end: 000000001fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000001fff3000 size: 000000000000d000 end: 0000000020000000 type: 3
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f66c0
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 VIA694                                ) @ 0x000f80c0
[    0.000000] ACPI: RSDT (v001 VIA694 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[    0.000000] ACPI: FADT (v001 VIA694 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[    0.000000] ACPI: MADT (v001 VIA694 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff5880
[    0.000000] ACPI: DSDT (v001 VIA694 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:4 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[    0.000000] Detected 799.699 MHz processor.
[   28.192716] Built 1 zonelists.  Total pages: 130033
[   28.192726] Kernel command line: root=UUID=9fa610e4-4d1f-4a9a-b110-75a826973a62 ro single rootflags=data=writeback elevator=cfq
[   28.193171] mapped APIC to ffffd000 (fee00000)
[   28.193177] mapped IOAPIC to ffffc000 (fec00000)
[   28.193185] Enabling fast FPU save and restore... done.
[   28.193210] Initializing CPU#0
[   28.193340] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   28.194788] Console: colour VGA+ 80x25
[   28.198173] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.198895] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.235116] Memory: 508828k/524224k available (2020k kernel code, 14868k reserved, 893k data, 328k init, 0k highmem)
[   28.235218] virtual kernel memory layout:
[   28.235220]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
[   28.235224]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   28.235227]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
[   28.235231]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   28.235234]       .init : 0xc03df000 - 0xc0431000   ( 328 kB)
[   28.235238]       .data : 0xc02f9114 - 0xc03d8754   ( 893 kB)
[   28.235241]       .text : 0xc0100000 - 0xc02f9114   (2020 kB)
[   28.235691] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.383260] Calibrating delay using timer specific routine.. 1600.93 BogoMIPS (lpj=8004657)
[   28.383470] Security Framework v1.0.0 initialized
[   28.383539] SELinux:  Disabled at boot.
[   28.383629] Mount-cache hash table entries: 512
[   28.383998] CPU: After generic identify, caps: 0183fbff c1c7fbff 00000000 00000000 00000000 00000000 00000000
[   28.384020] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   28.384086] CPU: L2 Cache: 256K (64 bytes/line)
[   28.384146] CPU: After all inits, caps: 0183fbff c1c7fbff 00000000 00000420 00000000 00000000 00000000
[   28.384172] Compat vDSO mapped to ffffe000.
[   28.384238] Remapping vsyscall page to ffffe000
[   28.384312] Checking 'hlt' instruction... OK.
[   28.423355] SMP alternatives: switching to UP code
[   28.423902] Freeing SMP alternatives: 11k freed
[   28.424466] Early unpacking initramfs... done
[   29.129326] ACPI: Core revision 20060707
[   29.136658] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   29.140906] CPU0: AMD Athlon(tm) processor stepping 02
[   29.141087] Total of 1 processors activated (1600.93 BogoMIPS).
[   29.141918] ENABLING IO-APIC IRQs
[   29.142327] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   29.352931] Brought up 1 CPUs
[   29.353594] Booting paravirtualized kernel on bare hardware
[   29.353794] Time:  2:57:32  Date: 03/21/107
[   29.353925] NET: Registered protocol family 16
[   29.354208] EISA bus registered
[   29.354271] ACPI: bus type pci registered
[   29.387385] PCI: PCI BIOS revision 2.10 entry at 0xfb590, last bus=1
[   29.387448] PCI: Using configuration type 1
[   29.387505] Setting up standard PCI resources
[   29.405088] ACPI: Interpreter enabled
[   29.405157] ACPI: Using IOAPIC for interrupt routing
[   29.406544] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   29.406615] PCI: Probing PCI hardware (bus 00)
[   29.406791] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   29.407463] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   29.407531] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[   29.407834] Boot video device is 0000:01:00.0
[   29.407895] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   29.431451] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   29.432638] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   29.433970] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   29.435280] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   29.440461] Linux Plug and Play Support v0.97 (c) Adam Belay
[   29.440545] pnp: PnP ACPI init
[   29.446375] pnp: PnP ACPI: found 13 devices
[   29.446443] PnPBIOS: Disabled by ACPI PNP
[   29.446638] PCI: Using ACPI for IRQ routing
[   29.446701] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   29.469983] NET: Registered protocol family 8
[   29.470044] NET: Registered protocol family 20
[   29.470119] NetLabel: Initializing
[   29.470175] NetLabel:  domain hash size = 128
[   29.470232] NetLabel:  protocols = UNLABELED CIPSOv4
[   29.470321] NetLabel:  unlabeled traffic allowed by default
[   29.471746] PCI: Bridge: 0000:00:01.0
[   29.471807]   IO window: disabled.
[   29.471867]   MEM window: dc000000-ddffffff
[   29.471928]   PREFETCH window: d4000000-dbffffff
[   29.472008] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   29.472066] NET: Registered protocol family 2
[   29.542933] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   29.543204] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   29.543843] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   29.544199] TCP: Hash tables configured (established 16384 bind 8192)
[   29.544263] TCP reno registered
[   29.573000] checking if image is initramfs... it is
[   30.918551] Freeing initrd memory: 6645k freed
[   30.919741] audit: initializing netlink socket (disabled)
[   30.919829] audit(1177124253.580:1): initialized
[   30.920117] VFS: Disk quotas dquot_6.5.1
[   30.920217] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.920394] io scheduler noop registered
[   30.920493] io scheduler anticipatory registered
[   30.920590] io scheduler deadline registered
[   30.920700] io scheduler cfq registered (default)
[   30.920862] Applying VIA southbridge workaround.
[   30.920925] PCI: Enabling Via external APIC routing
[   30.921466] isapnp: Scanning for PnP cards...
[   31.278798] isapnp: No Plug & Play device found
[   31.347651] Real Time Clock Driver v1.12ac
[   31.347828] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.348133] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.348633] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.350142] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.350853] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.351524] mice: PS/2 mouse device common for all mice
[   31.353066] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.353714] input: Macintosh mouse button emulation as /class/input/input0
[   31.353855] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   31.353923] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   31.354421] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   31.354940] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.355008] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.355326] EISA: Probing bus 0 at eisa.0
[   31.355424] Cannot allocate resource for EISA slot 4
[   31.355485] Cannot allocate resource for EISA slot 5
[   31.355545] Cannot allocate resource for EISA slot 6
[   31.355620] EISA: Detected 0 cards.
[   31.386097] TCP cubic registered
[   31.386167] NET: Registered protocol family 1
[   31.386269] Using IPI No-Shortcut mode
[   31.386516] ACPI: (supports S0 S1 S4 S5)
[   31.386866]   Magic number: 3:217:966
[   31.386961]   hash matches device ttyb7
[   31.388135] Freeing unused kernel memory: 328k freed
[   31.391865] Time: tsc clocksource has been installed.
[   31.400500] input: AT Translated Set 2 keyboard as /class/input/input1
[   31.770490] Capability LSM initialized
[   32.984671] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[   32.984780] VP_IDE: chipset revision 6
[   32.984838] VP_IDE: not 100% native mode: will probe irqs later
[   32.984915] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
[   32.984996]     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:DMA, hdb:pio
[   32.985164]     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:DMA, hdd:pio
[   32.986146] Probing IDE interface ide0...
[   33.103213] usbcore: registered new interface driver usbfs
[   33.103351] usbcore: registered new interface driver hub
[   33.103474] usbcore: registered new device driver usb
[   33.105974] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   33.108138] USB Universal Host Controller Interface driver v3.0
[   33.371708] Floppy drive(s): fd0 is 1.44M
[   33.418585] FDC 0 is a post-1991 82077
[   33.481116] hda: ST3200822A, ATA DISK drive
[   33.960885] hdb: HL-DT-ST GCE-8525B, ATAPI CD/DVD-ROM drive
[   34.021472] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   34.021728] Probing IDE interface ide1...
[   34.950438] hdc: MATSHITADVD-ROM SR-8586, ATAPI CD/DVD-ROM drive
[   35.310506] ide1 at 0x170-0x177,0x376 on irq 15
[   35.326825] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 19 (level, low) -> IRQ 16
[   35.331097] eth0: VIA Rhine II at 0x1ec00, 00:50:ba:64:a6:49, IRQ 16.
[   35.332110] eth0: MII PHY found at address 8, status 0x782d advertising 01e1 Link 45e1.
[   35.333523] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   35.333594] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   35.333754] PCI: VIA VLink IRQ fixup for 0000:00:07.2, from 10 to 11
[   35.333844] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   35.334206] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   35.334321] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000d400
[   35.334656] usb usb1: configuration #1 chosen from 1 choice
[   35.334793] hub 1-0:1.0: USB hub found
[   35.334868] hub 1-0:1.0: 2 ports detected
[   35.339436] SCSI subsystem initialized
[   35.354322] libata version 2.20 loaded.
[   35.440295] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   35.440470] PCI: VIA VLink IRQ fixup for 0000:00:07.3, from 10 to 11
[   35.440566] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   35.440672] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   35.440773] uhci_hcd 0000:00:07.3: irq 11, io base 0x0000d800
[   35.441051] usb usb2: configuration #1 chosen from 1 choice
[   35.441166] hub 2-0:1.0: USB hub found
[   35.441240] hub 2-0:1.0: 2 ports detected
[   35.585214] hda: max request size: 512KiB
[   35.587716] hda: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63
[   35.590998] hda: cache flushes supported
[   35.591151]  hda: hda1 hda2 hda3 < hda5 > hda4
[   35.690114] hdb: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   35.690509] Uniform CD-ROM driver Revision: 3.20
[   35.741969] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[   36.003190] Attempting manual resume
[   36.003256] swsusp: Resume From Partition 3:5
[   36.003260] PM: Checking swsusp image.
[   36.003601] PM: Resume from disk failed.
[   36.050591] kjournald starting.  Commit interval 5 seconds
[   36.050687] EXT3-fs: mounted filesystem with writeback data mode.
[   43.698824] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   44.781780] NET: Registered protocol family 17
[   46.378911] parport_pc: VIA 686A/8231 detected
[   46.378921] parport_pc: probing current configuration
[   46.378946] parport_pc: Current parallel port base: 0x378
[   46.379008] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   46.419161] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.424792] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.704911] parport_pc: VIA parallel port: io=0x378, irq=7
[   46.823704] Linux agpgart interface v0.102 (c) Dave Jones
[   47.191465] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   47.198148] agpgart: AGP aperture is 64M @ 0xd0000000
[   47.271161] input: PC Speaker as /class/input/input2
[   47.460510] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   48.178563] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   48.178654] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   48.178814] PCI: VIA VLink IRQ fixup for 0000:00:07.5, from 11 to 10
[   48.179058] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   48.919101] lp0: using parport0 (interrupt-driven).
[   48.987485] Adding 248968k swap on /dev/disk/by-uuid/6b4cb9b1-eb05-481a-8252-b616e4b00642.  Priority:-1 extents:1 across:248968k
[   48.999721] EXT3 FS on hda2, internal journal
[   49.229889] NET: Registered protocol family 10
[   49.230105] lo: Disabled Privacy Extensions
[   49.437199] kjournald starting.  Commit interval 5 seconds
[   49.437627] EXT3 FS on hda4, internal journal
[   49.437639] EXT3-fs: mounted filesystem with writeback data mode.
[   59.808696] eth0: no IPv6 routers present

```

Thanks in advance for any help.

---

### Post by VileTimes on 2007-04-21
This is (might be?) interesting.

I tried to su to my default username while in recovery mode. After a "startx" I received an error message indicating that I did not have the authority to run the X server?

Is this a hint?

---

### Post by skip27 on 2007-04-21
/var/log/messages & dmesg do not indicate any problems. Additionally, and most importantly, since you CAN boot up in recovery mode, i.e. single user mode, it isolates the problem as one being with X.

I'm not sure if the fact that you can't run X as a superuser is a hint of anything; what I think is that it has more to do with the fact that you aren't operating at runlevel 2. To change runlevels, type 'telinit 2', which changes it to runlevel 2 and is the runlevel for running X (in Slackware, Fedora, etc. its runlevel 5).

What do your X logs say? There should be Xorg.0.log in /var/log/ and an Xorg.20.log. Post those. In the meantime, I would recommend stripping your xorg.conf of any unnecessary options and use the 'vesa' driver for now. Make sure to backup your xorg.conf before making any modifications (sudo cp xorg.conf xorg.conf~).

Also, another thing you can try: when booting in recovery mode, telinit 2. Then, 'startx' (no need for sudo). If this works, it probably has something to do with gdm.

Let us know.

---

### Post by Blauer Drakken on 2007-04-21
> **pdrift said:**
> PLZ HELP! i updated to fiesty thru update manager, everything went smoothly until it was time to reboot.When i try to boot, it shows the Ubuntu splash screen then it just goes blank except for the mouse icon. what can i do? i don't want to lose my data thats why i updated instead of doing a full install with fiesty. man i had edgy running like a champ. please someone help!

My room-mate had the exact same problem. His Login screen was black, but he could still log in. Try typing your user name and password accordingly. 

Now he has a new problem. He upgraded to Fiesty Fawn and now it doesn't work anymore.

---

### Post by VileTimes on 2007-04-21
> **skip27 said:**
> /var/log/messages & dmesg do not indicate any problems. Additionally, and most importantly, since you CAN boot up in recovery mode, i.e. single user mode, it isolates the problem as one being with X.

I'm not sure if the fact that you can't run X as a superuser is a hint of anything; what I think is that it has more to do with the fact that you aren't operating at runlevel 2. To change runlevels, type 'telinit 2', which changes it to runlevel 2 and is the runlevel for running X (in Slackware, Fedora, etc. its runlevel 5).

Typing "telinit 2" has the machine hanging at the exact same place.

I don't think I was very clear with my last post. When I boot up into recovery mode, type "su bob", and try  a "startx", I get this error:

```

xauth: creating new authority file /home/bob/.serverauth.3840

X: user not authorized to run the X server, aborting.
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.

```

Of course, I have no problems starting X as root in recovery mode.

I've attached a copy of my Xorg.0.log file, since it was simply too large to post.

Thanks for all of your help!

---

### Post by DoktorSeven on 2007-04-21
Skip recovery mode; when the system boots and freezes, can you hit CTRL+ALT+F2 and get to a text mode login screen?

You should be able to login normally and do a startx from there.  Doing su to your user won't set up the environment correctly and thus you won't be able to do startx.

---

### Post by VileTimes on 2007-04-21
> **DoktorSeven said:**
> Skip recovery mode; when the system boots and freezes, can you hit CTRL+ALT+F2 and get to a text mode login screen?

You should be able to login normally and do a startx from there.  Doing su to your user won't set up the environment correctly and thus you won't be able to do startx.
Ah! I see. I will try this now.

---

### Post by VileTimes on 2007-04-21
That worked! Now how do I get this wonderful login prompt for when I boot the machine?

Hmm.... I did have to edit the tty1 file in /etc/events.d for an autologin script. Could that have anything to do with it? If so, could someone post their tty1 file so I can get it back to how it was originally?

Getting closer ... Thanks! :)

---

### Post by kingmob on 2007-04-22
> **VileTimes said:**
> That worked! Now how do I get this wonderful login prompt for when I boot the machine?

Hmm.... I did have to edit the tty1 file in /etc/events.d for an autologin script. Could that have anything to do with it? If so, could someone post their tty1 file so I can get it back to how it was originally?

Getting closer ... Thanks! :)

I have the exact same problem and i also had an autologin script. There was an error on bootup that says there is a problem with tty1, so i looked there and tty1 had become corrupted. 
However when i change it to a proper (apparently new) format, it will still hang at the rc.local part, but the tty1 error is gone.

Here is my current tty1, various testing with commenting out stuff doesn't change anything.
```

# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on runlevel-2
start on runlevel-3
start on runlevel-4
start on runlevel-5

#stop on runlevel-0
#stop on runlevel-1
#stop on runlevel-6

stop on shutdown
respawn
exec /sbin/getty 38400 tty1
#exec /sbin/getty -n -l /usr/bin/autologin 38400 tty1

```
Just for completeness. Did you also upgrade a command-line only install from edgy to feisty by editing sources.list?
I have this, with an automatic login of the mythtv user and then an automatic openbox/mythtv run. It worked fine before changing the repositories :(.

---

### Post by kingmob on 2007-04-22
Doh, writing that i noticed the - at the runlevels. I put them there because there was a tty.dpk-something file that had it. Looking at tty2 etc though showed it shouldn't be there, so now tty1 looks like this:

```

# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

stop on shutdown
respawn
#exec /sbin/getty 38400 tty1
exec /sbin/getty -n -l /usr/bin/autologin 38400 tty1

```
Now it autologins and x is started. Boot is not very smooth yet though. Still strange kinit errors about sda (i don't even have sata) and boot takes much longer than in edgy. Also some network problems.

---

### Post by VileTimes on 2007-04-22
Thanks, kingmob!

At least now I can log in via tty1 and figure out what's wrong with the autologin script. It just prints a carriage return every few seconds with the blinking cursor.

> **kingmob said:**
> Just for completeness. Did you also upgrade a command-line only install from edgy to feisty by editing sources.list?

Yes, I did. 

Here is my souces.list.

```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
#deb http://ca.archive.ubuntu.com/ubuntu feisty main restricted 
#deb http://ca.archive.ubuntu.com/ubuntu feisty-updates main restricted
#deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
#deb http://ca.archive.ubuntu.com/ubuntu feisty universe multiverse 
#deb http://ca.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
#deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb http://seveas.imbrandon.com feisty-seveas all 

# Ubuntu backports project
# GPG key: 437D05B5
#deb http://ca.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse 

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free 

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.canonical.com feisty-commercial main 

```

---

### Post by desicrew on 2007-04-24
I am having the same problem...and I did all the suggested workarounds.....starting up thru recovery mode gets me into X under root but, when logging in normally i get a white screen...moreover when i press control-alt-F2 and attempt to type startx through my user login this happens...[IMG]http://www.asianvibrations.com/crazyImages/error.jpg[/IMG]

- sorry for the blurry image but taking a picture of my screen was the only thing i could think of!

*just wanted to add that I had edgy working PERFECTLY (with compiz before the upgrade)

---

### Post by desicrew on 2007-04-24
well i figured out my own solution.  It's an annoying one but it worked....i "simply" deleted .gconf and .gconfd folders from home folder (view hidden files to make them visible) and i was in.  Sure all my old settings were lost but atleast I am in ubuntu right now =)

---

### Post by Michl on 2007-04-24
I have been pouring over all these threads about upgrading to Feisty and the message is clear:  unless you are adventurous, have lots of time, or are an experienced ubuntu user, do not upgrade.

Michl

---

### Post by VileTimes on 2007-04-24
I finally got autologin working following [_this guide_](http://ubuntuforums.org/showthread.php?p=1782383#post1782383"). Make sure to scroll down for [_my reply_]("http://ubuntuforums.org/showpost.php?p=2528709&postcount=2") to get this working with Feisty Fawn.

---

### Post by kingmob on 2007-04-25
> **Michl said:**
> I have been pouring over all these threads about upgrading to Feisty and the message is clear:  unless you are adventurous, have lots of time, or are an experienced ubuntu user, do not upgrade.

Michl
Most, if not all problems come from people who have been fiddling around with their edgy install. These people are at least adventurous and won't be scared if x doesn't run after an update.
On my desktop that has only 'light' fiddling, upgrading went fine. I think simple users have nothing to fear when upgrading.

---


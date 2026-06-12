---
title: "Random Freeze Dont know where to start"
date: 2008-06-03
forum: General Help
---

### Post by iitywygms on 2008-06-03
computer=Presario 2100
Hardy heron

lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
kevin@kevin-laptop:~$ 

I dont know where to start.  Every other day or so the computer will freeze.  The keyboard still works and so does the mouse.  I cant click on the menu or any icon on the desktop, all i can do is cntl-alt-backspace.  When I do that I get a Ext-3 error.  So I run force a diskcheck after a hard reboot.  No errors are reported.
I am not doing anything in particular at the time of the freeze.  Sometimes it happens while I am surfing the net using firefox (beta 3-5)  Other times it will be frozen when I open the lid after it has been idol for some time.

I ran a memory check from a live cd, no errors.

Where should I start? What info can I provide?

Thanks for the help.

---

### Post by Sam Lars on 2008-06-03
Could you be more specific about this Ext3 error?  It sounds like the hard disk is having a problem.

---

### Post by iaculallad on 2008-06-03
Just a toss up question: are you using compiz?

---

### Post by iitywygms on 2008-06-03
I dont remember specifically.  its close to ext-3 error, error reading file (some numbers i dont remember)
I run chkdisk with no errors reported.

---

### Post by iitywygms on 2008-06-03
> **iaculallad said:**
> Just a toss up question: are you using compiz?

No compiz or any fancy graphics running.

---

### Post by iitywygms on 2008-06-05
bump

---

### Post by Sam Lars on 2008-06-05
Could you find out what the error is?  It seems to be related to the problem you have.

---

### Post by iitywygms on 2008-06-12
Okay, it happened again.

Here is the error messages:

[12077.6977283] ext3-fs error (device hda1) ext3_get_inode_loc, unable to read i node block - indode =6149794, block=1220815

Then below that.

[121100.471163] buffer I/O error on dev hda1, logical block 10780672

So, I run a disk check, again, no errors reported. (Booted from live cd)

I dual boot to windblows and never have a problem there.  Any ideas?

---

### Post by aldolat on 2008-06-12
I have a very similar problem with Hardy Heron. Unlike iitywygms, I can't use my keyboard to reboot my GUI (e.g. Gtrl+Alt+Backspace): I have to force an hardware reboot. The freeze happens randomly.

So I reinstalled Gutsy and no freeze happens: all is fine. Only Firefox 3 RC2 crashes when flash is used in webpages; Opera works very well and fast and never crashed.

Why I can use **Gutsy with no problems** (except FF) and not Hardy? Is Hardy the problem? If the problem were an hardware issue (memory, HD, etc.), I should have it in Gutsy too. o_O

---

### Post by iitywygms on 2008-06-12
Results of disk check. Anybody have any idea what is going on? It just happened again.  :confused:

ubuntu@ubuntu:~$ sudo e2fsck -f -v /dev/hda1
e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  184221 inodes used (2.57%)
    2027 non-contiguous inodes (1.1%)
         # of inodes with ind/dind/tind blocks: 8361/109/0
 1308726 blocks used (9.14%)
       0 bad blocks
       1 large file

  140374 regular files
   22533 directories
     127 character device files
      26 block device files
       2 fifos
     464 links
   21145 symbolic links (19469 fast symbolic links)
       5 sockets
--------
  184676 files
ubuntu@ubuntu:~$ sudo e2fsck -c /dev/hda1
e2fsck 1.40-WIP (14-Nov-2006)
Checking for bad blocks (read-only test): done                                
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/hda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/hda1: 184221/7162176 files (1.1% non-contiguous), 1308726/14321939 blocks
ubuntu@ubuntu:~$

---

### Post by iitywygms on 2008-06-13
Bump

---

### Post by tech0007 on 2008-06-13
does it freeze when you go to recovery mode? can you post the output of tail /var/log/message when your system hangs? i believe this is partly due to the graphics driver. try specifying vesa in /etc/X11/xorg.conf.

---

### Post by iitywygms on 2008-06-13
It only hangs about once every 3 days or so.  I am not going to be in recovery mode for that long.  I will post the output of error logs when it happens again.

---

### Post by iitywygms on 2008-06-14
kevin@kevin-laptop:/var/log$ tail /var/log/messages
Jun 13 20:54:16 kevin-laptop -- MARK --
Jun 13 21:14:16 kevin-laptop -- MARK --
Jun 13 21:34:16 kevin-laptop -- MARK --
Jun 13 21:54:16 kevin-laptop -- MARK --
Jun 13 22:14:16 kevin-laptop -- MARK --
Jun 13 22:34:16 kevin-laptop -- MARK --
Jun 13 22:54:16 kevin-laptop -- MARK --
Jun 13 23:14:16 kevin-laptop -- MARK --
Jun 13 23:34:16 kevin-laptop -- MARK --
Jun 13 23:54:16 kevin-laptop -- MARK --

Is this what you are looking for?
This is becoming a real bummer.  I always liked ubuntu because of the stability, but this is getting crazy.  

IS THERE ANY PLACE THAT HAS A ERROR FILE THAT MIGHT SHED SOME LIGHT ON THIS ISSUE?
Here is dmesg just because

kevin@kevin-laptop:/var/log$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 4 16:35:01 UTC 2008 (Ubuntu 2.6.24-19.33-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bef0000 (usable)
[    0.000000]  BIOS-e820: 000000001bef0000 - 000000001beff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001beff000 - 000000001bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bf00000 - 000000001c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 446MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 114416) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114416
[    0.000000]   HighMem    114416 ->   114416
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114416
[    0.000000] On node 0 totalpages: 114416
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 861 pages used for memmap
[    0.000000]   Normal zone: 109459 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7290 checksum 0
[    0.000000] ACPI: RSDP 000F7290, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1BEF8B67, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 1BEFEE2B, 0074 (r1 ATI    Raptor    6040000 ATI     F4240)
[    0.000000] ACPI: DSDT 1BEF8B97, 6294 (r1    ATI U1_M1535  6040000 MSFT  100000D)
[    0.000000] ACPI: FACS 1BEFFFC0, 0040
[    0.000000] ACPI: BOOT 1BEFEE9F, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 1BEFEEC7, 0139 (r1 PTLTD  POWERNOW  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3fc0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 113523
[    0.000000] Kernel command line: root=UUID=674156e2-7627-46e7-b593-bc283659273e ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0138d000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2120.141 MHz processor.
[   16.231595] Console: colour VGA+ 80x25
[   16.231600] console [tty0] enabled
[   16.232187] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.232537] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.251987] Memory: 441604k/457664k available (2177k kernel code, 15460k reserved, 1006k data, 368k init, 0k highmem)
[   16.251996] virtual kernel memory layout:
[   16.251997]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   16.251999]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.252000]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[   16.252001]     lowmem  : 0xc0000000 - 0xdbef0000   ( 446 MB)
[   16.252002]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   16.252003]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   16.252004]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   16.252008] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.252073] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   16.331945] Calibrating delay using timer specific routine.. 4242.74 BogoMIPS (lpj=8485483)
[   16.331990] Security Framework initialized
[   16.332002] SELinux:  Disabled at boot.
[   16.332032] AppArmor: AppArmor initialized
[   16.332038] Failure registering capabilities with primary security module.
[   16.332051] Mount-cache hash table entries: 512
[   16.332245] Initializing cgroup subsys ns
[   16.332253] Initializing cgroup subsys cpuacct
[   16.332267] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   16.332278] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.332281] CPU: L2 Cache: 512K (64 bytes/line)
[   16.332285] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000 00000000
[   16.332299] Compat vDSO mapped to ffffe000.
[   16.332318] Checking 'hlt' instruction... OK.
[   16.348250] SMP alternatives: switching to UP code
[   16.349652] Freeing SMP alternatives: 11k freed
[   16.349816] Early unpacking initramfs... done
[   16.688160] ACPI: Core revision 20070126
[   16.688340] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.690461] ACPI: setting ELCR to 0200 (from 0e28)
[   16.692401] CPU0: AMD mobile AMD Athlon(tm) XP2800+ stepping 00
[   16.692409] SMP motherboard not detected.
[   16.692412] Local APIC not detected. Using dummy APIC emulation.
[   16.692497] Brought up 1 CPUs
[   16.692531] CPU0 attaching sched-domain:
[   16.692535]  domain 0: span 01
[   16.692537]   groups: 01
[   16.692858] net_namespace: 64 bytes
[   16.692870] Booting paravirtualized kernel on bare hardware
[   16.693353] Time:  7:37:44  Date: 06/14/08
[   16.693401] NET: Registered protocol family 16
[   16.693661] EISA bus registered
[   16.693679] ACPI: bus type pci registered
[   16.706076] PCI: PCI BIOS revision 2.10 entry at 0xfd87b, last bus=2
[   16.706079] PCI: Using configuration type 1
[   16.706090] Setting up standard PCI resources
[   16.708199] ACPI: EC: Look up EC in DSDT
[   16.737049] ACPI: Interpreter enabled
[   16.737053] ACPI: (supports S0 S3 S4 S5)
[   16.737068] ACPI: Using PIC for interrupt routing
[   16.743034] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[   16.743037] ACPI: EC: driver started in poll mode
[   16.743084] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.743473] PCI quirk: region 8000-803f claimed by ali7101 ACPI
[   16.743477] PCI quirk: region 8040-805f claimed by ali7101 SMB
[   16.743686] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.743753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   16.745461] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 *10)
[   16.745573] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 *11)
[   16.745681] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 10) *0, disabled.
[   16.745790] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 10) *9
[   16.745897] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 10) *0, disabled.
[   16.746004] ACPI: PCI Interrupt Link [LNKF] (IRQs 7 11) *0, disabled.
[   16.746112] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 6 10)
[   16.746219] ACPI: PCI Interrupt Link [LNKH] (IRQs *5 7)
[   16.746325] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 6 10) *9
[   16.746451] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.746498] pnp: PnP ACPI init
[   16.746507] ACPI: bus type pnp registered
[   16.749476] pnp: PnP ACPI: found 11 devices
[   16.749478] ACPI: ACPI bus type pnp unregistered
[   16.749484] PnPBIOS: Disabled by ACPI PNP
[   16.749787] PCI: Using ACPI for IRQ routing
[   16.749791] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.755229] NET: Registered protocol family 8
[   16.755232] NET: Registered protocol family 20
[   16.755341] AppArmor: AppArmor Filesystem Enabled
[   16.759111] Time: tsc clocksource has been installed.
[   16.767138] system 00:07: ioport range 0x40b-0x40b has been reserved
[   16.767141] system 00:07: ioport range 0x480-0x48f has been reserved
[   16.767144] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   16.767146] system 00:07: ioport range 0x4d6-0x4d6 has been reserved
[   16.767149] system 00:07: ioport range 0x8000-0x807f could not be reserved
[   16.767152] system 00:07: ioport range 0xff00-0xff01 has been reserved
[   16.767155] system 00:07: ioport range 0x8004-0x8005 has been reserved
[   16.767158] system 00:07: ioport range 0xfe00-0xfefe has been reserved
[   16.767161] system 00:07: iomem range 0xd0400000-0xd0400fff has been reserved
[   16.797567] PCI: Bridge: 0000:00:01.0
[   16.797570]   IO window: 9000-9fff
[   16.797573]   MEM window: d0100000-d01fffff
[   16.797577]   PREFETCH window: e0000000-efffffff
[   16.797581] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[   16.797584]   IO window: 00001000-000010ff
[   16.797587]   IO window: 00001400-000014ff
[   16.797591]   PREFETCH window: 20000000-23ffffff
[   16.797594]   MEM window: 24000000-27ffffff
[   16.797617] PCI: Enabling device 0000:00:0a.0 (0000 -> 0003)
[   16.797776] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[   16.797781] PCI: setting IRQ 11 as level-triggered
[   16.797784] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[   16.797792] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   16.797807] NET: Registered protocol family 2
[   16.835108] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   16.835376] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   16.835731] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   16.836079] TCP: Hash tables configured (established 16384 bind 16384)
[   16.836083] TCP reno registered
[   16.847111] checking if image is initramfs... it is
[   17.298098] Switched to high resolution mode on CPU 0
[   17.466465] Freeing initrd memory: 7331k freed
[   17.466748] Simple Boot Flag at 0x36 set to 0x1
[   17.467377] audit: initializing netlink socket (disabled)
[   17.467403] audit(1213429064.196:1): initialized
[   17.469829] VFS: Disk quotas dquot_6.5.1
[   17.469919] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.470098] io scheduler noop registered
[   17.470100] io scheduler anticipatory registered
[   17.470103] io scheduler deadline registered
[   17.470113] io scheduler cfq registered (default)
[   17.470130] ATI Northbridge, reserving I/O ports 0x3b0 to 0x3bb.
[   17.685191] Activating ISA DMA hang workarounds.
[   17.685205] Boot video device is 0000:01:05.0
[   17.685525] isapnp: Scanning for PnP cards...
[   17.952052] isapnp: No Plug & Play device found
[   17.984831] Real Time Clock Driver v1.12ac
[   17.984981] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.985143] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.985968] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.986426] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 3
[   17.986430] PCI: setting IRQ 3 as level-triggered
[   17.986434] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKG] -> GSI 3 (level, low) -> IRQ 3
[   17.986446] ACPI: PCI interrupt for device 0000:00:08.0 disabled
[   17.987294] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.987382] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   17.987503] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   17.990966] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.990973] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.000592] mice: PS/2 mouse device common for all mice
[   18.000724] EISA: Probing bus 0 at eisa.0
[   18.000735] Cannot allocate resource for EISA slot 1
[   18.000762] Cannot allocate resource for EISA slot 8
[   18.000765] EISA: Detected 0 cards.
[   18.000770] cpuidle: using governor ladder
[   18.000771] cpuidle: using governor menu
[   18.000968] NET: Registered protocol family 1
[   18.001004] Using IPI No-Shortcut mode
[   18.001056] registered taskstats version 1
[   18.001165]   Magic number: 12:372:622
[   18.001328]   hash matches device ptybf
[   18.001517] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.001520] EDD information not available.
[   18.002245] Freeing unused kernel memory: 368k freed
[   18.040464] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.232588] fuse init (API version 7.9)
[   19.257205] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   19.260122] ACPI: Thermal Zone [THRM] (80 C)
[   19.260756] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   19.957495] usbcore: registered new interface driver usbfs
[   19.957534] usbcore: registered new interface driver hub
[   19.968253] usbcore: registered new device driver usb
[   19.978972] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   19.978981] PCI: setting IRQ 10 as level-triggered
[   19.978984] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   19.979017] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x02, vendor 0x4243)
[   19.979022] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[   19.979027] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x01, vendor 0x4243)
[   19.979031] ssb: Core 3 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[   19.979036] ssb: Core 4 found: PCI (cc 0x804, rev 0x07, vendor 0x4243)
[   19.979040] ssb: Core 5 found: IEEE 802.11 (cc 0x812, rev 0x04, vendor 0x4243)
[   19.979042] ssb: Ignoring additional 802.11 core
[   19.982393] ssb: Sonics Silicon Backplane found on PCI device 0000:00:09.0
[   19.996408] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.996791] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 10
[   19.996796] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKU] -> GSI 10 (level, low) -> IRQ 10
[   19.996820] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   19.997311] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   19.997335] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0002000
[   20.036334] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.036346] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.054420] usb usb1: configuration #1 chosen from 1 choice
[   20.054456] hub 1-0:1.0: USB hub found
[   20.054469] hub 1-0:1.0: 4 ports detected
[   20.057354] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[   20.057358]   originally by Donald Becker <becker@scyld.com>
[   20.057359]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[   20.156366] alim15x3: ATI Radeon IGP Northbridge is not yet fully tested.
[   20.156376] ALI15X3: IDE controller (0x10b9:0x5229 rev 0xc4) at  PCI slot 0000:00:10.0
[   20.156412] ACPI: Unable to derive IRQ for device 0000:00:10.0
[   20.156424] ALI15X3: not 100% native mode: will probe irqs later
[   20.156446]     ide0: BM-DMA at 0x8080-0x8087, BIOS settings: hda:DMA, hdb:pio
[   20.156467]     ide1: BM-DMA at 0x8088-0x808f, BIOS settings: hdc:pio, hdd:pio
[   20.156482] Probing IDE interface ide0...
[   20.230921] FDC 0 is a post-1991 82077
[   21.114147] hda: TOSHIBA MK6025GAS, ATA DISK drive
[   21.114206] hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[   21.114258] hda: UDMA/100 mode selected
[   21.114337] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   21.163218] Probing IDE interface ide1...
[   22.567085] hdc: SONY CD-RW/DVD-ROM CRX830E, ATAPI CD/DVD-ROM drive
[   22.567139] hdc: host max PIO5 wanted PIO255(auto-tune) selected PIO4
[   22.567314] hdc: MWDMA2 mode selected
[   22.567439] ide1 at 0x170-0x177,0x376 on irq 15
[   22.575851] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   22.575861] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   22.577795] natsemi eth0: NatSemi DP8381[56] at 0xd0005000 (0000:00:12.0), 00:0f:20:21:fe:37, IRQ 11, port TP.
[   22.580078] SCSI subsystem initialized
[   22.590577] libata version 3.00 loaded.
[   22.609136] hda: max request size: 128KiB
[   22.610463] hda: 117210240 sectors (60011 MB), CHS=65535/16/63
[   22.610532] hda: cache flushes supported
[   22.610580]  hda: hda1 hda2 < hda5 >
[   22.697565] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[   22.697577] Uniform CD-ROM driver Revision: 3.20
[   23.251709] Attempting manual resume
[   23.251716] swsusp: Resume From Partition 3:5
[   23.251718] PM: Checking swsusp image.
[   23.271335] PM: Resume from disk failed.
[   23.322214] EXT3-fs: INFO: recovery required on readonly filesystem.
[   23.322223] EXT3-fs: write access will be enabled during recovery.
[   34.634372] kjournald starting.  Commit interval 5 seconds
[   34.634406] EXT3-fs: hda1: orphan cleanup on readonly fs
[   34.634416] ext3_orphan_cleanup: deleting unreferenced inode 5379815
[   34.634464] EXT3-fs: hda1: 1 orphan inode deleted
[   34.634466] EXT3-fs: recovery complete.
[   34.659387] EXT3-fs: mounted filesystem with ordered data mode.
[   49.466455] Linux agpgart interface v0.102
[   49.526484] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   49.566305] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   49.879813] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:0024]
[   49.879837] Yenta: Using CSCINT to route CSC interrupts to PCI
[   49.879839] Yenta: Routing CardBus interrupts to PCI
[   49.879843] Yenta TI: socket 0000:00:0a.0, mfunc 0x01111112, devctl 0x64
[   49.965455] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   50.109429] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[   50.109437] Socket status: 30000006
[   50.165126] agpgart: Detected Ati IGP320/M chipset
[   50.174043] agpgart: AGP aperture is 64M @ 0xd4000000
[   50.174115] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   50.174121] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[   50.200171] input: Power Button (FF) as /devices/virtual/input/input3
[   50.212850] ACPI: Power Button (FF) [PWRF]
[   50.213054] input: Power Button (CM) as /devices/virtual/input/input4
[   50.224719] ACPI: Power Button (CM) [PWRB]
[   50.224819] input: Lid Switch as /devices/virtual/input/input5
[   50.225893] ACPI: Lid Switch [LID]
[   50.245144] ACPI: AC Adapter [ACAD] (on-line)
[   50.281978] ACPI: Battery Slot [BAT1] (battery present)
[   50.544326] parport_pc 00:09: reported by Plug and Play ACPI
[   50.544403] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   50.975864] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input6
[   51.007174] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   52.104954] b43legacy-phy0: Broadcom 4306 WLAN found
[   52.140691] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   52.140717] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   52.164649] b43legacy-phy0 debug: Radio initialized
[   52.181160] phy0: Selected rate control algorithm 'simple'
[   52.509190] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[   52.509199] PCI: setting IRQ 5 as level-triggered
[   52.509202] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[   52.937326] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[   52.974136] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   54.444738] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[   54.446892] cs: IO port probe 0x3e0-0x4ff: clean.
[   54.447745] cs: IO port probe 0x820-0x8ff: clean.
[   54.448578] cs: IO port probe 0xc00-0xcf7: clean.
[   54.449555] cs: IO port probe 0xa00-0xaff: clean.
[   55.226188] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2061: AC'97 1 does not respond - RESET
[   55.242151] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2070: AC'97 1 access is not valid [0xffffffff], removing mixer.
[   55.242164] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ali5451/ali5451.c:1927: ali mixer 1 creating error.
[   56.243680] lp0: using parport0 (interrupt-driven).
[   56.321141] Adding 1317288k swap on /dev/hda5.  Priority:-1 extents:1 across:1317288k
[   56.873817] EXT3 FS on hda1, internal journal
[   58.100699] ip_tables: (C) 2000-2006 Netfilter Core Team
[   58.694735] No dock devices found.
[   58.919332] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[   58.925571] powernow: No PST tables match this cpuid (0x7a0)
[   58.925574] powernow: This is indicative of a broken BIOS.
[   58.925576] powernow: Trying ACPI perflib
[   58.925640] powernow: Minimum speed 530 MHz. Maximum speed 2120 MHz.
[   59.336175] apm: BIOS not found.
[   59.426664] ppdev: user-space parallel port driver
[   59.721464] audit(1213429107.637:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4690 profile="/usr/sbin/cupsd" namespace="default"
[  101.264343] Marking TSC unstable due to: cpufreq changes.
[  101.270843] Time: acpi_pm clocksource has been installed.
[  101.434787] Clocksource tsc unstable (delta = -69382338 ns)
[   60.484144] eth0: DSPCFG accepted after 0 usec.
[   60.595645] Bluetooth: Core ver 2.11
[   60.596410] NET: Registered protocol family 31
[   60.596413] Bluetooth: HCI device and connection manager initialized
[   60.596419] Bluetooth: HCI socket layer initialized
[   60.640969] Bluetooth: L2CAP ver 2.9
[   60.640977] Bluetooth: L2CAP socket layer initialized
[   60.692802] Bluetooth: RFCOMM socket layer initialized
[   60.692835] Bluetooth: RFCOMM TTY layer initialized
[   60.692837] Bluetooth: RFCOMM ver 1.8
[   60.986001] b43legacy-phy0 debug: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   61.088449] b43legacy-phy0 debug: Chip initialized
[   61.089094] b43legacy-phy0 debug: 30-bit DMA initialized
[   61.089220] b43legacy-phy0 debug: Wireless interface started
[   61.089226] b43legacy-phy0 debug: Adding Interface type 2
[   62.208940] [drm] Initialized drm 1.1.0 20060810
[   62.222400] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   62.222410] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   62.222845] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[  251.759132] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  251.759170] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  251.759225] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[  253.053968] [drm] Setting GART location based on new memory map
[  253.054039] [drm] writeback test succeeded in 1 usecs
[   76.435440] NET: Registered protocol family 10
[   76.435736] lo: Disabled Privacy Extensions
[   76.436160] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   76.436587] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   80.295237] NET: Registered protocol family 17
[  103.643867] wlan0: Initial auth_alg=0
[  103.643877] wlan0: authenticate with AP 00:11:50:05:1e:fd
[  103.645466] wlan0: RX authentication from 00:11:50:05:1e:fd (alg=0 transaction=2 status=0)
[  103.645471] wlan0: authenticated
[  103.645475] wlan0: associate with AP 00:11:50:05:1e:fd
[  103.647904] wlan0: RX AssocResp from 00:11:50:05:1e:fd (capab=0x411 status=0 aid=3)
[  103.647909] wlan0: associated
[  103.647915] wlan0: switched to short barker preamble (BSSID=00:11:50:05:1e:fd)
[  103.648207] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  103.658492] b43legacy-phy0 debug: Using software based encryption for mac: 00:11:50:05:1e:fd
[  103.666432] b43legacy-phy0 debug: Using software based encryption for mac: ff:ff:ff:ff:ff:ff
[  354.579199] wlan0: no IPv6 routers present
[  426.843193] b43legacy-phy0 debug: Using software based encryption for mac: ff:ff:ff:ff:ff:ff
kevin@kevin-laptop:/var/log$

---

### Post by iitywygms on 2008-06-15
bump

---

### Post by mgbridges on 2008-06-16
> **aldolat said:**
> I have a very similar problem with Hardy Heron. Unlike iitywygms, I can't use my keyboard to reboot my GUI (e.g. Gtrl+Alt+Backspace): I have to force an hardware reboot. The freeze happens randomly.

So I reinstalled Gutsy and no freeze happens: all is fine. Only Firefox 3 RC2 crashes when flash is used in webpages; Opera works very well and fast and never crashed.

Why I can use **Gutsy with no problems** (except FF) and not Hardy? Is Hardy the problem? If the problem were an hardware issue (memory, HD, etc.), I should have it in Gutsy too. o_O

This sounds exactly like my situation. I too reverted to Gutsy and everything has been fine.

This really needs some focus to get it sorted out - it sounds like a non-trivial issue.

Martin

---

### Post by iitywygms on 2008-06-17
I am going to set up a dual boot and try gutsy for a while unless someone has some good advice.

---

### Post by greco8523 on 2008-06-18
Random freezing is a sign that your hard drive is on the way out, it may not come up with errors with the utilities your using. But I would suggest that you Backup your data now!!! Maxtor or a new Seagate?

---

### Post by iitywygms on 2008-06-18
> **greco8523 said:**
> Random freezing is a sign that your hard drive is on the way out, it may not come up with errors with the utilities your using. But I would suggest that you Backup your data now!!! Maxtor or a new Seagate?

I agree, BUT I am now using gutsy with no errors. Granted, it has only been just one day.

---

### Post by iitywygms on 2008-06-20
2 days with Gutsy and no issues. ???????????????????????

---

### Post by iitywygms on 2008-06-20
3 days with gutsy and no issues.  This is a problem with Hardy.

---

### Post by bpont on 2008-06-21
> **iitywygms said:**
> 3 days with gutsy and no issues.  This is a problem with Hardy.

I am having the exact same random system freezes as you, but with no keyboard or mouse access and am forced to hard reboot.

Will also revert to gutsy, and yes, hardy is undeniably the shittiest release ubuntu has ever put out.  Linux systems are NOT supposed to behave this way...this kind of crap is why I ditched MS Windows in the first place!

---

### Post by ushills on 2008-06-21
I have the same issue with Hardy but only when trying to log back in after a period away from the screen.

Mouse responds but have to do a hard re-boot to get back in.

---

### Post by TwiStEr55 on 2008-06-21
I have this problem as well ... it always happens after different amounts of time. Sometimes after a day, sometimes after a hour has passed ...

I mostly play music on it and I notic the freezing, when the music stops. I move the mouse and everything continues, for about 2 seconds .. then Ill have to move the mouse again .... ALT+CTL+BACKSPACE will completly freeze the system and hard reboot is required ... this really sucks

---

### Post by iitywygms on 2008-06-24
One week no issues with Gutsy.  I wish someone could figure out what the issue was.  I agree, I left windblows because of stability issues.  I realize this is free, but linux (ubuntu) has always been solid until now.:confused:

---

### Post by aimpau on 2008-06-27
This is ALL OF OUR PROBLEM:

[ 59.721464] audit(1213429107.637:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4690 profile="/usr/sbin/cupsd" namespace="default"

try the suggestions here:
[http://ubuntuforums.org/showthread.php?t=787166&highlight=inode_permission](http://ubuntuforums.org/showthread.php?t=787166&highlight=inode_permission)

---

### Post by iitywygms on 2008-07-02
> **aimpau said:**
> This is ALL OF OUR PROBLEM:

[ 59.721464] audit(1213429107.637:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4690 profile="/usr/sbin/cupsd" namespace="default"

try the suggestions here:
[http://ubuntuforums.org/showthread.php?t=787166&highlight=inode_permission](http://ubuntuforums.org/showthread.php?t=787166&highlight=inode_permission)



Thanks but no help.  I tried this although I have no problems with cups.
How can I log what the problem is?  Is there a way to monitor and record what is going on?

---


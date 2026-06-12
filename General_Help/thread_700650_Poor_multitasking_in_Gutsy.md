---
title: "Poor multitasking in Gutsy"
date: 2008-02-18
forum: General Help
---

### Post by DrMega on 2008-02-18
I've seen a bug report about poor multitasking in Hardy, but I'm using Gutsy and it is not great at multitasking. I am wondering if it is something specific to my setup or if it is a general issue.

My machine's spec is not great I'll admit. It is as follows:

AMD Duron 1.8GHz
512MB RAM
60GB hard disk (total) of which about 20GB is spare and available to Ubuntu.
nVidia N6200 258MB graphics card.

What I've noticed is that if I start downloading a large file, I pretty much can't do anything else without  frequent annoying pauses in responsiveness.

I know that file downloading is quite a hit on my network resources, but it shouldn't be much of a hit on CPU, RAM and hard disk, so I can't understand why it should have such an impact on multitasking.

I was always on the understanding that Linux (in general) was ace at multitasking.

Any ideas?

---

### Post by Linux_Man on 2008-02-18
What application are you using to download your file in? Firefox? wget? Or something else? It sounds more like a bug in your application then anything else.

---

### Post by bwhite82 on 2008-02-18
Your specs are completely fine, I'm not sure why you have an issue multitasking. It may very well be a bug, as you described. I've had better luck with Feisty myself, you could use that until Hardy is released. BTW, could you provide a link to the bug report? Thanks.

-Cheers

---

### Post by DrMega on 2008-02-18
I mostly use FireFox, but it still happens if I'm installing apps via Synaptic.

---

### Post by DrMega on 2008-02-18
> **Soldierboy said:**
> Your specs are completely fine, I'm not sure why you have an issue multitasking. It may very well be a bug, as you described. I've had better luck with Feisty myself, you could use that until Hardy is released. BTW, could you provide a link to the bug report? Thanks.

-Cheers

It's discussed in this thread:
[http://ubuntuforums.org/showthread.php?t=699186&highlight=multitasking]("http://ubuntuforums.org/showthread.php?t=699186&highlight=multitasking")

---

### Post by chrisccoulson on 2008-02-18
I find that desktop responsiveness drops off with high disk I/O. Are you sure your problems aren't with disk bandwidth? I'm not sure what tools are available to check this, but does your hard drive light flash a lot during the periods when responsiveness drops off? If you run top, what process is using most CPU bandwidth?

Are you running Tracker? (The answer is yes unless you have intentionally disabled it)
Is DMA enabled for your hard drive?

---

### Post by DrMega on 2008-02-18
> **chrisccoulson said:**
> I find that desktop responsiveness drops off with high disk I/O. Are you sure your problems aren't with disk bandwidth? I'm not sure what tools are available to check this, but does your hard drive light flash a lot during the periods when responsiveness drops off? If you run top, what process is using most CPU bandwidth?

Disk IO is (or should be) fine. My Internet connection speed is only 4 MBits, my ethernet card can easily handle that (100MBit) and my disks should easily handle that too.


> **chrisccoulson said:**
> Are you running Tracker? (The answer is yes unless you have intentionally disabled it)

I haven't really changed any default settings, so I guess the answer is yes, but my ISP blocks all sorts so I doubt if this is having any effect. That said, how do I disable it just in case?

> **chrisccoulson said:**
> Is DMA enabled for your hard drive?

No idea. How do I check?

thanks.

---

### Post by chrisccoulson on 2008-02-18
Yes, disk IO *should* be ok, but *is* it actually ok? There's obviously something not right, else you wouldn't be seeing this poor performance.

To disable Tracker, go to System -> Preferences -> Search and Indexing. Uncheck 'Enable indexing' and 'Enable watching'.

What is the output of:
```
sudo hdparm /dev/hd*
```
..where '*' is 'a', 'b', 'c' or whatever your disk is.

---

### Post by DrMega on 2008-02-19
[QUOTE=chrisccoulson;4357756
What is the output of:
```
sudo hdparm /dev/hd*
```
..where '*' is 'a', 'b', 'c' or whatever your disk is.[/QUOTE]

If I try it with hda or hdb it tells me no such file or directly. I browse my file system I can't see my hard disks by such names.

---

### Post by chrisccoulson on 2008-02-19
What does this say?
```
cat /etc/mtab
```

---

### Post by DrMega on 2008-02-19
> **chrisccoulson said:**
> What does this say?
```
cat /etc/mtab
```

```

/dev/sdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0

```

This is weird, I'm no Linux guru but shouldn't I see my hard disks mentioned in there?

---

### Post by jocko on 2008-02-19
> **DrMega said:**
> ```

[COLOR=Red] /dev/sdb1 / ext3 rw,errors=remount-ro 0 0[/COLOR]
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0

```[COLOR=Red]This is weird, I'm no Linux guru but shouldn't I see my hard disks mentioned in there?[/COLOR]

yep. /dev/sdb1 is a hard disk containing your root (/) file system. Do you have more disks?.

---

### Post by DrMega on 2008-02-19
> **jocko said:**
> yep. /dev/sdb1 is a hard disk containing your root (/) file system. Do you have more disks?.

I have two physical hard disks, one is given to Ubuntu, the other to Windows. Both have more than one partition. When I think about it though, the Windows disk is not mounted by default, so I'm not concerned that only one disk shows.

I ran hdparms against sdb1. This is what I got:

```

/dev/sdb1:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 2495/255/63, sectors = 38331027, start = 63

```

I'm a bit concerned about that IO_support = 0 (default 16-bit) line. Shouldn't it be 32 bit? It is a very very old disk that I salvaged out of a machine that I'd scrapped. I know its not the fastest disk but I do get serious slowdowns. My CD drive is also very very slow. Does this give any clues (my CD drive is nice and fast in Windows so I know it is capable).

---

### Post by chrisccoulson on 2008-02-19
Is it a SATA disk, or PATA disk?

What are the results of this:
```
sudo hdparm -tT /dev/sdb
```

---

### Post by DrMega on 2008-02-19
> **chrisccoulson said:**
> Is it a SATA disk, or PATA disk?

What are the results of this:
```
sudo hdparm -tT /dev/sdb
```

I's an old IDE 20GB job.

Here's the output from that command:

```

/dev/sdb:
 Timing cached reads:   554 MB in  2.01 seconds = 276.09 MB/sec
 Timing buffered disk reads:   72 MB in  3.02 seconds =  23.85 MB/sec

```

23MB/sec seems slow even for an old disk.

---

### Post by chrisccoulson on 2008-02-19
I don't think those numbers are too bad for an old disk. Here is the output from mine (this is a newer SATA disk though):
```
/dev/sdb:
 Timing cached reads:   1670 MB in  2.00 seconds = 834.82 MB/sec
 Timing buffered disk reads:  188 MB in  3.03 seconds =  62.05 MB/sec

```

The reason I asked you to check this is because some people seem to be having an issue with DMA on PATA disks (see [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/110636"). I don't think this is your problem though

I think you need to monitor top when you notice responsiveness drop, just to see if there is something eating up all your CPU power. Have you noticed anything strange in any of your system logs?

Posting the output of dmesg here might help (wrapped in CODE tags). I might not be able to help directly, but someone on here might spot something odd.

Have you made any changes to the standard install (I'm thinking changes to runlevel configuration, fstab, menu.lst etc)? Are you using a filesystem other than ext3, or have you altered any of the mount options in your fstab? I'm just trying to think of anything that could directly affect performance.

---

### Post by DrMega on 2008-02-20
Output of dmesg:

I'm surprised to see mention of SCSI in there, and PATA. As far as I was aware there are no SCSI devices in my machine. I don't think I even have a SCSI controller. It's all IDE I thought.

Anyway, thanks for all your help on this.

```

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 00000000000ea000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
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
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA1D0 checksum 0
[    0.000000] ACPI: RSDP 000FA1D0, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 1FFF0000, 002C (r1 AMIINT SiS740XX     1000 MSFT  100000B)
[    0.000000] ACPI: FACP 1FFF0030, 0081 (r1 AMIINT SiS740XX       11 MSFT  100000B)
[    0.000000] ACPI: DSDT 1FFF0110, 3586 (r1    SiS      740      100 MSFT  100000D)
[    0.000000] ACPI: FACS 1FFF8000, 0040
[    0.000000] ACPI: APIC 1FFF00C0, 0050 (r1 AMIINT SiS740XX     1000 MSFT  100000B)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=d0c2bf1f-a099-40d0-9ff2-7194dcacda45 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1800.173 MHz processor.
[   21.485929] Console: colour VGA+ 80x25
[   21.486404] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.487269] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.506263] Memory: 508172k/524224k available (2015k kernel code, 15440k reserved, 916k data, 364k init, 0k highmem)
[   21.506276] virtual kernel memory layout:
[   21.506277]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   21.506279]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.506280]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   21.506282]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   21.506283]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   21.506285]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   21.506286]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   21.506290] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.506349] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   21.586253] Calibrating delay using timer specific routine.. 3602.28 BogoMIPS (lpj=7204572)
[   21.586296] Security Framework v1.0.0 initialized
[   21.586306] SELinux:  Disabled at boot.
[   21.586327] Mount-cache hash table entries: 512
[   21.586523] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   21.586535] CPU: CLK_CTL MSR was 6003d22f. Reprogramming to 2003d22f
[   21.586539] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.586542] CPU: L2 Cache: 64K (64 bytes/line)
[   21.586546] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   21.586561] Compat vDSO mapped to ffffe000.
[   21.586580] Checking 'hlt' instruction... OK.
[   21.602441] SMP alternatives: switching to UP code
[   21.602863] Freeing SMP alternatives: 11k freed
[   21.603378] Early unpacking initramfs... done
[   21.967836] ACPI: Core revision 20070126
[   21.967962] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.971715] CPU0: AMD Duron(tm)  stepping 01
[   21.971743] Total of 1 processors activated (3602.28 BogoMIPS).
[   21.971856] ENABLING IO-APIC IRQs
[   21.972042] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   22.117561] Brought up 1 CPUs
[   22.117764] Booting paravirtualized kernel on bare hardware
[   22.117856] Time: 19:57:43  Date: 01/20/108
[   22.117906] NET: Registered protocol family 16
[   22.118102] EISA bus registered
[   22.118121] ACPI: bus type pci registered
[   22.119655] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=2
[   22.119658] PCI: Using configuration type 1
[   22.119660] Setting up standard PCI resources
[   22.131259] ACPI: EC: Look up EC in DSDT
[   22.135118] ACPI: Interpreter enabled
[   22.135127] ACPI: (supports S0 S1 S4 S5)
[   22.135146] ACPI: Using IOAPIC for interrupt routing
[   22.142191] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.142202] PCI: Probing PCI hardware (bus 00)
[   22.142420] Enabling SiS 96x SMBus.
[   22.143019] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.144857] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[   22.144969] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
[   22.145071] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[   22.145181] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *11 12 14 15)
[   22.145283] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[   22.145382] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 *11 12 14 15)
[   22.145573] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   22.145681] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[   22.145963] ACPI: Power Resource [URP1] (off)
[   22.145999] ACPI: Power Resource [URP2] (off)
[   22.146030] ACPI: Power Resource [FDDP] (off)
[   22.146061] ACPI: Power Resource [LPTP] (off)
[   22.146085] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.146108] pnp: PnP ACPI init
[   22.146131] ACPI: bus type pnp registered
[   22.149898] pnp: PnP ACPI: found 10 devices
[   22.149905] ACPI: ACPI bus type pnp unregistered
[   22.149912] PnPBIOS: Disabled by ACPI PNP
[   22.150036] PCI: Using ACPI for IRQ routing
[   22.150042] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.153363] NET: Registered protocol family 8
[   22.153366] NET: Registered protocol family 20
[   22.153447] Time: tsc clocksource has been installed.
[   22.153615] pnp: 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[   22.184047] PCI: Bridge: 0000:00:01.0
[   22.184052]   IO window: disabled.
[   22.184059]   MEM window: cb500000-cf6fffff
[   22.184064]   PREFETCH window: ab200000-cb3fffff
[   22.184105] NET: Registered protocol family 2
[   22.221433] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   22.221542] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   22.222015] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   22.222322] TCP: Hash tables configured (established 16384 bind 16384)
[   22.222328] TCP reno registered
[   22.233530] checking if image is initramfs... it is
[   22.684692] Switched to high resolution mode on CPU 0
[   22.912572] Freeing initrd memory: 7065k freed
[   22.913220] audit: initializing netlink socket (disabled)
[   22.913244] audit(1203537463.044:1): initialized
[   22.915725] VFS: Disk quotas dquot_6.5.1
[   22.915817] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.915972] io scheduler noop registered
[   22.915976] io scheduler anticipatory registered
[   22.915978] io scheduler deadline registered
[   22.916004] io scheduler cfq registered (default)
[   22.940282] Boot video device is 0000:01:00.0
[   22.940607] isapnp: Scanning for PnP cards...
[   23.293679] isapnp: No Plug & Play device found
[   23.388863] Real Time Clock Driver v1.12ac
[   23.388995] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.389146] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.391221] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.392604] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.392998] input: Macintosh mouse button emulation as /class/input/input0
[   23.393113] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   23.393117] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   23.397812] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.398055] mice: PS/2 mouse device common for all mice
[   23.398226] EISA: Probing bus 0 at eisa.0
[   23.398267] EISA: Detected 0 cards.
[   23.398604] TCP cubic registered
[   23.398641] NET: Registered protocol family 1
[   23.398673] Using IPI No-Shortcut mode
[   23.399012]   Magic number: 12:934:1001
[   23.399030]   hash matches device ttye0
[   23.399262]   hash matches device 00:03
[   23.400043] Freeing unused kernel memory: 364k freed
[   23.464852] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.770308] AppArmor: AppArmor initialized<5>audit(1203537465.044:2):  type=1505 info="AppArmor initialized" pid=1175
[   24.783013] fuse init (API version 7.8)
[   24.791464] Failure registering capabilities with primary security module.
[   25.939876] SCSI subsystem initialized
[   25.946451] libata version 2.21 loaded.
[   25.950133] pata_sis 0000:00:02.5: version 0.5.1
[   25.950433] scsi0 : pata_sis
[   25.950526] scsi1 : pata_sis
[   25.950682] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ff00 irq 14
[   25.950687] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ff08 irq 15
[   25.987725] usbcore: registered new interface driver usbfs
[   25.987776] usbcore: registered new interface driver hub
[   25.987808] usbcore: registered new device driver usb
[   25.989044] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   26.041266] sis900.c: v1.08.10 Apr. 2 2006
[   26.119769] ata1.00: ATA-7: SAMSUNG SP0411N, TW100-08, max UDMA/133
[   26.119776] ata1.00: 78242976 sectors, multi 16: LBA48 
[   26.120589] ata1.01: ATA-4: WDC WD205BA, 16.13M16, max UDMA/66
[   26.120596] ata1.01: 40088160 sectors, multi 16: LBA 
[   26.127809] ata1.00: configured for UDMA/133
[   26.144425] ata1.01: configured for UDMA/66
[   26.150824] Floppy drive(s): fd0 is 1.44M
[   26.192765] FDC 0 is a post-1991 82077
[   26.463110] ata2.00: ATAPI: SAMSUNG CDRW/DVD SM-352N, TA00, max UDMA/33
[   26.634850] ata2.00: configured for UDMA/33
[   26.635066] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP0411N  TW10 PQ: 0 ANSI: 5
[   26.635933] scsi 0:0:1:0: Direct-Access     ATA      WDC WD205BA      16.1 PQ: 0 ANSI: 5
[   26.637131] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SM-352N TA00 PQ: 0 ANSI: 5
[   26.638088] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   26.638114] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   26.638466] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   26.638501] ohci_hcd 0000:00:03.0: irq 16, io mem 0xcfffd000
[   26.666101] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   26.666156] sd 0:0:0:0: [sda] Write Protect is off
[   26.666159] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.666180] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.666281] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   26.666293] sd 0:0:0:0: [sda] Write Protect is off
[   26.666296] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.666312] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.666322]  sda: sda1
[   26.672339] sd 0:0:0:0: [sda] Attached SCSI disk
[   26.672843] sd 0:0:1:0: [sdb] 40088160 512-byte hardware sectors (20525 MB)
[   26.672865] sd 0:0:1:0: [sdb] Write Protect is off
[   26.672868] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   26.672888] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.672987] sd 0:0:1:0: [sdb] 40088160 512-byte hardware sectors (20525 MB)
[   26.672998] sd 0:0:1:0: [sdb] Write Protect is off
[   26.673001] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   26.673017] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.673021]  sdb:<6>usb usb1: configuration #1 chosen from 1 choice
[   26.692767] hub 1-0:1.0: USB hub found
[   26.692786] hub 1-0:1.0: 3 ports detected
[   26.697142]  sdb1 sdb2 < sdb5 >
[   26.718453] sd 0:0:1:0: [sdb] Attached SCSI disk
[   26.726324] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   26.726844] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   26.727276] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   26.790285] sr0: scsi3-mmc drive: 1x/52x writer cd/rw xa/form2 cdda tray
[   26.790296] Uniform CD-ROM driver Revision: 3.20
[   26.790966] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   26.794665] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[   26.794693] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   26.794745] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   26.794772] ohci_hcd 0000:00:03.1: irq 17, io mem 0xcfffe000
[   26.852505] usb usb2: configuration #1 chosen from 1 choice
[   26.852557] hub 2-0:1.0: USB hub found
[   26.852576] hub 2-0:1.0: 3 ports detected
[   26.954561] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 18
[   26.954586] ehci_hcd 0000:00:03.2: EHCI Host Controller
[   26.954658] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   26.954718] PCI: cache line size of 64 is not supported by device 0000:00:03.2
[   26.954736] ehci_hcd 0000:00:03.2: irq 18, io mem 0xcffff000
[   26.954746] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.954868] usb usb3: configuration #1 chosen from 1 choice
[   26.954918] hub 3-0:1.0: USB hub found
[   26.954933] hub 3-0:1.0: 6 ports detected
[   27.058397] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[   27.059621] 0000:00:04.0: VIA 6103 PHY transceiver found at address 1.
[   27.069575] 0000:00:04.0: Using transceiver found at address 1 as default
[   27.070475] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 19, 00:0d:87:33:1f:6e.
[   27.153693] Attempting manual resume
[   27.153701] swsusp: Resume From Partition 8:21
[   27.153703] PM: Checking swsusp image.
[   27.153986] PM: Resume from disk failed.
[   27.215484] kjournald starting.  Commit interval 5 seconds
[   27.215512] EXT3-fs: mounted filesystem with ordered data mode.
[   27.601164] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   27.818007] usb 2-1: configuration #1 chosen from 1 choice
[   38.858419] Linux agpgart interface v0.102 (c) Dave Jones
[   38.968357] agpgart: Detected SiS chipset - id:1862
[   38.978845] agpgart: AGP aperture is 128M @ 0xd0000000
[   39.012831] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.032966] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.065015] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   39.614492] nvidia: module license 'NVIDIA' taints kernel.
[   39.874087] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   39.874835] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   40.234544] input: PC Speaker as /class/input/input2
[   40.693208] parport_pc 00:09: reported by Plug and Play ACPI
[   40.693308] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   40.829381] usbcore: registered new interface driver hiddev
[   40.838107] input: Qtronix Corp USB MOUSE as /class/input/input3
[   40.839103] input: USB HID v1.10 Mouse [Qtronix Corp USB MOUSE] on usb-0000:00:03.1-1
[   40.839135] usbcore: registered new interface driver usbhid
[   40.839141] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.109501] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 21
[   41.432037] intel8x0_measure_ac97_clock: measured 54772 usecs
[   41.432045] intel8x0: clocking to 48000
[   42.049264] lp0: using parport0 (interrupt-driven).
[   42.128051] Adding 875500k swap on /dev/sdb5.  Priority:-1 extents:1 across:875500k
[   42.622107] EXT3 FS on sdb1, internal journal
[   46.196112] No dock devices found.
[   46.290990] input: Power Button (FF) as /class/input/input4
[   46.298626] ACPI: Power Button (FF) [PWRF]
[   46.349400] input: Power Button (CM) as /class/input/input5
[   46.357067] ACPI: Power Button (CM) [PWRB]
[   46.404498] input: Sleep Button (CM) as /class/input/input6
[   46.405025] ACPI: Sleep Button (CM) [SLPB]
[   49.845569] ppdev: user-space parallel port driver
[   50.001329] audit(1203537490.940:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4799 profile="/usr/sbin/cupsd"
[   51.701020] eth0: Media Link On 100mbps full-duplex 
[   53.598948] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   53.598957] apm: overridden by ACPI.
[   56.308381] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   56.516739] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   56.537046] NFSD: starting 90-second grace period
[   57.513464] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   57.513474] vboxdrv: Successfully done.
[   58.026636] Failure registering capabilities with primary security module.
[   58.298942] Bluetooth: Core ver 2.11
[   58.299140] NET: Registered protocol family 31
[   58.299143] Bluetooth: HCI device and connection manager initialized
[   58.299149] Bluetooth: HCI socket layer initialized
[   58.320117] Bluetooth: L2CAP ver 2.8
[   58.320125] Bluetooth: L2CAP socket layer initialized
[   58.395130] Bluetooth: RFCOMM socket layer initialized
[   58.395264] Bluetooth: RFCOMM TTY layer initialized
[   58.395268] Bluetooth: RFCOMM ver 1.8
[   60.875862] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   60.875887] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   60.875892] agpgart: SiS delay workaround: giving bridge time to recover.
[   60.890435] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   62.783117] NET: Registered protocol family 17
[   68.421190] NET: Registered protocol family 10
[   68.421474] lo: Disabled Privacy Extensions
[   79.362163] eth0: no IPv6 routers present


```

---


---
title: "What does this mean?"
date: 2007-05-01
forum: General Help
---

### Post by Sam Taylor on 2007-05-01
[mntent]: warning: no final newline at the end of /etc/fstab

mount: special device /dev/hdb does not exist

I'm lost again!
My computer has recently decided it no longer has a CD ROM or DVD ROM. Nothing had changed here but now it tells me there must not be any media in the cd and the above message for the writer.
What do I need to do?
Cheers

---

### Post by Aetherius on 2007-05-01
open a terminal and type

```
sudo gedit /etc/fstab
```

then make sure there is a blank line at the end of this document.

If there isn't just go the last line, hit return, save and quit.

then restart

---

### Post by Sam Taylor on 2007-05-01
Thanks for your help Aetherius,
               Now the computeer is saying...
mount: special device /dev/hdb does not exist

Why would it stop working? Any ideas welcome
Cheers
Sam

---

### Post by taurus on 2007-05-01
Can you post the output of these two commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
```

p.s.  The problem is not a blank line at the end of /etc/fstab.  The problem is you need to mount the second harddrive with something like /dev/hdb1.

---

### Post by Sam Taylor on 2007-05-01
Hello there Taurus,
 This is what terminal says


Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161   83  Linux
/dev/sda2            9730       10011     2265165    5  Extended
/dev/sda5            9730       10011     2265133+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244193432    b  W95 FAT32
sam@Sam:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=b8fe0bbe-c2db-40ce-a307-fc693a91ccb8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=1ea19862-b95c-4f19-b43c-9d2f59891889 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Thanks for taking an interest
Cheers
Sam

---

### Post by taurus on 2007-05-01
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and place a # in front of the line for /dev/hdb to comment it out.  Also, you should add an entry for your second harddrive, /dev/sdb1.

```
/dev/sdb1   /media/sdb1   vfat   iocharset=utf8,umask=000   0   0
```
Save the changes.  Now, create a new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```
Can you post the complete output of this command from a terminal here?

```
dmesg
```

---

### Post by psusi on 2007-05-01
Yes, comment out the hdb line, and also your floppy line is hosed up as well.  If you have a floppy it should say /dev/fd0, not just /dev/.  If you don't have a floppy then remove the line completely.  In fact, let's just comment that one out as well.  

Do you have a /dev/cdrom?  run ls -al /dev/cdrom

---

### Post by Sam Taylor on 2007-05-01
Hello Taurus 

sam@Sam:~$ sudo mkdir /media/sdb1
mkdir: cannot create directory `/media/sdb1': File exists
sam@Sam:~$ sudo mount -a
mount: special device dev/sdb1 does not exist
sam@Sam:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              74G  6.1G   64G   9% /
varrun                379M  108K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M  132K  379M   1% /proc/bus/usb
udev                  379M  132K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-15-generic/volatile
/dev/sdb1             233G  175G   58G  76% /media/FREECOM HDD_


Is this what i'm meant to post you?
Well out of my depth I'm afraid
Cheers
Sam

---

### Post by taurus on 2007-05-01
Your /dev/sdb1 is already mounted to /media/FREECOM HDD_ so you don't need an entry for /dev/sdb1 in /etc/fstab anymore.  Therefore, you can remove it then.

```
gksudo gedit /etc/fstab
```

---

### Post by Sam Taylor on 2007-05-01
> **psusi said:**
> Yes, comment out the hdb line, and also your floppy line is hosed up as well.  If you have a floppy it should say /dev/fd0, not just /dev/.  If you don't have a floppy then remove the line completely.  In fact, let's just comment that one out as well.  

Do you have a /dev/cdrom?  run ls -al /dev/cdrom

Hello psusi
lrwxrwxrwx 1 root root 4 2007-05-01 14:22 /dev/cdrom -> scd0

What does this mean?
Cheers for everything
Sam

---

### Post by Sam Taylor on 2007-05-01
> **taurus said:**
> Your /dev/sdb1 is already mounted to /media/FREECOM HDD_ so you don't need an entry for /dev/sdb1 in /etc/fstab anymore.  Therefore, you can remove it then.

```
gksudo gedit /etc/fstab
```

Hello Taurus
 So I think I've managed that thanks to you.
Still no sign of any dvd writer though.
Cheers
Sam

---

### Post by taurus on 2007-05-01
Can you post the output of this command here?

```
dmesg
```

---

### Post by psusi on 2007-05-01
> **Sam Taylor said:**
> Hello psusi
lrwxrwxrwx 1 root root 4 2007-05-01 14:22 /dev/cdrom -> scd0

What does this mean?
Cheers for everything
Sam

It means that your computer sees the cdrom drive, and combined with this line in your fstab:

/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0

Should work just fine.  Does cdrom0 not show up on your desktop when you insert a cd?

---

### Post by Sam Taylor on 2007-05-01
Sorry Taurus, you asked for that before didn't you?

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000002fef0000 end: 000000002fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000002fff0000 size: 0000000000008000 end: 000000002fff8000 type: 3
[    0.000000] copy_e820_map() start: 000000002fff8000 size: 0000000000008000 end: 0000000030000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002fff8000 - 0000000030000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fb8e0
[    0.000000] Entering add_active_range(0, 0, 196592) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196592
[    0.000000]   HighMem    196592 ->   196592
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196592
[    0.000000] On node 0 totalpages: 196592
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1503 pages used for memmap
[    0.000000]   Normal zone: 190993 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa530
[    0.000000] ACPI: RSDT (v001 AMIINT AMIINI09 0x00000010 MSFT 0x0100000d) @ 0x2fff0000
[    0.000000] ACPI: FADT (v001 AMIINT AMIINI09 0x00000011 MSFT 0x0100000d) @ 0x2fff0030
[    0.000000] ACPI: MADT (v001 AMIINT AMIINI09 0x00000011 MSFT 0x0100000d) @ 0x2fff00c0
[    0.000000] ACPI: DSDT (v001  INTEL   TEHAMA 0x00001000 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:1 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] Detected 1707.599 MHz processor.
[   41.183539] Built 1 zonelists.  Total pages: 195057
[   41.183545] Kernel command line: root=UUID=b8fe0bbe-c2db-40ce-a307-fc693a91ccb8 ro quiet splash
[   41.183795] mapped APIC to ffffd000 (fee00000)
[   41.183799] mapped IOAPIC to ffffc000 (fec00000)
[   41.183803] Enabling fast FPU save and restore... done.
[   41.183808] Enabling unmasked SIMD FPU exception support... done.
[   41.183823] Initializing CPU#0
[   41.183918] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   41.185461] Console: colour VGA+ 80x25
[   41.186176] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   41.187189] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   41.217086] Memory: 768320k/786368k available (1992k kernel code, 17384k reserved, 893k data, 328k init, 0k highmem)
[   41.217101] virtual kernel memory layout:
[   41.217103]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   41.217105]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   41.217106]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   41.217108]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
[   41.217110]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   41.217112]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   41.217113]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   41.217118] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   41.295802] Calibrating delay using timer specific routine.. 3418.76 BogoMIPS (lpj=6837524)
[   41.295868] Security Framework v1.0.0 initialized
[   41.295878] SELinux:  Disabled at boot.
[   41.295904] Mount-cache hash table entries: 512
[   41.296130] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   41.296149] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   41.296154] CPU: L2 cache: 256K
[   41.296157] CPU: Hyper-Threading is disabled
[   41.296161] CPU: After all inits, caps: 3febfbff 00000000 00000000 00003080 00000000 00000000 00000000
[   41.296177] Compat vDSO mapped to ffffe000.
[   41.296182] Remapping vsyscall page to ffffe000
[   41.296201] Checking 'hlt' instruction... OK.
[   41.311979] SMP alternatives: switching to UP code
[   41.312304] Freeing SMP alternatives: 11k freed
[   41.312655] Early unpacking initramfs... done
[   41.783745] ACPI: Core revision 20060707
[   41.785718] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   41.788445] CPU0: Intel(R) Pentium(R) 4 CPU 1.70GHz stepping 02
[   41.788501] Total of 1 processors activated (3418.76 BogoMIPS).
[   41.788649] ENABLING IO-APIC IRQs
[   41.788851] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   41.935166] Brought up 1 CPUs
[   41.935558] Booting paravirtualized kernel on bare hardware
[   41.935683] Time: 13:21:19  Date: 04/01/107
[   41.935733] NET: Registered protocol family 16
[   41.935892] EISA bus registered
[   41.935900] ACPI: bus type pci registered
[   41.940035] PCI: PCI BIOS revision 2.10 entry at 0xfdae1, last bus=2
[   41.940038] PCI: Using configuration type 1
[   41.940041] Setting up standard PCI resources
[   41.949707] ACPI: Interpreter enabled
[   41.949714] ACPI: Using IOAPIC for interrupt routing
[   41.950419] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   41.950431] PCI: Probing PCI hardware (bus 00)
[   41.951311] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   41.951318] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   41.951752] Boot video device is 0000:01:00.0
[   41.952294] PCI: Transparent bridge - 0000:00:1e.0
[   41.952336] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   41.971606] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.ICHB._PRT]
[   41.972904] ACPI: Power Resource [URP1] (off)
[   41.973032] ACPI: Power Resource [URP2] (off)
[   41.973148] ACPI: Power Resource [FDDP] (off)
[   41.973264] ACPI: Power Resource [LPTP] (off)
[   41.977960] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   41.978338] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   41.978711] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   41.979114] ACPI: PCI Interrupt Link [LNKD] (IRQs 9) *10
[   41.979497] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   41.979874] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   41.980244] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   41.980612] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[   41.980886] Linux Plug and Play Support v0.97 (c) Adam Belay
[   41.980905] pnp: PnP ACPI init
[   41.986435] pnp: PnP ACPI: found 11 devices
[   41.986445] PnPBIOS: Disabled by ACPI PNP
[   41.986545] PCI: Using ACPI for IRQ routing
[   41.986551] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   42.009660] NET: Registered protocol family 8
[   42.009664] NET: Registered protocol family 20
[   42.010335] PCI: Bridge: 0000:00:01.0
[   42.010339]   IO window: disabled.
[   42.010346]   MEM window: edd00000-efdfffff
[   42.010351]   PREFETCH window: d5a00000-e5afffff
[   42.010363] PCI: Bridge: 0000:00:1e.0
[   42.010367]   IO window: 9000-afff
[   42.010374]   MEM window: efe00000-efefffff
[   42.010380]   PREFETCH window: e5b00000-e5bfffff
[   42.010403] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   42.010456] NET: Registered protocol family 2
[   42.047093] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   42.047364] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   42.048674] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   42.049418] TCP: Hash tables configured (established 131072 bind 65536)
[   42.049424] TCP reno registered
[   42.059197] checking if image is initramfs... it is
[   42.988204] Freeing initrd memory: 6750k freed
[   42.988813] audit: initializing netlink socket (disabled)
[   42.988832] audit(1178025680.884:1): initialized
[   42.989073] VFS: Disk quotas dquot_6.5.1
[   42.989105] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   42.989179] io scheduler noop registered
[   42.989185] io scheduler anticipatory registered
[   42.989188] io scheduler deadline registered
[   42.989208] io scheduler cfq registered (default)
[   42.989652] isapnp: Scanning for PnP cards...
[   43.343594] isapnp: No Plug & Play device found
[   43.424388] Real Time Clock Driver v1.12ac
[   43.424468] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   43.424615] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   43.425019] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   43.426581] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   43.427189] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   43.427741] mice: PS/2 mouse device common for all mice
[   43.428709] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   43.428977] input: Macintosh mouse button emulation as /class/input/input0
[   43.429045] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   43.429052] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   43.429488] PNP: No PS/2 controller found. Probing ports directly.
[   43.685482] serio: i8042 KBD port at 0x60,0x64 irq 1
[   43.685718] EISA: Probing bus 0 at eisa.0
[   43.685767] EISA: Detected 0 cards.
[   43.715878] TCP cubic registered
[   43.715890] NET: Registered protocol family 1
[   43.715927] Using IPI No-Shortcut mode
[   43.716043] ACPI: (supports S0 S1 S4 S5)
[   43.716114]   Magic number: 7:268:381
[   43.716783] Freeing unused kernel memory: 328k freed
[   43.717158] Time: tsc clocksource has been installed.
[   45.097234] Capability LSM initialized
[   45.171646] ACPI: Processor [CPU1] (supports 8 throttling states)
[   46.045375] SCSI subsystem initialized
[   46.054694] libata version 2.20 loaded.
[   46.061023] ata_piix 0000:00:1f.1: version 2.10ac1
[   46.061065] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   46.061147] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ff00 irq 14
[   46.061198] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ff08 irq 15
[   46.061227] scsi0 : ata_piix
[   46.085185] usbcore: registered new interface driver usbfs
[   46.085227] usbcore: registered new interface driver hub
[   46.085273] usbcore: registered new device driver usb
[   46.142341] USB Universal Host Controller Interface driver v3.0
[   46.215360] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   46.258071] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   46.338400] Floppy drive(s): fd0 is 1.44M
[   46.399160] FDC 0 is a post-1991 82077
[   53.214154] ata1: port is slow to respond, please be patient (Status 0x80)
[   76.203627] ata1: port failed to respond (30 secs, Status 0x80)
[   76.214945] ATA: abnormal status 0x80 on port 0x000101f7
[   76.226203] ATA: abnormal status 0x80 on port 0x000101f7
[   76.391677] ata1.01: ATAPI, max UDMA/33
[   76.555488] ata1.01: configured for UDMA/33
[   76.555507] scsi1 : ata_piix
[   76.735458] ata2.01: ata_hpa_resize 1: sectors = 160836480, hpa_sectors = 160836480
[   76.735466] ata2.01: ATA-5: IC35L080AVVA07-0, VA4OA50K, max UDMA/100
[   76.735470] ata2.01: 160836480 sectors, multi 16: LBA 
[   76.743427] ata2.01: ata_hpa_resize 1: sectors = 160836480, hpa_sectors = 160836480
[   76.743432] ata2.01: configured for UDMA/100
[   76.743805] scsi 0:0:1:0: CD-ROM                     ATAPI CDROM.     100A PQ: 0 ANSI: 5
[   76.744540] scsi 1:0:1:0: Direct-Access     ATA      IC35L080AVVA07-0 VA4O PQ: 0 ANSI: 5
[   76.745158] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 16
[   76.745179] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   76.745185] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   76.745369] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   76.745407] uhci_hcd 0000:00:1f.2: irq 16, io base 0x0000dc00
[   76.745596] usb usb1: configuration #1 chosen from 1 choice
[   76.745639] hub 1-0:1.0: USB hub found
[   76.745651] hub 1-0:1.0: 2 ports detected
[   76.778715] sr0: scsi3-mmc drive: 135x/52x cd/rw xa/form2 cdda tray
[   76.778723] Uniform CD-ROM driver Revision: 3.20
[   76.779115] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   76.786911] sr 0:0:1:0: Attached scsi generic sg0 type 5
[   76.787192] sd 1:0:1:0: Attached scsi generic sg1 type 0
[   76.796487] SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
[   76.797325] sda: Write Protect is off
[   76.797332] sda: Mode Sense: 00 3a 00 00
[   76.797372] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   76.797587] SCSI device sda: 160836480 512-byte hdwr sectors (82348 MB)
[   76.797605] sda: Write Protect is off
[   76.797609] sda: Mode Sense: 00 3a 00 00
[   76.797637] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   76.797642]  sda: sda1 sda2 < sda5 >
[   76.832057] sd 1:0:1:0: Attached scsi disk sda
[   76.851119] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 17
[   76.851138] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   76.851144] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   76.851183] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   76.851216] uhci_hcd 0000:00:1f.4: irq 17, io base 0x0000d800
[   76.851362] usb usb2: configuration #1 chosen from 1 choice
[   76.851407] hub 2-0:1.0: USB hub found
[   76.851420] hub 2-0:1.0: 2 ports detected
[   76.955078] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 18
[   76.955100] ohci_hcd 0000:02:01.0: OHCI Host Controller
[   76.955153] ohci_hcd 0000:02:01.0: new USB bus registered, assigned bus number 3
[   76.955177] ohci_hcd 0000:02:01.0: irq 18, io mem 0xefeff000
[   77.040764] usb usb3: configuration #1 chosen from 1 choice
[   77.040816] hub 3-0:1.0: USB hub found
[   77.040831] hub 3-0:1.0: 3 ports detected
[   77.094621] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   77.106443] Attempting manual resume
[   77.106450] swsusp: Resume From Partition 8:5
[   77.106453] PM: Checking swsusp image.
[   77.106681] PM: Resume from disk failed.
[   77.146715] ACPI: PCI Interrupt 0000:02:01.1[B] -> GSI 22 (level, low) -> IRQ 19
[   77.146741] ohci_hcd 0000:02:01.1: OHCI Host Controller
[   77.146780] ohci_hcd 0000:02:01.1: new USB bus registered, assigned bus number 4
[   77.146802] ohci_hcd 0000:02:01.1: irq 19, io mem 0xefefe000
[   77.152320] kjournald starting.  Commit interval 5 seconds
[   77.152343] EXT3-fs: mounted filesystem with ordered data mode.
[   77.232464] usb usb4: configuration #1 chosen from 1 choice
[   77.232521] hub 4-0:1.0: USB hub found
[   77.232535] hub 4-0:1.0: 2 ports detected
[   77.309835] usb 1-1: configuration #1 chosen from 1 choice
[   77.338667] ACPI: PCI Interrupt 0000:02:01.2[C] -> GSI 16 (level, low) -> IRQ 20
[   77.338688] ehci_hcd 0000:02:01.2: EHCI Host Controller
[   77.338741] ehci_hcd 0000:02:01.2: new USB bus registered, assigned bus number 5
[   77.362306] ehci_hcd 0000:02:01.2: irq 20, io mem 0xefefdf00
[   77.362319] ehci_hcd 0000:02:01.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   77.362475] usb usb5: configuration #1 chosen from 1 choice
[   77.362521] hub 5-0:1.0: USB hub found
[   77.362533] hub 5-0:1.0: 5 ports detected
[   77.466469] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   77.466475] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[   78.005561] usb 5-3: new high speed USB device using ehci_hcd and address 2
[   78.246206] usb 5-3: configuration #1 chosen from 1 choice
[   78.916507] usb 4-2: new full speed USB device using ohci_hcd and address 2
[   79.131541] usb 4-2: configuration #1 chosen from 1 choice
[   79.443897] usb 3-3: new low speed USB device using ohci_hcd and address 2
[   79.657831] usb 3-3: configuration #1 chosen from 1 choice
[   89.855053] iTCO_vendor_support: vendor-support=0
[   89.856734] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   89.856884] iTCO_wdt: Found a ICH2 TCO device (Version=1, TCOBASE=0x0460)
[   89.856944] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   89.875725] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   89.888666] intel_rng: FWH not detected
[   90.180024] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   90.262252] Linux agpgart interface v0.102 (c) Dave Jones
[   90.265168] agpgart: Detected an Intel i850 Chipset.
[   90.269128] agpgart: AGP aperture is 64M @ 0xe8000000
[   90.716333] input: PC Speaker as /class/input/input1
[   91.014820] parport: PnPBIOS parport detected.
[   91.014925] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   91.507057] 8139too Fast Ethernet driver 0.9.28
[   91.507149] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 16 (level, low) -> IRQ 20
[   91.507555] eth0: RealTek RTL8139 at 0xf091ce00, 00:50:fc:3a:77:95, IRQ 20
[   91.507560] eth0:  Identified 8139 chip type 'RTL-8139C'
[   91.562213] gameport: EMU10K1 is pci0000:02:04.1/gameport0, io 0xa000, speed 903kHz
[   91.756955] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 18 (level, low) -> IRQ 21
[   91.856506] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 22
[   91.856547] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   91.871279] usbcore: registered new interface driver hiddev
[   92.002265] eth0: link down
[   92.010663] input: HID 1241:1111 as /class/input/input2
[   92.010844] input: USB HID v1.10 Mouse [HID 1241:1111] on usb-0000:00:1f.2-1
[   92.165487] eth1: register 'cdc_ether' at usb-0000:02:01.1-2, CDC Ethernet Device, 00:0e:9b:72:fa:e3
[   92.170560] input: Device USB Device as /class/input/input3
[   92.170658] input: USB HID v1.00 Keyboard [Device USB Device] on usb-0000:02:01.0-3
[   92.181588] input: Device USB Device as /class/input/input4
[   92.181780] input: USB HID v1.00 Mouse [Device USB Device] on usb-0000:02:01.0-3
[   92.181807] usbcore: registered new interface driver usbhid
[   92.181813] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   92.182511] usbcore: registered new interface driver cdc_ether
[   92.183959] usbcore: registered new interface driver libusual
[   92.195088] intel8x0_measure_ac97_clock: measured 60870 usecs
[   92.195094] intel8x0: clocking to 48000
[   92.205025] Initializing USB Mass Storage driver...
[   92.205894] scsi2 : SCSI emulation for USB Mass Storage devices
[   92.206063] usbcore: registered new interface driver usb-storage
[   92.206069] USB Mass Storage support registered.
[   92.206253] usb-storage: device found at 2
[   92.206258] usb-storage: waiting for device to settle before scanning
[   92.866976] lp0: using parport0 (interrupt-driven).
[   92.918259] Adding 2265124k swap on /dev/disk/by-uuid/1ea19862-b95c-4f19-b43c-9d2f59891889.  Priority:-1 extents:1 across:2265124k
[   92.986696] EXT3 FS on sda1, internal journal
[   93.197775] NET: Registered protocol family 17
[   97.199884] usb-storage: device scan complete
[   97.235481] scsi 2:0:0:0: Direct-Access     SAMSUNG  SP2514N          VF10 PQ: 0 ANSI: 0
[   97.239436] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   97.240560] sdb: Write Protect is off
[   97.240566] sdb: Mode Sense: 03 00 00 00
[   97.240569] sdb: assuming drive cache: write through
[   97.242686] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   97.243806] sdb: Write Protect is off
[   97.243813] sdb: Mode Sense: 03 00 00 00
[   97.243816] sdb: assuming drive cache: write through
[   97.243823]  sdb: sdb1
[   97.254801] sd 2:0:0:0: Attached scsi disk sdb
[   97.254868] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   97.412809] NET: Registered protocol family 10
[   97.412960] lo: Disabled Privacy Extensions
[   97.413043] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   98.254918] input: Power Button (FF) as /class/input/input5
[   98.261738] ACPI: Power Button (FF) [PWRF]
[   98.320913] input: Power Button (CM) as /class/input/input6
[   98.327704] ACPI: Power Button (CM) [PWRB]
[   98.374139] input: Sleep Button (CM) as /class/input/input7
[   98.374479] ACPI: Sleep Button (CM) [SLPB]
[   98.412567] Using specific hotkey driver
[   98.459898] No dock devices found.
[   98.528052] ibm_acpi: ec object not found
[   98.706981] pcc_acpi: loading...
[  106.672848] ppdev: user-space parallel port driver
[  107.637714] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  107.637721] apm: overridden by ACPI.
[  108.767792] Bluetooth: Core ver 2.11
[  108.767881] NET: Registered protocol family 31
[  108.767885] Bluetooth: HCI device and connection manager initialized
[  108.767890] Bluetooth: HCI socket layer initialized
[  108.844832] Bluetooth: L2CAP ver 2.8
[  108.844840] Bluetooth: L2CAP socket layer initialized
[  108.849980] Bluetooth: RFCOMM socket layer initialized
[  108.850011] Bluetooth: RFCOMM TTY layer initialized
[  108.850014] Bluetooth: RFCOMM ver 1.8
[  121.747133] eth1: no IPv6 routers present


Thanks again 
Sam

---

### Post by Sam Taylor on 2007-05-01
> **psusi said:**
> It means that your computer sees the cdrom drive, and combined with this line in your fstab:

/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0

Should work just fine.  Does cdrom0 not show up on your desktop when you insert a cd?

It says 
"Unable to mount media.
There is probably no media in the drive."

Nah, It's not having any of it!
Cheers
Sam

---

### Post by psusi on 2007-05-01
You do only have one optical drive right?  Insert a cd, preferably a pressed one, not burned, and do this:

sudo dd if=/dev/cdrom of=/dev/null bs=32768 count=1

---

### Post by Sam Taylor on 2007-05-01
Hi psusi,
          Thanks again for all your time!
I have 2- cd rom and dvd writer. This is what is said to the pressed cd

dd: opening `/dev/cdrom': No medium found

Same as if there were nothing in it. Fires up and makes appropriate noises and then does nothing. If I look at computer and then try to open it the message is the same as before Unable to mount etc. Also the dvd icon has gone now due to earlier attempts but that wouldn't mount either. Both drives have power but nothing going on.
Any help cheerfully accepted,
 
Sam

---

### Post by hartz on 2007-05-01
Hi SAM,

from these lines from your dmesg output I see that you have a real SCSI CDROM:

```
[ 76.778723] Uniform CD-ROM driver Revision: 3.20
[ 76.779115] sr 0:0:1:0: Attached scsi CD-ROM sr0
[ 76.786911] sr 0:0:1:0: Attached scsi generic sg0 type 5
```

This is also reflected by the "-> scd0" part of the output of ls -l /dev/cdrom.

Could you please do this (The first command needs to be first):

```
cd /dev
ls -l |grep dvd
ls -l |grep "-> hd"
ls -l hd*
ls -l sd*
```

Lets see if we can sort this out for you.

---

### Post by psusi on 2007-05-01
Which one if them is the scsi one?  Are you sure you put the cd in the scsi drive?  Try inserting it in the other two drives.

---

### Post by Sam Taylor on 2007-05-01
Hello hartz3 

sam@Sam:~$ cd /dev
sam@Sam:/dev$ ls -l |grep dvd
sam@Sam:/dev$ ls -l |grep "-> hd"
grep: invalid option -- >
Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
sam@Sam:/dev$ ls -l hd*
ls: hd*: No such file or directory
sam@Sam:/dev$ ls -l sd*
brw-rw---- 1 root disk    8,  0 2007-05-01 14:21 sda
brw-rw---- 1 root disk    8,  1 2007-05-01 14:22 sda1
brw-rw---- 1 root disk    8,  2 2007-05-01 14:21 sda2
brw-rw---- 1 root disk    8,  5 2007-05-01 14:21 sda5
brw-rw---- 1 root plugdev 8, 16 2007-05-01 14:22 sdb
brw-rw---- 1 root plugdev 8, 17 2007-05-01 14:22 sdb1


Hi psusi
Tried both cd and dvd but to no avail

Thank you both for helping

---

### Post by psusi on 2007-05-01
To make sure you are not mixing up the drives, I'd suggest you disconnect the other two, then see if you still get the same error with that dd command.  If so, then I'd say the drive is toast.

---

### Post by Sam Taylor on 2007-05-01
> **psusi said:**
> To make sure you are not mixing up the drives, I'd suggest you disconnect the other two, then see if you still get the same error with that dd command.  If so, then I'd say the drive is toast.

I think you might be right there but i'm too new to this to tell.
There are just 2 drives for cds and an external harddrive, which is the freecom thing, but both disc drives went down at the same time and maybe they have just had it.

---

### Post by mikkojhe on 2007-07-26
> **Sam Taylor said:**
> [mntent]: warning: no final newline at the end of /etc/fstab

mount: special device /dev/hdb does not exist

I'm lost again!
My computer has recently decided it no longer has a CD ROM or DVD ROM. Nothing had changed here but now it tells me there must not be any media in the cd and the above message for the writer.
What do I need to do?
Cheers

I have almost exactly the same problem but with only one CD ROM installed. I think the problem occurred after the update from Edgy to Feisty. Can't be sure since I don't use CD ROM very often.

My error message looks like this:

[mntent]: warning: no final newline at the end of /etc/fstab

mount: special device /dev/cdrom does not exist

It's the same message whether I have CD in or not.

Thanks for your help.

---

### Post by TimTang on 2007-12-27
I have exactly the same problem: same error message, same everything. I've tried everything on this thread...nothing!

The DVD/CD has been working since I first installed Ubuntu then today it doesn't exist.

It still works in WinXP and Fedora, just not in Ubuntu. It's ironic that it's always been there on my desktop but the day I want to use it, the icon is gone and the drive no longer exists. Could this be some kind of electronic conspiracy?

I want to use it to do a virtual installation of WinXP with ubuntu as the host.

Could VirtualBox have anything to do with it. My fstab file hasn't changed at all since the initial install. I've used the DVD on several occasions to play movies. Why would it just suddenly disappear for no apparent reason.

Is there some way I can force a mount with a command line in the terminal?

Any help would be greatly appreciated.

---


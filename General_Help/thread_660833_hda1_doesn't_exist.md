---
title: "hda1 doesn't exist?"
date: 2008-01-07
forum: General Help
---

### Post by abbigail on 2008-01-07
i'm trying to mount my Windows hard drive to copy off the files from it since it died a day ago, but unlike last year when i had to use Ubuntu for a similar situation, /dev/hda1 is being said to not exist by Ubuntu. would it be because this time i have my hard drive split into 3 partitions on Windows? how can i access and backup the files from all of them? sda1 is all that's showing up, which is my external hd :[

---

### Post by vanadium on 2008-01-07
Your question probably belongs in the "Absolute beginners forum". With the command "sudo fdisk -l", you can see all the drives that your system recognizes. This does not mean they are mounted. To see the drives that are actually mounted, use the "mount" command. If your drive is in the output of the first command, but not in the second, you will need to mount it manually.

---

### Post by abbigail on 2008-01-08
all that shows is my external hd. it doesn't make sense how the sudo .dev/hda1 thing worked last year but now it doesn't? i just get the message that /dev/hda1 doesn't exist. if that's the case, how do i find out what my 3 partitions are called or where they are? btw, i'm a total noob at this kind of thing so try not to speak too smart! x:

---

### Post by geirha on 2008-01-08
In Gutsy ide drives are often named sda, sdb etc instead of hda, hdb, etc (as opposed to earlier ubuntu releases). Are you sure **sudo fdisk -l** only displays one harddrive? And if so, perhaps your harddrive crashed? There should be some messages from the kernel in such a case. Try running ```
dmesg|less
``` in a terminal, or ```
less /var/log/syslog
```

---

### Post by vanadium on 2008-01-08
Do not hesitate to post the output of "sudo fdisk -l" and "mount" here if it is confusing you. We can help you explain what it means.

---

### Post by Wiifreak on 2008-01-08
Or else download Knoppix CD and check if you are able to see the partitions.

---

### Post by abbigail on 2008-01-08
sudo fdisk -l shows..

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

..which is my external hd.

sudo mkdir /media/windows

and then,

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222 shows..

mount: special device /dev/hda1 does not exist

both dmesg|less and less /var/log/syslog showed a bunch of seemingly useless stuff :/

---

### Post by vanadium on 2008-01-09
The output of fdisk reveals that your drive is recognised as dev/sda, and that it contains one ntfs formatted partition, /dev/sda1. What version of Ubuntu are you using? A removable hard drive should mount automatically since several versions (if not since the first!). There is no problem with the partition, therefore the problem will be with the file system which probably is not "clean". You probably will need to check the ntfs volume.

The best way to fix an ntfs volume is to load Windows, attach the drive and use the windows tools to check file systems. then exit Windows completely (= surely not a hibernate, because disconnecting from a hibernated Windows can be a cause for an unclean ntfs volume). When you boot Linux again, and connect the drive, it should be mounted automatically with an icon on the desktop (options in "System - Preferences - removable media" must be set for automatic mounting).

Unclean ntfs volumes are a very common cause for removable drives not auto-mounting anymore.

---

### Post by marufaberlin on 2008-01-09
Try looking in /proc/ide for your ide drive. If it is not listed there, it is probly not being detected by your system.

marufaberlin

---

### Post by abbigail on 2008-01-09
how would i find out the version of Ubuntu that i'm using? i downloaded it in december of 2006. also, the external hd isn't the dead one. i only have it plugged in to move files from my dead internal hd which isn't showing up. everything with the external works perfectly fine. i can't even load windows with my internal hd. i upgraded to SP2 and back down to SP1 (before it died), but while Windows was copying the files, it froze for 12+ hours and when i crashed my pc (what else to do?), Windows wouldn't load back up. is this a hopeless cause? i have too many important files on my hd that i can't afford to lose! :[

---

### Post by vanadium on 2008-01-10
Do you happen to access your system with a live CD? Must be, otherwise we would see at least a linux partition. If your external drive is the only one you see, then it seems that the system does simply not recognize the internal drive. This looks like a hardware problem. Try perhaps checking the drives connections. If the files are very valuable, you might need specialized help to recover the data.

---

### Post by abbigail on 2008-01-10
i use a live cd of Ubuntu, which last year let me access my internal hd when it went corrupt and gave me the same "operating system not found" error on bootup. if Ubuntu can't do it, does anyone think SpinRite ([http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)) could? i'm really looking for any way possible to get these files back. somebody point me in the right direction, please! it's all on a 320gb hd, too. lots :[

---

### Post by marufaberlin on 2008-01-11
Do you use Gnome? then have a look in system menu on about ubuntu and on about gnome.

---

### Post by abbigail on 2008-01-11
i use Windows XP and a live cd of Ubuntu :/

---

### Post by geirha on 2008-01-12
It really sounds like your harddrive may have crashed, to be sure though, I would open up the hood and make sure all cables to and from the harddrive are connected properly. Also, after a fresh boot of the ubuntu CD, run the command ```
dmesg >~/Desktop/dmesg.log
```
Then attach or paste the content of that file here, and we might find some more clues about your harddrive. If you paste the output, please put it inside [ CODE ]-tags. (Mark the text you've pasted, then click the #-icon above the textarea)

And based on the date you downloaded the CD, you most likely have Ubuntu 6.10 Edgy Eft. The following command will display it though: ```
cat /etc/lsb-release
```

---

### Post by abbigail on 2008-01-13
```
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[17179569.184000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000017ef0000 (usable)
[17179569.184000]  BIOS-e820: 0000000017ef0000 - 0000000017effc00 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000017effc00 - 0000000017f00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000017f00000 - 0000000018000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 382MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 98032
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 93936 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6550
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x17efac70
[17179569.184000] ACPI: FADT (v001 INTEL  Whitney  0x06040000 PTL  0x000f4240) @ 0x17effb32
[17179569.184000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x17effba6
[17179569.184000] ACPI: DSDT (v001  INTEL  Whitney 0x06040000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:8 APIC version 17
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7f00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1000.126 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.904000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.908000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.952000] Memory: 378728k/392128k available (1910k kernel code, 12816k reserved, 1070k data, 308k init, 0k highmem)
[17179569.952000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.032000] Calibrating delay using timer specific routine.. 2002.24 BogoMIPS (lpj=4004482)
[17179570.032000] Security Framework v1.0.0 initialized
[17179570.032000] SELinux:  Disabled at boot.
[17179570.032000] Mount-cache hash table entries: 512
[17179570.032000] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.032000] CPU: After vendor identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.032000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179570.032000] CPU: L2 cache: 128K
[17179570.032000] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[17179570.032000] Checking 'hlt' instruction... OK.
[17179570.048000] SMP alternatives: switching to UP code
[17179570.048000] Freeing SMP alternatives: 16k freed
[17179570.048000] checking if image is initramfs... it is
[17179571.164000] Freeing initrd memory: 5564k freed
[17179571.164000] ACPI: Core revision 20060707
[17179571.164000] ACPI: Looking for DSDT ... not found!
[17179571.168000] CPU0: Intel Celeron (Coppermine) stepping 0a
[17179571.168000] Total of 1 processors activated (2002.24 BogoMIPS).
[17179571.168000] ENABLING IO-APIC IRQs
[17179571.168000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179571.312000] Brought up 1 CPUs
[17179571.312000] migration_cost=0
[17179571.312000] NET: Registered protocol family 16
[17179571.312000] EISA bus registered
[17179571.312000] ACPI: bus type pci registered
[17179571.312000] PCI: PCI BIOS revision 2.10 entry at 0xfd9b0, last bus=1
[17179571.312000] PCI: Using configuration type 1
[17179571.312000] Setting up standard PCI resources
[17179571.324000] ACPI: Interpreter enabled
[17179571.324000] ACPI: Using IOAPIC for interrupt routing
[17179571.324000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.324000] PCI: Probing PCI hardware (bus 00)
[17179571.324000] Boot video device is 0000:00:01.0
[17179571.324000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179571.324000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179571.324000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179571.328000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.328000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.332000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[17179571.332000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[17179571.332000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
[17179571.332000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[17179571.336000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[17179571.336000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.336000] pnp: PnP ACPI init
[17179571.376000] pnp: PnP ACPI: found 13 devices
[17179571.376000] PnPBIOS: Disabled by ACPI PNP
[17179571.376000] PCI: Using ACPI for IRQ routing
[17179571.376000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.380000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:01.0
[17179571.380000] PCI: Bridge: 0000:00:1e.0
[17179571.380000]   IO window: disabled.
[17179571.380000]   MEM window: f4100000-f41fffff
[17179571.380000]   PREFETCH window: disabled.
[17179571.380000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.380000] NET: Registered protocol family 2
[17179571.416000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179571.416000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179571.416000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179571.416000] TCP: Hash tables configured (established 16384 bind 8192)
[17179571.416000] TCP reno registered
[17179571.420000] audit: initializing netlink socket (disabled)
[17179571.420000] audit(1200263452.420:1): initialized
[17179571.420000] VFS: Disk quotas dquot_6.5.1
[17179571.420000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.420000] Initializing Cryptographic API
[17179571.420000] io scheduler noop registered
[17179571.420000] io scheduler anticipatory registered
[17179571.420000] io scheduler deadline registered
[17179571.420000] io scheduler cfq registered (default)
[17179571.420000] isapnp: Scanning for PnP cards...
[17179571.776000] isapnp: No Plug & Play device found
[17179571.916000] Real Time Clock Driver v1.12ac
[17179571.916000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.916000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.920000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.920000] mice: PS/2 mouse device common for all mice
[17179571.924000] RAMDISK driver initialized: 16 RAM disks of 1048576K size 1024 blocksize
[17179571.924000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.924000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.924000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179571.924000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.924000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.928000] EISA: Probing bus 0 at eisa.0
[17179571.928000] Cannot allocate resource for EISA slot 1
[17179571.928000] EISA: Detected 0 cards.
[17179571.928000] TCP bic registered
[17179571.928000] NET: Registered protocol family 1
[17179571.928000] NET: Registered protocol family 8
[17179571.928000] NET: Registered protocol family 20
[17179571.928000] Using IPI No-Shortcut mode
[17179571.928000] ACPI: (supports S0 S1 S5)
[17179571.928000] Freeing unused kernel memory: 308k freed
[17179571.956000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.248000] Capability LSM initialized
[17179573.380000] ACPI: Invalid PBLK length [5]
[17179575.076000] ICH: IDE controller at PCI slot 0000:00:1f.1
[17179575.076000] ICH: chipset revision 2
[17179575.076000] ICH: not 100% native mode: will probe irqs later
[17179575.076000]     ide0: BM-DMA at 0x1800-0x1807, BIOS settings: hda:DMA, hdb:pio
[17179575.076000]     ide1: BM-DMA at 0x1808-0x180f, BIOS settings: hdc:DMA, hdd:pio
[17179575.076000] Probing IDE interface ide0...
[17179575.368000] hda: WDC WD3200JB-00KFA0, ATA DISK drive
[17179576.040000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.044000] Probing IDE interface ide1...
[17179576.784000] hdc: SONY DVD RW DRU-720A, ATAPI CD/DVD-ROM drive
[17179577.460000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.480000] hda: max request size: 512KiB
[17179577.508000] hda: 625142448 sectors (320072 MB) w/8192KiB Cache, CHS=38913/255/63, UDMA(66)
[17179577.512000] hda: cache flushes supported
[17179577.512000]  hda: hda1 hda2 < hda5 hda6 >
[17179577.580000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.580000] Uniform CD-ROM driver Revision: 3.20
[17179578.296000] usbcore: registered new driver usbfs
[17179578.296000] usbcore: registered new driver hub
[17179578.304000] USB Universal Host Controller Interface driver v3.0
[17179578.304000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 169
[17179578.304000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[17179578.304000] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[17179578.308000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[17179578.308000] uhci_hcd 0000:00:1f.2: irq 169, io base 0x00001820
[17179578.308000] usb usb1: configuration #1 chosen from 1 choice
[17179578.308000] hub 1-0:1.0: USB hub found
[17179578.308000] hub 1-0:1.0: 2 ports detected
[17179578.336000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.420000] ACPI: PCI Interrupt 0000:01:0e.0[A] -> GSI 16 (level, low) -> IRQ 177
[17179578.420000] ohci_hcd 0000:01:0e.0: OHCI Host Controller
[17179578.420000] ohci_hcd 0000:01:0e.0: new USB bus registered, assigned bus number 2
[17179578.420000] ohci_hcd 0000:01:0e.0: irq 177, io mem 0xf4100000
[17179578.508000] usb usb2: configuration #1 chosen from 1 choice
[17179578.508000] hub 2-0:1.0: USB hub found
[17179578.508000] hub 2-0:1.0: 3 ports detected
[17179578.612000] ACPI: PCI Interrupt 0000:01:0e.1[B] -> GSI 17 (level, low) -> IRQ 185
[17179578.612000] ohci_hcd 0000:01:0e.1: OHCI Host Controller
[17179578.616000] ohci_hcd 0000:01:0e.1: new USB bus registered, assigned bus number 3
[17179578.616000] ohci_hcd 0000:01:0e.1: irq 185, io mem 0xf4101000
[17179578.652000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179578.704000] usb usb3: configuration #1 chosen from 1 choice
[17179578.704000] hub 3-0:1.0: USB hub found
[17179578.704000] hub 3-0:1.0: 2 ports detected
[17179578.816000] ACPI: PCI Interrupt 0000:01:0e.2[C] -> GSI 18 (level, low) -> IRQ 193
[17179578.816000] ehci_hcd 0000:01:0e.2: EHCI Host Controller
[17179578.816000] ehci_hcd 0000:01:0e.2: new USB bus registered, assigned bus number 4
[17179578.840000] ehci_hcd 0000:01:0e.2: irq 193, io mem 0xf4102000
[17179578.840000] ehci_hcd 0000:01:0e.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.840000] usb usb4: configuration #1 chosen from 1 choice
[17179578.844000] hub 4-0:1.0: USB hub found
[17179578.844000] hub 4-0:1.0: 5 ports detected
[17179578.848000] usb 1-1: configuration #1 chosen from 1 choice
[17179579.220000] usb 4-2: new high speed USB device using ehci_hcd and address 2
[17179579.364000] usb 4-2: configuration #1 chosen from 1 choice
[17179579.388000] usbcore: registered new driver libusual
[17179579.428000] SCSI subsystem initialized
[17179579.432000] Initializing USB Mass Storage driver...
[17179579.432000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179579.432000] usbcore: registered new driver usb-storage
[17179579.432000] USB Mass Storage support registered.
[17179579.436000] usb-storage: device found at 2
[17179579.436000] usb-storage: waiting for device to settle before scanning
[17179580.600000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179580.628000] ISO 9660 Extensions: RRIP_1991A
[17179580.676000] Registering unionfs 1.1.4
[17179580.716000] loop: loaded (max 8 devices)
[17179580.824000] squashfs: version 3.0 (2006/03/15) Phillip Lougher
[17179584.436000] usb-storage: device scan complete
[17179584.440000]   Vendor: MDT MD25  Model: MDT-MCAL74817886  Rev: 2D08
[17179584.440000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179584.468000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179584.468000] sda: Write Protect is off
[17179584.468000] sda: Mode Sense: 00 38 00 00
[17179584.468000] sda: assuming drive cache: write through
[17179584.468000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[17179584.468000] sda: Write Protect is off
[17179584.468000] sda: Mode Sense: 00 38 00 00
[17179584.468000] sda: assuming drive cache: write through
[17179584.468000]  sda: sda1
[17179584.480000] sd 0:0:0:0: Attached scsi disk sda
[17179652.236000] input: PC Speaker as /class/input/input1
[17179653.020000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179653.056000] Linux agpgart interface v0.101 (c) Dave Jones
[17179653.076000] agpgart: Detected an Intel i810 Chipset.
[17179653.088000] agpgart: AGP aperture is 64M @ 0xf8000000
[17179653.152000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179653.196000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179653.304000] parport: PnPBIOS parport detected.
[17179653.304000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179653.364000] Floppy drive(s): fd0 is 1.44M
[17179653.384000] FDC 0 is a post-1991 82077
[17179653.408000] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[17179653.596000] hw_random: RNG not detected
[17179653.952000] ts: Compaq touchscreen protocol output
[17179654.020000] drivers/usb/net/rtl8150.c: rtl8150 based usb-ethernet driver v0.6.2 (2004/08/27)
[17179654.024000] drivers/usb/net/rtl8150.c: eth0: rtl8150 is detected
[17179654.024000] usbcore: registered new driver rtl8150
[17179654.716000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 185
[17179654.716000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179655.036000] intel8x0_measure_ac97_clock: measured 59089 usecs
[17179655.036000] intel8x0: clocking to 48000
[17179656.308000] drivers/usb/net/rtl8150.c: eth0: allmulti set
[17179656.308000] drivers/usb/net/rtl8150.c: eth0: allmulti set
[17179656.308000] drivers/usb/net/rtl8150.c: eth0: allmulti set
[17179656.616000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179657.600000] NET: Registered protocol family 17
[17179659.560000] drivers/usb/net/rtl8150.c: eth0: allmulti set
[17179659.560000] drivers/usb/net/rtl8150.c: eth0: allmulti set
[17179672.328000] ACPI: Power Button (FF) [PWRF]
[17179672.328000] ACPI: Power Button (CM) [PWRB]
[17179672.668000] ibm_acpi: ec object not found
[17179672.748000] pcc_acpi: loading...
[17179677.784000] lp0: using parport0 (interrupt-driven).
[17179678.492000] ppdev: user-space parallel port driver
[17179680.104000] NET: Registered protocol family 10
[17179680.104000] lo: Disabled Privacy Extensions
[17179680.104000] drivers/usb/net/rtl8150.c: eth0: allmulti set
[17179680.104000] drivers/usb/net/rtl8150.c: eth0: allmulti set
[17179680.104000] IPv6 over IPv4 tunneling driver
[17179690.048000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179690.048000] apm: overridden by ACPI.
[17179690.744000] eth0: no IPv6 routers present
[17179717.696000] Bluetooth: Core ver 2.8
[17179717.696000] NET: Registered protocol family 31
[17179717.696000] Bluetooth: HCI device and connection manager initialized
[17179717.696000] Bluetooth: HCI socket layer initialized
[17179717.932000] Bluetooth: L2CAP ver 2.8
[17179717.932000] Bluetooth: L2CAP socket layer initialized
[17179719.024000] Bluetooth: RFCOMM socket layer initialized
[17179719.024000] Bluetooth: RFCOMM TTY layer initialized
[17179719.024000] Bluetooth: RFCOMM ver 1.7
[17179740.800000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179740.804000] NTFS-fs warning (device sda1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
[17179740.892000] NTFS volume version 3.1.
```

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"
```

---

### Post by geirha on 2008-01-13
> **abbigail said:**
> ```

[17179577.480000] hda: max request size: 512KiB
[17179577.508000] hda: 625142448 sectors (320072 MB) w/8192KiB Cache, CHS=38913/255/63, UDMA(66)
[17179577.512000] hda: cache flushes supported
[17179577.512000]  hda: hda1 hda2 < hda5 hda6 >
[17179577.580000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
```

According to this, it finds an ide drive with 4 partitions, and I couldn't see any errors about it, so it's odd that fdisk can't find it.

Are the device nodes there? ```
ls -l /dev/hda*
```
if not, try adding them manually and see if you can mount it then:
```
sudo mknod /dev/hda b 3 0
sudo mknod /dev/hda1 b 3 1
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows

```

If that works, there must be a bug with udev on that ubuntu CD

---

### Post by abbigail on 2008-01-13
this is so weird. before you even replied i tried the sudo mount hda1 code again and it worked? then i tried hd5 and it showed one of my other partitions. i don't get it! i'm so afraid that whenever i restart ubuntu it won't work again, yet i need to. still a problem though. it says i don't have permission to write to my external hd (when i try to move files from /media/windows over to it.) am i forgetting a simple process that i knew last year? how do i move files over..?

---

### Post by geirha on 2008-01-13
Edgy doesn't have ntfs-3g which you need in order to write to an ntfs partition, you'll need to install it. It should be possible to install that while the liveCD is loaded though. You could try this guide which was the first hit on my google search: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Have you tried checking the cables to the harddrive btw? could be one of the cables isn't connected 100%

Oh, and when you get your system back up to normal, get a copy of the latest ubuntu cd. It comes with the ntfs-3g driver out of the box ;)

---

### Post by abbigail on 2008-01-13
i have 2 internals so i can download that right now if it'll help! i never needed it before though when i transferred files from an internal to this same external. everything seems to be hooked up properly. especially since i have to keep unplugging my internals to switch back and forth (with the system off of course.) i wonder what changed to let me see my files. where's the logic! i typed it in dozens of times over the past week, so a typo couldn't have been it. straaange.

---

### Post by geirha on 2008-01-13
Is it possible you were using a different filesystem on your external drive at that point? FAT32 for instance ...

Perhaps it's the ide-cable itself that is the problem...

---

### Post by abbigail on 2008-01-14
do externals come as FAT32 to begin with? i don't even remember. i did a lot of partitioning for the first time though after i got everything set back up. i noticed on the internal hd that a few of the pins or whatever they are were bent (where i plug the long thin gray thingy into.) i had to adjust them to even plug it in. maybe that was the issue. almost 100% downloaded for 7.10, lal ala lal a..

---

### Post by abbigail on 2008-01-14
small question. i write the downloaded iso to a disc with Nero's bootable option, yes? just as i did earlier in the week with the Knoppix that somebody suggested, both show a bunch of text and then want me to enter something after A:\> or something like that. i didn't see anything mentioned about that and with 6.10 it just lets me choose to "start" Ubuntu. i'll need to write it again forever from now as my good internal just died on me too! again! ah i love that operating system not found message :] hours and hours of reformatting, downloading all of Microsoft's updates and restarting my pc a couple dozen times definitely fills in a day..

---

### Post by geirha on 2008-01-14
The iso contains the boot information, so you should not select any extra boot options in nero. I did a quick google just now, and found this: [http://ubuntuclips.org/videos_5.html](http://ubuntuclips.org/videos_5.html) A video of how to burn the ubuntu iso with nero :)

Do you have any extra ide cables around? perhaps try another one ...

---

### Post by abbigail on 2008-01-14
well that problem's solved. yet again "hda1 doesn't exist". woohoo! the time it DID exist, i looked under the proc/ide folder like said and i saw hda, hda1, hdc, and some others. under 7.10, there's only a file called "drivers". everything's seemingly plugged in fine. i don't think it'd be the cables because i unplug them and plug them into my other internal which works. i don't have any extra cables either. maybe it's just luck? randomly it'll let me access it? hm. thankfully i can copy files to my external now, just waiting for my internal to say hello :[

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000017ef0000 - 0000000017effc00 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017effc00 - 0000000017f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000017f00000 - 0000000018000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 382MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 98032) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    98032
[    0.000000]   HighMem     98032 ->    98032
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    98032
[    0.000000] On node 0 totalpages: 98032
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 733 pages used for memmap
[    0.000000]   Normal zone: 93203 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6550 checksum 0
[    0.000000] ACPI: RSDP 000F6550, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 17EFAC70, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 17EFFB32, 0074 (r1 INTEL  Whitney   6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 17EFAC9C, 4E96 (r1  INTEL  Whitney  6040000 MSFT  100000B)
[    0.000000] ACPI: FACS 17EFFFC0, 0040
[    0.000000] ACPI: APIC 17EFFBA6, 005A (r1 PTLTD    APIC    6040000  LTP        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7f00000)
[    0.000000] Built 1 zonelists.  Total pages: 97267
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1000.064 MHz processor.
[   55.972426] Console: colour VGA+ 80x25
[   55.973933] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   55.976199] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   56.020822] Memory: 376844k/392128k available (2015k kernel code, 14656k reserved, 916k data, 364k init, 0k highmem)
[   56.020846] virtual kernel memory layout:
[   56.020848]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   56.020851]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   56.020854]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   56.020857]     lowmem  : 0xc0000000 - 0xd7ef0000   ( 382 MB)
[   56.020860]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   56.020863]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   56.020866]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   56.020873] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   56.020966] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   56.100928] Calibrating delay using timer specific routine.. 2001.76 BogoMIPS (lpj=4003526)
[   56.100999] Security Framework v1.0.0 initialized
[   56.101022] SELinux:  Disabled at boot.
[   56.101059] Mount-cache hash table entries: 512
[   56.101414] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   56.101443] CPU: L1 I cache: 16K, L1 D cache: 16K
[   56.101449] CPU: L2 cache: 128K
[   56.101458] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[   56.101484] Compat vDSO mapped to ffffe000.
[   56.101530] Checking 'hlt' instruction... OK.
[   56.117190] SMP alternatives: switching to UP code
[   56.117681] Freeing SMP alternatives: 11k freed
[   56.118391] Early unpacking initramfs... done
[   56.927847] ACPI: Core revision 20070126
[   56.928254] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   56.931806] CPU0: Intel Celeron (Coppermine) stepping 0a
[   56.931870] Total of 1 processors activated (2001.76 BogoMIPS).
[   56.932031] ENABLING IO-APIC IRQs
[   56.932320] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   57.076235] Brought up 1 CPUs
[   57.076620] Booting paravirtualized kernel on bare hardware
[   57.076777] Time: 18:18:52  Date: 00/14/108
[   57.076872] NET: Registered protocol family 16
[   57.077273] EISA bus registered
[   57.077310] ACPI: bus type pci registered
[   57.077934] PCI: PCI BIOS revision 2.10 entry at 0xfd9b0, last bus=1
[   57.077941] PCI: Using configuration type 1
[   57.077946] Setting up standard PCI resources
[   57.082964] ACPI: EC: Look up EC in DSDT
[   57.091652] ACPI: Interpreter enabled
[   57.091670] ACPI: (supports S0 S1 S5)
[   57.091710] ACPI: Using IOAPIC for interrupt routing
[   57.100989] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   57.101019] PCI: Probing PCI hardware (bus 00)
[   57.101405] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   57.101414] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   57.101939] PCI: Transparent bridge - 0000:00:1e.0
[   57.101990] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   57.102413] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[   57.105808] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   57.105994] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   57.106165] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   57.106337] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   57.106697] Linux Plug and Play Support v0.97 (c) Adam Belay
[   57.106738] pnp: PnP ACPI init
[   57.106794] ACPI: bus type pnp registered
[   57.137898] pnp: PnP ACPI: found 13 devices
[   57.137912] ACPI: ACPI bus type pnp unregistered
[   57.137924] PnPBIOS: Disabled by ACPI PNP
[   57.138146] PCI: Using ACPI for IRQ routing
[   57.138156] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   57.140668] NET: Registered protocol family 8
[   57.140674] NET: Registered protocol family 20
[   57.140989] pnp: 00:01: iomem range 0xff800000-0xffffffff could not be reserved
[   57.144043] Time: tsc clocksource has been installed.
[   57.172342] PCI: Bridge: 0000:00:1e.0
[   57.172346]   IO window: disabled.
[   57.172356]   MEM window: f4100000-f41fffff
[   57.172364]   PREFETCH window: disabled.
[   57.172385] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   57.172454] NET: Registered protocol family 2
[   57.212155] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   57.212362] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   57.213464] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   57.214336] TCP: Hash tables configured (established 16384 bind 16384)
[   57.214346] TCP reno registered
[   57.224420] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   57.815754]  it is
[   58.675096] Freeing initrd memory: 7305k freed
[   58.676631] audit: initializing netlink socket (disabled)
[   58.676675] audit(1200334733.520:1): initialized
[   58.685331] VFS: Disk quotas dquot_6.5.1
[   58.685626] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   58.686073] io scheduler noop registered
[   58.686084] io scheduler anticipatory registered
[   58.686089] io scheduler deadline registered
[   58.686187] io scheduler cfq registered (default)
[   58.686229] Boot video device is 0000:00:01.0
[   58.686972] isapnp: Scanning for PnP cards...
[   59.040678] isapnp: No Plug & Play device found
[   59.223241] Real Time Clock Driver v1.12ac
[   59.223534] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   59.223699] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   59.226891] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   59.230258] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   59.230836] input: Macintosh mouse button emulation as /class/input/input0
[   59.231164] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   59.234177] serio: i8042 KBD port at 0x60,0x64 irq 1
[   59.234196] serio: i8042 AUX port at 0x60,0x64 irq 12
[   59.234931] mice: PS/2 mouse device common for all mice
[   59.235443] EISA: Probing bus 0 at eisa.0
[   59.235467] Cannot allocate resource for EISA slot 1
[   59.235503] EISA: Detected 0 cards.
[   59.235777] TCP cubic registered
[   59.235824] NET: Registered protocol family 1
[   59.235899] Using IPI No-Shortcut mode
[   59.236409]   Magic number: 8:201:342
[   59.238568] Freeing unused kernel memory: 364k freed
[   59.290160] input: AT Translated Set 2 keyboard as /class/input/input1
[   60.963270] AppArmor: AppArmor initialized<5>audit(1200334735.520:2):  type=1505 info="AppArmor initialized" pid=1156
[   60.991414] fuse init (API version 7.8)
[   61.012102] Failure registering capabilities with primary security module.
[   61.054272] ACPI: Invalid PBLK length [5]
[   63.254594] SCSI subsystem initialized
[   63.276213] libata version 2.21 loaded.
[   63.291076] ata_piix 0000:00:1f.1: version 2.11
[   63.291244] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   63.291644] scsi0 : ata_piix
[   63.291812] scsi1 : ata_piix
[   63.291925] ata1: PATA max UDMA/66 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011800 irq 14
[   63.291933] ata2: PATA max UDMA/66 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011808 irq 15
[   63.291995] ata1: port disabled. ignoring.
[   63.328842] usbcore: registered new interface driver usbfs
[   63.328936] usbcore: registered new interface driver hub
[   63.329025] usbcore: registered new device driver usb
[   63.332777] USB Universal Host Controller Interface driver v3.0
[   63.357861] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   63.701912] ata2.00: ATAPI: SONY    DVD RW DRU-720A, JY03, max UDMA/66
[   63.701941] ata2.00: limited to UDMA/33 due to 40-wire cable
[   63.756860] Floppy drive(s): fd0 is 1.44M
[   63.806700] FDC 0 is a post-1991 82077
[   63.873857] ata2.00: configured for UDMA/33
[   63.875080] scsi 1:0:0:0: CD-ROM            SONY     DVD RW DRU-720A  JY03 PQ: 0 ANSI: 5
[   63.875362] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 16
[   63.875390] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   63.875399] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   63.875856] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   63.875918] uhci_hcd 0000:00:1f.2: irq 16, io base 0x00001820
[   63.876315] usb usb1: configuration #1 chosen from 1 choice
[   63.876394] hub 1-0:1.0: USB hub found
[   63.876422] hub 1-0:1.0: 2 ports detected
[   63.978160] ACPI: PCI Interrupt 0000:01:0e.0[A] -> GSI 16 (level, low) -> IRQ 17
[   63.978201] ohci_hcd 0000:01:0e.0: OHCI Host Controller
[   63.978300] ohci_hcd 0000:01:0e.0: new USB bus registered, assigned bus number 2
[   63.978351] ohci_hcd 0000:01:0e.0: irq 17, io mem 0xf4100000
[   64.064358] usb usb2: configuration #1 chosen from 1 choice
[   64.064443] hub 2-0:1.0: USB hub found
[   64.064476] hub 2-0:1.0: 3 ports detected
[   64.165521] ACPI: PCI Interrupt 0000:01:0e.1[B] -> GSI 17 (level, low) -> IRQ 18
[   64.165555] ohci_hcd 0000:01:0e.1: OHCI Host Controller
[   64.165639] ohci_hcd 0000:01:0e.1: new USB bus registered, assigned bus number 3
[   64.165677] ohci_hcd 0000:01:0e.1: irq 18, io mem 0xf4101000
[   64.250965] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   64.252134] usb usb3: configuration #1 chosen from 1 choice
[   64.252217] hub 3-0:1.0: USB hub found
[   64.252246] hub 3-0:1.0: 2 ports detected
[   64.353725] ACPI: PCI Interrupt 0000:01:0e.2[C] -> GSI 18 (level, low) -> IRQ 19
[   64.353766] ehci_hcd 0000:01:0e.2: EHCI Host Controller
[   64.353865] ehci_hcd 0000:01:0e.2: new USB bus registered, assigned bus number 4
[   64.377102] ehci_hcd 0000:01:0e.2: irq 19, io mem 0xf4102000
[   64.377122] ehci_hcd 0000:01:0e.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   64.377459] usb usb4: configuration #1 chosen from 1 choice
[   64.377539] hub 4-0:1.0: USB hub found
[   64.377574] hub 4-0:1.0: 5 ports detected
[   64.436737] usb 1-1: configuration #1 chosen from 1 choice
[   64.568800] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   64.568906] Uniform CD-ROM driver Revision: 3.20
[   64.569787] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   64.585218] sr 1:0:0:0: Attached scsi generic sg0 type 5
[   64.808603] usb 4-2: new high speed USB device using ehci_hcd and address 2
[   64.900524] end_request: I/O error, dev fd0, sector 0
[   64.943883] usb 4-2: configuration #1 chosen from 1 choice
[   64.986822] usbcore: registered new interface driver libusual
[   65.011173] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   65.011190] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   65.022078] Initializing USB Mass Storage driver...
[   65.022333] scsi2 : SCSI emulation for USB Mass Storage devices
[   65.022513] usb-storage: device found at 2
[   65.022520] usb-storage: waiting for device to settle before scanning
[   65.022570] usbcore: registered new interface driver usb-storage
[   65.022577] USB Mass Storage support registered.
[   65.447927] ISO 9660 Extensions: Microsoft Joliet Level 3
[   65.476374] ISO 9660 Extensions: RRIP_1991A
[   65.767534] Registering unionfs 1.4
[   65.767547] unionfs: debugging is not enabled
[   65.833472] loop: module loaded
[   66.107199] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
[   70.016100] usb-storage: device scan complete
[   70.017205] scsi 2:0:0:0: Direct-Access     MDT MD25 MDT-MCAL74817886 2D08 PQ: 0 ANSI: 2 CCS
[   70.021290] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   70.044491] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   70.045204] sd 2:0:0:0: [sda] Write Protect is off
[   70.045211] sd 2:0:0:0: [sda] Mode Sense: 00 38 00 00
[   70.045218] sd 2:0:0:0: [sda] Assuming drive cache: write through
[   70.046334] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   70.047073] sd 2:0:0:0: [sda] Write Protect is off
[   70.047080] sd 2:0:0:0: [sda] Mode Sense: 00 38 00 00
[   70.047085] sd 2:0:0:0: [sda] Assuming drive cache: write through
[   70.047102]  sda: sda1
[   70.066921] sd 2:0:0:0: [sda] Attached SCSI disk
[  150.549843] Linux agpgart interface v0.102 (c) Dave Jones
[  150.681754] agpgart: Detected an Intel i810 Chipset.
[  150.694491] agpgart: AGP aperture is 64M @ 0xf8000000
[  150.747802] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[  151.193601] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  151.224036] iTCO_vendor_support: vendor-support=0
[  151.227976] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[  151.228221] iTCO_wdt: Found a ICH TCO device (Version=1, TCOBASE=0x1060)
[  151.228380] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  151.275898] intel_rng: FWH not detected
[  151.839982] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  152.496605] input: PC Speaker as /class/input/input2
[  152.499807] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[  152.739379] parport_pc 00:0a: reported by Plug and Play ACPI
[  152.739440] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  153.792425] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: rtl8150 based usb-ethernet driver v0.6.2 (2004/08/27)
[  153.820884] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: rtl8150 is detected
[  153.820965] usbcore: registered new interface driver rtl8150
[  154.354536] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 18
[  154.354591] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  154.949238] intel8x0_measure_ac97_clock: measured 55441 usecs
[  154.949254] intel8x0: clocking to 48000
[  163.779023] No dock devices found.
[  164.591798] input: Power Button (FF) as /class/input/input4
[  164.592671] ACPI: Power Button (FF) [PWRF]
[  164.627774] input: Power Button (CM) as /class/input/input5
[  164.628790] ACPI: Power Button (CM) [PWRB]
[  172.803374] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  172.803881] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  173.297959] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  173.416134] lp0: using parport0 (interrupt-driven).
[  173.551482] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  173.593876] ppdev: user-space parallel port driver
[  173.649051] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  174.004097] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  174.182874] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  175.505686] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  175.586184] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  175.586200] apm: overridden by ACPI.
[  175.753005] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  175.908170] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  176.032836] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  176.196296] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  176.294144] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  176.529546] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  176.673398] Failure registering capabilities with primary security module.
[  176.690983] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  176.912858] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  176.978751] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  177.123036] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  177.575377] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  177.852194] Bluetooth: Core ver 2.11
[  177.852569] NET: Registered protocol family 31
[  177.852581] Bluetooth: HCI device and connection manager initialized
[  177.852591] Bluetooth: HCI socket layer initialized
[  177.992878] Bluetooth: L2CAP ver 2.8
[  177.992892] Bluetooth: L2CAP socket layer initialized
[  178.216430] Bluetooth: RFCOMM socket layer initialized
[  178.216659] Bluetooth: RFCOMM TTY layer initialized
[  178.216665] Bluetooth: RFCOMM ver 1.8
[  179.753976] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  182.207673] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  182.207997] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  183.548850] NET: Registered protocol family 17
[  185.576296] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  185.578113] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  185.579748] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  185.581324] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  185.584362] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  185.585848] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  185.587621] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  185.983678] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  185.985415] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  187.817688] NET: Registered protocol family 10
[  187.818558] lo: Disabled Privacy Extensions
[  187.819135] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  187.819212] /build/buildd/linux-source-2.6.22-2.6.22/drivers/net/usb/rtl8150.c: eth0: allmulti set
[  198.283050] eth0: no IPv6 routers present
```

---

### Post by geirha on 2008-01-14
> **abbigail said:**
> ```

[   63.291995] ata1: port disabled. ignoring.

```

I believe this indicates that nothing is connected to the first ata-slot. (Not that linux is able to detect anyways) It's hard to know what's wrong. Just for testing, could you try to unplug the ide-cables out of the internal harddrive and the cdrom, then put the one that was in the cdrom, in the harddrive and vice versa, so the cdrom becomes primary master, while the harddrive becomes secondary master? The result should indicate whether there's something wrong with the cable or the connection on the motherboard. 

Other things I could think off, is trying to change the jumper on the harddrive, switching between cable-select and single-master, and see if that changes anything. Might be the bios is picky about that jumper setting.

Other than that, I'm out of ideas. Try rebooting till it magically works again ...?

Also, if the harddrive starts working again in gutsy, it will probably be named /dev/sda instead of /dev/hda or /dev/hdc. And the external will probably be /dev/sdb... and check /proc/scsi/scsi instead of /proc/ide.

---

### Post by abbigail on 2008-01-15
i switched the cables like you said and it seems to be working every time now, but..

```
ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/windows -t ntfs -o nls=utf8,umask=0222
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/windows ntfs-3g defaults,force 0 0
ubuntu@ubuntu:~$ mount -t ntfs-3g /dev/sda1 /media/windows -o force
mount: only root can do that
```

what! all 3 partitions even showed up when starting Ubuntu, labeled by their GB size.

---

### Post by kvonb on 2008-01-15
.-

---

### Post by abbigail on 2008-01-15
can those tools be installed and used on a live cd? how and what are they?

---

### Post by kvonb on 2008-01-15
-

---

### Post by jocko on 2008-01-15
> **abbigail said:**
> ```

ubuntu@ubuntu:~$ mount -t ntfs-3g /dev/sda1 /media/windows -o force
mount: only root can do that
```

The error message means this last command will only work if you put 'sudo' in front of it. Try again.

---

### Post by abbigail on 2008-01-15
eep! that worked! i hope this is the end of my Ubuntu problems. tyvm to everyone :3

before i wait days for it all to transfer (180+ gb :[), there's a problem i had when writing Knoppix/Ubuntu to cd's. both times i used my internal (that i can safely reformat without losing valuable data) to write them and after each finished and i had shut down (on different days), the internal i wrote them with had "operating system not found" on the next startup, even when i never tried using Knoppix/Ubuntu on them, just written with them. is this Ubuntu's fault? is it avoidable? at least for now i won't have to make any more cd's of Ubuntu.

i think that gray cable thingy (is that called an ide cable?) has gone bad. since switching it to the dvd/cd writer, the writer gets errors when copying files off discs. what makes them go bad? being too wrinkled/crooked? i should probably stop asking questions..

---

### Post by vanadium on 2008-01-17
Be aware that this is a temporary solution that allows you to access the data and copy it off the drive. The filesystem remains damaged, and you should not continue using the file system as is without having it repaired. You should either

* repair the ntfs volume using MS Windows
* copy the data elsewhere, reformat the disk and place the data back.

The linux tool "ntfsfix" might also be able to repair the ntfs volume, but is less guaranteed because the ntfs system is proprietary and has secrets.

---

### Post by geirha on 2008-01-18
> **abbigail said:**
> i think that gray cable thingy (is that called an ide cable?) has gone bad. since switching it to the dvd/cd writer, the writer gets errors when copying files off discs. what makes them go bad? being too wrinkled/crooked? i should probably stop asking questions..

Not exactly sure what the correct word for it is, but it's usually called IDE cable or ATA cable. The conductors inside it are very thin, so too much bending back and forth may damage some of them. They are fairly cheap though, so just buy a new one.

---


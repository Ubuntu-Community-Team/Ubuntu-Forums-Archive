---
title: "Nobody knows, CD-ROM"
date: 2007-08-18
forum: General Help
---

### Post by Ubunme2 on 2007-08-18
Dell Inspiron with Ubuntu 7.04, everything else is fine but it won't mount the CD-ROM.


The CD-ROM works, the operating system was installed from it, it is enabled in the bios, it shows up fine in the CD-ROM "drive properties" dialog box as a Samsung CD-ROM SC-148F.

Yes, there is a CD in the drive. and I have tried many different CDs both audio and data. Yes, I have checked the forums and read dozens of similar threads. 

I have tried to mount the device through the terminal, (many different ways) "no medium found", "mount point does not exist" or "permission denied". 

I have also installed "p mount" -hal for auto mount. All to no avail.

Doesn't anybody know what's wrong?  (Fourth posting)

---

### Post by HermanAB on 2007-08-18
Hmm, 'mount point doesn't exist'???

Try this:
$ sudo mkdir /media/cdrom
$ sudo mount -t iso9660 /dev/cdrom /media/cdrom

and see wat it tells you.

Cheers,

Herman

---

### Post by Ubunme2 on 2007-08-18
Thank you for your help, this problem hasn't gotten many replies.

When I tried:
sudo mkdir /media/cdrom

The answer I got was: 
cannot create directory ` /media/cdrom' : file exists

And when I entered:
sudo mount -t iso9660 /dev/cdrom /media/cdrom

I get the answer: 
mount: no medium found


I finally got into:
sudo nano etc/fatab  
and I found:
/dev/scd0 /media/cdrom0 udf ,iso9660 user ,noauto 00

---

### Post by Ubunme2 on 2007-08-18
Ok,

now I just got this:

dell@dell-desktop:~$ sudo mount -t iso9660 /dev/cdrom/media/cdrom
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
dell@dell-desktop:~$

---

### Post by HermanAB on 2007-08-18
In that last try, you are missing a space between the device and the mount point.

You have the mount point /media/cdrom.

What seems to be wrong is the device name.  Type:
$ ls /dev

to see all devices.  Try to identify the CDROM and substitute it in the mount command.

Cheers,

H.

---

### Post by jb1789 on 2007-08-18
I'm not sure if you have the same problem that I did, but try typing

```
sudo gedit /etc/modules
```

in the terminal and add

```
ide-generic
```

to the file.


JB

---

### Post by Ubunme2 on 2007-08-18
Yes, thank you, I took out that space (while trying many combinations) to make sure that I wasn't doing anything wrong while entering the command because of the "no medium found" answer.

I tried the new command that you suggested: "$ ls /dev " and found nothing close to "CD-ROM" (lots of gibberish though, I wish it would have let me copy and paste it here)

(Getting a little bit disappointed that 7.04 didn't work right out of the box like all of the other distributions)
 (I just want to put in a CD and have it play so I can give this computer away)

---

### Post by Ubunme2 on 2007-08-18
jb1789, 
Thank you, your suggestion looks very promising, I typed:

sudo gedit /etc/modules

In the terminal and got this:

# /etc/modules: kernel modules to load at boot time.
#
#this file contains the names of kernel modules that should be loaded
#at boot time, one per line.  Lines beginning with"#" are ignored.

Fuse
lp

And then I typed:

ide-generic

In the terminal, I am going to reboot with my fingers crossed.

---

### Post by Ubunme2 on 2007-08-18
No good,

Put a CD in the drive and nothing happens, go to "my computer" and search the CD-ROM that way, same answer "unable to mount media.  There is probably no media in the drive".

This is the first time I am installing 7.04, is there any special application has to be installed separately just to play a CD?

---

### Post by gmaniac on 2007-08-18
Take a look at System -> Administration -> System log
Do you see any errors there at the various logs.

You could also post the output of these commands ```
dmesg
``` 
and 
```
lsmod
```

after you insert a cd.

---

### Post by Ubunme2 on 2007-08-19
Thank You for your help.

This is what I get with: dmesg:

dell@dell-desktop:~$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000000fdc0000 end: 000000000fec0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000fec0000 size: 0000000000038000 end: 000000000fef8000 type: 3
[    0.000000] copy_e820_map() start: 000000000fef8000 size: 0000000000008000 end: 000000000ff00000 type: 4
[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000080000 end: 00000000ffc00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fec0000 (usable)
[    0.000000]  BIOS-e820: 000000000fec0000 - 000000000fef8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fef8000 - 000000000ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 254MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65216) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65216
[    0.000000]   HighMem     65216 ->    65216
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65216
[    0.000000] On node 0 totalpages: 65216
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 477 pages used for memmap
[    0.000000]   Normal zone: 60643 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 AMI                                   ) @ 0x000ff980
[    0.000000] ACPI: RSDT (v001 DELL   MUMMY    0x20001113 MSFT 0x00000097) @ 0x0fef0000
[    0.000000] ACPI: FADT (v001 DELL   MUMMY    0x20001113 MSFT 0x00000097) @ 0x0fef1000
[    0.000000] ACPI: DSDT (v001 DELL   DIM_L    0x00000012 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0ff00000:efc80000)
[    0.000000] Detected 598.113 MHz processor.
[   34.687180] Built 1 zonelists.  Total pages: 64707
[   34.687192] Kernel command line: root=UUID=3732cd70-f228-4960-b868-d793f7de90a9 ro quiet splash
[   34.687852] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   34.687878] mapped APIC to ffffd000 (0120a000)
[   34.687889] Enabling fast FPU save and restore... done.
[   34.687898] Enabling unmasked SIMD FPU exception support... done.
[   34.687925] Initializing CPU#0
[   34.688050] PID hash table entries: 1024 (order: 10, 4096 bytes)
[   34.690415] Console: colour VGA+ 80x25
[   34.691035] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   34.691788] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   34.726071] Memory: 247608k/260864k available (1992k kernel code, 12720k reserved, 900k data, 328k init, 0k highmem)
[   34.726113] virtual kernel memory layout:
[   34.726118]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   34.726123]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   34.726128]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   34.726133]     lowmem  : 0xc0000000 - 0xcfec0000   ( 254 MB)
[   34.726137]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   34.726142]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   34.726147]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   34.726159] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   34.804049] Calibrating delay using timer specific routine.. 1197.48 BogoMIPS (lpj=2394965)
[   34.804201] Security Framework v1.0.0 initialized
[   34.804228] SELinux:  Disabled at boot.
[   34.804291] Mount-cache hash table entries: 512
[   34.804787] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   34.804830] CPU: L1 I cache: 16K, L1 D cache: 16K
[   34.804840] CPU: L2 cache: 128K
[   34.804850] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   34.804888] Compat vDSO mapped to ffffe000.
[   34.804916] Remapping vsyscall page to ffffe000
[   34.804952] Checking 'hlt' instruction... OK.
[   34.820367] SMP alternatives: switching to UP code
[   34.820946] Freeing SMP alternatives: 11k freed
[   34.821637] Early unpacking initramfs... done
[   35.942706] ACPI: Core revision 20060707
[   35.944308] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   35.948824] ACPI: setting ELCR to 0200 (from 0e08)
[   35.949285] CPU0: Intel Celeron (Coppermine) stepping 06
[   35.949304] SMP motherboard not detected.
[   35.949313] Local APIC not detected. Using dummy APIC emulation.
[   35.949463] Brought up 1 CPUs
[   35.950330] Booting paravirtualized kernel on bare hardware
[   35.950591] Time: 13:53:26  Date: 07/19/107
[   35.950712] NET: Registered protocol family 16
[   35.951126] EISA bus registered
[   35.951152] ACPI: bus type pci registered
[   35.952177] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=1
[   35.952189] PCI: Using configuration type 1
[   35.952196] Setting up standard PCI resources
[   35.969201] ACPI: Interpreter enabled
[   35.969222] ACPI: Using PIC for interrupt routing
[   35.970636] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   35.970668] PCI: Probing PCI hardware (bus 00)
[   35.972992] Boot video device is 0000:00:01.0
[   35.973173] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   35.973185] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[   35.973634] PCI: Firmware left 0000:01:01.0 e100 interrupts enabled, disabling
[   35.973844] PCI: Transparent bridge - 0000:00:1e.0
[   35.973909] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   35.977921] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   35.986599] ACPI: Power Resource [URP1] (off)
[   35.986952] ACPI: Power Resource [URP2] (off)
[   35.987288] ACPI: Power Resource [FDDP] (off)
[   35.987631] ACPI: Power Resource [LPTP] (off)
[   35.991422] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   35.992367] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   35.993211] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   35.994062] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   35.994604] Linux Plug and Play Support v0.97 (c) Adam Belay
[   35.994682] pnp: PnP ACPI init
[   36.005522] pnp: PnP ACPI: found 12 devices
[   36.005543] PnPBIOS: Disabled by ACPI PNP
[   36.005777] PCI: Using ACPI for IRQ routing
[   36.005789] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   36.008652] NET: Registered protocol family 8
[   36.008660] NET: Registered protocol family 20
[   36.011331] PCI: Ignore bogus resource 6 [0:0] of 0000:00:01.0
[   36.011364] PCI: Bridge: 0000:00:1e.0
[   36.011373]   IO window: d000-dfff
[   36.011388]   MEM window: ff400000-ff8fffff
[   36.011399]   PREFETCH window: f6a00000-f6afffff
[   36.011432] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   36.011536] NET: Registered protocol family 2
[   36.044268] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   36.044590] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   36.044879] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   36.045038] TCP: Hash tables configured (established 8192 bind 4096)
[   36.045048] TCP reno registered
[   36.056497] checking if image is initramfs... it is
[   38.126798] Freeing initrd memory: 6767k freed
[   38.128470] audit: initializing netlink socket (disabled)
[   38.128520] audit(1187531608.624:1): initialized
[   38.129050] VFS: Disk quotas dquot_6.5.1
[   38.129129] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   38.129324] io scheduler noop registered
[   38.129336] io scheduler anticipatory registered
[   38.129344] io scheduler deadline registered
[   38.129387] io scheduler cfq registered (default)
[   38.130293] isapnp: Scanning for PnP cards...
[   38.484786] isapnp: No Plug & Play device found
[   38.688967] Real Time Clock Driver v1.12ac
[   38.689159] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   38.689502] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.693298] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.694563] mice: PS/2 mouse device common for all mice
[   38.697252] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   38.697987] input: Macintosh mouse button emulation as /class/input/input0
[   38.698175] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   38.698191] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   38.698909] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   38.702068] serio: i8042 KBD port at 0x60,0x64 irq 1
[   38.702090] serio: i8042 AUX port at 0x60,0x64 irq 12
[   38.702643] EISA: Probing bus 0 at eisa.0
[   38.702721] EISA: Detected 0 cards.
[   38.733024] TCP cubic registered
[   38.733059] NET: Registered protocol family 1
[   38.733140] Using IPI No-Shortcut mode
[   38.733457] ACPI: (supports S0 S1 S4 S5)
[   38.733610]   Magic number: 3:158:888
[   38.733807]   hash matches device ptyuf
[   38.733899]   hash matches device 0000:00:1f.1
[   38.735658] Freeing unused kernel memory: 328k freed
[   38.735819] Time: tsc clocksource has been installed.
[   38.753966] input: AT Translated Set 2 keyboard as /class/input/input1
[   40.705325] Capability LSM initialized
[   43.258462] SCSI subsystem initialized
[   43.291994] libata version 2.20 loaded.
[   43.300958] ata_piix 0000:00:1f.1: version 2.10ac1
[   43.301042] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   43.301260] ata1: PATA max UDMA/66 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   43.301385] ata2: PATA max UDMA/66 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   43.301446] scsi0 : ata_piix
[   43.343754] usbcore: registered new interface driver usbfs
[   43.343839] usbcore: registered new interface driver hub
[   43.343969] usbcore: registered new device driver usb
[   43.349557] USB Universal Host Controller Interface driver v3.0
[   43.410387] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   43.410402] e100: Copyright(c) 1999-2006 Intel Corporation
[   43.464275] ata1.00: ata_hpa_resize 1: sectors = 39876480, hpa_sectors = 39876480
[   43.464295] ata1.00: ATA-5: QUANTUM FIREBALLlct20 20, APL.0900, max UDMA/100
[   43.464307] ata1.00: 39876480 sectors, multi 8: LBA 
[   43.464334] ata1.00: limited to UDMA/33 due to 40-wire cable
[   43.472194] ata1.00: ata_hpa_resize 1: sectors = 39876480, hpa_sectors = 39876480
[   43.472213] ata1.00: configured for UDMA/33
[   43.472251] scsi1 : ata_piix
[   43.761216] Floppy drive(s): fd0 is 1.44M
[   43.791793] ata2.00: ATAPI, max UDMA/33
[   43.821598] FDC 0 is a post-1991 82077
[   43.955802] ata2.00: configured for UDMA/33
[   43.963696] scsi 0:0:0:0: Direct-Access     ATA      QUANTUM FIREBALL APL. PQ: 0 ANSI: 5
[   43.964599] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-ROM SC-148F   F007 PQ: 0 ANSI: 5
[   43.983403] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   43.983424] PCI: setting IRQ 9 as level-triggered
[   43.983433] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   43.983468] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   43.983532] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   43.983937] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   43.983996] uhci_hcd 0000:00:1f.2: irq 9, io base 0x0000ef80
[   43.984454] usb usb1: configuration #1 chosen from 1 choice
[   43.984583] hub 1-0:1.0: USB hub found
[   43.984619] hub 1-0:1.0: 2 ports detected
[   44.093037] ACPI: PCI Interrupt 0000:01:01.0[A] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   44.117765] e100: eth0: e100_probe: addr 0xff8fd000, irq 9, MAC addr 00:03:47:21:EA:5E
[   44.127626] SCSI device sda: 39876480 512-byte hdwr sectors (20417 MB)
[   44.131073] sda: Write Protect is off
[   44.131093] sda: Mode Sense: 00 3a 00 00
[   44.131219] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.131450] SCSI device sda: 39876480 512-byte hdwr sectors (20417 MB)
[   44.131537] sda: Write Protect is off
[   44.131546] sda: Mode Sense: 00 3a 00 00
[   44.131601] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.131614]  sda: sda1 sda2 < sda5 >
[   44.229300] sd 0:0:0:0: Attached scsi disk sda
[   44.233354] sr0: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[   44.233366] Uniform CD-ROM driver Revision: 3.20
[   44.234216] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   44.265902] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   44.266639] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   44.331590] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   44.494424] usb 1-2: configuration #1 chosen from 1 choice
[   44.497229] hub 1-2:1.0: USB hub found
[   44.500050] hub 1-2:1.0: 4 ports detected
[   44.967664] Attempting manual resume
[   44.967680] swsusp: Resume From Partition 8:5
[   44.967687] PM: Checking swsusp image.
[   44.993191] PM: Resume from disk failed.
[   45.105951] kjournald starting.  Commit interval 5 seconds
[   45.106007] EXT3-fs: mounted filesystem with ordered data mode.
[   66.242358] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   68.038467] NET: Registered protocol family 17
[   70.859618] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[   72.480668] intel_rng: Firmware space is locked read-only. If you can't or
[   72.480677] intel_rng: don't want to disable this in firmware setup, and if
[   72.480683] intel_rng: you are certain that your system has a functional
[   72.480688] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   72.504283] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   72.521066] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   72.534626] input: PC Speaker as /class/input/input2
[   72.588807] Linux agpgart interface v0.102 (c) Dave Jones
[   72.605155] agpgart: Detected an Intel i810 E Chipset.
[   72.613428] agpgart: detected 4MB dedicated video ram.
[   72.622843] agpgart: AGP aperture is 64M @ 0xf8000000
[   72.716347] iTCO_vendor_support: vendor-support=0
[   72.721585] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   72.721994] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   72.722016] iTCO_wdt: No card detected
[   73.911706] parport: PnPBIOS parport detected.
[   73.911755] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   73.919267] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   75.234213] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 3
[   75.234233] PCI: setting IRQ 3 as level-triggered
[   75.234242] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNKC] -> GSI 3 (level, low) -> IRQ 3
[   76.628876] fuse init (API version 7.8)
[   76.708452] lp0: using parport0 (interrupt-driven).
[   76.754991] ide0: I/O resource 0x3F6-0x3F6 not free.
[   76.755007] ide0: ports already in use, skipping probe
[   76.755017] ide1: I/O resource 0x376-0x376 not free.
[   76.755024] ide1: ports already in use, skipping probe
[   76.895613] Adding 746980k swap on /dev/disk/by-uuid/d11f2cdd-5351-4449-b3c5-ae4ac958fd52.  Priority:-1 extents:1 across:746980k
[   77.152752] EXT3 FS on sda1, internal journal
[   77.606443] NET: Registered protocol family 10
[   77.606835] lo: Disabled Privacy Extensions
[   86.168110] No dock devices found.
[   86.461080] Using specific hotkey driver
[   86.837055] input: Power Button (FF) as /class/input/input4
[   86.837925] ACPI: Power Button (FF) [PWRF]
[   87.161967] ibm_acpi: ec object not found
[   87.275015] pcc_acpi: loading...
[   88.172736] eth0: no IPv6 routers present
[  100.151943] ppdev: user-space parallel port driver
[  105.171804] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  105.171822] apm: overridden by ACPI.
[  108.369873] Bluetooth: Core ver 2.11
[  108.370082] NET: Registered protocol family 31
[  108.370091] Bluetooth: HCI device and connection manager initialized
[  108.370102] Bluetooth: HCI socket layer initialized
[  108.572737] Bluetooth: L2CAP ver 2.8
[  108.572756] Bluetooth: L2CAP socket layer initialized
[  108.590101] Bluetooth: RFCOMM socket layer initialized
[  108.590164] Bluetooth: RFCOMM TTY layer initialized
[  108.590172] Bluetooth: RFCOMM ver 1.8
[  113.523157] eth0: no IPv6 routers present
[ 1856.406795] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1856.406831] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x46 data 8 in
[ 1856.406837]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1863.406294] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 1886.420847] ata2: port failed to respond (30 secs, Status 0xd0)
[ 1886.420877] ata2: soft resetting port
[ 1886.905073] ata2.00: configured for UDMA/33
[ 1886.905175] ata2: EH complete
dell@dell-desktop:~$

---

### Post by Ubunme2 on 2007-08-19
And this is what I get with: lsmod:

dell@dell-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
asus_acpi              17308  0 
sbs                    15652  0 
button                  8720  0 
video                  16388  0 
backlight               7040  1 asus_acpi
battery                10756  0 
i2c_ec                  6016  1 sbs
container               5248  0 
dock                   10268  0 
ac                      6020  0 
ipv6                  268960  8 
ide_generic             2304  0 [permanent]
lp                     12452  0 
fuse                   46612  0 
snd_ens1371            27552  1 
gameport               16520  1 snd_ens1371
snd_ac97_codec         98464  1 snd_ens1371
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  1 snd_pcm
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
psmouse                38920  0 
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25244  1 
agpgart                35400  2 intel_agp
pcspkr                  4224  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
serio_raw               7940  0 
i2c_i810                6276  0 
i2c_algo_bit            8712  1 i2c_i810
i2c_core               22656  3 i2c_ec,i2c_i810,i2c_algo_bit
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  2 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
generic                 5124  0 [permanent]
ata_generic             9092  0 
floppy                 59524  0 
e100                   36232  0 
mii                     6528  1 e100
uhci_hcd               25360  0 
usbcore               134280  2 uhci_hcd
ata_piix               15492  2 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  4 sg,sr_mod,sd_mod,libata
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
dell@dell-desktop:~$

---

### Post by bronzefury on 2007-08-26
Hi,

I'm getting the same problem.  I just don't get it.  Something as simple as the CD-ROM not working?  Btw, I get the same problem with the floppy.  I booted Xubuntu Feisty Fawn using the exact same CD-ROM, but when OS finally running, it doesn't load the CD-ROM or Floppy.

some excerpts from dmesg
=====
.....
[15966.028692] hdc: CD-224E, ATAPI CD/DVD-ROM drive
....
...

<SO CD-ROM is seen, but then I get..>
...
..
[15966.799673] ide_cd: Unknown symbol register_cdrom
[15966.800069] ide_cd: Unknown symbol cdrom_ioctl
[15966.801708] ide_cd: Unknown symbol cdrom_mode_select
[15966.802652] ide_cd: Unknown symbol cdrom_media_changed
[15966.802982] ide_cd: Unknown symbol cdrom_get_last_written
[15966.803689] ide_cd: Unknown symbol cdrom_mode_sense
[15966.804470] ide_cd: Unknown symbol cdrom_get_media_event
..
.
What gives?  Any pointers to resolving this would help..

bronzefury

---


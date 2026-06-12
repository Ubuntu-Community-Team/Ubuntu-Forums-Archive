---
title: "Errors when doing upgrading..."
date: 2005-09-13
forum: General Help
---

### Post by occy on 2005-09-13
When I went to upgrade my system this morning, via the gnome applet for Package Manager, I had an error after the upgrade.

```
E: /var/cache/apt/archives/xlibs_6.8.2-10.1_all.deb:  unable to stat `./etc/X11/xkb/symbols' (which I was about to install): Input/output error
``` 

From here, I decided to try:  apt-get -f install

That seemed to go smooth, however, when I(from a terminal) ran: apt-get dist-upgrade   I got the following error:

```
root@sometimes:~ # apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  mozilla-firefox-dom-inspector
The following packages will be upgraded:
  mozilla-firefox mozilla-firefox-dev mozilla-firefox-gnome-support xlibs
4 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/12.0MB of archives.
After unpacking 799kB disk space will be freed.
Do you want to continue [Y/n]?

Preconfiguring packages ...
(Reading database ... 81916 files and directories currently installed.)
Removing mozilla-firefox-dom-inspector ...
Updating mozilla-firefox chrome registry...done.
(Reading database ... 81898 files and directories currently installed.)
Preparing to replace mozilla-firefox-gnome-support 1.0.6-0ubuntu0.1 (using .../mozilla-firefox-gnome-support_1.0.6-0ubuntu0.2_i386.deb) ...
Unpacking replacement mozilla-firefox-gnome-support ...
Preparing to replace mozilla-firefox-dev 1.0.6-0ubuntu0.1 (using .../mozilla-firefox-dev_1.0.6-0ubuntu0.2_i386.deb) ...
Unpacking replacement mozilla-firefox-dev ...
Preparing to replace xlibs 6.8.2-10 (using .../xlibs_6.8.2-10.1_all.deb) ...
Unpacking replacement xlibs ...
dpkg: xlibs: warning - conffile `etc/X11/xkb/semantics/complete' is not a plain file or symlink (= `/etc/X11/xkb/semantics/complete')
dpkg: xlibs: warning - conffile `etc/X11/xkb/semantics/default' is not a plain file or symlink (= `/etc/X11/xkb/semantics/default')
dpkg: xlibs: warning - conffile `etc/X11/xkb/semantics/xtest' is not a plain file or symlink (= `/etc/X11/xkb/semantics/xtest')
dpkg: error processing /var/cache/apt/archives/xlibs_6.8.2-10.1_all.deb (--unpack):
 unable to stat `./etc/X11/xkb/symbols' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace mozilla-firefox 1.0.6-0ubuntu0.1 (using .../mozilla-firefox_1.0.6-0ubuntu0.2_i386.deb) ...
Unpacking replacement mozilla-firefox ...
Errors were encountered while processing:
 /var/cache/apt/archives/xlibs_6.8.2-10.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` 

I didn't know if it would be helpful, but here is my sources.list

```
root@sometimes:~ # cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary universe

deb http://us.archive.ubuntu.com/ubuntu/ hoary multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary multiverse


deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

deb http://ubuntu.nooms.de/ hoary/
``` 

Any help would be greatly appreciated.

Thanks,
Trae

---

### Post by occy on 2005-09-13
After checking with bob2 on #ubuntu, It seems there may be some disk issues.

Here is the output of my dmesg in case it offers more info.

```
0 (reserved)
 BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
 BIOS-e820: 000000001f6e0000 - 000000001f6eb000 (ACPI data)
 BIOS-e820: 000000001f6eb000 - 000000001f700000 (ACPI NVS)
 BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
 BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
 BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
 BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
 BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
502MB LOWMEM available.
On node 0 totalpages: 128736
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 124640 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI present.
ACPI: RSDP (v000 HP                                    ) @ 0x000f76f0
ACPI: RSDT (v001 HP     09BC     0x06040000  LTP 0x00000000) @ 0x1f6e5167
ACPI: FADT (v001 HP     09BC     0x06040000 LOHR 0x0000005f) @ 0x1f6eae88
ACPI: MADT (v001 HP     09BC     0x06040000 LOHR 0x0000005f) @ 0x1f6eaefc
ACPI: BOOT (v001 HP     09BC     0x06040000  LTP 0x00000001) @ 0x1f6eafd8
ACPI: MCFG (v001 HP     09BC     0x06040000 LOHR 0x0000005f) @ 0x1f6eaf9c
ACPI: SSDT (v001 HP     09BC     0x00003000 INTL 0x20030224) @ 0x1f6e55c3
ACPI: SSDT (v001 HP     09BC     0x00003001 INTL 0x20030224) @ 0x1f6e53eb
ACPI: SSDT (v001 HP     09BC     0x00003000 INTL 0x20030224) @ 0x1f6e52d7
ACPI: SSDT (v001 HP     09BC     0x00000001 INTL 0x20030224) @ 0x1f6e51ab
ACPI: DSDT (v001 HP     09BC     0x06040000 MSFT 0x0100000e) @ 0x00000000
ACPI: PM-Timer IO Port: 0x1008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 6:13 APIC version 20
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 1597.017 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 502940k/514944k available (1436k kernel code, 11404k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3153.92 BogoMIPS (lpj=1576960)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000
CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000
CPU: L1 I cache: 32K, L1 D cache: 32K
CPU: L2 cache: 2048K
CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000180 00000000
CPU: Intel(R) Pentium(R) M processor 1.60GHz stepping 08
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 pin1=2 pin2=-1
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd850, last bus=7
PCI: Using MMCONFIG
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
ACPI: Embedded Controller [EC0] (gpe 27)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 8 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
Simple Boot Flag at 0x36 set to 0x1
audit: initializing netlink socket (disabled)
audit(1126577646.903:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
i8042.c: Detected active multiplexing controller, rev 1.1.
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ACPI: PCI interrupt 0000:00:1e.3[B] -> GSI 20 (level, low) -> IRQ 20
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 2
Cannot allocate resource for EISA slot 3
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices: 
LID0 RP01 LANC PS2K PS2M 
ACPI: (supports S0 S3 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
ACPI: Thermal Zone [THR0] (53 C)
ACPI: Thermal Zone [THR1] (44 C)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ICH6: IDE controller at PCI slot 0000:00:1f.1
ACPI: PCI interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
ICH6: chipset revision 4
ICH6: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:DMA
Probing IDE interface ide0...
hda: FUJITSU MHT2060AT PL, ATA DISK drive
hdb: HL-DT-ST DVD-RW GCA-4080N, ATAPI CD/DVD-ROM drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory...  -\|/done (458 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 1485972k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
lp: driver loaded but no devices found
mice: PS/2 mouse device common for all mice
input: PS/2 Generic Mouse on isa0060/serio4
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 915GM Chipset.
agpgart: Maximum main memory to use for agp memory: 430M
agpgart: Detected 7932K stolen memory.
agpgart: AGP aperture is 256M @ 0xc0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: Fails to gain control of native hot-plug
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
uhci_hcd 0000:00:1d.0: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 23, io base 0x1820
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0x1840
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0x1860
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.3: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 16, io base 0x1880
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xb0040000
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
PCI: cache line size of 32 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
hw_random hardware driver 1.0.0 loaded
ACPI: PCI interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1e.2 to 64
intel8x0_measure_ac97_clock: measured 49486 usecs
intel8x0: clocking to 48000
ieee80211_crypt: registered algorithm 'NULL'
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI interrupt 0000:06:05.0[A] -> GSI 20 (level, low) -> IRQ 20
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ACPI: PCI interrupt 0000:06:06.0[A] -> GSI 22 (level, low) -> IRQ 22
Yenta: CardBus bridge found at 0000:06:06.0 [103c:3081]
Yenta: ISA IRQ mask 0x0cf8, PCI irq 22
Socket status: 30000006
ieee80211_crypt: registered algorithm 'WEP'
ipw2200: Fatal error
ipw2200: Start IPW Error Log Dump:
ipw2200: Status: 0x80000241, Config: 00000142
ipw2200: Start IPW Event Log Dump:
ipw2200: Fatal error
ipw2200: Start IPW Error Log Dump:
ipw2200: Status: 0x00200100, Config: 00000142
ipw2200: Start IPW Event Log Dump:
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:06:06.2[C] -> GSI 21 (level, low) -> IRQ 21
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[b0108000-b01087ff]  Max Packet=[2048]
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:06:07.0[A] -> GSI 20 (level, low) -> IRQ 20
eth1: RealTek RTL8139 at 0x3000, 00:0a:e4:d3:b7:7f, IRQ 20
eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[05e40a00a4175026]
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
eth0: duplicate address detected!
ACPI: AC Adapter [AC] (off-line)
mtrr: no more MTRRs available
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID0]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
apm: BIOS not found.
cs: IO port probe 0x0100-0x04ff: excluding 0x200-0x20f 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: excluding 0x800-0x80f
cs: IO port probe 0x0c00-0x0cff: excluding 0xcf8-0xcff
cs: IO port probe 0x0a00-0x0aff: clean.
init_special_inode: bogus i_mode (2767)
init_special_inode: bogus i_mode (2767)
usb 1-1: new low speed USB device using uhci_hcd and address 2
usbcore: registered new driver hiddev
input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse® Explorer] on usb-0000:00:1d.0-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
init_special_inode: bogus i_mode (2767)
init_special_inode: bogus i_mode (2767)
init_special_inode: bogus i_mode (2767)
init_special_inode: bogus i_mode (2767)
```

---

### Post by samkon on 2006-11-02
> **occy said:**
> After checking with bob2 on #ubuntu, It seems there may be some disk issues.

Here is the output of my dmesg in case it offers more info.

```
 unable to stat `./etc/X11/xkb/symbols' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace mozilla-firefox 1.0.6-0ubuntu0.1 (using .../mozilla-firefox_1.0.6-0ubuntu0.2_i386.deb) ...
Unpacking replacement mozilla-firefox ...
Errors were encountered while processing:
 /var/cache/apt/archives/xlibs_6.8.2-10.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have the same problem :(

---


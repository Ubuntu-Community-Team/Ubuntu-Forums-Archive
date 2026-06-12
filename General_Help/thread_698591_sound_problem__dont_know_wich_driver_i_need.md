---
title: "sound problem : dont know wich driver i need"
date: 2008-02-16
forum: General Help
---

### Post by StevenRoose3 on 2008-02-16
hi,

i see much topics about sound not working here, but all the ones i tried failed...

i dont really know what sound hardware i have (i think SB450 HDA Audio).
here is the lshw list:
```

ste02-linux
    description: Computer
    product: Satellite A100
    vendor: TOSHIBA
    version: PSAA2E-03U025BT
    serial: 46016690Q
    width: 32 bits
    capabilities: smbios-2.34 dmi-2.34
    configuration: administrator_password=enabled boot=oem-specific frontpanel_p
assword=unknown keyboard_password=unknown power-on_password=enabled uuid=B607A64
0-C08C-11DA-A70E-00A0D13967F2
  *-core
       description: Motherboard
       product: SB450
       vendor: ATI
       physical id: 0
       version: Rev0.4b
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 1.50 (01/23/06)
          size: 103KB
          capacity: 448KB
          capabilities: pci pcmcia pnp apm upgrade shadowing cdboot bootselect e
dd int13floppynec int13floppy360 int13floppy1200 int13floppy720 int13floppy2880
int5printscreen int9keyboard int14serial int17printer int10video usb
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: U23
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic
 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up
        *-cache
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 1MB
             capacity: 1MB
             capabilities: burst internal write-back
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB
        *-bank:0
             description: SODIMM DDR Synchronous [empty]
             physical id: 0
             slot: M1
        *-bank:1
             description: SODIMM DDR Synchronous 533 MHz (1.9 ns)
             physical id: 1
             slot: M2
             size: 512MB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: ATI Technologies Inc
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200M]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm msi vga bus_master cap_list
                configuration: latency=66 mingnt=8
        *-ide:0
             description: IDE interface
             product: 4379 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list emulated
             configuration: driver=sata_sil latency=64 module=sata_sil
           *-disk
                description: SCSI Disk
                product: HTS541080G9SA00
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MB4O
                serial: MPBDL0X6KPRREM
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: HPFS/NTFS partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 24GB
                   capabilities: primary bootable
              *-volume:1
                   description: HPFS/NTFS partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 34GB
                   capabilities: primary
              *-volume:2
                   description: Linux filesystem partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   capacity: 14GB
                   capabilities: primary
              *-volume:3
                   description: Linux swap / Solaris partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   capacity: 1027MB
                   capabilities: primary nofs
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 81
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide:1
             description: IDE interface
             product: Standard Dual Channel PCI IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list
             configuration: driver=ATIIXP_IDE latency=0 module=atiixp
           *-ide
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: MATSHITADVD-RAM UJ-841S
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1.50
                   capabilities: packet atapi cdrom removable nonmagnetic dma lb
a iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2 status=nodisc
        *-multimedia UNCLAIMED
             description: Audio device
             product: SB450 HDA Audio
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=64
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 80
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
           *-network:0
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: wifi0
                version: 01
                serial: 00:16:e3:0e:70:5e
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical w
ireless
                configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.
5 (0.9.3.2) ip=192.168.1.2 latency=168 maxlatency=28 mingnt=10 module=ath_pci mu
lticast=yes wireless=IEEE 802.11g
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 min
gnt=192 module=yenta_socket
           *-network:1
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:02:07.0
                logical name: eth0
                version: 10
                serial: 00:a0:d1:39:67:f2
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10                                                                                                   bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too d                                                                                                   riverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 modul                                                                                                   e=8139too multicast=yes port=MII speed=10MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: a
                bus info: pci@0000:02:0a.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2                                                                                                    module=ohci1394
  *-battery
       physical id: 1
       slot: Left Front

```

can someone help me with giving the right driver and the howto reference.

thanks,
Steven

---

### Post by kuja on 2008-02-16
This looks like it may be related: [http://www.mepis.org/node/13776](http://www.mepis.org/node/13776)

---

### Post by Sokertes on 2008-02-17
Since it says unclaimed for your audio run

sudo update-pciids

This updates the db for pci ids

Then run 

lspci

and post what you have listed. This will tell what you have for your sound card using the updated pci ids. From there we should be able to get you going in the correct direction on this issue.


Sokertes

---

### Post by StevenRoose3 on 2008-02-17
lspci:
```
steven@ste02-linux:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:04.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)

```

---

### Post by danwood76 on 2008-02-17
You will either have the ALC861 or ALC861VD in your laptop.
(You can check by using hardware information)

You may need to modify the alsa-project source and compile it from that.
I have found that toshiba seem to use the same hardware IDs for several different cards so the alsa drivers tend to get a little confused on what card you have.

I just had a quick look through the source code and it says to put
```

option snd-hda-intel model=auto

```
 in your modprobe alsa-base file which should sort it.

---

### Post by StevenRoose3 on 2008-02-17
i tried to compile the alsa driver with
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
but i dont know my sound card name.
mabe this helps to find:
```

 lspci -v : 


00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <access denied>

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at 8440 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8420 [size=8]
        I/O ports at 8410 [size=4]
        I/O ports at 8400 [size=16]
        Memory at c0004000 (32-bit, non-prefetchable) [size=512]
        [virtual] Expansion ROM at 24000000 [disabled] [size=512K]
        Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: 66MHz, medium devsel
        I/O ports at 8450 [size=16]
        Memory at c0004400 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 8460 [size=16]
        Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, slow devsel, latency 64, IRQ 11
        Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: c0200000-c02fffff
        Prefetchable memory behind bridge: 20000000-23ffffff

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA controller])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at 9000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: <access denied>

02:04.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7094
        Flags: bus master, medium devsel, latency 168, IRQ 20
        Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 168, IRQ 16
        Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=03, sec-latency=176
        Memory window 0: 20000000-23fff000 (prefetchable)
        Memory window 1: 28000000-2bfff000
        I/O window 0: 0000a400-0000a4ff
        I/O window 1: 0000a800-0000a8ff
        16-bit legacy interface ports at 0001

02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at a000 [size=256]
        Memory at c0215000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 17
        Memory at c0215800 (32-bit, non-prefetchable) [size=2K]
        Memory at c0210000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

when i select all, the sudo modprobe snd- commands gives this error:
```
steven@ste02-linux:~$ sudo modprobe snd-
[sudo] password for steven:
FATAL: Module snd_ not found.

```

Steven

---


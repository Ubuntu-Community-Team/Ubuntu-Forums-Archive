---
title: "Quick message on start up - hot plug firmware failed - ?"
date: 2014-11-30
forum: General Help
---

### Post by michael-piziak on 2014-11-30
I have Ubuntu 14.x LTS installed on my sisters Intel Quad 4 computer (HP brand).

It's been working fine for 3 days.  One thing that I would like to know about.  On boot up, a quick little paragraph, that I can't read because it disappears so quickly, says something about "Hotplug firmware failed"  etc...

Just curious if this is detrimental, or should I not be concerned about it, as like I said all is working good.

p.s. I'm leaving her house soon to travel back home, so if there's something that needs fixed and I can fix before I leave, I'd like to do.

---

### Post by dragonfly41 on 2014-11-30
This is a total guess since I've no experience of HP .. and your clock is ticking.

First .. do you see "hot plug firmware" or "hot play firmware"?

Your post title and content are inconsistent.

If "hot plug" could it be a disk hot swap?

[http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02628004](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02628004)

if "hot play" .. do you have some hotplay playstation attached?

That's as far as my guess can go.

---

### Post by michael-piziak on 2014-11-30
> **dragonfly41 said:**
> This is a total guess since I've no experience of HP .. and your clock is ticking.

First .. do you see "hot plug firmware" or "hot play firmware"?

Your post title and content are inconsistent.

If "hot plug" could it be a disk hot swap?

[http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02628004](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02628004)

if "hot play" .. do you have some hotplay playstation attached?

That's as far as my guess can go.

It is "hotplug firmware failed."  I corrected that in the first post.  Thanks.

I believe the link you supplied is a way to fix an HP firmware problem.  Is there a terminal code line or other way I can determine which firmware she has now ?

Also, is it possible to do a firmware update with a computer running just Ubuntu 14.x LTS  ?  There is no MS Windows on this computer at all.

---

### Post by dragonfly41 on 2014-11-30
Hardware configuration is found by this command ...

sudo lshw

---

### Post by dragonfly41 on 2014-11-30
Perhaps more information here ...

[http://h20566.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c01186030&lang=en&cc=us](http://h20566.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c01186030&lang=en&cc=us)

---

### Post by michael-piziak on 2014-11-30
> **dragonfly41 said:**
> Hardware configuration is found by this command ...

sudo lshw

Which reports this:
```

house@house-KJ294AA-ABA-m9252p:~$ sudo lshw
[sudo] password for house: 
house-kj294aa-aba-m9252p  
    description: Desktop Computer
    product: KJ294AA-ABA m9252p (KJ294AA#ABA)
    vendor: HP-Pavilion
    version: Chassis Version
    serial: MXU81308VQ
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall32
    configuration: boot=normal chassis=desktop family=103C_53316J sku=KJ294AA#ABA uuid=CC38777E-25FC-DC11-8BE4-75570BA92958
  *-core
       description: Motherboard
       product: Benicia
       vendor: PEGATRON CORPORATION
       physical id: 0
       version: 1.01
       serial: X312345678
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 5.21
          date: 02/26/2008
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Quad CPU    Q6700  @ 2.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Quad CPU    Q6700  @ 2.66GHz
          slot: CPU 1
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 267MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal write-back instruction
     *-memory
          description: System Memory
          physical id: 2a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: M3 78T2953EZ3-CF7
             vendor: Samsung
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: M3 78T2953EZ3-CF7
             vendor: Samsung
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: M3 78T2953EZ3-CF7
             vendor: Samsung
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 800 MHz (1.2 ns)
             product: M3 78T2953EZ3-CF7
             vendor: Samsung
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: 82G33/G31/P35/P31 Express PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:d000(size=4096) memory:fa000000-feafffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G86 [GeForce 8500 GT]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:05:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:dc00(size=128) memory:feae0000-feafffff
        *-usb:0
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:a400(size=32)
        *-usb:1
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:a480(size=32)
        *-usb:2
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:18 memory:f9cfec00-f9cfefff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:f9cf4000-f9cf7fff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:f0000000-f01fffff ioport:f0200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:f9e00000-f9ffffff ioport:f0400000(size=2097152)
           *-multimedia
                description: Multimedia video controller
                product: CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb
                vendor: Conexant Systems, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 0f
                width: 64 bits
                clock: 33MHz
                capabilities: pciexpress pm vpd msi bus_master cap_list
                configuration: driver=cx23885 latency=0
                resources: irq:17 memory:f9e00000-f9ffffff
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:e000(size=4096) memory:feb00000-febfffff ioport:f8f00000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:1f:c6:10:a4:44
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:44 ioport:e800(size=256) memory:febff000-febfffff memory:f8ff0000-f8ffffff memory:febc0000-febdffff
        *-usb:3
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:a800(size=32)
        *-usb:4
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:a880(size=32)
        *-usb:5
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ac00(size=32)
        *-usb:6
             description: USB controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:b000(size=32)
        *-usb:7
             description: USB controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f9cff800-f9cffbff
        *-pci:4
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 92
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:c000(size=4096) memory:f9d00000-f9dfffff
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax Modem
                vendor: Conexant Systems, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
                resources: memory:f9de0000-f9deffff ioport:cc00(size=8)
           *-firewire
                description: FireWire (IEEE 1394)
                product: FW322/323 [TrueFire] 1394a Controller
                vendor: LSI Corporation
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 70
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=24 mingnt=12
                resources: irq:20 memory:f9dff000-f9dfffff
        *-isa
             description: ISA bridge
             product: 82801IR (ICH9R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: RAID bus controller
             product: 82801 SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:45 ioport:b880(size=8) ioport:b800(size=4) ioport:b480(size=8) ioport:b400(size=4) ioport:b080(size=32) memory:f9cff000-f9cff7ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f9cffc00-f9cffcff ioport:400(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST3750640AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 3.CH
             serial: 5QD4QPV0
             size: 698GiB (750GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00017465
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 85c2bdf3-9438-4c11-8b95-100b58a96676
                size: 694GiB
                capacity: 694GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-11-28 15:07:41 filesystem=ext4 lastmountpoint=/ modified=2014-11-30 15:27:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-11-30 15:27:48 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 4094MiB
                capacity: 4094MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4094MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM GH10L
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: FC09
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 3
          bus info: usb@2:5.2
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             configuration: sectorsize=512
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
             configuration: sectorsize=512
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
             configuration: sectorsize=512
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
             configuration: sectorsize=512
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:4
       logical name: wlan0
       serial: 00:16:44:b0:1b:ae
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.13.0-40-generic firmware=1.7 ip=192.168.1.3 link=yes multicast=yes wireless=IEEE 802.11bg
house@house-KJ294AA-ABA-m9252p:~$
```

---

### Post by michael-piziak on 2014-11-30
I seen both websites that you and the other user linked me to.

I'm not quite sure what to do from here.  I don't no program language or anything.  I can only type into terminal what you guys/gals tell me to.

---

### Post by michael-piziak on 2014-12-01
When typing  "[COLOR=#000000][FONT=Ubuntu Mono]dmesg | tail -n 40"  into terminal, I get this reported.

[/FONT][/COLOR]
[COLOR=#000000]house@house-KJ294AA-ABA-m9252p:~$ dmesg | tail -n 40[/COLOR]
[COLOR=#000000][ 18.811932] Please fix your hotplug setup, the board will not work without firmware loaded![/COLOR]
[COLOR=#000000][ 18.812404] cx23885_initialize_codec() f/w load failed[/COLOR]
[COLOR=#000000][ 18.812635] cx23885_dvb_register() allocating 1 frontend(s)[/COLOR]
[COLOR=#000000][ 18.812672] cx23885[0]: cx23885 based dvb card[/COLOR]
[COLOR=#000000][ 18.846405] MT2131: successfully identified at address 0x61[/COLOR]
[COLOR=#000000][ 18.848056] DVB: registering new adapter (cx23885[0])[/COLOR]
[COLOR=#000000][ 18.848061] cx23885 0000:03:00.0: DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...[/COLOR]
[COLOR=#000000][ 18.848354] cx23885_dev_checkrevision() Hardware revision = 0xb1[/COLOR]
[COLOR=#000000][ 18.848360] cx23885[0]/0: found at 0000:03:00.0, rev: 15, irq: 17, latency: 0, mmio: 0xf9e00000[/COLOR]
[COLOR=#000000][ 19.141702] r8169 0000:02:00.0 eth0: link down[/COLOR]
[COLOR=#000000][ 19.141738] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready[/COLOR]
[COLOR=#000000][ 19.141960] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready[/COLOR]
[COLOR=#000000][ 19.143450] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt73.bin'[/COLOR]
[COLOR=#000000][ 19.169126] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 1.7[/COLOR]
[COLOR=#000000][ 19.244817] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready[/COLOR]
[COLOR=#000000][ 19.245168] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready[/COLOR]
[COLOR=#000000][ 20.520245] wlan0: authenticate with e0:91:f5:80:17:0a[/COLOR]
[COLOR=#000000][ 20.568219] wlan0: send auth to e0:91:f5:80:17:0a (try 1/3)[/COLOR]
[COLOR=#000000][ 20.569779] wlan0: authenticated[/COLOR]
[COLOR=#000000][ 20.572027] wlan0: associate with e0:91:f5:80:17:0a (try 1/3)[/COLOR]
[COLOR=#000000][ 20.574657] wlan0: RX AssocResp from e0:91:f5:80:17:0a (capab=0x411 status=0 aid=2)[/COLOR]
[COLOR=#000000][ 20.584528] wlan0: associated[/COLOR]
[COLOR=#000000][ 20.584540] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready[/COLOR]
[COLOR=#000000][ 24.822802] init: plymouth-upstart-bridge main process ended, respawning[/COLOR]
[COLOR=#000000][ 24.839669] init: plymouth-upstart-bridge main process ended, respawning[/COLOR]
[COLOR=#000000][ 47.688082] audit_printk_skb: 150 callbacks suppressed[/COLOR]
[COLOR=#000000][ 47.688086] type=1400 audit(1417451974.602:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2150 comm="apparmor_parser"[/COLOR]
[COLOR=#000000][ 47.688093] type=1400 audit(1417451974.602:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2150 comm="apparmor_parser"[/COLOR]
[COLOR=#000000][ 47.688510] type=1400 audit(1417451974.602:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2150 comm="apparmor_parser"[/COLOR]
[COLOR=#000000][ 1983.474043] usb 2-5.3: USB disconnect, device number 6[/COLOR]
[COLOR=#000000][ 3121.608253] usb 2-5.4: new low-speed USB device number 7 using ehci-pci[/COLOR]
[COLOR=#000000][ 3121.706376] usb 2-5.4: New USB device found, idVendor=03f0, idProduct=0f0c[/COLOR]
[COLOR=#000000][ 3121.706381] usb 2-5.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0[/COLOR]
[COLOR=#000000][ 3121.706385] usb 2-5.4: Product: USB Multimedia Wireless Kit[/COLOR]
[COLOR=#000000][ 3121.706388] usb 2-5.4: Manufacturer: Chicony[/COLOR]
[COLOR=#000000][ 3121.709265] input: Chicony USB Multimedia Wireless Kit as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.4/2-5.4:1.0/input/input14[/COLOR]
[COLOR=#000000][ 3121.709424] hid-generic 0003:03F0:0F0C.0003: input,hidraw2: USB HID v1.11 Keyboard [Chicony USB Multimedia Wireless Kit] on usb-0000:00:1d.7-5.4/input0[/COLOR]
[COLOR=#000000][ 3121.715219] input: Chicony USB Multimedia Wireless Kit as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.4/2-5.4:1.1/input/input15[/COLOR]
[COLOR=#000000][ 3121.715447] hid-generic 0003:03F0:0F0C.0004: input,hiddev0,hidraw3: USB HID v1.11 Mouse [Chicony USB Multimedia Wireless Kit] on usb-0000:00:1d.7-5.4/input1[/COLOR]
[COLOR=#000000][ 3121.756307] WARNING! power/level is deprecated; use power/control instead[/COLOR]
[COLOR=#000000]house@house-KJ294AA-ABA-m9252p:~$



Can someone walk me through how to perhaps fix this firmware problem.  This is an HP Pavilion Elite m9252p PC.

p.s. Everything is working properly on the computer except the computer won't recognize any USB thumb drive (but it does recognize usb gamepads and usb external hard drives.


[/COLOR]

---

### Post by michael-piziak on 2014-12-01
> **dragonfly41 said:**
> This is a total guess since I've no experience of HP .. and your clock is ticking.

First .. do you see "hot plug firmware" or "hot play firmware"?

Your post title and content are inconsistent.

If "hot plug" could it be a disk hot swap?

[http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02628004](http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c02628004)

if "hot play" .. do you have some hotplay playstation attached?

That's as far as my guess can go.

hmmm, the link to the ***resolution*** on that web site is dead.

---

### Post by michael-piziak on 2014-12-01
> **dragonfly41 said:**
> Perhaps more information here ...

[http://h20566.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c01186030&lang=en&cc=us](http://h20566.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c01186030&lang=en&cc=us)

Once at that webpage, all the links under resolution do not work for linux.

hmmmmm

[COLOR=#000000]This system has been running for 3+ days with no problem other than the usb thumb drives not being recognized. HP apparently doesn't support linux firmware fixes. Does anyone think this little firmware error will be detrimental to this computer?[/COLOR]

---

### Post by dragonfly41 on 2014-12-01
Posting two parallel threads on the same topic is not a good idea ...

However on this site ...

[http://h10010.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01545853](http://h10010.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01545853)

I read ...

> 
HP may not provide drivers, patches, or upgrades for Linux on its HP Pavilion and Presario notebook computers. However, Linux is a free, open source community. Visit the Linux Community Website (in English) and for more information.

So HP seems to support mainly Windows and you may find it difficult to find firmware to run on Ubuntu.

But I would keep looking and perhaps post a question on the HP forum.

This is as far as my research goes into HP.

---

### Post by michael-piziak on 2014-12-01
> **dragonfly41 said:**
> Posting two parallel threads on the same topic is not a good idea ...

However on this site ...

[http://h10010.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01545853](http://h10010.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c01545853)

I read ...



So HP seems to support mainly Windows and you may find it difficult to find firmware to run on Ubuntu.

But I would keep looking and perhaps post a question on the HP forum.

This is as far as my research goes into HP.

The two threads kind of evolved toward each other - one thread was about the firmware error & the other thread was about USB thumbdrive not working (and a user pointed out the firmware error) - but sorry about that.

Thanks for you help.  I'll continue to look around the net and perhaps post on the hp forum as you suggested.   I'm inclined to just ignore this problem, as I have run this computer for 3+ days and no other problems have been discovered (other than the usb stick problem).

---


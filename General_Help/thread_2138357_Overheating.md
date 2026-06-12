---
title: "Overheating"
date: 2013-04-23
forum: General Help
---

### Post by aassdd on 2013-04-23
[COLOR=#333333][FONT=Ubuntu Beta] my computer get too hot
output of sensors
[/FONT][/COLOR]

Adapter: Virtual device
temp1:        +76.0°C  (crit = +99.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +78.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +78.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +77.0°C  (high = +86.0°C, crit = +100.0°C)


radeon-pci-0100
Adapter: PCI adapter
temp1:        +84.0°C 


help plxxxx

thx

---

### Post by pqwoerituytrueiwoq on 2013-04-23
system model and os version/edition

---

### Post by Impavidus on 2013-04-23
Sounds like your graphics card is running hot. Have you installed any proprietary divers? And post the exact details on your hardware.

---

### Post by aassdd on 2013-04-23
> **pqwoerituytrueiwoq said:**
> system model and os version/edition


how do i know it ?

---

### Post by piedog98 on 2013-04-23
System Settings/ Details

---

### Post by aassdd on 2013-04-23
driver: unknown :S
OS type: 32 bits

---

### Post by tgalati4 on 2013-04-23
Everything is running hot.  Open a terminal and run:

```
top
```

You might have a stuck process.  Are you running multiple programs?  Check your fans for dirt.

---

### Post by robert shearer on 2013-04-23
> **aassdd said:**
> how do i know it ?

Open a terminal (Ctrl+Alt+T ) and type in..
```
sudo lshw
```

Hit enter then copy and paste the output here inside code tags..( # )

lshw = list hardware

also post back the output of....
```
uname -a
```

---

### Post by aassdd on 2013-04-23
sudo lshw output     

      
 capabilities: synchronous internal write-through unified

        *-logicalcpu:0
             description: Logical CPU
             physical id: 3.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 3.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 3.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 3.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 3.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 3.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 3.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 3.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 3.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 3.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 3.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 3.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 3.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 3.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 3.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 3.10
             width: 64 bits
             capabilities: logical
     *-cache
          description: L1 cache
          physical id: 1c
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.10.7
          serial: 0002-06A7-0000-0000-0000-0000
          size: 800MHz
          capacity: 800MHz
          capabilities: vmx ht cpufreq
          configuration: id=3
        *-logicalcpu:0
             description: Logical CPU
             physical id: 3.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 3.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 3.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 3.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 3.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 3.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 3.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 3.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 3.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 3.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 3.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 3.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 3.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 3.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 3.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 3.10
             capabilities: logical
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:5000(size=4096) memory:c6500000-c74fffff ioport:a0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: Whistler XT [AMD Radeon HD 6700M Series]
                vendor: Advanced Micro Devices [AMD] nee ATI
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:51 memory:a0000000-afffffff memory:c6500000-c651ffff ioport:5000(size=256) memory:c6520000-c653ffff
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:49 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:6000(size=64)
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:48 memory:c7504000-c750400f
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:c750a000-c750a3ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:52 memory:c7500000-c7503fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:4000(size=4096) memory:c5500000-c64fffff ioport:c0400000(size=16777216)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: eth0
                version: 06
                serial: 10:1f:74:14:0c:06
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:47 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:c4500000-c54fffff ioport:c1400000(size=16777216)
           *-network
                description: Wireless interface
                product: Centrino Wireless-N 1030
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:0d:00.0
                logical name: wlan0
                version: 34
                serial: 4c:eb:42:70:d9:6f
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-17-generic firmware=18.168.6.1 ip=192.168.1.35 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:50 memory:c4500000-c4501fff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:2000(size=4096) memory:c3500000-c44fffff ioport:c2400000(size=16777216)
           *-generic
                description: Unassigned class
                product: RTS5209 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:13:00.0
                logical name: scsi6
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom emulated scsi-host
                configuration: driver=rts_pstor latency=0
                resources: irq:18 memory:c3500000-c3500fff memory:c2400000-c240ffff
              *-disk
                   description: SCSI Disk
                   product: xD/SD/M.S.
                   vendor: Generic-
                   physical id: 0.0.0
                   bus info: scsi@6:0.0.0
                   logical name: /dev/sdb
                   version: 1.00
                   serial: 3
                   capabilities: removable
                   configuration: sectorsize=512
                 *-medium
                      physical id: 0
                      logical name: /dev/sdb
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b5
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 memory:c3400000-c34fffff
           *-usb
                description: USB controller
                product: uPD720200 USB 3.0 Host Controller
                vendor: NEC Corporation
                physical id: 0
                bus info: pci@0000:19:00.0
                version: 04
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:19 memory:c3400000-c3401fff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:20 memory:c7509000-c75093ff
        *-isa
             description: ISA bridge
             product: HM65 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:6098(size=8) ioport:60bc(size=4) ioport:6090(size=8) ioport:60b8(size=4) ioport:6060(size=32) memory:c7508000-c75087ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c7506000-c75060ff ioport:6040(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST640LM000 HM641
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2AJ1
             serial: S25YJ9CC216124
             size: 596GiB (640GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00042ab7
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: f6a0262d-bf91-42de-9121-45bbb0fc6c99
                size: 588GiB
                capacity: 588GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-04-23 22:36:57 filesystem=ext4 lastmountpoint=/target modified=2013-04-23 22:58:18 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-04-23 22:58:21 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 8139MiB
                capacity: 8139MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 8139MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi5
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD A  DS8A8SH
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: KH61
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium Ion Battery
       product: MU06062
       vendor: 13-54
       physical id: 1
       slot: Primary
       capacity: 62160mWh
       configuration: voltage=11.1V



uname -a output

3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux
wenawenachoro@asesinatodoblenemig

---

### Post by aassdd on 2013-04-25
solved

---

### Post by mörgæs on 2013-04-25
Thanks for posting, but this is the preferred way:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


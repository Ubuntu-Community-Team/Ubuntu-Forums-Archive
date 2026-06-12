---
title: "Erratic behaviour of cursor"
date: 2017-02-23
forum: General Help
---

### Post by Suchetana on 2017-02-23
Hi
I am using Ubuntu 14.04. My system is regularly updated. Of late (most likely after installing gnuplot with x11), I notice a weird behaviour on my cursor. Every time I point it over a picture and then use the cursor over texts (be it some text file in WPS (strangely not on Libre Office though) or website like Quora etc), the cursor as if shows a part of the picture/symbol/colour etc. It becomes very difficult to use the cursor.
How do I go about rectifying this? I tried taking a screenshot of this, but the resultant image showed no such thing at all.
Any help would be highly appreciated. Thanks in advance.
Regards
Suchetana

---

### Post by mörgæs on 2017-02-24
Maybe the hardware details will give an idea about what is wrong. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Suchetana on 2017-02-24
```
computer
    description: Desktop Computer
    product: 500-101in (H6N23AA#ACJ)
    vendor: Hewlett-Packard
    version: 1.00
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=desktop family=103C_53316J G=D frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=H6N23AA#ACJ uuid=[REMOVED]
  *-core
       description: Motherboard
       product: 2AF7
       vendor: Hewlett-Packard
       physical id: 0
       version: 1.03
       serial: [REMOVED]
     *-firmware
          description: BIOS
          vendor: AMI
          physical id: 0
          version: 80.07
          date: 09/05/2013
          size: 64KiB
          capacity: 8128KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification netboot uefi
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 0
             serial: [REMOVED]
             slot: DIMM1
        *-bank:1
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: M378B1G73QH0-CK0
             vendor: Samsung
             physical id: 1
             serial: [REMOVED]
             slot: DIMM2
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-4570 CPU @ 3.20GHz
          vendor: Intel Corp.
          physical id: 1f
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-4570 CPU @ 3.20GHz
          slot: SOCKET 0
          size: 3201MHz
          capacity: 3201MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L2 cache
             physical id: 20
             slot: CPU Internal L2
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 21
             slot: CPU Internal L1
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-back
        *-cache:2
             description: L3 cache
             physical id: 22
             slot: CPU Internal L3
             size: 6MiB
             capacity: 6MiB
             capabilities: internal write-back unified
     *-pci
          description: Host bridge
          product: 4th Gen Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 06
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e8000000(size=167772160)
           *-display
                description: VGA compatible controller
                product: GF119 [GeForce GT 625 OEM]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:50 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
           *-multimedia
                description: Audio device
                product: GF119 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 34MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:f7080000-f7083fff
        *-usb:0
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:45 memory:f7300000-f730ffff
        *-communication
             description: Communication controller
             product: 8 Series/C220 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:48 memory:f731a000-f731a00f
        *-usb:1
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7318000-f73183ff
        *-multimedia
             description: Audio device
             product: 8 Series/C220 Series Chipset High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:49 memory:f7310000-f7313fff
        *-pci:1
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:e0000000-e01fffff ioport:e0200000(size=2097152)
        *-pci:2
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 memory:f7200000-f72fffff
           *-network UNCLAIMED
                description: Network controller
                product: RT3290 Wireless 802.11n 1T/1R PCIe
                vendor: Ralink corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: memory:f7210000-f721ffff
           *-generic UNCLAIMED
                description: Bluetooth
                product: RT3290 Bluetooth
                vendor: Ralink corp.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: memory:f7200000-f720ffff
        *-pci:3
             description: PCI bridge
             product: 8 Series/C220 Series Chipset Family PCI Express Root Port #7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: d4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:d000(size=4096) memory:f7100000-f71fffff ioport:f2100000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 0c
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resources: irq:47 ioport:d000(size=256) memory:f7100000-f7100fff memory:f2100000-f2103fff
        *-usb:2
             description: USB controller
             product: 8 Series/C220 Series Chipset Family USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7317000-f73173ff
        *-isa
             description: ISA bridge
             product: H87 Express LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:46 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:f7316000-f73167ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series/C220 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7315000-f73150ff ioport:f000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST4000DM000-1F21
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CC52
             serial: [REMOVED]
             size: 3726GiB (4TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=4c030c24-2f58-4a21-b0d6-3d7bc10da603 sectorsize=4096
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: [REMOVED]
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 500GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-07-01 17:43:17 filesystem=ext4 label=Ubuntu OS lastmountpoint=/ modified=2017-02-23 16:40:51 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-02-23 16:40:51 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: [REMOVED]
                size: 8129MiB
                capacity: 8130MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:3
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: FAT32
                serial: [REMOVED]
                size: 499GiB
                capacity: 499GiB
                capabilities: fat initialized
                configuration: FATs=2 filesystem=fat label=DATA2
           *-volume:4
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                version: FAT32
                serial: [REMOVED]
                size: 499GiB
                capacity: 499GiB
                capabilities: fat initialized
                configuration: FATs=2 filesystem=fat label=DATA3
           *-volume:5
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                version: FAT32
                serial: [REMOVED]
                size: 499GiB
                capacity: 499GiB
                capabilities: fat initialized
                configuration: FATs=2 filesystem=fat label=DATA4
           *-volume:6
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 7
                bus info: scsi@0:0.0.0,7
                logical name: /dev/sda7
                logical name: /media/suchetana/DATA5
                version: FAT32
                serial: [REMOVED]
                size: 999GiB
                capacity: 999GiB
                capabilities: fat initialized
                configuration: FATs=2 filesystem=fat label=DATA5 mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
           *-volume:7
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 8
                bus info: scsi@0:0.0.0,8
                logical name: /dev/sda8
                logical name: /media/suchetana/DATA6
                version: FAT32
                serial: [REMOVED]
                size: 717GiB
                capacity: 717GiB
                capabilities: fat initialized
                configuration: FATs=2 filesystem=fat label=DATA6 mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM GHA3N
             vendor: hp
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: RH06
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-power UNCLAIMED
       description: N/A
       product: Standard Efficiency
       vendor: NULL
       physical id: 1
       version: NULL
       serial: [REMOVED]
       capacity: 32768mWh
```

---

### Post by mörgæs on 2017-02-24
With a graphics processor that new I would not expect 14.04 to work. Better to try 16.10 or at least 16.04.2.

---

### Post by Suchetana on 2017-02-24
It was working fine until I installed gnuplot with x11. Is there anyother workaround? I am not really keen on upgrading the OS

---

### Post by ajgreeny on 2017-02-24
You may find that installing the hardware enablement stack for xenial in your trusty system adds the required xorg drivers and kernel modules needed so give that a try as well if you have not already done so.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by Suchetana on 2017-02-25
As of now, it worked. However, in the process, my WPS got uninstalled. I did a reinstall. Now it looks fine. Let's see.. Thanks to everyone who helped.

---


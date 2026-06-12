---
title: "ubuntu 14.04 freezes"
date: 2014-04-12
forum: General Help
---

### Post by AbhimanyuAryan on 2014-04-12
i don't know whats the reason but ubuntu 14.04(final beta) freezes some times & i have no choice than to power off my laptop :(

---

### Post by gifford on 2014-04-12
Can you indicate what type of laptop and hardware you have?

---

### Post by AbhimanyuAryan on 2014-04-12
```
 description: Logical CPU             physical id: 3.c
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
          physical id: a
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-through data
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 0
             serial: Empty
             slot: DIMM0
        *-bank:1
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 1
             serial: Empty
             slot: DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: AM1U16BC4P2-B19B
             vendor: A-DATA Technology
             physical id: 2
             serial: 00004546
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 3
             serial: Empty
             slot: DIMM3
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
             resources: irq:40 ioport:2000(size=4096) memory:b2000000-b2ffffff ioport:a0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: irq:51 memory:b2000000-b2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:2000(size=128)
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
             resources: irq:44 memory:b3000000-b33fffff memory:c0000000-cfffffff ioport:3000(size=64)
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:41 memory:b3600000-b360ffff
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:43 memory:b3614000-b361400f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:b3619000-b36193ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:b3610000-b3613fff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:9fb00000-9fbfffff ioport:b3400000(size=1048576)
           *-network
                description: Ethernet interface
                product: NetLink BCM57785 Gigabit Ethernet PCIe
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 10
                serial: 20:89:84:77:44:5c
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 firmware=sb latency=0 link=no multicast=yes port=twisted pair
                resources: irq:16 memory:b3430000-b343ffff memory:b3440000-b344ffff memory:b3450000-b34507ff
           *-generic:0
                description: SD Host controller
                product: BCM57765/57785 SDXC/MMC Card Reader
                vendor: Broadcom Corporation
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:b3400000-b340ffff
           *-generic:1 UNCLAIMED
                description: System peripheral
                product: BCM57765/57785 MS Card Reader
                vendor: Broadcom Corporation
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:b3410000-b341ffff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: BCM57765/57785 xD-Picture Card Reader
                vendor: Broadcom Corporation
                physical id: 0.3
                bus info: pci@0000:02:00.3
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:b3420000-b342ffff
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:b3500000-b35fffff ioport:9fc00000(size=1048576)
           *-network
                description: Wireless interface
                product: AR9462 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: bc:85:56:12:98:27
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.13.0-24-generic firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:17 memory:b3500000-b357ffff memory:9fc00000-9fc0ffff
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:b3618000-b36183ff
        *-isa
             description: ISA bridge
             product: HM77 Express Chipset LPC Controller
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
             product: 7 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:3088(size=8) ioport:3094(size=4) ioport:3080(size=8) ioport:3090(size=4) ioport:3060(size=32) memory:b3617000-b36177ff
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b3615000-b36150ff ioport:3040(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST500LT012-9WS14
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0001
             serial: W0V9P461
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=0003c053
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: bc6f51c5-7821-416c-bdd8-53535a21329f
                size: 461GiB
                capacity: 461GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-04-10 03:18:11 filesystem=ext4 lastmountpoint=/ modified=2014-04-13 01:10:09 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-04-13 01:10:10 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 3985MiB
                capacity: 3985MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 3985MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi2
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GT90N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc





```

---

### Post by AbhimanyuAryan on 2014-04-13
this is ```
lshw
``` command result

---

### Post by carl4926 on 2014-04-13
Do I detect Hybrid Graphics?

---

### Post by AbhimanyuAryan on 2014-04-13
hybrid graphics means? how can i check if my laptop has hybrid graphics or not.

---

### Post by carl4926 on 2014-04-13
```
[COLOR=#000000][FONT=Ubuntu Mono]*-display[/FONT][/COLOR]                description: VGA compatible controller
                product: GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: irq:51 memory:b2000000-b2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:2000(size=128)
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
             configuration: driver=i915 latency=0 [COLOR=#000000][FONT=Ubuntu Mono]             resources: irq:44 memory:b3000000-b33fffff memory:c0000000-cfffffff ioport:3000(size=64)[/FONT][/COLOR]
```

= more than one graphics device

---

### Post by martinsmihov on 2014-04-19
I've got the same problem. The screen freezes (the mouse is not moving, keyboard is not reacting, screen is frozen), however everything else continues to work normally (sound is being playes, videos are playing, programs are running). And this happens at really random times, I cannot cause it myself.

However I've found a workaround for me, that at least doesn't need to restart the computer: Just go to console (Ctrl+Alt+F2) and then back to the desktop (Ctrl+Alt+F7). After doing this everything is working fine, until the next time. If anyone can find the cause of the problem it would be great.

I have Asus N56VJ. 64bit quad core i7, 8GB ram, NVIDIA GeForce GT 635M.

```
martinch0-n56vj               description: Notebook
    product: N56VJ (ASUS-NotebookSKU)
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: CBN0BC34692946C
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=N sku=ASUS-NotebookSKU uuid=5154434E-4A38-4130-4332-50465D3CC5ED
  *-core
       description: Motherboard
       product: N56VJ
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: N56VJ.203
          date: 08/29/2012
          size: 64KiB
          capacity: 6080KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-cache:0
          description: L2 cache
          physical id: 8
          slot: CPU Internal L2
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-through unified
     *-cache:1
          description: L1 cache
          physical id: 9
          slot: CPU Internal L1
          size: 256KiB
          capacity: 256KiB
          capabilities: internal write-through data
     *-cache:2
          description: L3 cache
          physical id: a
          slot: CPU Internal L3
          size: 6MiB
          capacity: 6MiB
          capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: HMT351S6CFR8C-PB
             vendor: Hynix/Hyundai
             physical id: 0
             serial: 1A30F1DB
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-04-10 12:53+0000X-Generator: Launchpad (build 16976) [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 1
             serial: [Empty]
             slot: ChannelA-DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: HMT351S6CFR8C-PB
             vendor: Hynix/Hyundai
             physical id: 2
             serial: 1A20F1DD
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2014-04-10 12:53+0000X-Generator: Launchpad (build 16976) [empty]
             product: [Empty]
             vendor: [Empty]
             physical id: 3
             serial: [Empty]
             slot: ChannelB-DIMM1
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz
          vendor: Intel Corp.
          physical id: c
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz
          slot: SOCKET 0
          size: 1300MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-pci
          description: Host bridge
          product: 3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GF108M [GeForce GT 635M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:46 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:41 memory:f7a00000-f7a0ffff
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:42 memory:f7a19000-f7a1900f
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:f7a17000-f7a173ff
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:f7a10000-f7a13fff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:f7900000-f79fffff
           *-network
                description: Wireless interface
                product: AR9485 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: dc:85:de:89:5e:c7
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.13.0-24-generic firmware=N/A ip=192.168.1.115 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f7900000-f797ffff memory:f7980000-f798ffff
        *-pci:3
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:d000(size=4096) memory:f7800000-f78fffff
           *-network
                description: Ethernet interface
                product: AR8161 Gigabit Ethernet
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: eth0
                version: 10
                serial: 50:46:5d:3c:c5:ed
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
                resources: irq:45 memory:f7800000-f783ffff ioport:d000(size=128)
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:f7a16000-f7a163ff
        *-isa
             description: ISA bridge
             product: HM76 Express Chipset LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 7 Series Chipset Family 4-port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f110(size=8) ioport:f100(size=4) ioport:f0f0(size=8) ioport:f0e0(size=4) ioport:f0d0(size=16) ioport:f0c0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7a15000-f7a150ff ioport:f040(size=32)
        *-ide:1
             description: IDE interface
             product: 7 Series Chipset Family 2-port SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=16) ioport:f060(size=16)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST750LM022 HN-M7
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2AR1
             serial: S2UQJ9CCA30597
             size: 698GiB (750GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=092e8c1c-41fe-4571-bcc7-eb8cf608b4bc sectorsize=4096
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 7839-4398
                size: 298MiB
                capacity: 299MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2014-02-28 21:01:17 filesystem=ntfs label=Recovery modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot/efi
                version: FAT32
                serial: a83a-fbe5
                size: 83MiB
                capacity: 99MiB
                capabilities: boot precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: b3571472-be12-4ed0-b833-3ee2bfc9bafb
                capacity: 127MiB
                capabilities: nofs precious readonly hidden nomount
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: 4e7f3a27-62da-494f-a89a-fcecc11cf1a8
                size: 175GiB
                capacity: 175GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2014-02-28 21:01:54 filesystem=ntfs name=Basic data partition state=clean
           *-volume:4
                description: EXT4 volume
                vendor: Linux
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                logical name: /
                version: 1.0
                serial: 140d4d90-5ce6-4322-9344-1ff96c668ecd
                size: 100GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-04-17 23:01:15 filesystem=ext4 lastmountpoint=/ modified=2014-04-18 22:06:35 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-04-18 22:06:36 name=Linux filesystem state=mounted
           *-volume:5
                description: Linux swap volume
                vendor: Linux
                physical id: 6
                bus info: scsi@0:0.0.0,6
                logical name: /dev/sda6
                version: 1
                serial: 9c34acc4-b279-402f-b6c6-efc73d1e7ea0
                size: 19GiB
                capacity: 19GiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap name=Linux swap pagesize=4095
           *-volume:6
                description: Windows NTFS volume
                vendor: Windows
                physical id: 7
                bus info: scsi@0:0.0.0,7
                logical name: /dev/sda7
                logical name: /mnt/6839C5516C45B717
                version: 3.1
                serial: f6f8fdf6-85e5-0643-850a-9bc6171de5a9
                size: 402GiB
                capacity: 402GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2013-12-20 17:17:40 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 name=Microsoft basic data state=mounted
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ8C0
             vendor: MATSHITA
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:1
          physical id: 2
          bus info: usb@1:1.4
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Card  Reader
             vendor: Multiple
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 1.00
             size: 3781MiB (3965MB)
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 3781MiB (3965MB)
                capabilities: partitioned partitioned:dos
              *-volume
                   description: Windows FAT volume
                   physical id: 1
                   logical name: /dev/sdb1
                   logical name: /media/martinch0/3965-3862
                   version: FAT32
                   serial: 3965-3862
                   size: 3770MiB
                   capacity: 3777MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted



```

---

### Post by carl4926 on 2014-04-19
```
[COLOR=#000000][FONT=Ubuntu Mono]*-display[/FONT][/COLOR]                description: VGA compatible controller
                product: GF108M [GeForce GT 635M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:46 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0 [COLOR=#000000][FONT=Ubuntu Mono]             resources: irq:43 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)[/FONT][/COLOR]
```

Also hybrid

---

### Post by martinsmihov on 2014-04-19
Also forgot to mention, I am currently using NVIDIA binary driver - version 331.38 from nvidia-331 (proprietary, tested).

---

### Post by carl4926 on 2014-04-19
> **martinsmihov said:**
> Also forgot to mention, I am currently using NVIDIA binary driver - version 331.38 from nvidia-331 (proprietary, tested).

I'm not sure it's that simple
You could do with someone answering who uses such graphics, I don't.

---

### Post by rmlourenco on 2014-04-27
Hi there. I also have that problem. The system freezes randomly. Only doing Ctrl + Alt + F1 followed by Ctrl + Alt + F7 unfreezes it. This apparently only happens when using the discrete graphics (GeForce GTX765M in my case). I started by using the official 331.38 version and then I detected this issue. After that I have already searched the issue on the web and throughout it was suggested to upgrade the drivers to 331.67 as it (supposedly) would solve the issue. But after upgrading the driver and rebooting the computer I still have the same problem. I will now try the 337 driver. If it solves the problem I will post here.

Cheers,

Rafael

PS: Sorry for my poor english...

---

### Post by sam_baker2 on 2014-04-27
me too.
I have a desktop using 12.04 Xubuntu with a 650 Nvidia card.
In the past, I could not ever remember my machine freezing up, but in about the last 
week or two, my machine has froze up about 5 or 6 times.
I have reset my driver to the basic Nvidia 304 driver.

---

### Post by martinsmihov on 2014-04-28
I have switched back to the X.org X server drivers and the issue is gone. However I am not able to use any of the NVidia's drivers as they keep freezing randomly.

---

### Post by Ben_Lev on 2014-06-06
> **martinsmihov said:**
> I have switched back to the X.org X server drivers and the issue is gone. However I am not able to use any of the NVidia's drivers as they keep freezing randomly.

I have the same problem on my asus laptop (nvidia geforce 720m), using the X.org X server doesn't help.
Anyway, It's ridiculous to not be able to use your graphic card with the suitable drivers.

---


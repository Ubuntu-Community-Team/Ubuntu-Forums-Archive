---
title: "HP EliteBook 840 G1 - Ubuntu 14.04 - Bluetooth - Help."
date: 2015-02-01
forum: General Help
---

### Post by iason on 2015-02-01
Hello,

Pretty novice linux user here and trying to get bluetooth up and running on this elitebook 840.  Where do I start?  Is it even possible? Searching the forums said it should be possible with proprietary drivers, looks like I am running those drivers now though with no luck.

```
description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 15GiB
     *-cpu
          product: Intel(R) Core(TM) i7-4600U CPU @ 2.10GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 756MHz
          capacity: 756MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm cpufreq
     *-pci
          description: Host bridge
          product: Haswell-ULT DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0b
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Haswell-ULT Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0b
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:65 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:3000(size=64)
        *-multimedia:0
             description: Audio device
             product: Haswell-ULT HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0b
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:68 memory:d0730000-d0733fff
        *-usb:0
             description: USB controller
             product: Lynx Point-LP USB xHCI HC
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:61 memory:d0720000-d072ffff
        *-communication:0
             description: Communication controller
             product: Lynx Point-LP HECI #0
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:62 memory:d0739000-d073901f
        *-communication:1
             description: Serial controller
             product: Lynx Point-LP HECI KT
             vendor: Intel Corporation
             physical id: 16.3
             bus info: pci@0000:00:16.3
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: 16550 bus_master cap_list
             configuration: driver=serial latency=0
             resources: irq:19 ioport:30b0(size=8) memory:d073f000-d073ffff
        *-network
             description: Ethernet interface
             product: Ethernet Connection I218-LM
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 04
             serial: 64:51:06:9f:91:9a
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.3-4 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:66 memory:d0700000-d071ffff memory:d073e000-d073efff ioport:3080(size=32)
        *-multimedia:1
             description: Audio device
             product: Lynx Point-LP HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:69 memory:d0734000-d0737fff
        *-pci:0
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:58 memory:d0600000-d06fffff
        *-pci:1
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:59 memory:d0500000-d05fffff
           *-network
                description: Wireless interface
                product: Wireless 7260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 73
                serial: a0:a8:cd:b1:29:7f
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-44-generic firmware=22.24.8.0 ip=192.168.1.104 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:67 memory:d0500000-d0501fff
        *-pci:2
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:60 ioport:2000(size=4096) memory:d0400000-d04fffff ioport:bf300000(size=2097152)
           *-generic
                description: Unassigned class
                product: RTS5227 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:63 memory:d0400000-d0400fff
        *-usb:1
             description: USB controller
             product: Lynx Point-LP USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:17 memory:d073d000-d073d3ff
        *-isa
             description: ISA bridge
             product: Lynx Point-LP LPC Controller
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
             product: Lynx Point-LP SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:64 ioport:30a8(size=8) ioport:30bc(size=4) ioport:30a0(size=8) ioport:30b8(size=4) ioport:3060(size=32) memory:d073c000-d073c7ff
        *-serial UNCLAIMED
             description: SMBus
             product: Lynx Point-LP SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d0738000-d07380ff ioport:ef80(size=32)
```

---

### Post by zeljko-baralic on 2015-05-08
Hi,

Is Bluetooth enabled in BIOS?

---


---
title: "HP x360 Bluetooth Woes"
date: 2016-12-29
forum: General Help
---

### Post by Sableyes on 2016-12-29
Hello Ubuntu's

I have a HP Pavilion x360 [(this model)]("http://amzn.to/2hvOVa8"), and I am having issues having both the Bluetooth and WiFi on at the same time. Wifi works on it's own, and Bluetooth works on it's own, but when I have both turned on at the same time, both wifi and bluetooth slow to a crawl. Guessing its a shared card.

lshw gives me the below output. 

Any help greatly appreciated!

```
   lshw
 sablex360                    
     description: Computer
     width: 64 bits
     capabilities: smp vsyscall32
   *-core
        description: Motherboard
        physical id: 0
      *-memory
           description: System memory
           physical id: 0
           size: 7903MiB
      *-cpu
           product: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz
           vendor: Intel Corp.
           physical id: 1
           bus info: cpu@0
           size: 499MHz
           capacity: 2800MHz
           width: 64 bits
           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
      *-pci
           description: Host bridge
           product: Skylake Host Bridge/DRAM Registers
           vendor: Intel Corporation
           physical id: 100
           bus info: pci@0000:00:00.0
           version: 08
           width: 32 bits
           clock: 33MHz
         *-display
              description: VGA compatible controller
              product: HD Graphics 520
              vendor: Intel Corporation
              physical id: 2
              bus info: pci@0000:00:02.0
              version: 07
              width: 64 bits
              clock: 33MHz
              capabilities: vga_controller bus_master cap_list rom
              configuration: driver=i915 latency=0
              resources: irq:282 memory:b0000000-b0ffffff memory:a0000000-afffffff ioport:4000(size=64) memory:c0000-dffff
         *-generic:0
              description: Signal processing controller
              product: Skylake Processor Thermal Subsystem
              vendor: Intel Corporation
              physical id: 4
              bus info: pci@0000:00:04.0
              version: 08
              width: 64 bits
              clock: 33MHz
              capabilities: bus_master cap_list
              configuration: driver=proc_thermal latency=0
              resources: irq:16 memory:b1620000-b1627fff
         *-generic:1 UNCLAIMED
              description: Non-VGA unclassified device
              product: Intel Corporation
              vendor: Intel Corporation
              physical id: 13
              bus info: pci@0000:00:13.0
              version: 21
              width: 64 bits
              clock: 33MHz
              capabilities: bus_master cap_list
              configuration: latency=0
              resources: memory:b1632000-b1632fff
         *-usb
              description: USB controller
              product: Sunrise Point-LP USB 3.0 xHCI Controller
              vendor: Intel Corporation
              physical id: 14
              bus info: pci@0000:00:14.0
              version: 21
              width: 64 bits
              clock: 33MHz
              capabilities: xhci bus_master cap_list
              configuration: driver=xhci_hcd latency=0
              resources: irq:126 memory:b1600000-b160ffff
         *-generic:2
              description: Signal processing controller
              product: Sunrise Point-LP Thermal subsystem
              vendor: Intel Corporation
              physical id: 14.2
              bus info: pci@0000:00:14.2
              version: 21
              width: 64 bits
              clock: 33MHz
              capabilities: bus_master cap_list
              configuration: driver=intel_pch_thermal latency=0
              resources: irq:18 memory:b1633000-b1633fff
         *-generic:3
              description: Signal processing controller
              product: Sunrise Point-LP Serial IO I2C Controller #0
              vendor: Intel Corporation
              physical id: 15
              bus info: pci@0000:00:15.0
              version: 21
              width: 64 bits
              clock: 33MHz
              capabilities: bus_master cap_list
              configuration: driver=intel-lpss latency=0
              resources: irq:16 memory:b1634000-b1634fff
         *-generic:4
              description: Signal processing controller
              product: Sunrise Point-LP Serial IO I2C Controller #1
              vendor: Intel Corporation
              physical id: 15.1
              bus info: pci@0000:00:15.1
              version: 21
              width: 64 bits
              clock: 33MHz
              capabilities: bus_master cap_list
              configuration: driver=intel-lpss latency=0
              resources: irq:17 memory:b1635000-b1635fff
         *-communication
              description: Communication controller
              product: Sunrise Point-LP CSME HECI #1
              vendor: Intel Corporation
              physical id: 16
              bus info: pci@0000:00:16.0
              version: 21
              width: 64 bits
              clock: 33MHz
              capabilities: bus_master cap_list
              configuration: driver=mei_me latency=0
              resources: irq:283 memory:b1636000-b1636fff
         *-storage
              description: SATA controller
              product: Sunrise Point-LP SATA Controller [AHCI mode]
              vendor: Intel Corporation
              physical id: 17
              bus info: pci@0000:00:17.0
              version: 21
              width: 32 bits
              clock: 66MHz
              capabilities: storage ahci_1.0 bus_master cap_list
              configuration: driver=ahci latency=0
              resources: irq:279 memory:b1630000-b1631fff memory:b1639000-b16390ff ioport:4080(size=8) ioport:4088(size=4) ioport:4060(size=32) memory:b1637000-b16377ff
         *-pci:0
              description: PCI bridge
              product: Intel Corporation
              vendor: Intel Corporation
              physical id: 1c
              bus info: pci@0000:00:1c.0
              version: f1
              width: 32 bits
              clock: 33MHz
              capabilities: pci normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:122 ioport:5000(size=4096) memory:90100000-902fffff ioport:90300000(size=2097152)
         *-pci:1
              description: PCI bridge
              product: Sunrise Point-LP PCI Express Root Port #5
              vendor: Intel Corporation
              physical id: 1c.4
              bus info: pci@0000:00:1c.4
              version: f1
              width: 32 bits
              clock: 33MHz
              capabilities: pci normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:123 memory:b1500000-b15fffff
            *-network
                 description: Wireless interface
                 product: Wireless 3165
                 vendor: Intel Corporation
                 physical id: 0
                 bus info: pci@0000:02:00.0
                 logical name: wlp2s0
                 version: 81
                 serial: 00:db:df:bb:f8:0a
                 width: 64 bits
                 clock: 33MHz
                 capabilities: bus_master cap_list ethernet physical wireless
                 configuration: broadcast=yes driver=iwlwifi driverversion=4.8.0-32-generic firmware=22.361476.0 ip=192.168.0.16 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                 resources: irq:284 memory:b1500000-b1501fff
         *-pci:2
              description: PCI bridge
              product: Sunrise Point-LP PCI Express Root Port #6
              vendor: Intel Corporation
              physical id: 1c.5
              bus info: pci@0000:00:1c.5
              version: f1
              width: 32 bits
              clock: 33MHz
              capabilities: pci normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:124 ioport:3000(size=4096) memory:b1400000-b14fffff
            *-network
                 description: Ethernet interface
                 product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
                 vendor: Realtek Semiconductor Co., Ltd.
                 physical id: 0
                 bus info: pci@0000:03:00.0
                 logical name: enp3s0
                 version: 0a
                 serial: dc:4a:3e:ac:b7:3f
                 size: 10Mbit/s
                 capacity: 100Mbit/s
                 width: 64 bits
                 clock: 33MHz
                 capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                 configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8107e-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                 resources: irq:281 ioport:3000(size=256) memory:b1404000-b1404fff memory:b1400000-b1403fff
         *-pci:3
              description: PCI bridge
              product: Sunrise Point-LP PCI Express Root Port #9
              vendor: Intel Corporation
              physical id: 1d
              bus info: pci@0000:00:1d.0
              version: f1
              width: 32 bits
              clock: 33MHz
              capabilities: pci normal_decode bus_master cap_list
              configuration: driver=pcieport
              resources: irq:125 memory:b1300000-b13fffff
            *-generic
                 description: Unassigned class
                 product: RTS522A PCI Express Card Reader
                 vendor: Realtek Semiconductor Co., Ltd.
                 physical id: 0
                 bus info: pci@0000:04:00.0
                 version: 01
                 width: 32 bits
                 clock: 33MHz
                 capabilities: bus_master cap_list
                 configuration: driver=rtsx_pci latency=0
                 resources: irq:280 memory:b1300000-b1300fff
         *-isa
              description: ISA bridge
              product: Sunrise Point-LP LPC Controller
              vendor: Intel Corporation
              physical id: 1f
              bus info: pci@0000:00:1f.0
              version: 21
              width: 32 bits
              clock: 33MHz
              capabilities: isa bus_master
              configuration: latency=0
         *-memory
              description: Memory controller
              product: Sunrise Point-LP PMC
              vendor: Intel Corporation
              physical id: 1f.2
              bus info: pci@0000:00:1f.2
              version: 21
              width: 32 bits
              clock: 33MHz (30.3ns)
              capabilities: bus_master
              configuration: driver=intel_pmc_core latency=0
              resources: irq:0 memory:b162c000-b162ffff
         *-multimedia
              description: Audio device
              product: Sunrise Point-LP HD Audio
              vendor: Intel Corporation
              physical id: 1f.3
              bus info: pci@0000:00:1f.3
              version: 21
              width: 64 bits
              clock: 33MHz
              capabilities: bus_master cap_list
              configuration: driver=snd_hda_intel latency=32
              resources: irq:285 memory:b1628000-b162bfff memory:b1610000-b161ffff
         *-serial UNCLAIMED
              description: SMBus
              product: Sunrise Point-LP SMBus
              vendor: Intel Corporation
              physical id: 1f.4
              bus info: pci@0000:00:1f.4
              version: 21
              width: 64 bits
              clock: 33MHz
              configuration: latency=0
              resources: memory:b1638000-b16380ff ioport:4040(size=32)
         *-generic:5
              description: Non-Essential Instrumentation
              product: Intel Corporation
              vendor: Intel Corporation
              physical id: 1f.7
              bus info: pci@0000:00:1f.7
              version: 21
              width: 64 bits
              clock: 33MHz
              capabilities: bus_master cap_list
              configuration: driver=intel_th_pci latency=0
              resources: irq:16 memory:b1200000-b12fffff memory:fe200000-fe3fffff
 
 

```

---

### Post by jeremy31 on 2016-12-29
The iwlwifi module enables bluetooth coexistence by default we can see is disabling it helps any
```
echo "options iwlwifi bt_coex_active=0" | sudo tee /etc/modprobe.d/iwlopt.conf
```

Reboot

If things are worse delete the file with ```
sudo rm /etc/modprobe.d/iwlopt.conf
```
Reboot

---

### Post by Sableyes on 2016-12-29
Thank you for that, the first line appears to have cleared it up.

Cheers!

---

### Post by Sableyes on 2017-02-22
Update. That worked for a few days then the Bluetooth / WiFi at the same time got progressively worse to a point now where it is unusable.

Not sure if I just had a lucky run right after entering the above into terminal or if it had any effect.

---


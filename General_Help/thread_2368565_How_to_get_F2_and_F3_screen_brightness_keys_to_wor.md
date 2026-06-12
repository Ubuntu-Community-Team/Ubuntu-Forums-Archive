---
title: "How to get F2 and F3 screen brightness keys to work Ubuntu 16.04"
date: 2017-08-12
forum: General Help
---

### Post by hh1488 on 2017-08-12
Hello I have installed Ubuntu 16.04 on my HP x360 Laptop and I have tried many different things and as of yet not been able to get my brightness keys working. I have however installed a utility that adjusts the brightness manually but it is buggy and never remembers settings after reboot.

Here are the details of my system.

Help would be much appreciated.



[PHP]dannyfitzgerald@Terminal-x360:~$ sudo lshw
[sudo] password for dannyfitzgerald: 
terminal-x360             
    description: Computer
    product: HP Spectre x360 Convertible (X0T30PA#ABG)
    vendor: HP
    version: Chassis Version
    serial: 5CD6357VW1
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 vsyscall32
    configuration: boot=normal family=103C_5335KV G=N L=CON B=HP S=SPT sku=X0T30PA#ABG uuid=35434436-3335-3756-5731-315635334435
  *-core
       description: Motherboard
       product: 81A1
       vendor: HP
       physical id: 0
       version: 33.78
       serial: PFYMA018J400TD
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: F.46
          date: 06/01/2017
          size: 64KiB
          capacity: 6080KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-cache:0
          description: L1 cache
          physical id: 10
          slot: L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-cache:1
          description: L1 cache
          physical id: 11
          slot: L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back instruction
          configuration: level=1
     *-cache:2
          description: L2 cache
          physical id: 12
          slot: L2 Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:3
          description: L3 cache
          physical id: 13
          slot: L3 Cache
          size: 4MiB
          capacity: 4MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz
          vendor: Intel Corp.
          physical id: 14
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 3GHz
          capacity: 3100MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: Row of chips Synchronous 1600 MHz (0.6 ns)
             product: K4E6E304EB-EGCF
             vendor: Samsung
             physical id: 0
             serial: Not Available
             slot: Bottom - on board
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: Row of chips Synchronous 1600 MHz (0.6 ns)
             product: K4E6E304EB-EGCF
             vendor: Samsung
             physical id: 1
             serial: Not Available
             slot: Bottom - on board
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Sky Lake Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 08
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Sky Lake Integrated Graphics
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:131 memory:de000000-deffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff
        *-generic:0
             description: Non-VGA unclassified device
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel_ish_ipc latency=0
             resources: irq:20 memory:df32b000-df32bfff
        *-usb
             description: USB controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:125 memory:df310000-df31ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.10.0-30-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.10
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: HP USB Optical Mouse
                   vendor: PixArt
                   physical id: 3
                   bus info: usb@1:3
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:1
                   description: Video
                   product: HP Wide Vision FHD Camera
                   vendor: SuYin
                   physical id: 6
                   bus info: usb@1:6
                   version: 1.00
                   serial: HF2017-T830-SN03-3-REV0100
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 7
                   bus info: usb@1:7
                   version: 0.01
                   capabilities: bluetooth usb-2.01
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:3
                   description: Human interface device
                   product: Synaptics Touch Digitizer V04
                   vendor: SYNAPTICS
                   physical id: 8
                   bus info: usb@1:8
                   version: 50.05
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=400mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.10.0-30-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.10
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic:1
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:df32a000-df32afff
        *-communication
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:132 memory:df329000-df329fff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 memory:df200000-df2fffff
           *-generic
                description: Unassigned class
                product: RTS5227 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:126 memory:df200000-df200fff
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 memory:df100000-df1fffff
           *-network
                description: Wireless interface
                product: Wireless 7265
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlo1
                version: 61
                serial: a4:02:b9:f7:53:8c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-30-generic firmware=22.391740.0 ip=192.168.43.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:153 memory:df100000-df101fff
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 ioport:e000(size=4096) memory:df000000-df0fffff
           *-storage
                description: Non-Volatile memory controller
                product: Samsung Electronics Co Ltd
                vendor: Samsung Electronics Co Ltd
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:df000000-df003fff ioport:e000(size=256)
        *-isa
             description: ISA bridge
             product: Intel Corporation
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
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             configuration: driver=intel_pmc_core latency=0
             resources: irq:0 memory:df324000-df327fff
        *-multimedia
             description: Multimedia audio controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:154 memory:df320000-df323fff memory:df300000-df30ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 21
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:df328000-df3280ff ioport:f040(size=32)
  *-battery
       product: PK03056XL
       vendor: 3332C
       physical id: 1
       slot: Primary
       capacity: 56540mWh
       configuration: voltage=11.4V[/PHP]

---

### Post by efflandt on 2017-08-12
That is normally a function of ACPI. Most laptops have ACPI functions as primary functions now for F# keys, and if you want actual F1 - F12 functions, you need to use **fn** key like a shift key for them. That is why the ACPI functions are shown larger on the keys than tiny F#'s in upper corners of those keys on my laptop.

See if dmesg in a terminal window shows anything after pressing F2 and/or F3. That works for me running Ubuntu 16.04 on a very low end Win10 HP laptop (slow quad-core Pentium). Even though F2/F3 does adjust brightness for me, dmesg shows the following because X itself is ignoring those keys. Although, when I pressed F3 to increase brightness, then F2 to reduce it, it appears to be same keycode, so maybe the keycode is just if something wants to monitor that brightness has changed:```
[  132.967711] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[  132.967742] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[  132.975836] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[  132.975847] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[  135.955035] atkbd serio0: Unknown key pressed (translated set 2, code 0xab on isa0060/serio0).
[  135.955045] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
[  135.963575] atkbd serio0: Unknown key released (translated set 2, code 0xab on isa0060/serio0).
[  135.963591] atkbd serio0: Use 'setkeycodes e02b <keycode>' to make it known.
```My laptop apparently uses different BIOS/UEFI (never heard of Insyde before):```
hp1604-64
    description: Notebook
    product: HP Notebook (V3T73UA#ABA)
    vendor: HP
    version: Type1ProductConfigId
    serial: CND61105ZP
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5335KV G=N L=CON B=HP sku=V3T73UA#ABA uuid=8778EBA5-E5A1-11E5-B27E-705A0FB5D429
  *-core
       description: Motherboard
       product: 80C5
       vendor: HP
       physical id: 0
       version: 97.48
       serial: PFEHUF21U16IHA
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde
          physical id: 0
          version: F.21
          date: 05/17/2016
          size: 64KiB
          capacity: 3008KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU  N3700  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU  N3700  @ 1.60GHz
          serial: To Be Filled By O.E.M.
          slot: CHV
          size: 821MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 83MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
          configuration: cores=4 enabledcores=4 threads=4
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
```

**Settings** > **Brightness & Lock** is also able to adjust my screen brightness and has a checkbox for "Dim to save power", but not sure what time period before that happens. I don't know if any of that survives boot, that might be a setting in UEFI/BIOS. But I would think that if you set it in Brightness & Lock, Ubuntu would use that setting when it runs.

---


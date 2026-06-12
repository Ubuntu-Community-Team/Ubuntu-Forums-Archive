---
title: "Desktop boots to a solid white screen"
date: 2017-07-14
forum: General Help
---

### Post by bryan.sailer on 2017-07-14
After allowing my desktop to time out and lock the screen it would not unlock.  I tried CTRL-ALT-DEL and ESC but the screen remained black.  Then I rebooted my computer and it appeared to boot with no errors but after the KDE symbol and version number finished flashing the screen goes white.  Prior to my computer screen locking I was on the Ubuntu Forum site updating my profile.  The only changes I have made to my system today was installing plymouth-manager, to change my login and splash screen, and applying the latest updates.  The information about my system is listed below.  If you need any other information let me know.  Currently, I booted my system from a Live DVD.

```
kubuntu@kubuntu:~/Public$ sudo lshw
kubuntu                     
    description: Desktop Computer
    product: GA-78LMT-USB3 6.0
    vendor: Gigabyte Technology Co., Ltd.
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 smp vsyscall32
    configuration: boot=normal chassis=desktop uuid=34303844-3543-3734-3942-3730FFFFFFFF
  *-core
       description: Motherboard
       product: GA-78LMT-USB3 6.0
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: SEx
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: F2
          date: 11/25/2014
          size: 128KiB
          capacity: 4032KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD FX(tm)-4350 Quad-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD FX(tm)-4350 Quad-Core Processor
          slot: Socket M2
          size: 2GHz
          capacity: 4200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb cpb hw_pstate vmmcall bmi1 arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
             configuration: level=1
        *-cache:1
             description: L3 cache
             physical id: c
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous internal write-back
             configuration: level=3
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 23
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM 1333 MHz (0.8 ns) [empty]
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM 1333 MHz (0.8 ns) [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:2
             description: DIMM 1333 MHz (0.8 ns) [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:3
             description: DIMM 1333 MHz (0.8 ns)
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             size: 8GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci:0
          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 64 bits
          clock: 66MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 0)
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) memory:fb000000-fcffffff ioport:c0000000(size=536870912)
           *-display
                description: VGA compatible controller
                product: GM206 [GeForce GTX 950]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nouveau latency=0
                resources: irq:29 memory:fb000000-fbffffff memory:c0000000-cfffffff memory:de000000-dfffffff ioport:ef00(size=128) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:19 memory:fcffc000-fcffffff
```

---


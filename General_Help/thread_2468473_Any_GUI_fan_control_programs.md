---
title: "Any GUI fan control programs?"
date: 2021-10-30
forum: General Help
---

### Post by cwblanch on 2021-10-30
I've finally made my way back to Linux because the games actually work now, well a lot of them do at least.

I tried Googling and looking around the forum (also most of the results I found were quite old) but I couldn't find any GUI based fan controls, I don't mind using terminal but I don't really trust these results:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289403&stc=1[/IMG]

My main problem is that I'm transcoding videos right now and earlier while I was installing something, my CPU would spike to 70-100% but it seems like my fans aren't ramping up to match the usage. Which also makes me worry about my GPU's fan while gaming. I'm running Ubuntu 20.04, fresh install and let me know if you need any more info.

Thanks

---

### Post by dragonfly41 on 2021-10-30
You can play with GKrellM (in repo)  and its settings/plugins.

[http://gkrellm.net](http://gkrellm.net)

---

### Post by Frogs Hair on 2021-10-30
I have not used this , but it is a maintained project and offers profile setting for software programs.

 [https://gitlab.com/corectrl/corectrl](https://gitlab.com/corectrl/corectrl)

---

### Post by QIII on 2021-10-30
Why don't you trust those results?  They are being reported to the OS by your hardware.  That's exactly how it works in Windows.  In each case they are presented to you by software that gathers them.

Software fan control can never be as efficient or responsive as the hardware's own controls.  That is also the case for Windows, but GUI controls are expected by users.  While we do occasionally have requests for assistance with this sort of thing, it is uncommon.  There is, generally speaking, not an issue with such things.  (By the way, Linux not only "works now", it has for a very long time. I've been using various distributions of Linux since the mid-90s.  Games are the bailiwick of the developers.  You would be more correct to say that game developers have made their products work with Linux.  That's no fault of Linux.)

If you could provide us with some information about your hardware and driver modules, we might be better able to assist.

---

### Post by cwblanch on 2021-11-02
> **QIII said:**
> Why don't you trust those results?  They are being reported to the OS by your hardware.  That's exactly how it works in Windows.  In each case they are presented to you by software that gathers them.

Software fan control can never be as efficient or responsive as the hardware's own controls.  That is also the case for Windows, but GUI controls are expected by users.  While we do occasionally have requests for assistance with this sort of thing, it is uncommon.  There is, generally speaking, not an issue with such things.  (By the way, Linux not only "works now", it has for a very long time. I've been using various distributions of Linux since the mid-90s.  Games are the bailiwick of the developers.  You would be more correct to say that game developers have made their products work with Linux.  That's no fault of Linux.)

If you could provide us with some information about your hardware and driver modules, we might be better able to assist.



I guess I should put more trust into the information being given, but since my fans don't seems to be doing anything besides spinning at what sounds like minimum I figured something might be wrong. I now trust the video card because I heard it ramp up while playing a game, not so much with the 2 CPU fans though.


And you're not wrong I didn't phrase it very well, I'm just glad to be back with linux because I used it for a number of years back when I played games on consoles and pc gaming wasn't the priority. But once I switched to PC gaming I had to go back to Windows because the game devs didn't really support linux at that point.


I'm a bit busy right now so I'll get you some hardware info from my desktop in a bit, I'll just edit this post with some screenshots

---

### Post by QIII on 2021-11-02
If you have a dedicated GPU and it is being used on the game, then I would not expect your CPU to be carrying much of the load, if any.  Most modern games are targeted at the GPU and will tax that unless it is not able to do the work. I would expect your GPU to heat up and those fans to run faster.

If your game is not targeted specifically at the GPU, each could be exercised to some extent or another.  If you have an APU, both will surely get warmer.

It looks like your K10 temp is elevated.  Is this an APU?  Do you have a dedicated GPU?

---

### Post by cwblanch on 2021-11-02
> **QIII said:**
> If you have a dedicated GPU and it is being used on the game, then I would not expect your CPU to be carrying much of the load, if any.  Most modern games are targeted at the GPU and will tax that unless it is not able to do the work. I would expect your GPU to heat up and those fans to run faster.

If your game is not targeted specifically at the GPU, each could be exercised to some extent or another.  If you have an APU, both will surely get warmer.

It looks like your K10 temp is elevated.  Is this an APU?  Do you have a dedicated GPU?

I have a dedicated GPU and most of my experience gaming comes from Windows, often when a lot is going on the CPU temps climb also, maybe it's different in Linux. To be fair I haven't tried all of the games I have just yet, only a few that were easy to install.

My CPU/GPU are: Ryzen 5 3600 and GTX 1660 Super. Also just in case you need more information than that I just pasted all of lshw

Thanks for all the help btw

```
description: Computer    width: 64 bits
    capabilities: smp vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 32GiB
     *-cpu
          product: AMD Ryzen 5 3600 6-Core Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 2199MHz
          capacity: 4208MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb cat_l3 cdp_l3 hw_pstate sme ssbd mba sev ibpb stibp vmmcall sev_es fsgsbase bmi1 avx2 smep bmi2 cqm rdt_a rdseed adx smap clflushopt clwb sha_ni xsaveopt xsavec xgetbv1 xsaves cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local clzero irperf xsaveerptr rdpru wbnoinvd arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif umip rdpid overflow_recov succor smca cpufreq
     *-pci:0
          description: Host bridge
          product: Starship/Matisse Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-generic UNCLAIMED
             description: IOMMU
             product: Starship/Matisse IOMMU
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: Starship/Matisse GPP Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:f7a00000-f7afffff
           *-storage
                description: Non-Volatile memory controller
                product: NVMe SSD Controller SM981/PM981/PM983
                vendor: Samsung Electronics Co Ltd
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: storage nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:62 memory:f7a00000-f7a03fff
              *-nvme0
                   description: NVMe device
                   product: Samsung SSD 970 EVO 500GB
                   physical id: 0
                   logical name: /dev/nvme0
                   version: 2B2QEXE7
                   serial: S466NX0KC43231R
                   configuration: nqn=nqn.2014.08.org.nvmexpress:144d144dS466NX0KC43231R     Samsung SSD 970 EVO 500GB state=live
                 *-namespace
                      description: NVMe namespace
                      physical id: 1
                      logical name: /dev/nvme0n1
        *-pci:1
             description: PCI bridge
             product: Starship/Matisse GPP Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:f000(size=4096) memory:f7500000-f77fffff
           *-usb
                description: USB controller
                product: 400 Series Chipset USB 3.1 XHCI Controller
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:50 memory:f77a0000-f77a7fff
           *-sata
                description: SATA controller
                product: 400 Series Chipset SATA Controller
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: sata ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:45 memory:f7780000-f779ffff memory:f7700000-f777ffff
           *-pci
                description: PCI bridge
                product: 400 Series Chipset PCIe Bridge
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:03:00.2
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pci normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: irq:34 ioport:f000(size=4096) memory:f7500000-f76fffff
              *-pci:0
                   description: PCI bridge
                   product: 400 Series Chipset PCIe Port
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 0
                   bus info: pci@0000:20:00.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:36
              *-pci:1
                   description: PCI bridge
                   product: 400 Series Chipset PCIe Port
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 1
                   bus info: pci@0000:20:01.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:38
              *-pci:2
                   description: PCI bridge
                   product: 400 Series Chipset PCIe Port
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 4
                   bus info: pci@0000:20:04.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:39 ioport:f000(size=4096) memory:f7600000-f76fffff
                 *-network
                      description: Ethernet interface
                      product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                      vendor: Realtek Semiconductor Co., Ltd.
                      physical id: 0
                      bus info: pci@0000:25:00.0
                      logical name: enp37s0
                      version: 15
                      serial: 00:d8:61:0e:df:95
                      capacity: 1Gbit/s
                      width: 64 bits
                      clock: 33MHz
                      capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                      configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.11.0-38-generic firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=twisted pair
                      resources: irq:35 ioport:f000(size=256) memory:f7604000-f7604fff memory:f7600000-f7603fff
              *-pci:3
                   description: PCI bridge
                   product: 400 Series Chipset PCIe Port
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 5
                   bus info: pci@0000:20:05.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:40 memory:f7500000-f75fffff
                 *-network
                      description: Wireless interface
                      product: Dual Band Wireless-AC 3168NGW [Stone Peak]
                      vendor: Intel Corporation
                      physical id: 0
                      bus info: pci@0000:26:00.0
                      logical name: wlp38s0
                      version: 10
                      serial: 48:a4:72:ba:51:d5
                      width: 64 bits
                      clock: 33MHz
                      capabilities: bus_master cap_list ethernet physical wireless
                      configuration: broadcast=yes driver=iwlwifi driverversion=5.11.0-38-generic firmware=29.1654887522.0 3168-29.ucode ip=10.0.0.99 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                      resources: irq:100 memory:f7500000-f7501fff
              *-pci:4
                   description: PCI bridge
                   product: 400 Series Chipset PCIe Port
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 6
                   bus info: pci@0000:20:06.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:41
              *-pci:5
                   description: PCI bridge
                   product: 400 Series Chipset PCIe Port
                   vendor: Advanced Micro Devices, Inc. [AMD]
                   physical id: 7
                   bus info: pci@0000:20:07.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:42
        *-pci:2
             description: PCI bridge
             product: Starship/Matisse GPP Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e0000000(size=303038464)
           *-display
                description: VGA compatible controller
                product: TU116 [GeForce GTX 1660 SUPER]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:29:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:105 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: TU116 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:29:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:101 memory:f7080000-f7083fff
           *-usb
                description: USB controller
                product: TU116 USB 3.1 Host Controller
                vendor: NVIDIA Corporation
                physical id: 0.2
                bus info: pci@0000:29:00.2
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: xhci cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:52 memory:f2000000-f203ffff memory:f2040000-f204ffff
           *-serial
                description: Serial bus controller
                product: TU116 [GeForce GTX 1650 SUPER]
                vendor: NVIDIA Corporation
                physical id: 0.3
                bus info: pci@0000:29:00.3
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=nvidia-gpu latency=0
                resources: irq:44 memory:f7084000-f7084fff
        *-pci:3
             description: PCI bridge
             product: Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 7.1
             bus info: pci@0000:00:07.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:30
           *-generic UNCLAIMED
                description: Non-Essential Instrumentation
                product: Starship/Matisse PCIe Dummy Function
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:2a:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
        *-pci:4
             description: PCI bridge
             product: Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:31 memory:f7200000-f74fffff
           *-generic:0 UNCLAIMED
                description: Non-Essential Instrumentation
                product: Starship/Matisse Reserved SPP
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:2b:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
           *-generic:1
                description: Encryption controller
                product: Starship/Matisse Cryptographic Coprocessor PSPCPP
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.1
                bus info: pci@0000:2b:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ccp latency=0
                resources: irq:97 memory:f7300000-f73fffff memory:f7408000-f7409fff
           *-usb
                description: USB controller
                product: Matisse USB 3.0 Host Controller
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.3
                bus info: pci@0000:2b:00.3
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:53 memory:f7200000-f72fffff
           *-multimedia
                description: Audio device
                product: Starship/Matisse HD Audio Controller
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.4
                bus info: pci@0000:2b:00.4
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:103 memory:f7400000-f7407fff
        *-pci:5
             description: PCI bridge
             product: Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.2
             bus info: pci@0000:00:08.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:32 memory:f7900000-f79fffff
           *-sata
                description: SATA controller
                product: FCH SATA Controller [AHCI mode]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:30:00.0
                version: 51
                width: 32 bits
                clock: 33MHz
                capabilities: sata ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:47 memory:f7900000-f79007ff
        *-pci:6
             description: PCI bridge
             product: Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.3
             bus info: pci@0000:00:08.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:33 memory:f7800000-f78fffff
           *-sata
                description: SATA controller
                product: FCH SATA Controller [AHCI mode]
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0
                bus info: pci@0000:31:00.0
                version: 51
                width: 32 bits
                clock: 33MHz
                capabilities: sata ahci_1.0 bus_master cap_list
                configuration: driver=ahci latency=0
                resources: irq:49 memory:f7800000-f78007ff
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 61
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 51
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: Starship/Matisse PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:01.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Starship/Matisse PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:02.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Starship/Matisse PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:03.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Starship/Matisse PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:04.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Starship/Matisse PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:05.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Starship/Matisse PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:07.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Starship/Matisse PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:08.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Matisse Device 24: Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Matisse Device 24: Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Matisse Device 24: Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10a
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: Matisse Device 24: Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10b
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:12
          description: Host bridge
          product: Matisse Device 24: Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10c
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:13
          description: Host bridge
          product: Matisse Device 24: Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10d
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:14
          description: Host bridge
          product: Matisse Device 24: Function 6
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10e
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:15
          description: Host bridge
          product: Matisse Device 24: Function 7
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10f
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pnp00:00
          product: PnP device PNP0c01
          physical id: 2
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0c02
          physical id: 3
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0b00
          physical id: 4
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:03
          product: PnP device PNP0c02
          physical id: 5
          capabilities: pnp
          configuration: driver=system
     *-pnp00:04
          product: PnP device PNP0c02
          physical id: 6
          capabilities: pnp
          configuration: driver=system
  *-scsi:0
       physical id: 1
       bus info: scsi@10
       logical name: scsi10
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@11
       logical name: scsi11
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:2
       physical id: 3
       bus info: scsi@12
       logical name: scsi12
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:3
       physical id: 4
       bus info: scsi@13
       logical name: scsi13
       capabilities: scsi-host
       configuration: driver=usb-storage

```

---


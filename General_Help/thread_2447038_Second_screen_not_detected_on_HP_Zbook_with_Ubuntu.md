---
title: "Second screen not detected on HP Zbook with Ubuntu 19.10"
date: 2020-07-11
forum: General Help
---

### Post by sylvaind on 2020-07-11
Hello,

Recently, I tried to use my BenQ monitor on my HP Zbook running Ubuntu 19.10 but I could not manage to detect the screen.

The only video output on the computer is HDMI while the monitor has DVI-D and VGA inputs.
I've tried the following setups:
 - HDMI to DVI-D cable
 - HDMI to VGA adapter (AUKEY) and VGA to VGA cable

The output for xrandr is the same when the screen is plugged or not:

```
xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DP-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080     60.01*+  40.00  
DP-2 disconnected (normal left inverted right x axis y axis)

```

And I do not see any relevant event in dmesg when I plug/unplug the screen.

Here is what I have in NVidea X Server Settings:
[[IMG]https://i.ibb.co/vhdTp0w/Capture-d-cran-de-2020-07-11-18-49-00.png[/IMG]]("https://ibb.co/f9Nyfj1")

Finally, here is the output of lshw just in case:
```
frpfawlx0053
    description: Ordinateur Bloc-notes
    produit: HP ZBook 15 G6 (6CJ06AV)
    fabricant: HP
    numéro de série: 5CD9468135
    bits: 64 bits
    fonctionnalités: smbios-3.1.0 dmi-3.1.0 smp vsyscall32
    configuration : administrator_password=disabled boot=normal chassis=notebook family=103C_5336AN HP ZBook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=6CJ06AV uuid=0A0B48D9-3BB8-352A-37D9-CE7DB120D240
  *-core
       description: Carte mère
       produit: 860F
       fabricant: HP
       identifiant matériel: 0
       version: KBC Version 65.23.00
       numéro de série: PJJUN048JCY00V
     *-firmware
          description: BIOS
          fabricant: HP
          identifiant matériel: 1
          version: R92 Ver. 01.02.01
          date: 09/25/2019
          taille: 64KiB
          capacité: 32MiB
          fonctionnalités: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-memory
          description: Mémoire Système
          identifiant matériel: 7
          emplacement: Carte mère
          taille: 32GiB
        *-bank:0
             description: SODIMM DDR4 Synchrone 2667 MHz (0,4 ns)
             produit: M471A2K43CB1-CTD
             fabricant: Samsung
             identifiant matériel: 0
             numéro de série: 34D32223
             emplacement: Top-Slot 1(left)
             taille: 16GiB
             bits: 64 bits
             horloge: 2667MHz (0.4ns)
        *-bank:1
             description: SODIMM DDR4 Synchrone 2667 MHz (0,4 ns)
             produit: M471A2K43CB1-CTD
             fabricant: Samsung
             identifiant matériel: 1
             numéro de série: 34D320A1
             emplacement: Top-Slot 2(right)
             taille: 16GiB
             bits: 64 bits
             horloge: 2667MHz (0.4ns)
        *-bank:2
             description: Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2019-07-11 23:21+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2019-10-10 15:05+0000X-Generator: Launchpad (build af2eefe214bd95389a09b7c956720881bab16807)Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2019-07-11 23:21+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2019-10-10 15:05+0000X-Generator: Launchpad (build af2eefe214bd95389a09b7c956720881bab16807) [vide]
             identifiant matériel: 2
             emplacement: Bottom-Slot 1(left)
        *-bank:3
             description: Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2019-07-11 23:21+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2019-10-10 15:05+0000X-Generator: Launchpad (build af2eefe214bd95389a09b7c956720881bab16807)Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2019-07-11 23:21+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2019-10-10 15:05+0000X-Generator: Launchpad (build af2eefe214bd95389a09b7c956720881bab16807) [vide]
             identifiant matériel: 3
             emplacement: Bottom-Slot 2(right)
     *-cache:0
          description: L1 cache
          identifiant matériel: 12
          emplacement: L1 Cache
          taille: 512KiB
          capacité: 512KiB
          fonctionnalités: synchronous internal write-back unified
          configuration : level=1
     *-cache:1
          description: L2 cache
          identifiant matériel: 13
          emplacement: L2 Cache
          taille: 2MiB
          capacité: 2MiB
          fonctionnalités: synchronous internal write-back unified
          configuration : level=2
     *-cache:2
          description: L3 cache
          identifiant matériel: 14
          emplacement: L3 Cache
          taille: 16MiB
          capacité: 16MiB
          fonctionnalités: synchronous internal write-back unified
          configuration : level=3
     *-cpu
          description: CPU
          produit: Intel(R) Core(TM) i9-9880H CPU @ 2.30GHz
          fabricant: Intel Corp.
          identifiant matériel: 15
          information bus: cpu@0
          version: Intel(R) Core(TM) i9-9880H CPU @ 2.30GHz
          numéro de série: To Be Filled By O.E.M.
          emplacement: U3E1
          taille: 2200MHz
          capacité: 4800MHz
          bits: 64 bits
          horloge: 100MHz
          fonctionnalités: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities cpufreq
          configuration : cores=8 enabledcores=8 threads=16
     *-pci
          description: Host bridge
          produit: Intel Corporation
          fabricant: Intel Corporation
          identifiant matériel: 100
          information bus: pci@0000:00:00.0
          version: 0d
          bits: 32 bits
          horloge: 33MHz
        *-pci:0
             description: PCI bridge
             produit: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
             fabricant: Intel Corporation
             identifiant matériel: 1
             information bus: pci@0000:00:01.0
             version: 0d
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:121 portE/S:4000(taille=4096) mémoire:e8000000-e90fffff portE/S:a0000000(taille=301989888)
           *-display
                description: VGA compatible controller
                produit: TU117GLM [Quadro T1000 Mobile]
                fabricant: NVIDIA Corporation
                identifiant matériel: 0
                information bus: pci@0000:01:00.0
                version: a1
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration : driver=nvidia latency=0
                ressources : irq:168 mémoire:e8000000-e8ffffff mémoire:a0000000-afffffff mémoire:b0000000-b1ffffff portE/S:4000(taille=128) mémoire:e9080000-e90fffff
           *-multimedia
                description: Audio device
                produit: NVIDIA Corporation
                fabricant: NVIDIA Corporation
                identifiant matériel: 0.1
                information bus: pci@0000:01:00.1
                version: a1
                bits: 32 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list
                configuration : driver=snd_hda_intel latency=0
                ressources : irq:17 mémoire:e9000000-e9003fff
        *-generic:0
             description: Signal processing controller
             produit: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
             fabricant: Intel Corporation
             identifiant matériel: 4
             information bus: pci@0000:00:04.0
             version: 0d
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: msi pm cap_list
             configuration : driver=proc_thermal latency=0
             ressources : mémoireE/S:400-3ff irq:16 mémoire:404a100000-404a107fff
        *-generic:1
             description: Signal processing controller
             produit: Cannon Lake PCH Thermal Controller
             fabricant: Intel Corporation
             identifiant matériel: 12
             information bus: pci@0000:00:12.0
             version: 10
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi cap_list
             configuration : driver=intel_pch_thermal latency=0
             ressources : mémoireE/S:400-3ff irq:16 mémoire:404a111000-404a111fff
        *-usb
             description: USB controller
             produit: Cannon Lake PCH USB 3.1 xHCI Host Controller
             fabricant: Intel Corporation
             identifiant matériel: 14
             information bus: pci@0000:00:14.0
             version: 10
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi xhci bus_master cap_list
             configuration : driver=xhci_hcd latency=0
             ressources : irq:129 mémoire:ed2a0000-ed2affff
           *-usbhost:0
                produit: xHCI Host Controller
                fabricant: Linux 5.3.0-62-generic xhci-hcd
                identifiant matériel: 0
                information bus: usb@1
                nom logique: usb1
                version: 5.03
                fonctionnalités: usb-2.00
                configuration : driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Périphérique audio
                   produit: Logitech USB Headset H340
                   fabricant: Logitech Inc.
                   identifiant matériel: 1
                   information bus: usb@1:1
                   version: 1.15
                   fonctionnalités: usb-2.00 audio-control
                   configuration : driver=usbhid maxpower=120mA speed=12Mbit/s
              *-usb:1
                   description: Vidéo
                   produit: HP HD Camera
                   fabricant: Quanta
                   identifiant matériel: 7
                   information bus: usb@1:7
                   version: 0.06
                   numéro de série: 0001
                   fonctionnalités: usb-2.00
                   configuration : driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: Interface sans fil Bluetooth
                   fabricant: Intel Corp.
                   identifiant matériel: e
                   information bus: usb@1:e
                   version: 0.01
                   fonctionnalités: bluetooth usb-2.01
                   configuration : driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                produit: xHCI Host Controller
                fabricant: Linux 5.3.0-62-generic xhci-hcd
                identifiant matériel: 1
                information bus: usb@2
                nom logique: usb2
                version: 5.03
                fonctionnalités: usb-3.10
                configuration : driver=hub slots=10 speed=10000Mbit/s
        *-memory NON-RÉCLAMÉ
             description: RAM memory
             produit: Cannon Lake PCH Shared SRAM
             fabricant: Intel Corporation
             identifiant matériel: 14.2
             information bus: pci@0000:00:14.2
             version: 10
             bits: 64 bits
             horloge: 33MHz (30.3ns)
             fonctionnalités: pm cap_list
             configuration : latency=0
             ressources : mémoireE/S:400-3ff mémoire:ed2b2000-ed2b3fff mémoire:404a110000-404a110fff
        *-serial:0
             description: Serial bus controller
             produit: Cannon Lake PCH Serial IO I2C Controller #0
             fabricant: Intel Corporation
             identifiant matériel: 15
             information bus: pci@0000:00:15.0
             version: 10
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration : driver=intel-lpss latency=0
             ressources : irq:16 mémoire:404a10e000-404a10efff
        *-serial:1
             description: Serial bus controller
             produit: Cannon Lake PCH Serial IO I2C Controller #1
             fabricant: Intel Corporation
             identifiant matériel: 15.1
             information bus: pci@0000:00:15.1
             version: 10
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration : driver=intel-lpss latency=0
             ressources : irq:17 mémoire:404a10f000-404a10ffff
        *-communication:0
             description: Communication controller
             produit: Cannon Lake PCH HECI Controller
             fabricant: Intel Corporation
             identifiant matériel: 16
             information bus: pci@0000:00:16.0
             version: 10
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration : driver=mei_me latency=0
             ressources : mémoireE/S:400-3ff irq:151 mémoire:404a10d000-404a10dfff
        *-communication:1
             description: Serial controller
             produit: Cannon Lake PCH Active Management Technology - SOL
             fabricant: Intel Corporation
             identifiant matériel: 16.3
             information bus: pci@0000:00:16.3
             version: 10
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: msi pm 16550 cap_list
             configuration : driver=serial latency=0
             ressources : irq:19 portE/S:5048(taille=8) mémoire:ed2b7000-ed2b7fff
        *-sata
             description: SATA controller
             produit: Cannon Lake Mobile PCH SATA AHCI Controller
             fabricant: Intel Corporation
             identifiant matériel: 17
             information bus: pci@0000:00:17.0
             nom logique: scsi3
             version: 10
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: sata msi pm ahci_1.0 bus_master cap_list emulated
             configuration : driver=ahci latency=0
             ressources : irq:133 mémoire:ed2b0000-ed2b1fff mémoire:ed2b6000-ed2b60ff portE/S:5040(taille=8) portE/S:5050(taille=4) portE/S:5020(taille=32) mémoire:ed2b5000-ed2b57ff
           *-disk
                description: ATA Disk
                produit: MTFDDAK1T0TBN-1A
                identifiant matériel: 0.0.0
                information bus: scsi@3:0.0.0
                nom logique: /dev/sda
                version: 0014
                numéro de série: UGXVN01N4CF93B
                taille: 953GiB (1024GB)
                fonctionnalités: gpt-1.00 partitioned partitioned:gpt
                configuration : ansiversion=5 guid=3de201ac-3cac-4729-9de9-c9a141478c0c logicalsectorsize=512 sectorsize=4096
              *-volume:0 NON-RÉCLAMÉ
                   description: Windows FAT volume
                   fabricant: mkfs.fat
                   identifiant matériel: 1
                   information bus: scsi@3:0.0.0,1
                   version: FAT32
                   numéro de série: eba8-b0a0
                   taille: 510MiB
                   capacité: 511MiB
                   fonctionnalités: boot fat initialized
                   configuration : FATs=2 filesystem=fat name=EFI System Partition
              *-volume:1
                   description: Volume EXT4
                   fabricant: Linux
                   identifiant matériel: 2
                   information bus: scsi@3:0.0.0,2
                   nom logique: /dev/sda2
                   nom logique: /boot
                   version: 1.0
                   numéro de série: 1e10d201-2bca-44e2-b8a4-0e0386e112cd
                   taille: 732MiB
                   fonctionnalités: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuration : created=2019-12-24 11:03:47 filesystem=ext4 lastmountpoint=/boot modified=2020-07-11 09:53:59 mount.fstype=ext4 mount.options=rw,relatime mounted=2020-07-11 09:53:59 state=mounted
              *-volume:2
                   description: EFI partition
                   identifiant matériel: 3
                   information bus: scsi@3:0.0.0,3
                   nom logique: /dev/sda3
                   numéro de série: 328911c6-f90a-4dbc-af86-6ea91686cb70
                   taille: 952GiB
                   capacité: 952GiB
                   bits: 3007434104 bits
                   fonctionnalités: encrypted luks initialized
                   configuration : bits=3007434104 filesystem=luks hash=sha256 version=2
        *-pci:1
             description: PCI bridge
             produit: Cannon Lake PCH PCI Express Root Port #3
             fabricant: Intel Corporation
             identifiant matériel: 1c
             information bus: pci@0000:00:1c.0
             version: f0
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:122 portE/S:3000(taille=4096) mémoire:e4000000-e7ffffff portE/S:e9100000(taille=67108864)
           *-generic
                description: Unassigned class
                produit: RTS525A PCI Express Card Reader
                fabricant: Realtek Semiconductor Co., Ltd.
                identifiant matériel: 0
                information bus: pci@0000:02:00.0
                version: 01
                bits: 32 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list
                configuration : driver=rtsx_pci latency=0
                ressources : irq:131 mémoire:e4000000-e4000fff
        *-pci:2
             description: PCI bridge
             produit: Cannon Lake PCH PCI Express Root Port #5
             fabricant: Intel Corporation
             identifiant matériel: 1c.4
             information bus: pci@0000:00:1c.4
             version: f0
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:123 portE/S:6000(taille=12288) mémoire:b4000000-e20fffff portE/S:4000000000(taille=1241513984)
           *-pci
                description: PCI bridge
                produit: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
                fabricant: Intel Corporation
                identifiant matériel: 0
                information bus: pci@0000:04:00.0
                version: 06
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
                configuration : driver=pcieport
                ressources : mémoireE/S:71610-7160f irq:16 portE/S:6000(taille=8192) mémoire:b4000000-e20fffff portE/S:4000000000(taille=1241513984)
              *-pci:0
                   description: PCI bridge
                   produit: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
                   fabricant: Intel Corporation
                   identifiant matériel: 0
                   information bus: pci@0000:05:00.0
                   version: 06
                   bits: 32 bits
                   horloge: 33MHz
                   fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration : driver=pcieport
                   ressources : irq:125 mémoire:e2000000-e20fffff
                 *-generic
                      description: System peripheral
                      produit: JHL7540 Thunderbolt 3 NHI [Titan Ridge 4C 2018]
                      fabricant: Intel Corporation
                      identifiant matériel: 0
                      information bus: pci@0000:06:00.0
                      version: 06
                      bits: 32 bits
                      horloge: 33MHz
                      fonctionnalités: pm msi pciexpress msix bus_master cap_list
                      configuration : driver=thunderbolt latency=0
                      ressources : irq:16 mémoire:e2000000-e203ffff mémoire:e2040000-e2040fff
              *-pci:1
                   description: PCI bridge
                   produit: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
                   fabricant: Intel Corporation
                   identifiant matériel: 1
                   information bus: pci@0000:05:01.0
                   version: 06
                   bits: 32 bits
                   horloge: 33MHz
                   fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration : driver=pcieport
                   ressources : irq:126 portE/S:6000(taille=4096) mémoire:b4000000-caefffff portE/S:4000000000(taille=620756992)
              *-pci:2
                   description: PCI bridge
                   produit: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
                   fabricant: Intel Corporation
                   identifiant matériel: 2
                   information bus: pci@0000:05:02.0
                   version: 06
                   bits: 32 bits
                   horloge: 33MHz
                   fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration : driver=pcieport
                   ressources : irq:127 mémoire:caf00000-caffffff
                 *-usb
                      description: USB controller
                      produit: JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 4C 2018]
                      fabricant: Intel Corporation
                      identifiant matériel: 0
                      information bus: pci@0000:3a:00.0
                      version: 06
                      bits: 32 bits
                      horloge: 33MHz
                      fonctionnalités: pm msi pciexpress xhci cap_list
                      configuration : driver=xhci_hcd latency=0
                      ressources : irq:130 mémoire:caf00000-caf0ffff
                    *-usbhost:0
                         produit: xHCI Host Controller
                         fabricant: Linux 5.3.0-62-generic xhci-hcd
                         identifiant matériel: 0
                         information bus: usb@3
                         nom logique: usb3
                         version: 5.03
                         fonctionnalités: usb-2.00
                         configuration : driver=hub slots=2 speed=480Mbit/s
                    *-usbhost:1
                         produit: xHCI Host Controller
                         fabricant: Linux 5.3.0-62-generic xhci-hcd
                         identifiant matériel: 1
                         information bus: usb@4
                         nom logique: usb4
                         version: 5.03
                         fonctionnalités: usb-3.10
                         configuration : driver=hub slots=2 speed=10000Mbit/s
              *-pci:3
                   description: PCI bridge
                   produit: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
                   fabricant: Intel Corporation
                   identifiant matériel: 4
                   information bus: pci@0000:05:04.0
                   version: 06
                   bits: 32 bits
                   horloge: 33MHz
                   fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration : driver=pcieport
                   ressources : irq:128 portE/S:7000(taille=4096) mémoire:cb000000-e1ffffff portE/S:4025000000(taille=620756992)
        *-pci:3
             description: PCI bridge
             produit: Cannon Lake PCH PCI Express Root Port #14
             fabricant: Intel Corporation
             identifiant matériel: 1d
             information bus: pci@0000:00:1d.0
             version: f0
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:124 mémoire:ed100000-ed1fffff
           *-network
                description: Interface réseau sans fil
                produit: Intel Corporation
                fabricant: Intel Corporation
                identifiant matériel: 0
                information bus: pci@0000:6f:00.0
                nom logique: wlp111s0
                version: 1a
                numéro de série: 94:e6:f7:e4:4a:49
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration : broadcast=yes driver=iwlwifi driverversion=5.3.0-62-generic firmware=48.4fa0041f.0 ip=192.168.1.18 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                ressources : irq:17 mémoire:ed100000-ed103fff
        *-isa
             description: ISA bridge
             produit: Intel Corporation
             fabricant: Intel Corporation
             identifiant matériel: 1f
             information bus: pci@0000:00:1f.0
             version: 10
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: isa bus_master
             configuration : latency=0
        *-multimedia
             description: Multimedia audio controller
             produit: Cannon Lake PCH cAVS
             fabricant: Intel Corporation
             identifiant matériel: 1f.3
             information bus: pci@0000:00:1f.3
             version: 10
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration : driver=sof-audio-pci latency=64
             ressources : mémoireE/S:400-3ff mémoireE/S:400-3ff irq:16 mémoire:404a108000-404a10bfff mémoire:404a000000-404a0fffff
        *-serial:2
             description: SMBus
             produit: Cannon Lake PCH SMBus Controller
             fabricant: Intel Corporation
             identifiant matériel: 1f.4
             information bus: pci@0000:00:1f.4
             version: 10
             bits: 64 bits
             horloge: 33MHz
             configuration : driver=i801_smbus latency=0
             ressources : mémoireE/S:400-3ff irq:16 mémoire:404a10c000-404a10c0ff portE/S:efa0(taille=32)
        *-serial:3 NON-RÉCLAMÉ
             description: Serial bus controller
             produit: Cannon Lake PCH SPI Controller
             fabricant: Intel Corporation
             identifiant matériel: 1f.5
             information bus: pci@0000:00:1f.5
             version: 10
             bits: 32 bits
             horloge: 33MHz
             configuration : latency=0
             ressources : mémoire:fe010000-fe010fff
        *-network
             description: Ethernet interface
             produit: Ethernet Connection (7) I219-LM
             fabricant: Intel Corporation
             identifiant matériel: 1f.6
             information bus: pci@0000:00:1f.6
             nom logique: enp0s31f6
             version: 10
             numéro de série: 04:0e:3c:a5:40:78
             capacité: 1Gbit/s
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration : autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.5-4 latency=0 link=no multicast=yes port=twisted pair
             ressources : irq:149 mémoire:ed280000-ed29ffff
     *-pnp00:00
          produit: PnP device PNP0c02
          identifiant matériel: 0
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:01
          produit: PnP device PNP0c02
          identifiant matériel: 2
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:02
          produit: PnP device PNP0c02
          identifiant matériel: 3
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:03
          produit: PnP device PNP0c02
          identifiant matériel: 4
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:04
          produit: PnP device PNP0b00
          identifiant matériel: 5
          fonctionnalités: pnp
          configuration : driver=rtc_cmos
     *-pnp00:05
          produit: PnP device INT3f0d
          identifiant matériel: 6
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:06
          produit: PnP device HPQ8002
          identifiant matériel: 8
          fonctionnalités: pnp
          configuration : driver=i8042 kbd
     *-pnp00:07
          produit: PnP device ALP0126
          identifiant matériel: 9
          fonctionnalités: pnp
          configuration : driver=i8042 aux
     *-pnp00:08
          produit: PnP device PNP0c02
          identifiant matériel: a
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:09
          produit: PnP device PNP0c02
          identifiant matériel: b
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:0a
          produit: PnP device PNP0c02
          identifiant matériel: c
          fonctionnalités: pnp
          configuration : driver=system
  *-battery
       produit: VX04090XL
       fabricant: 333-1C-2C-A
       identifiant matériel: 1
       emplacement: Primary
       capacité: 89990mWh
       configuration : voltage=15,4V
  *-network:0
       description: Ethernet interface
       identifiant matériel: 2
       nom logique: virbr0
       numéro de série: 52:54:00:5c:d4:ce
       fonctionnalités: ethernet physical
       configuration : broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=no multicast=yes
  *-network:1 DÉSACTIVÉ
       description: Ethernet interface
       identifiant matériel: 3
       nom logique: virbr0-nic
       numéro de série: 52:54:00:5c:d4:ce
       taille: 10Mbit/s
       fonctionnalités: ethernet physical
       configuration : autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
```

Also:
 - I've never used this computer with other monitors
 - I've used that monitor with other computers (Windows & much older Ubuntu versions) without any problem

I never had any issue with screen being not detected on my other Ubuntu computers so I am a bit lost here. Any suggestion is welcome.

Thanks in advance

---

### Post by Impavidus on 2020-07-11
I'm not so familiar with nvidia driver settings...

Have you tried a 20.04 live disk? I ask because 19.10 is only two weeks or so away from end of life, so it isn't really worth fixing this on 19.10 if that same fix isn't needed on or doesn't apply to 20.04. But then, I don't think you can actually load the proprietary nvidia drivers in a live session.

Unless you're in an extreme hurry and need this fixed by Tuesday, I suggest you first try and get on 20.04, then see whether the issue still exists.

---

### Post by sylvaind on 2020-07-13
Thanks, this is a very good idea indeed. I'll try that :D

---

### Post by sdsurfer on 2020-07-13
This is likely going to be a hardware issue in some way - I work with dual monitors exclusively and have experienced many challenges getting things to work with cable adapters. All of my comps have Nvidia GPU's, what I see in your screen shot looks more or less normal. I've dug around in those too, if it's the latest drivers it doesn't seem to help when I encounter these issues, which tells me it's not the card or drivers. Most of the Nvidia server software manages optimization more than anything. What you might gather from this is that the ***system*** is not detecting the monitor and is not passing what it knows along to the Nvidia server.

Are you able to detect the screens in settings->Display? If not, I return to hardware. I have had issues just with the cables, swap out a cable and everything works. This is a repeatable "bug," put the "bad" cable back on, doesn't work.

Last, this may seem really simplistic, but there are often cable selects in the monitor itself. I have dual BenQ's and when the monitor starts, I have to select the cable input, HDMI, DVI, or display port. Make sure you are selecting the right port.

If this gives no releif, I would begin looking at what the computer actually detects for output ports, it may be something as simple as the incorrect driver for the ports.

---

### Post by ActionParsnip on 2020-07-13
[https://www.omgubuntu.co.uk/2020/07/ubuntu-19-10-end-of-life](https://www.omgubuntu.co.uk/2020/07/ubuntu-19-10-end-of-life)

19.10 is end of life (EOL) in _**4 days**_. I suggest you upgrade to Focal (Ubuntu 20.04) which is LTS (19.10 is not LTS). The newer packages may help, especially the newer kernel and display manager

---

### Post by Impavidus on 2020-07-13
I see, a week or so sooner than I expected. [https://lists.ubuntu.com/archives/ubuntu-announce/2020-July/000257.html](https://lists.ubuntu.com/archives/ubuntu-announce/2020-July/000257.html)
It wasn't yet on [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) (actually, still isn't). I only installed 20.04 a week ago.

---

### Post by sylvaind on 2020-07-13
I'm back with Ubuntu 20.04 and things do not look any better.

In case it can help anyone:

```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal
```

```

$ uname -r
5.4.0-40-generic
```

```
lshw

frpfawlx0053
    description: Ordinateur Bloc-notes
    produit: HP ZBook 15 G6 (6CJ06AV)
    fabricant: HP
    numéro de série: 5CD9468135
    bits: 64 bits
    fonctionnalités: smbios-3.1.0 dmi-3.1.0 smp vsyscall32
    configuration : administrator_password=disabled boot=normal chassis=notebook family=103C_5336AN HP ZBook frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=6CJ06AV uuid=0A0B48D9-3BB8-352A-37D9-CE7DB120D240
  *-core
       description: Carte mère
       produit: 860F
       fabricant: HP
       identifiant matériel: 0
       version: KBC Version 65.23.00
       numéro de série: PJJUN048JCY00V
     *-firmware
          description: BIOS
          fabricant: HP
          identifiant matériel: 1
          version: R92 Ver. 01.02.01
          date: 09/25/2019
          taille: 64KiB
          capacité: 32MiB
          fonctionnalités: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot uefi
     *-memory
          description: Mémoire Système
          identifiant matériel: 7
          emplacement: Carte mère
          taille: 32GiB
        *-bank:0
             description: SODIMM DDR4 Synchrone 2667 MHz (0,4 ns)
             produit: M471A2K43CB1-CTD
             fabricant: Samsung
             identifiant matériel: 0
             numéro de série: 34D32223
             emplacement: Top-Slot 1(left)
             taille: 16GiB
             bits: 64 bits
             horloge: 2667MHz (0.4ns)
        *-bank:1
             description: SODIMM DDR4 Synchrone 2667 MHz (0,4 ns)
             produit: M471A2K43CB1-CTD
             fabricant: Samsung
             identifiant matériel: 1
             numéro de série: 34D320A1
             emplacement: Top-Slot 2(right)
             taille: 16GiB
             bits: 64 bits
             horloge: 2667MHz (0.4ns)
        *-bank:2
             description: Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2020-04-03 08:20+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2020-04-16 17:42+0000X-Generator: Launchpad (build 2e26c9bbd21cdca248baaea29aeffb920afcc32a)Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2020-04-03 08:20+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2020-04-16 17:42+0000X-Generator: Launchpad (build 2e26c9bbd21cdca248baaea29aeffb920afcc32a) [vide]
             identifiant matériel: 2
             emplacement: Bottom-Slot 1(left)
        *-bank:3
             description: Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2020-04-03 08:20+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2020-04-16 17:42+0000X-Generator: Launchpad (build 2e26c9bbd21cdca248baaea29aeffb920afcc32a)Project-Id-Version: @(#) $Id$Report-Msgid-Bugs-To: PO-Revision-Date: 2020-04-03 08:20+0000Last-Translator: Lyonel Vincent <Unknown>Language-Team: MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2020-04-16 17:42+0000X-Generator: Launchpad (build 2e26c9bbd21cdca248baaea29aeffb920afcc32a) [vide]
             identifiant matériel: 3
             emplacement: Bottom-Slot 2(right)
     *-cache:0
          description: L1 cache
          identifiant matériel: 12
          emplacement: L1 Cache
          taille: 512KiB
          capacité: 512KiB
          fonctionnalités: synchronous internal write-back unified
          configuration : level=1
     *-cache:1
          description: L2 cache
          identifiant matériel: 13
          emplacement: L2 Cache
          taille: 2MiB
          capacité: 2MiB
          fonctionnalités: synchronous internal write-back unified
          configuration : level=2
     *-cache:2
          description: L3 cache
          identifiant matériel: 14
          emplacement: L3 Cache
          taille: 16MiB
          capacité: 16MiB
          fonctionnalités: synchronous internal write-back unified
          configuration : level=3
     *-cpu
          description: CPU
          produit: Intel(R) Core(TM) i9-9880H CPU @ 2.30GHz
          fabricant: Intel Corp.
          identifiant matériel: 15
          information bus: cpu@0
          version: Intel(R) Core(TM) i9-9880H CPU @ 2.30GHz
          numéro de série: To Be Filled By O.E.M.
          emplacement: U3E1
          taille: 2200MHz
          capacité: 4800MHz
          bits: 64 bits
          horloge: 100MHz
          fonctionnalités: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp ibrs_enhanced tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities cpufreq
          configuration : cores=8 enabledcores=8 threads=16
     *-pci
          description: Host bridge
          produit: Intel Corporation
          fabricant: Intel Corporation
          identifiant matériel: 100
          information bus: pci@0000:00:00.0
          version: 0d
          bits: 32 bits
          horloge: 33MHz
        *-pci:0
             description: PCI bridge
             produit: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
             fabricant: Intel Corporation
             identifiant matériel: 1
             information bus: pci@0000:00:01.0
             version: 0d
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:121 portE/S:4000(taille=4096) mémoire:e8000000-e90fffff portE/S:a0000000(taille=301989888)
           *-display
                description: VGA compatible controller
                produit: TU117GLM [Quadro T1000 Mobile]
                fabricant: NVIDIA Corporation
                identifiant matériel: 0
                information bus: pci@0000:01:00.0
                version: a1
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration : driver=nvidia latency=0
                ressources : irq:169 mémoire:e8000000-e8ffffff mémoire:a0000000-afffffff mémoire:b0000000-b1ffffff portE/S:4000(taille=128) mémoire:e9080000-e90fffff
           *-multimedia
                description: Audio device
                produit: NVIDIA Corporation
                fabricant: NVIDIA Corporation
                identifiant matériel: 0.1
                information bus: pci@0000:01:00.1
                version: a1
                bits: 32 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list
                configuration : driver=snd_hda_intel latency=0
                ressources : irq:17 mémoire:e9000000-e9003fff
        *-generic:0
             description: Signal processing controller
             produit: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
             fabricant: Intel Corporation
             identifiant matériel: 4
             information bus: pci@0000:00:04.0
             version: 0d
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: msi pm cap_list
             configuration : driver=proc_thermal latency=0
             ressources : mémoireE/S:400-3ff irq:16 mémoire:404a100000-404a107fff
        *-generic:1
             description: Signal processing controller
             produit: Cannon Lake PCH Thermal Controller
             fabricant: Intel Corporation
             identifiant matériel: 12
             information bus: pci@0000:00:12.0
             version: 10
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi cap_list
             configuration : driver=intel_pch_thermal latency=0
             ressources : mémoireE/S:400-3ff irq:16 mémoire:404a111000-404a111fff
        *-usb
             description: USB controller
             produit: Cannon Lake PCH USB 3.1 xHCI Host Controller
             fabricant: Intel Corporation
             identifiant matériel: 14
             information bus: pci@0000:00:14.0
             version: 10
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi xhci bus_master cap_list
             configuration : driver=xhci_hcd latency=0
             ressources : irq:129 mémoire:ed2a0000-ed2affff
           *-usbhost:0
                produit: xHCI Host Controller
                fabricant: Linux 5.4.0-40-generic xhci-hcd
                identifiant matériel: 0
                information bus: usb@1
                nom logique: usb1
                version: 5.04
                fonctionnalités: usb-2.00
                configuration : driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Périphérique audio
                   produit: Logitech USB Headset H340
                   fabricant: Logitech Inc.
                   identifiant matériel: 1
                   information bus: usb@1:1
                   version: 1.15
                   fonctionnalités: usb-2.00 audio-control
                   configuration : driver=usbhid maxpower=120mA speed=12Mbit/s
              *-usb:1
                   description: Vidéo
                   produit: HP HD Camera
                   fabricant: Quanta
                   identifiant matériel: 7
                   information bus: usb@1:7
                   version: 0.06
                   numéro de série: 0001
                   fonctionnalités: usb-2.00
                   configuration : driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:2
                   description: Interface sans fil Bluetooth
                   fabricant: Intel Corp.
                   identifiant matériel: e
                   information bus: usb@1:e
                   version: 0.01
                   fonctionnalités: bluetooth usb-2.01
                   configuration : driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                produit: xHCI Host Controller
                fabricant: Linux 5.4.0-40-generic xhci-hcd
                identifiant matériel: 1
                information bus: usb@2
                nom logique: usb2
                version: 5.04
                fonctionnalités: usb-3.10
                configuration : driver=hub slots=10 speed=10000Mbit/s
        *-memory NON-RÉCLAMÉ
             description: RAM memory
             produit: Cannon Lake PCH Shared SRAM
             fabricant: Intel Corporation
             identifiant matériel: 14.2
             information bus: pci@0000:00:14.2
             version: 10
             bits: 64 bits
             horloge: 33MHz (30.3ns)
             fonctionnalités: pm cap_list
             configuration : latency=0
             ressources : mémoireE/S:400-3ff mémoire:ed2b2000-ed2b3fff mémoire:404a110000-404a110fff
        *-serial:0
             description: Serial bus controller
             produit: Cannon Lake PCH Serial IO I2C Controller #0
             fabricant: Intel Corporation
             identifiant matériel: 15
             information bus: pci@0000:00:15.0
             version: 10
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration : driver=intel-lpss latency=0
             ressources : irq:16 mémoire:404a10e000-404a10efff
        *-serial:1
             description: Serial bus controller
             produit: Cannon Lake PCH Serial IO I2C Controller #1
             fabricant: Intel Corporation
             identifiant matériel: 15.1
             information bus: pci@0000:00:15.1
             version: 10
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm bus_master cap_list
             configuration : driver=intel-lpss latency=0
             ressources : irq:17 mémoire:404a10f000-404a10ffff
        *-communication:0
             description: Communication controller
             produit: Cannon Lake PCH HECI Controller
             fabricant: Intel Corporation
             identifiant matériel: 16
             information bus: pci@0000:00:16.0
             version: 10
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration : driver=mei_me latency=0
             ressources : mémoireE/S:400-3ff irq:151 mémoire:404a10d000-404a10dfff
        *-communication:1
             description: Serial controller
             produit: Cannon Lake PCH Active Management Technology - SOL
             fabricant: Intel Corporation
             identifiant matériel: 16.3
             information bus: pci@0000:00:16.3
             version: 10
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: msi pm 16550 cap_list
             configuration : driver=serial latency=0
             ressources : irq:19 portE/S:5048(taille=8) mémoire:ed2b7000-ed2b7fff
        *-sata
             description: SATA controller
             produit: Cannon Lake Mobile PCH SATA AHCI Controller
             fabricant: Intel Corporation
             identifiant matériel: 17
             information bus: pci@0000:00:17.0
             nom logique: scsi3
             version: 10
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: sata msi pm ahci_1.0 bus_master cap_list emulated
             configuration : driver=ahci latency=0
             ressources : irq:132 mémoire:ed2b0000-ed2b1fff mémoire:ed2b6000-ed2b60ff portE/S:5040(taille=8) portE/S:5050(taille=4) portE/S:5020(taille=32) mémoire:ed2b5000-ed2b57ff
           *-disk
                description: ATA Disk
                produit: MTFDDAK1T0TBN-1A
                identifiant matériel: 0.0.0
                information bus: scsi@3:0.0.0
                nom logique: /dev/sda
                version: 0014
                numéro de série: UGXVN01N4CF93B
                taille: 953GiB (1024GB)
                fonctionnalités: gpt-1.00 partitioned partitioned:gpt
                configuration : ansiversion=5 guid=3de201ac-3cac-4729-9de9-c9a141478c0c logicalsectorsize=512 sectorsize=4096
              *-volume:0 NON-RÉCLAMÉ
                   description: Windows FAT volume
                   fabricant: mkfs.fat
                   identifiant matériel: 1
                   information bus: scsi@3:0.0.0,1
                   version: FAT32
                   numéro de série: eba8-b0a0
                   taille: 510MiB
                   capacité: 511MiB
                   fonctionnalités: boot fat initialized
                   configuration : FATs=2 filesystem=fat name=EFI System Partition
              *-volume:1
                   description: Volume EXT4
                   fabricant: Linux
                   identifiant matériel: 2
                   information bus: scsi@3:0.0.0,2
                   nom logique: /dev/sda2
                   nom logique: /boot
                   version: 1.0
                   numéro de série: 1e10d201-2bca-44e2-b8a4-0e0386e112cd
                   taille: 732MiB
                   fonctionnalités: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                   configuration : created=2019-12-24 11:03:47 filesystem=ext4 lastmountpoint=/boot modified=2020-07-14 01:04:24 mount.fstype=ext4 mount.options=rw,relatime mounted=2020-07-14 01:04:24 state=mounted
              *-volume:2
                   description: EFI partition
                   identifiant matériel: 3
                   information bus: scsi@3:0.0.0,3
                   nom logique: /dev/sda3
                   numéro de série: 328911c6-f90a-4dbc-af86-6ea91686cb70
                   taille: 952GiB
                   capacité: 952GiB
                   bits: 3007434104 bits
                   fonctionnalités: encrypted luks initialized
                   configuration : bits=3007434104 filesystem=luks hash=sha256 version=2
        *-pci:1
             description: PCI bridge
             produit: Cannon Lake PCH PCI Express Root Port #3
             fabricant: Intel Corporation
             identifiant matériel: 1c
             information bus: pci@0000:00:1c.0
             version: f0
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:122 portE/S:3000(taille=4096) mémoire:e4000000-e7ffffff portE/S:e9100000(taille=67108864)
           *-generic
                description: Unassigned class
                produit: RTS525A PCI Express Card Reader
                fabricant: Realtek Semiconductor Co., Ltd.
                identifiant matériel: 0
                information bus: pci@0000:02:00.0
                version: 01
                bits: 32 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list
                configuration : driver=rtsx_pci latency=0
                ressources : irq:131 mémoire:e4000000-e4000fff
        *-pci:2
             description: PCI bridge
             produit: Cannon Lake PCH PCI Express Root Port #5
             fabricant: Intel Corporation
             identifiant matériel: 1c.4
             information bus: pci@0000:00:1c.4
             version: f0
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:123 portE/S:6000(taille=12288) mémoire:b4000000-e20fffff portE/S:4000000000(taille=1241513984)
           *-pci
                description: PCI bridge
                produit: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
                fabricant: Intel Corporation
                identifiant matériel: 0
                information bus: pci@0000:04:00.0
                version: 06
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
                configuration : driver=pcieport
                ressources : mémoireE/S:71610-7160f irq:16 portE/S:6000(taille=8192) mémoire:b4000000-e20fffff portE/S:4000000000(taille=1241513984)
              *-pci:0
                   description: PCI bridge
                   produit: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
                   fabricant: Intel Corporation
                   identifiant matériel: 0
                   information bus: pci@0000:05:00.0
                   version: 06
                   bits: 32 bits
                   horloge: 33MHz
                   fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration : driver=pcieport
                   ressources : irq:125 mémoire:e2000000-e20fffff
                 *-generic
                      description: System peripheral
                      produit: JHL7540 Thunderbolt 3 NHI [Titan Ridge 4C 2018]
                      fabricant: Intel Corporation
                      identifiant matériel: 0
                      information bus: pci@0000:06:00.0
                      version: 06
                      bits: 32 bits
                      horloge: 33MHz
                      fonctionnalités: pm msi pciexpress msix bus_master cap_list
                      configuration : driver=thunderbolt latency=0
                      ressources : irq:16 mémoire:e2000000-e203ffff mémoire:e2040000-e2040fff
              *-pci:1
                   description: PCI bridge
                   produit: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
                   fabricant: Intel Corporation
                   identifiant matériel: 1
                   information bus: pci@0000:05:01.0
                   version: 06
                   bits: 32 bits
                   horloge: 33MHz
                   fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration : driver=pcieport
                   ressources : irq:126 portE/S:6000(taille=4096) mémoire:b4000000-caefffff portE/S:4000000000(taille=620756992)
              *-pci:2
                   description: PCI bridge
                   produit: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
                   fabricant: Intel Corporation
                   identifiant matériel: 2
                   information bus: pci@0000:05:02.0
                   version: 06
                   bits: 32 bits
                   horloge: 33MHz
                   fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration : driver=pcieport
                   ressources : irq:127 mémoire:caf00000-caffffff
                 *-usb
                      description: USB controller
                      produit: JHL7540 Thunderbolt 3 USB Controller [Titan Ridge 4C 2018]
                      fabricant: Intel Corporation
                      identifiant matériel: 0
                      information bus: pci@0000:3a:00.0
                      version: 06
                      bits: 32 bits
                      horloge: 33MHz
                      fonctionnalités: pm msi pciexpress xhci cap_list
                      configuration : driver=xhci_hcd latency=0
                      ressources : irq:130 mémoire:caf00000-caf0ffff
                    *-usbhost:0
                         produit: xHCI Host Controller
                         fabricant: Linux 5.4.0-40-generic xhci-hcd
                         identifiant matériel: 0
                         information bus: usb@3
                         nom logique: usb3
                         version: 5.04
                         fonctionnalités: usb-2.00
                         configuration : driver=hub slots=2 speed=480Mbit/s
                    *-usbhost:1
                         produit: xHCI Host Controller
                         fabricant: Linux 5.4.0-40-generic xhci-hcd
                         identifiant matériel: 1
                         information bus: usb@4
                         nom logique: usb4
                         version: 5.04
                         fonctionnalités: usb-3.10
                         configuration : driver=hub slots=2 speed=10000Mbit/s
              *-pci:3
                   description: PCI bridge
                   produit: JHL7540 Thunderbolt 3 Bridge [Titan Ridge 4C 2018]
                   fabricant: Intel Corporation
                   identifiant matériel: 4
                   information bus: pci@0000:05:04.0
                   version: 06
                   bits: 32 bits
                   horloge: 33MHz
                   fonctionnalités: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration : driver=pcieport
                   ressources : irq:128 portE/S:7000(taille=4096) mémoire:cb000000-e1ffffff portE/S:4025000000(taille=620756992)
        *-pci:3
             description: PCI bridge
             produit: Cannon Lake PCH PCI Express Root Port #14
             fabricant: Intel Corporation
             identifiant matériel: 1d
             information bus: pci@0000:00:1d.0
             version: f0
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration : driver=pcieport
             ressources : irq:124 mémoire:ed100000-ed1fffff
           *-network
                description: Interface réseau sans fil
                produit: Wi-Fi 6 AX200
                fabricant: Intel Corporation
                identifiant matériel: 0
                information bus: pci@0000:6f:00.0
                nom logique: wlp111s0
                version: 1a
                numéro de série: 94:e6:f7:e4:4a:49
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
                configuration : broadcast=yes driver=iwlwifi driverversion=5.4.0-40-generic firmware=48.4fa0041f.0 ip=192.168.1.18 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                ressources : irq:17 mémoire:ed100000-ed103fff
        *-isa
             description: ISA bridge
             produit: Intel Corporation
             fabricant: Intel Corporation
             identifiant matériel: 1f
             information bus: pci@0000:00:1f.0
             version: 10
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: isa bus_master
             configuration : latency=0
        *-multimedia
             description: Multimedia audio controller
             produit: Cannon Lake PCH cAVS
             fabricant: Intel Corporation
             identifiant matériel: 1f.3
             information bus: pci@0000:00:1f.3
             version: 10
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration : driver=sof-audio-pci latency=64
             ressources : mémoireE/S:400-3ff mémoireE/S:400-3ff irq:168 mémoire:404a108000-404a10bfff mémoire:404a000000-404a0fffff
        *-serial:2
             description: SMBus
             produit: Cannon Lake PCH SMBus Controller
             fabricant: Intel Corporation
             identifiant matériel: 1f.4
             information bus: pci@0000:00:1f.4
             version: 10
             bits: 64 bits
             horloge: 33MHz
             configuration : driver=i801_smbus latency=0
             ressources : mémoireE/S:400-3ff irq:16 mémoire:404a10c000-404a10c0ff portE/S:efa0(taille=32)
        *-serial:3 NON-RÉCLAMÉ
             description: Serial bus controller
             produit: Cannon Lake PCH SPI Controller
             fabricant: Intel Corporation
             identifiant matériel: 1f.5
             information bus: pci@0000:00:1f.5
             version: 10
             bits: 32 bits
             horloge: 33MHz
             configuration : latency=0
             ressources : mémoire:fe010000-fe010fff
        *-network
             description: Ethernet interface
             produit: Ethernet Connection (7) I219-LM
             fabricant: Intel Corporation
             identifiant matériel: 1f.6
             information bus: pci@0000:00:1f.6
             nom logique: enp0s31f6
             version: 10
             numéro de série: 04:0e:3c:a5:40:78
             capacité: 1Gbit/s
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration : autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.5-4 latency=0 link=no multicast=yes port=twisted pair
             ressources : irq:149 mémoire:ed280000-ed29ffff
     *-pnp00:00
          produit: PnP device PNP0c02
          identifiant matériel: 0
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:01
          produit: PnP device PNP0c02
          identifiant matériel: 2
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:02
          produit: PnP device PNP0c02
          identifiant matériel: 3
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:03
          produit: PnP device PNP0c02
          identifiant matériel: 4
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:04
          produit: PnP device PNP0b00
          identifiant matériel: 5
          fonctionnalités: pnp
          configuration : driver=rtc_cmos
     *-pnp00:05
          produit: PnP device INT3f0d
          identifiant matériel: 6
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:06
          produit: PnP device HPQ8002
          identifiant matériel: 8
          fonctionnalités: pnp
          configuration : driver=i8042 kbd
     *-pnp00:07
          produit: PnP device ALP0126
          identifiant matériel: 9
          fonctionnalités: pnp
          configuration : driver=i8042 aux
     *-pnp00:08
          produit: PnP device PNP0c02
          identifiant matériel: a
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:09
          produit: PnP device PNP0c02
          identifiant matériel: b
          fonctionnalités: pnp
          configuration : driver=system
     *-pnp00:0a
          produit: PnP device PNP0c02
          identifiant matériel: c
          fonctionnalités: pnp
          configuration : driver=system
  *-battery
       produit: VX04090XL
       fabricant: 333-1C-2C-A
       identifiant matériel: 1
       emplacement: Primary
       capacité: 89990mWh
       configuration : voltage=15,4V
  *-network:0 DÉSACTIVÉ
       description: Ethernet interface
       identifiant matériel: 2
       nom logique: virbr0-nic
       numéro de série: 52:54:00:5c:d4:ce
       taille: 10Mbit/s
       fonctionnalités: ethernet physical
       configuration : autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
  *-network:1
       description: Ethernet interface
       identifiant matériel: 3
       nom logique: virbr0
       numéro de série: 52:54:00:5c:d4:ce
       fonctionnalités: ethernet physical
       configuration : broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=no multicast=yes
```

[[IMG]https://i.ibb.co/hLxjjgx/Capture-d-cran-de-2020-07-14-01-15-21.png[/IMG]]("https://ibb.co/9cmLLpm")

[[IMG]https://i.ibb.co/b3njprV/Capture-d-cran-de-2020-07-14-01-16-30.png[/IMG]]("https://ibb.co/JdPWXzT")


```
$ xrandr 
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DP-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080     60.01*+  40.00  
DP-2 disconnected (normal left inverted right x axis y axis)

```


I've retried unplugging/replugging everything (unfortunately, I have each cable only once) and nothing works any better.

I'm running out of ideas so any suggestion is welcome.

---

### Post by sdsurfer on 2020-07-16
That is the ***settings*** screen, that is not the one you want. I am looking at three displays at the moment - a laptop and two BenQ's - and when I go to Settings->Display screen it says "could not get screen information."

Tye searching for ***System Settings***. I know, weird that there are two, but they don't appear to be the same. (I hope this is still on 20+, I am on 18.04.) It should open a different window with icons. Hitting the "Displays" icon should look something like screen shot #1.

If all your displays don't show there, I still go back to some hardware problem (but there is a high likelihood I am incorrect.)

There is one more thing to check - it **looks** like the Nvidia driver is fine, but go into Software & Updates->Additional Drivers. A lot of users will see nothing here, but what I found was that it was defaulted to the noveau driver and when I selected the Nvidia driver (open source - important) display problems went away. If you make a change here, reboot.

---

### Post by sylvaind on 2020-07-17
Thanks for the tip! I'll have a look asap. The fact that there are multiple Settings apps is a bit confusing and even more so when the name does not end up being translated the same way on my French setup. I'll switch back to English to make things easier and give it a try!

---

### Post by claudiuxyz on 2021-03-21
I succeed to fix this issue by going to Bios settings (press F10)
*) Advanced
*) Built-In Device Options
*)Graphics:  choose [Discrete Graphics] instead of &#8220;auto&#8221;

---


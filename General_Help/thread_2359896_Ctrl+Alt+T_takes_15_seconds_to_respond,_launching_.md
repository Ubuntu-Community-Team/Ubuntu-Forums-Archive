---
title: "Ctrl+Alt+T takes 15 seconds to respond, launching Chrome takes about a minute"
date: 2017-04-29
forum: General Help
---

### Post by cranerja on 2017-04-29
After installing updates, I have found that Google Chrome no longer launches immediately, but rather takes about a minute to create a window that freezes. Only after a couple minutes does it start working normally.

The terminal shortcut is very delayed as well, but launching it from the dash works fine. 

I have already tried reinstalling Chrome but to no avail.

Any ideas?

---

### Post by mörgæs on 2017-04-30
Let's see the hardware details first. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by agent4 on 2017-04-30
Hello,

I have the exact same problems. Here is my lshw.txt : 
```
computer
    description: Ordinateur Bloc-notes
    produit: UX303UA (ASUS-NotebookSKU)
    fabriquant: ASUSTeK COMPUTER INC.
    version: 1.0
    numéro de série: [REMOVED]
    bits: 64 bits
    fonctionnalités: smbios-3.0 dmi-3.0 vsyscall32
    configuration: boot=normal chassis=notebook family=UX sku=ASUS-NotebookSKU uuid=[REMOVED]
  *-core
       description: Carte mère
       produit: UX303UA
       fabriquant: ASUSTeK COMPUTER INC.
       identifiant matériel: 0
       version: 1.0
       numéro de série: [REMOVED]
       emplacement: MIDDLE
     *-firmware
          description: BIOS
          fabriquant: American Megatrends Inc.
          identifiant matériel: 0
          version: UX303UA.202
          date: 08/27/2015
          taille: 64KiB
          capacité: 5952KiB
          fonctionnalités: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-cache:0
          description: L1 cache
          identifiant matériel: d
          emplacement: L1 Cache
          taille: 64KiB
          capacité: 64KiB
          fonctionnalités: synchronous internal write-back data
          configuration: level=1
     *-cache:1
          description: L1 cache
          identifiant matériel: e
          emplacement: L1 Cache
          taille: 64KiB
          capacité: 64KiB
          fonctionnalités: synchronous internal write-back instruction
          configuration: level=1
     *-cache:2
          description: L2 cache
          identifiant matériel: f
          emplacement: L2 Cache
          taille: 512KiB
          capacité: 512KiB
          fonctionnalités: synchronous internal write-back unified
          configuration: level=2
     *-cache:3
          description: L3 cache
          identifiant matériel: 10
          emplacement: L3 Cache
          taille: 3MiB
          capacité: 3MiB
          fonctionnalités: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          produit: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz
          fabriquant: Intel Corp.
          identifiant matériel: 11
          information bus: cpu@0
          version: Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz
          numéro de série: [REMOVED]
          emplacement: U3E1
          taille: 2700MHz
          capacité: 2800MHz
          bits: 64 bits
          horloge: 100MHz
          fonctionnalités: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-memory
          description: Mémoire Système
          identifiant matériel: 12
          emplacement: Carte mère
          taille: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchrone 1600 MHz (0,6 ns)
             produit: M471B5173DB0-YK0
             fabriquant: Samsung
             identifiant matériel: 0
             numéro de série: [REMOVED]
             emplacement: ChannelA-DIMM0
             taille: 4GiB
             bits: 64 bits
             horloge: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchrone 1600 MHz (0,6 ns)
             produit: HMT451S6BFR8A-PB
             fabriquant: SK Hynix
             identifiant matériel: 1
             numéro de série: [REMOVED]
             emplacement: ChannelB-DIMM0
             taille: 4GiB
             bits: 64 bits
             horloge: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          produit: Sky Lake Host Bridge/DRAM Registers
          fabriquant: Intel Corporation
          identifiant matériel: 100
          information bus: pci@0000:00:00.0
          version: 08
          bits: 32 bits
          horloge: 33MHz
        *-display
             description: VGA compatible controller
             produit: Sky Lake Integrated Graphics
             fabriquant: Intel Corporation
             identifiant matériel: 2
             information bus: pci@0000:00:02.0
             version: 07
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915_bpo latency=0
             ressources: irq:125 mémoire:de000000-deffffff mémoire:c0000000-cfffffff portE/S:f000(taille=64)
        *-generic:0
             description: Signal processing controller
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 4
             information bus: pci@0000:00:04.0
             version: 08
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: msi pm bus_master cap_list
             configuration: driver=proc_thermal latency=0
             ressources: irq:16 mémoire:df120000-df127fff
        *-usb
             description: USB controller
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 14
             information bus: pci@0000:00:14.0
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             ressources: irq:123 mémoire:df110000-df11ffff
           *-usbhost:0
                produit: xHCI Host Controller
                fabriquant: Linux 4.4.0-75-generic xhci-hcd
                identifiant matériel: 0
                information bus: usb@2
                nom logique: usb2
                version: 4.04
                fonctionnalités: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
           *-usbhost:1
                produit: xHCI Host Controller
                fabriquant: Linux 4.4.0-75-generic xhci-hcd
                identifiant matériel: 1
                information bus: usb@1
                nom logique: usb1
                version: 4.04
                fonctionnalités: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb
                   description: Vidéo
                   produit: USB2.0 UVC HD Webcam
                   fabriquant: SuYin
                   identifiant matériel: 5
                   information bus: usb@1:5
                   version: 1.01
                   numéro de série: [REMOVED]
                   fonctionnalités: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-generic:1 NON-RÉCLAMÉ
             description: Signal processing controller
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 14.2
             information bus: pci@0000:00:14.2
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration: latency=0
             ressources: mémoire:df136000-df136fff
        *-communication
             description: Communication controller
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 16
             information bus: pci@0000:00:16.0
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             ressources: irq:126 mémoire:df135000-df135fff
        *-storage
             description: SATA controller
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 17
             information bus: pci@0000:00:17.0
             version: 21
             bits: 32 bits
             horloge: 66MHz
             fonctionnalités: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             ressources: irq:124 mémoire:df130000-df131fff mémoire:df134000-df1340ff portE/S:f090(taille=8) portE/S:f080(taille=4) portE/S:f060(taille=32) mémoire:df133000-df1337ff
        *-pci
             description: PCI bridge
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 1c
             information bus: pci@0000:00:1c.0
             version: f1
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             ressources: irq:122 mémoire:df000000-df0fffff
           *-network
                description: Interface réseau sans fil
                produit: Wireless 7265
                fabriquant: Intel Corporation
                identifiant matériel: 0
                information bus: pci@0000:01:00.0
                nom logique: wlp1s0
                version: 59
                numéro de série: [REMOVED]
                bits: 64 bits
                horloge: 33MHz
                fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-75-generic firmware=17.352738.0 ip=[REMOVED] latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                ressources: irq:127 mémoire:df000000-df001fff
        *-isa
             description: ISA bridge
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 1f
             information bus: pci@0000:00:1f.0
             version: 21
             bits: 32 bits
             horloge: 33MHz
             fonctionnalités: isa bus_master
             configuration: latency=0
        *-memory NON-RÉCLAMÉ
             description: Memory controller
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 1f.2
             information bus: pci@0000:00:1f.2
             version: 21
             bits: 32 bits
             horloge: 33MHz (30.3ns)
             fonctionnalités: bus_master
             configuration: latency=0
             ressources: mémoire:df12c000-df12ffff
        *-multimedia
             description: Audio device
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 1f.3
             information bus: pci@0000:00:1f.3
             version: 21
             bits: 64 bits
             horloge: 33MHz
             fonctionnalités: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             ressources: irq:128 mémoire:df128000-df12bfff mémoire:df100000-df10ffff
        *-serial NON-RÉCLAMÉ
             description: SMBus
             produit: Intel Corporation
             fabriquant: Intel Corporation
             identifiant matériel: 1f.4
             information bus: pci@0000:00:1f.4
             version: 21
             bits: 64 bits
             horloge: 33MHz
             configuration: latency=0
             ressources: mémoire:df132000-df1320ff portE/S:f040(taille=32)
     *-scsi
          identifiant matériel: 1
          nom logique: scsi0
          fonctionnalités: emulated
        *-disk
             description: ATA Disk
             produit: HFS256G32MND-220
             identifiant matériel: 0.0.0
             information bus: scsi@0:0.0.0
             nom logique: /dev/sda
             version: 0L00
             numéro de série: [REMOVED]
             taille: 238GiB (256GB)
             fonctionnalités: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=6cf3f2e0-065f-4a5a-92f7-adefc83592d7 logicalsectorsize=512 sectorsize=512
           *-volume:0 NON-RÉCLAMÉ
                description: Windows FAT volume
                fabriquant: MSDOS5.0
                identifiant matériel: 1
                information bus: scsi@0:0.0.0,1
                version: FAT32
                numéro de série: [REMOVED]
                taille: 255MiB
                capacité: 259MiB
                fonctionnalités: boot fat initialized
                configuration: FATs=2 filesystem=fat label=SYSTEM name=EFI system partition
           *-volume:1
                description: reserved partition
                fabriquant: Windows
                identifiant matériel: 2
                information bus: scsi@0:0.0.0,2
                nom logique: /dev/sda2
                numéro de série: [REMOVED]
                capacité: 15MiB
                fonctionnalités: nofs
                configuration: name=Microsoft reserved partition
           *-volume:2
                description: Windows NTFS volume
                fabriquant: Windows
                identifiant matériel: 3
                information bus: scsi@0:0.0.0,3
                nom logique: /dev/sda3
                nom logique: /media/agent4/OS
                version: 3.1
                numéro de série: [REMOVED]
                taille: 120GiB
                capacité: 120GiB
                fonctionnalités: ntfs initialized
                configuration: clustersize=4096 created=2015-12-05 18:19:00 filesystem=ntfs label=OS mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 name=Basic data partition state=mounted
           *-volume:3
                description: Windows NTFS volume
                fabriquant: Windows
                identifiant matériel: 4
                information bus: scsi@0:0.0.0,4
                nom logique: /dev/sda4
                version: 3.1
                numéro de série: [REMOVED]
                taille: 479MiB
                capacité: 498MiB
                fonctionnalités: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2015-12-05 18:06:34 filesystem=ntfs label=RECOVERY modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:4
                description: BIOS Boot partition
                fabriquant: EFI
                identifiant matériel: 5
                information bus: scsi@0:0.0.0,5
                nom logique: /dev/sda5
                numéro de série: [REMOVED]
                capacité: 1023KiB
                fonctionnalités: nofs
           *-volume:5
                description: Linux swap volume
                fabriquant: Linux
                identifiant matériel: 6
                information bus: scsi@0:0.0.0,6
                nom logique: /dev/sda6
                version: 1
                numéro de série: [REMOVED]
                taille: 1907MiB
                capacité: 1907MiB
                fonctionnalités: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:6
                description: Volume EXT4
                fabriquant: Linux
                identifiant matériel: 7
                information bus: scsi@0:0.0.0,7
                nom logique: /dev/sda7
                nom logique: /
                version: 1.0
                numéro de série: [REMOVED]
                taille: 115GiB
                fonctionnalités: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-04-23 18:13:32 filesystem=ext4 lastmountpoint=/ modified=2017-04-30 13:41:07 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-04-30 13:41:09 state=mounted
```

Many thanks !

---

### Post by mörgæs on 2017-04-30
Good to have more of the same in one thread. Maybe your posts can help each other.

Your hardware is strong so that's not the problem. First test: How does it work when you boot into an older kernel?

---

### Post by agent4 on 2017-05-02
The problem is still here when I boot on another kernel. 

Just right after the problem occur, I changed the line in /etc/default/grub from GRUB_CMDLINE_LINUX_DEFAULT to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

---

### Post by mörgæs on 2017-05-02
Next test: How does it work in a live boot of 17.04?

---


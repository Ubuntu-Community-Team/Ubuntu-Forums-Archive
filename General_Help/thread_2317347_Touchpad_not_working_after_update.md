---
title: "Touchpad not working after update"
date: 2016-03-15
forum: General Help
---

### Post by ian_kirkman2 on 2016-03-15
Hi, I hope someone can help. Today I clicked on the update tab that popped up, (as I usually do), and after the restart, I cannot see the cursor. I have a strong suspicion that the touchpad has been somehow disabled.
The laptop is an Acer Aspire ES1-512 and the os is Ubuntu 14.04
The laptop is now unusable so I hope someone can shed some light as I'm a newbie.
Thanks in advance. Ian

---

### Post by jondog154 on 2016-03-16
Hi Ian can you open a terminal and type sudo lshw it will ask for your login password... then post the output of lshw to me

---

### Post by ian_kirkman2 on 2016-03-16
Hi jondog154, thanks for the reply. I've done as you say and it initially shows info about the laptop, version etc.
If I then use the up/down keys, it shows some lines of text one by one. Is this the info you require? If it is, I'll need to write it down long hand and type it here as I cannot use that laptop now.

---

### Post by mörgæs on 2016-03-16
You could also try to boot into an old kernel.

---

### Post by ian_kirkman2 on 2016-03-16
Ok, have booted from previous kernal and all works fine, so I guess it's a bug in the latest update. At least now I can get all my files onto a stick in case I need to re-install. I'll also post the output of lshw.

---

### Post by ian_kirkman2 on 2016-03-16
Ok,jondog154, I've managed to get the output. Hope it helps.


ian1001@ian1001-Aspire-ES1-512:~$ sudo lshw
[sudo] password for ian1001: 
ian1001-aspire-es1-512    
    description: Notebook
    product: Aspire ES1-512 (EA53_BM_083D_1.09)
    vendor: Acer
    version: V1.09
    serial: NXMRWEK0024500AE156600
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: chassis=notebook family=BayTrail sku=EA53_BM_083D_1.09 uuid=2665EDFC-2B07-48B9-B39B-F4B9A169A404
  *-core
       description: Motherboard
       product: Aspire ES1-512
       vendor: Acer
       physical id: 0
       version: V1.09
       serial: NXMRWEK0024500AE156600
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: V1.09
          date: 10/24/2014
          size: 64KiB
          capacity: 3008KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int9keyboard int14serial int17printer int10video acpi usb zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU  N2840  @ 2.16GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Celeron(R) CPU  N2840  @ 2.16GHz
          slot: CPU 1
          size: 756MHz
          capacity: 756MHz
          width: 64 bits
          clock: 83MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch ida arat epb dtherm tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms cpufreq
          configuration: cores=2 enabledcores=2 threads=1
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: Unknown
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-cache
          description: L1 cache
          physical id: 7
          slot: Unknown
          size: 24KiB
          capacity: 24KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5173DB0-YK0
             vendor: Samsung
             physical id: 0
             serial: 24132111
             slot: DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>POT-Creation-Date: 2009-10-08 14:02+0200PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2015-02-19 11:31+0000X-Generator: Launchpad (build 17341) [empty]
             physical id: 1
             slot: DIMM1
     *-pci
          description: Host bridge
          product: Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0e
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:268 memory:90000000-903fffff memory:80000000-8fffffff ioport:2050(size=8)
        *-storage
             description: SATA controller
             product: Atom Processor E3800 Series SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 0e
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:265 ioport:2048(size=8) ioport:205c(size=4) ioport:2040(size=8) ioport:2058(size=4) ioport:2020(size=32) memory:9091c000-9091c7ff
        *-usb
             description: USB controller
             product: Atom Processor Z36xxx/Z37xxx Series USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 0e
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:264 memory:90900000-9090ffff
        *-generic
             description: Encryption controller
             product: Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:267 memory:90800000-908fffff memory:90700000-907fffff
        *-multimedia
             description: Audio device
             product: Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 0e
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:269 memory:90910000-90913fff
        *-pci:0
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:261 ioport:3000(size=4096)
        *-pci:1
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:262 ioport:4000(size=4096) memory:90600000-906fffff
           *-network
                description: Wireless interface
                product: QCA9565 / AR9565 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 01
                serial: ac:b5:7d:a0:38:d6
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.19.0-51-generic firmware=N/A ip=192.168.1.73 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:18 memory:90600000-9067ffff memory:90680000-9068ffff
        *-pci:2
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:263 ioport:1000(size=4096) memory:90500000-905fffff ioport:90400000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 0c
                serial: 20:6a:8a:a9:b0:03
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:266 ioport:1000(size=256) memory:90500000-90500fff memory:90400000-90403fff
        *-isa
             description: ISA bridge
             product: Atom Processor Z36xxx/Z37xxx Series Power Control Unit
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-serial UNCLAIMED
             description: SMBus
             product: Atom Processor E3800 Series SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:90918000-9091801f ioport:2000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD5000LPVX-2
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1A01
             serial: WD-WX11A74HS60S
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=c017cf03-5e8d-4220-9c6d-a19d7853def3 sectorsize=4096
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                version: FAT32
                serial: e945-2026
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: 4032b7ab-c21b-4e11-92ca-7ab88667df9f
                size: 461GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-08-15 15:56:02 filesystem=ext4 lastmountpoint=/ modified=2016-03-16 14:06:31 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-03-16 14:06:31 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: af5efed2-7620-46f5-9285-4d9be4c1d71b
                size: 3977MiB
                capacity: 3977MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ8HC
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
ian1001@ian1001-Aspire-ES1-512:~$ cd/etc/xdg/autostart/

---

### Post by mörgæs on 2016-03-16
It's better to post terminal output using CODE tags.

A kernel regression might be fixed soon. I would not recommend a reinstall yet, just wait and see what comes in the next kernel update.

---

### Post by ian_kirkman2 on 2016-03-16
Thanks Morgaes. Do I need to report the bug in some way?

---

### Post by mörgæs on 2016-03-16
Thanks for considering this. 14.04 is yesterday's news and it's not worth the effort to report a bug for it. A fixed kernel might appear in an update but there is no promise.

However, if you find the same bug in 16.04 (beta) a bug report will be appreciated.

---

### Post by ian_kirkman2 on 2016-03-16
Ok, I appreciate that Morgaes. So are you basically saying that it's time for me to upgrade to a newer version?

---

### Post by mörgæs on 2016-03-17
I was thinking of testing 16.04, not necessarily leave 14.04. You have a big hard disk so maybe you can do a dual boot. 

Testing from a live boot is also an option.

---


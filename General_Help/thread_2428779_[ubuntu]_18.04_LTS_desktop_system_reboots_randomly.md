---
title: "[ubuntu] 18.04 LTS desktop system reboots randomly"
date: 2019-10-09
forum: General Help
---

### Post by carlo8 on 2019-10-09
[COLOR=#242729][FONT=Arial]I recently installed Ubuntu 18.04, and every now and then the system reboots suddendly.
I have a dual boot with Windows 10 and I had been using the computer for a couple of months, before installing Ubuntu and experiencing this problem. I didn't check if it also happens on Windows, yet.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I would like to figure out whether it's an hardware problem or not.

Sensors report temperatures lower than 70 degrees, so I guess it shouldn't be that.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I checked /var/log/syslog, this should be the part referring to when the reboot occurred:

[/FONT][/COLOR]```

Oct  8 16:43:45 carlo dhclient[1267]: DHCPREQUEST of 212.235.208.14 on enp4s0 to 193.2.4.166 port 67 (xid=0xb419b73)
Oct  8 16:43:45 carlo dhclient[1267]: DHCPACK of 212.235.208.14 from 193.2.4.166
Oct  8 16:43:45 carlo NetworkManager[975]: <info>  [1570545825.4072] dhcp4 (enp4s0):   address 212.235.208.14
Oct  8 16:43:45 carlo NetworkManager[975]: <info>  [1570545825.4072] dhcp4 (enp4s0):   plen 24 (255.255.255.0)
Oct  8 16:43:45 carlo NetworkManager[975]: <info>  [1570545825.4072] dhcp4 (enp4s0):   gateway 212.235.208.1
Oct  8 16:43:45 carlo NetworkManager[975]: <info>  [1570545825.4072] dhcp4 (enp4s0):   lease time 1500
Oct  8 16:43:45 carlo NetworkManager[975]: <info>  [1570545825.4073] dhcp4 (enp4s0):   nameserver '193.2.4.248'
Oct  8 16:43:45 carlo NetworkManager[975]: <info>  [1570545825.4073] dhcp4 (enp4s0):   nameserver '193.2.4.247'
Oct  8 16:43:45 carlo NetworkManager[975]: <info>  [1570545825.4073] dhcp4 (enp4s0):   domain name 'ijs.si'
Oct  8 16:43:45 carlo NetworkManager[975]: <info>  [1570545825.4073] dhcp4 (enp4s0): state changed bound -> bound
Oct  8 16:43:45 carlo dbus-daemon[972]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.15' (uid=0 pid=975 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Oct  8 16:43:45 carlo systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct  8 16:43:45 carlo dbus-daemon[972]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct  8 16:43:45 carlo systemd[1]: Started Network Manager Script Dispatcher Service.
Oct  8 16:43:45 carlo nm-dispatcher: req:1 'dhcp4-change' [enp4s0]: new request (1 scripts)
Oct  8 16:43:45 carlo nm-dispatcher: req:1 'dhcp4-change' [enp4s0]: start running ordered scripts...
Oct  8 16:43:45 carlo dhclient[1267]: bound to 212.235.208.14 -- renewal in 726 seconds.
Oct  8 16:46:30 carlo systemd-modules-load[359]: Inserted module 'lp'
Oct  8 16:46:30 carlo systemd-modules-load[359]: Inserted module 'ppdev'
Oct  8 16:46:30 carlo systemd[1]: Starting Flush Journal to Persistent Storage...
Oct  8 16:46:30 carlo systemd[1]: Started Load/Save Random Seed.
Oct  8 16:46:30 carlo systemd[1]: Started Create Static Device Nodes in /dev.
Oct  8 16:46:30 carlo systemd[1]: Starting udev Kernel Device Manager...
Oct  8 16:46:30 carlo systemd[1]: Reached target Local File Systems (Pre).
Oct  8 16:46:30 carlo systemd-modules-load[359]: Inserted module 'parport_pc'
Oct  8 16:46:30 carlo systemd[1]: Mounting Mount unit for skype, revision 86...
Oct  8 16:46:30 carlo systemd[1]: Mounting Mount unit for vlc, revision 1049...
Oct  8 16:46:30 carlo systemd[1]: Mounting Mount unit for gnome-system-monitor, revision 100...
Oct  8 16:46:30 carlo systemd[1]: Mounting Mount unit for gtk-common-themes, revision 1313...
Oct  8 16:46:30 carlo systemd[1]: Mounting Mount unit for gnome-calculator, revision 501...
Oct  8 16:46:30 carlo systemd[1]: Mounting Mount unit for gnome-characters, revision 296...
Oct  8 16:46:30 carlo systemd[1]: Mounting Mount unit for core, revision 7270...
Oct  8 16:46:30 carlo systemd[1]: Mounting Mount unit for gimp, revision 189...
Oct  8 16:46:30 carlo systemd[1]: Mounting Mount unit for core18, revision 1144...
Oct  8 16:46:30 carlo systemd[1]

```[COLOR=#242729][FONT=Arial]


[/FONT][/COLOR][COLOR=#242729][FONT=Arial]but honestly I'm not really practical about it, so I don't know if there's anything useful here.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I ran[/FONT][/COLOR]

```

last reboot

```
[COLOR=#242729][FONT=Arial]
and I got[/FONT][/COLOR]

```

reboot   system boot  5.0.0-31-generic Tue Oct  8 16:45   still running
reboot   system boot  5.0.0-31-generic Tue Oct  8 13:05   still running
reboot   system boot  5.0.0-31-generic Mon Oct  7 14:04   still running
reboot   system boot  5.0.0-31-generic Mon Oct  7 11:53   still running
reboot   system boot  5.0.0-31-generic Mon Oct  7 11:26   still running
reboot   system boot  5.0.0-29-generic Fri Oct  4 13:10   still running
reboot   system boot  5.0.0-29-generic Wed Oct  2 17:03   still running
reboot   system boot  5.0.0-29-generic Tue Oct  1 08:35   still running

```


[COLOR=#242729][FONT=Arial]Any suggestion regarding how I could proceed? Thank you![/FONT][/COLOR]

---

### Post by mörgæs on 2019-10-10
Let's look closer at the hardware. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the command line, run it and post lshw.txt in CODE tags.

---

### Post by carlo8 on 2019-10-11
Thanks for the answer!
This is the output:

```

computer
    description: Desktop Computer
    product: System Product Name (ASUS_MB_CNL)
    vendor: System manufacturer
    version: System Version
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.1 dmi-3.1 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=ASUS_MB_CNL uuid=[REMOVED]
  *-core
       description: Motherboard
       product: PRIME H310-PLUS
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev X.0x
       serial: [REMOVED]
       slot: Default string
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1405
          date: 09/17/2018
          size: 64KiB
          capacity: 15MiB
          capabilities: pci apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 3b
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM DDR4 Synchronous 2666 MHz (0,4 ns)
             product: BLS16G4D26BFSE.16FD
             vendor: CRUCIAL
             physical id: 0
             serial: [REMOVED]
             slot: ChannelA-DIMM1
             size: 16GiB
             width: 64 bits
             clock: 2666MHz (0.4ns)
        *-bank:1
             description: [empty]
             physical id: 1
             slot: ChannelB-DIMM1
     *-cache:0
          description: L1 cache
          physical id: 44
          slot: L1 Cache
          size: 512KiB
          capacity: 512KiB
          capabilities: synchronous internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 45
          slot: L2 Cache
          size: 2MiB
          capacity: 2MiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 46
          slot: L3 Cache
          size: 12MiB
          capacity: 12MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-9700K CPU @ 3.60GHz
          vendor: Intel Corp.
          physical id: 47
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-9700K CPU @ 3.60GHz
          serial: [REMOVED]
          slot: LGA1151
          size: 4500MHz
          capacity: 4900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities cpufreq
          configuration: cores=8 enabledcores=8 threads=8
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0a
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:126 memory:a0000000-a0ffffff memory:90000000-9fffffff ioport:4000(size=64) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Cannon Lake PCH USB 3.1 xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:122 memory:a1200000-a120ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.0.0-31-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.00
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Keyboard
                   product: Lenovo Traditional USB Keyboard
                   vendor: Lenovo
                   physical id: 3
                   bus info: usb@1:3
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=1Mbit/s
              *-usb:1
                   description: Mouse
                   product: USB Laser Mouse
                   vendor: Logitech
                   physical id: 4
                   bus info: usb@1:4
                   version: 56.01
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=1Mbit/s
              *-usb:2
                   description: Generic USB device
                   product: BCM20702A0
                   vendor: Broadcom Corp
                   physical id: 6
                   bus info: usb@1:6
                   version: 1.12
                   serial: [REMOVED]
                   capabilities: usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.0.0-31-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.00
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
        *-memory UNCLAIMED
             description: RAM memory
             product: Cannon Lake PCH Shared SRAM
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 10
             width: 64 bits
             clock: 33MHz (30.3ns)
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:a1216000-a1217fff memory:a121b000-a121bfff
        *-communication
             description: Communication controller
             product: Cannon Lake PCH HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:125 memory:a121a000-a121afff
        *-storage
             description: SATA controller
             product: Cannon Lake PCH SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:123 memory:a1214000-a1215fff memory:a1219000-a12190ff ioport:4070(size=8) ioport:4060(size=4) ioport:4040(size=32) memory:a1218000-a12187ff
        *-pci:0
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode cap_list
             configuration: driver=pcieport
             resources: irq:0 ioport:5000(size=4096) memory:a1300000-a14fffff ioport:a1500000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:120
           *-pci
                description: PCI bridge
                product: ASM1083/1085 PCIe to PCI Bridge
                vendor: ASMedia Technology Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pci msi pm pciexpress normal_decode cap_list
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:121 ioport:3000(size=4096) memory:a1100000-a11fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: enp4s0
                version: 15
                serial: [REMOVED]
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=[REMOVED] latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:19 ioport:3000(size=256) memory:a1104000-a1104fff memory:a1100000-a1103fff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: Cannon Lake PCH cAVS
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:127 memory:a1210000-a1213fff memory:a1000000-a10fffff
        *-serial:0 UNCLAIMED
             description: SMBus
             product: Cannon Lake PCH SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 10
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:a1218800-a12188ff ioport:efa0(size=32)
        *-serial:1 UNCLAIMED
             description: Serial bus controller
             product: Cannon Lake PCH SPI Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 10
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe010000-fe010fff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 860
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 2B6Q
             serial: [REMOVED]
             size: 931GiB (1TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=e57c5cbd-1287-490d-b255-647ae4864ccf logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: Windows NTFS volume
                vendor: Windows
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: [REMOVED]
                size: 497MiB
                capacity: 498MiB
                capabilities: boot precious readonly hidden nomount ntfs initialized
                configuration: clustersize=4096 created=2019-05-31 18:39:38 filesystem=ntfs label=Recovery modified_by_chkdsk=true mounted_on_nt4=true name=Basic data partition resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /boot/efi
                version: FAT32
                serial: [REMOVED]
                size: 75MiB
                capacity: 98MiB
                capabilities: boot precious readonly hidden nomount fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI system partition state=mounted
           *-volume:2
                description: reserved partition
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                serial: [REMOVED]
                capacity: 15MiB
                capabilities: nofs precious readonly hidden nomount
                configuration: name=Microsoft reserved partition
           *-volume:3
                description: Windows NTFS volume
                vendor: Windows
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 3.1
                serial: [REMOVED]
                size: 930GiB
                capacity: 930GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2019-05-31 18:39:43 filesystem=ntfs name=Basic data partition state=clean
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA HDWE140
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: FP1R
             serial: [REMOVED]
             size: 3726GiB (4TB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=202d085a-bd61-49a6-bb34-b6e0b4a8d044 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                version: FAT32
                serial: [REMOVED]
                size: 617MiB
                capacity: 618MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sdb2
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 465GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2019-09-13 15:45:16 filesystem=ext4 lastmountpoint=/ modified=2019-10-09 10:38:19 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2019-10-09 10:38:25 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@1:0.0.0,3
                logical name: /dev/sdb3
                version: 1
                serial: [REMOVED]
                size: 14GiB
                capacity: 14GiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:3
                description: EXT4 volume
                vendor: Linux
                physical id: 4
                bus info: scsi@1:0.0.0,4
                logical name: /dev/sdb4
                logical name: /home
                version: 1.0
                serial: [REMOVED]
                size: 3244GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2019-09-13 15:45:24 filesystem=ext4 lastmountpoint=/home modified=2019-10-09 10:38:53 mount.fstype=ext4 mount.options=rw,relatime mounted=2019-10-09 10:38:53 state=mounted
     *-scsi:2
          physical id: 3
          logical name: scsi3
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DRW-24D5MT
             vendor: ASUS
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: 1.00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
  *-power UNCLAIMED
       description: To Be Filled By O.E.M.
       product: To Be Filled By O.E.M.
       vendor: To Be Filled By O.E.M.
       physical id: 1
       version: To Be Filled By O.E.M.
       serial: [REMOVED]
       capacity: 32768mWh

```

---

### Post by mörgæs on 2019-10-11
Several new BIOS packages have been released after your 1405. I suggest that you try an update. 

[https://www.asus.com/Motherboards/PRIME-H310-PLUS/HelpDesk_BIOS/](https://www.asus.com/Motherboards/PRIME-H310-PLUS/HelpDesk_BIOS/)

---


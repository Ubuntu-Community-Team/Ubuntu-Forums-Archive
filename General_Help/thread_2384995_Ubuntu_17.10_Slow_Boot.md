---
title: "Ubuntu 17.10 Slow Boot"
date: 2018-02-14
forum: General Help
---

### Post by anthrocoon12 on 2018-02-14
Hello all, I just installed Ubuntu 17.10 with cinnamon DE on my laptop, and it boot very slowly at 3-5 minutes. I previously use Ubuntu 16.04 and it's booting very fast, then i switch to Linux Mint 18.3 i experience slow boot at 2-3 minutes. I then switch to Ubuntu 17.10 but still experience slow boot, even worse than before.
Here is my systemd-analyze blame
```
      
	2min 260ms plymouth-quit-wait.service
	47.360s dev-sda1.device
	35.349s gpu-manager.service
	25.184s snapd.service
	20.906s NetworkManager.service
	18.603s udisks2.service
	18.438s mnt-sda3.mount
	16.853s accounts-daemon.service
	16.474s NetworkManager-wait-online.service
	16.214s systemd-fsck@dev-disk-by\x2duuid-566F\x2d28B3.service
	13.445s polkit.service
	13.138s apache2.service
	10.372s systemd-fsck@dev-disk-by\x2duuid-8ddae9bf\x2d5a8e\x2d4a8d\x2db23e\x2d138a24034d5f.service
	 8.891s plymouth-start.service
	 7.296s networking.service
	 7.111s bluetooth.service
	 6.890s grub-common.service
	 6.801s thermald.service
	 6.789s rsyslog.service
	 6.788s pppd-dns.service
	 6.788s sysstat.service
	 6.018s user@121.service
	 5.583s preload.service
	 5.274s home.mount
	 5.145s apport.service
	 4.906s lm-sensors.service
	 4.834s apparmor.service
	 4.754s tlp.service
	 4.378s postfix@-.service
	 3.888s systemd-backlight@backlight:intel_backlight.service
	 3.866s fwupd.service
	 3.470s systemd-random-seed.service
	 3.384s avahi-daemon.service
	 3.383s speech-dispatcher.service
	 3.272s wpa_supplicant.service
	 2.929s packagekit.service
	 2.849s systemd-udevd.service
	 2.604s systemd-tmpfiles-setup-dev.service
	 2.207s systemd-modules-load.service
	 2.131s alsa-restore.service
	 2.017s systemd-tmpfiles-setup.service
	 1.953s keyboard-setup.service
	 1.887s gdm.service
	 1.749s sys-kernel-debug.mount
	 1.748s dev-mqueue.mount
	 1.656s colord.service
	 1.643s binfmt-support.service
	 1.396s dev-hugepages.mount
	 1.311s dns-clean.service
	 1.267s console-setup.service
	  907ms systemd-update-utmp.service
	  856ms hddtemp.service
	  851ms systemd-timesyncd.service
	  843ms setvtrgb.service
	  779ms upower.service
	  742ms systemd-resolved.service
	  659ms systemd-sysctl.service
	  618ms systemd-logind.service
	  544ms plymouth-read-write.service
	  517ms ufw.service
	  508ms kmod-static-nodes.service
	  499ms snapd.socket
	  427ms kerneloops.service
	  423ms proc-sys-fs-binfmt_misc.mount
	  363ms boot-efi.mount
	  278ms user@1000.service
	  227ms systemd-journald.service
	  155ms systemd-user-sessions.service
	   99ms systemd-udev-trigger.service
	   61ms systemd-remount-fs.service
	   54ms systemd-journal-flush.service
	    4ms systemd-update-utmp-runlevel.service
	    4ms nvidia-persistenced.service
	    3ms rtkit-daemon.service
	    2ms sys-fs-fuse-connections.mount
	    2ms sys-kernel-config.mount

```
Here is my systemd-analyze critcal-chain
```

graphical.target @3min 53.613s
&#9492;&#9472;multi-user.target @3min 53.613s
  &#9492;&#9472;kerneloops.service @2min 10.292s +427ms
    &#9492;&#9472;network-online.target @2min 9.671s
      &#9492;&#9472;NetworkManager-wait-online.service @1min 53.196s +16.474s
        &#9492;&#9472;NetworkManager.service @1min 31.984s +20.906s
          &#9492;&#9472;dbus.service @1min 25.317s
            &#9492;&#9472;basic.target @1min 25.312s
              &#9492;&#9472;sockets.target @1min 25.312s
                &#9492;&#9472;snapd.socket @1min 24.812s +499ms
                  &#9492;&#9472;sysinit.target @1min 24.812s
                    &#9492;&#9472;apparmor.service @1min 19.971s +4.834s
                      &#9492;&#9472;local-fs.target @1min 19.969s
                        &#9492;&#9472;run-user-121.mount @2min 38.090s
                          &#9492;&#9472;local-fs-pre.target @20.203s
                            &#9492;&#9472;systemd-remount-fs.service @20.141s +61ms
                              &#9492;&#9472;system.slice @14.085s
                                &#9492;&#9472;-.slice @14.083s

```
and here is my lshw output
```

gaius-graucus
    description: Notebook
    product: X455LJ (ASUS-NotebookSKU)
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: F2N0WU18525309B
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    configuration: boot=normal chassis=notebook family=X sku=ASUS-NotebookSKU uuid=8B55FB95-00E6-4795-BBA5-FF52FA31ADD6
  *-core
       description: Motherboard
       product: X455LJ
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: X455LJ.201
          date: 01/15/2015
          size: 64KiB
          capacity: 6400KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-cache:0
          description: L1 cache
          physical id: d
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-cache:1
          description: L1 cache
          physical id: e
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back instruction
          configuration: level=1
     *-cache:2
          description: L2 cache
          physical id: f
          slot: L2 Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: synchronous internal write-back unified
          configuration: level=2
     *-cache:3
          description: L3 cache
          physical id: 10
          slot: L3 Cache
          size: 3MiB
          capacity: 3MiB
          capabilities: synchronous internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz
          vendor: Intel Corp.
          physical id: 11
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz
          serial: NULL
          slot: SOCKET 0
          size: 1440MHz
          capacity: 2700MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=2 enabledcores=2 threads=4
     *-memory
          description: System Memory
          physical id: 13
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)
             product: M471B5173EB0-YK0
             vendor: Samsung
             physical id: 0
             serial: D2CE9855
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)
             product: HMT451S6BFR8A-PB
             vendor: Hynix/Hyundai
             physical id: 1
             serial: 00000000
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-pci
          description: Host bridge
          product: Broadwell-U Host Bridge -OPI
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=bdw_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: HD Graphics 5500
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:49 memory:f5000000-f5ffffff memory:d0000000-dfffffff ioport:f000(size=64) memory:c0000-dffff
        *-multimedia:0
             description: Audio device
             product: Broadwell-U Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:50 memory:f731c000-f731ffff
        *-generic:0
             description: Signal processing controller
             product: Broadwell-U Processor Thermal Subsystem
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:f7310000-f7317fff
        *-usb
             description: USB controller
             product: Wildcat Point-LP USB xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:46 memory:f7300000-f730ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.13.0-32-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.13
                capabilities: usb-2.00
                configuration: driver=hub slots=11 speed=480Mbit/s
              *-usb:0
                   description: Video
                   product: USB2.0 VGA UVC WebCam
                   vendor: Chicony Electronics Co., Ltd
                   physical id: 5
                   bus info: usb@1:5
                   version: 99.14
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=200mA speed=480Mbit/s
              *-usb:1
                   description: Bluetooth wireless interface
                   vendor: IMC Networks
                   physical id: 6
                   bus info: usb@1:6
                   version: 0.02
                   capabilities: bluetooth usb-1.10
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.13.0-32-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.13
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
        *-communication
             description: Communication controller
             product: Wildcat Point-LP MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:51 memory:f7324000-f732401f
        *-multimedia:1
             description: Audio device
             product: Wildcat Point-LP High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:52 memory:f7318000-f731bfff
        *-pci:0
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:f2000000-f21fffff ioport:f2200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:e000(size=4096) memory:f7200000-f72fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: enp2s0
                version: 10
                serial: 08:62:66:ce:19:32
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:48 ioport:e000(size=256) memory:f7204000-f7204fff memory:f7200000-f7203fff
        *-pci:2
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 memory:f7100000-f71fffff
           *-network
                description: Wireless interface
                product: QCA9565 / AR9565 Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 01
                serial: 40:e2:30:ed:70:23
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=4.13.0-32-generic firmware=N/A ip=10.5.94.53 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:19 memory:f7100000-f717ffff memory:f7180000-f718ffff
        *-pci:3
             description: PCI bridge
             product: Wildcat Point-LP PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: e3
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:d000(size=4096) memory:f6000000-f70fffff ioport:e0000000(size=301989888)
           *-generic UNCLAIMED
                description: Unassigned class
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 0
                bus info: pci@0000:04:00.0
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
                resources: memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:d000(size=128) memory:f7000000-f707ffff
        *-isa
             description: ISA bridge
             product: Wildcat Point-LP LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: Wildcat Point-LP SATA Controller [AHCI Mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:47 ioport:f0b0(size=8) ioport:f0a0(size=4) ioport:f090(size=8) ioport:f080(size=4) ioport:f060(size=32) memory:f7322000-f73227ff
        *-serial UNCLAIMED
             description: SMBus
             product: Wildcat Point-LP SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f7321000-f73210ff ioport:f040(size=32)
        *-generic:1
             description: Signal processing controller
             product: Wildcat Point-LP Thermal Management Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:22 memory:f7320000-f7320fff
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST500LT012-1DG14
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: SDM1
             serial: S3PLZZ84
             size: 465GiB (500GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=2e869fc7-09d5-4826-afe3-c980d054b612 logicalsectorsize=512 sectorsize=4096
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: fc5d98d5-e5fb-4b2a-9f78-87086ffbeddd
                size: 160GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2018-02-13 17:02:41 filesystem=ext4 lastmountpoint=/ modified=2018-02-15 09:56:44 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2018-02-15 08:52:33 state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /home
                version: 1.0
                serial: 8ddae9bf-5a8e-4a8d-b23e-138a24034d5f
                size: 50GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2018-02-13 17:02:53 filesystem=ext4 lastmountpoint=/home modified=2018-02-15 09:58:06 mount.fstype=ext4 mount.options=rw,relatime,data=ordered mounted=2018-02-15 09:58:06 state=mounted
           *-volume:2
                description: Windows NTFS volume
                vendor: Windows
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                logical name: /mnt/sda3
                version: 3.1
                serial: 565e-a385
                size: 249GiB
                capacity: 249GiB
                capabilities: ntfs initialized
                configuration: clustersize=4096 created=2018-02-02 05:41:22 filesystem=ntfs label=Graucus mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096 state=mounted
           *-volume:3
                description: Linux swap volume
                vendor: Linux
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                version: 1
                serial: 76a7ffed-31c4-432b-8c4b-a901d91f1807
                size: 4095MiB
                capacity: 4095MiB
                capabilities: nofs swap initialized
                configuration: filesystem=swap pagesize=4095
           *-volume:4
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 5
                bus info: scsi@0:0.0.0,5
                logical name: /dev/sda5
                logical name: /boot/efi
                version: FAT32
                serial: 566f-28b3
                size: 248MiB
                capacity: 249MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat label=EFI mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVDRAM GUC0N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: AS01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc

```
Any thought on how to solve this slow boot? Thanks!

---


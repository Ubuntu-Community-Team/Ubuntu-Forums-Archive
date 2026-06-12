---
title: "Slow kernel boot on fresh 16.04 install"
date: 2016-12-29
forum: General Help
---

### Post by pranithkumar on 2016-12-29
I freshly installed 16.04 on my system and I am seeing really slow boot times. I see a 90s delay before the root file system is mounted:

```
[    2.146174] hid-generic 0003:047D:1020.0003: input,hidraw2: USB HID v1.10 Mouse
[    2.728552] clocksource: Switched to clocksource tsc
[   91.386683] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)

```
The other stats also indicate some problem in the kernel. Any help is really appreciated. Thanks!

    ```
$ systemd-analyze 
    Startup finished in 1min 31.417s (kernel) + 609ms (userspace) = 1min 32.026s

    $ systemd-analyze blame 
           434ms dev-sda1.device
           215ms console-setup.service
           211ms ModemManager.service
           139ms networking.service
           137ms systemd-logind.service
           112ms NetworkManager.service
           106ms apparmor.service
            97ms plymouth-quit-wait.service
            95ms systemd-rfkill.service
            88ms accounts-daemon.service
            82ms upower.service
            75ms alsa-restore.service
            53ms grub-common.service
            52ms systemd-udev-trigger.service
            51ms plymouth-start.service
            46ms apport.service
            45ms irqbalance.service
            45ms thermald.service
            43ms polkitd.service
            39ms avahi-daemon.service
            32ms keyboard-setup.service
            30ms speech-dispatcher.service
            29ms systemd-journald.service
            28ms ondemand.service
            28ms rsyslog.service
            22ms [email]user@108.servic[/email]e
            21ms gpu-manager.service
            20ms systemd-udevd.service
            20ms systemd-tmpfiles-setup-dev.service
            16ms lightdm.service
            15ms systemd-modules-load.service
            15ms ssh.service
            13ms plymouth-read-write.service
            10ms [email]user@1000.servic[/email]e
            10ms systemd-user-sessions.service
             9ms pppd-dns.service
             9ms snapd.autoimport.service
             9ms dev-hugepages.mount
             9ms dev-mqueue.mount
             7ms systemd-update-utmp.service
             7ms sys-kernel-debug.mount
             7ms colord.service
             7ms systemd-tmpfiles-setup.service
             7ms wpa_supplicant.service
             6ms systemd-timesyncd.service
             6ms resolvconf.service
             6ms setvtrgb.service
             5ms ufw.service
             5ms systemd-journal-flush.service
             5ms dns-clean.service
             5ms iio-sensor-proxy.service
             4ms kmod-static-nodes.service
             4ms bluetooth.service
             4ms systemd-random-seed.service
             3ms systemd-sysctl.service
             2ms rtkit-daemon.service
             2ms systemd-remount-fs.service
             2ms ureadahead-stop.service
```

```
$ sudo lshw
desktop               
    description: Desktop Computer
    product: (To be filled by O.E.M.)
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=E9C5C9A2-82FB-11E1-BFCF-0013206ECD20
  *-core
       description: Motherboard
       product: DZ77GA-70K
       vendor: Intel Corporation
       physical id: 0
       version: AAG39009-400
       serial: BQGA213000SK
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: GAZ7711H.86A.0059.2012.1106.1053
          date: 11/06/2012
          size: 64KiB
          capacity: 8MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
     *-cache:0
          description: L1 cache
          physical id: 4
          slot: CPU Internal L1
          size: 256KiB
          capacity: 256KiB
          capabilities: internal write-through data
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 5
          slot: CPU Internal L2
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-through unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: 6
          slot: CPU Internal L3
          size: 8MiB
          capacity: 8MiB
          capabilities: internal write-back unified
          configuration: level=3
     *-memory
          description: System Memory
          physical id: 7
          slot: System board or motherboard
          size: 32GiB
        *-bank:0
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 1600 CL9 Series
             vendor: 8502
             physical id: 0
             serial: 00000000
             slot: DIMM3
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 1600 CL9 Series
             vendor: 8502
             physical id: 1
             serial: 00000000
             slot: DIMM1
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:2
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 1600 CL9 Series
             vendor: 8502
             physical id: 2
             serial: 00000000
             slot: DIMM4
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
             product: 1600 CL9 Series
             vendor: 8502
             physical id: 3
             serial: 00000000
             slot: DIMM2
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-3770K CPU @ 3.50GHz
          vendor: Intel Corp.
          physical id: 2b
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-3770K CPU @ 3.50GHz
          slot: CPU 1
          size: 3574MHz
          capacity: 4500MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm epb tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
          configuration: driver=ivb_uncore
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:e000(size=4096) memory:ee000000-ef0fffff ioport:e0000000(size=167772160)
           *-display
                description: VGA compatible controller
                product: GK104 [GeForce GTX 660 Ti]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:41 memory:ee000000-eeffffff memory:e0000000-e7ffffff memory:e8000000-e9ffffff ioport:e000(size=128) memory:c0000-dffff
           *-multimedia
                description: Audio device
                product: GK104 HDMI Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:ef080000-ef083fff
        *-usb:0
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:31 memory:ef620000-ef62ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.8.0-32-generic xhci-hcd
                physical id: 0
                bus info: usb@3
                logical name: usb3
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=4 speed=480Mbit/s
              *-usb:0
                   description: USB hub
                   product: USB2.0 Hub 456
                   vendor: GenesysLogic
                   physical id: 1
                   bus info: usb@3:1
                   version: 30.12
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=3 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: Poker II
                      vendor: Heng Yu Technology
                      physical id: 1
                      bus info: usb@3:1.1
                      version: 1.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=500mA speed=12Mbit/s
                 *-usb:1
                      description: Mouse
                      product: Kensington Expert Mouse
                      vendor: Kensington
                      physical id: 2
                      bus info: usb@3:1.2
                      version: 1.00
                      capabilities: usb-1.10
                      configuration: driver=usbhid maxpower=100mA speed=2Mbit/s
              *-usb:1
                   description: USB hub
                   product: USB2.0 Hub 456
                   vendor: GenesysLogic
                   physical id: 4
                   bus info: usb@3:4
                   version: 30.12
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=3 speed=480Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.8.0-32-generic xhci-hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 4.08
                capabilities: usb-3.00
                configuration: driver=hub slots=4 speed=5000Mbit/s
              *-usb:0
                   description: USB hub
                   product: USB3.0 Hub 123
                   vendor: GenesysLogic
                   physical id: 1
                   bus info: usb@4:1
                   version: 30.12
                   capabilities: usb-3.00
                   configuration: driver=hub maxpower=144mA slots=3 speed=5000Mbit/s
              *-usb:1
                   description: USB hub
                   product: USB3.0 Hub 123
                   vendor: GenesysLogic
                   physical id: 4
                   bus info: usb@4:4
                   version: 30.12
                   capabilities: usb-3.00
                   configuration: driver=hub maxpower=144mA slots=3 speed=5000Mbit/s
        *-communication
             description: Communication controller
             product: 7 Series/C210 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:39 memory:ef63b000-ef63b00f
        *-network
             description: Ethernet interface
             product: 82579V Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eno1
             version: 04
             serial: 00:22:4d:81:ba:2e
             size: 100Mbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.13-4 ip=192.168.1.146 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
             resources: irq:34 memory:ef600000-ef61ffff memory:ef639000-ef639fff ioport:f040(size=32)
        *-usb:1
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:ef638000-ef6383ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.8.0-32-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb:0
                      description: Generic USB device
                      product: 802.11 n WLAN
                      vendor: Ralink
                      physical id: 1
                      bus info: usb@1:1.1
                      version: 1.01
                      serial: 1.0
                      capabilities: usb-2.00
                      configuration: driver=rt2800usb maxpower=450mA speed=480Mbit/s
                 *-usb:1
                      description: Bluetooth wireless interface
                      vendor: Micro Star International
                      physical id: 2
                      bus info: usb@1:1.2
                      version: 52.76
                      capabilities: bluetooth usb-2.00
                      configuration: driver=btusb speed=12Mbit/s
        *-multimedia
             description: Audio device
             product: 7 Series/C210 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:40 memory:ef630000-ef633fff
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:d000(size=4096) memory:ef500000-ef5fffff
           *-network
                description: Ethernet interface
                product: 82574L Gigabit Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: rename3
                version: 00
                serial: 00:22:4d:81:ba:32
                capacity: 1Gbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=2.1-2 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:16 memory:ef520000-ef53ffff memory:ef500000-ef51ffff ioport:d000(size=32) memory:ef540000-ef543fff
        *-pci:3
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:c000(size=4096) memory:ef100000-ef3fffff
           *-pci
                description: PCI bridge
                product: PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch
                vendor: PLX Technology, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: ba
                width: 64 bits
                clock: 33MHz
                capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                configuration: driver=pcieport
                resources: iomemory:c1c10-c1c0f irq:25 memory:ef300000-ef31ffff ioport:c000(size=4096) memory:ef100000-ef2fffff
              *-pci:0
                   description: PCI bridge
                   product: PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 1
                   bus info: pci@0000:05:01.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:26
              *-pci:1
                   description: PCI bridge
                   product: PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 4
                   bus info: pci@0000:05:04.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:27 ioport:c000(size=4096) memory:ef200000-ef2fffff
                 *-storage
                      description: SATA controller
                      product: 88SE9172 SATA 6Gb/s Controller
                      vendor: Marvell Technology Group Ltd.
                      physical id: 0
                      bus info: pci@0000:07:00.0
                      version: 11
                      width: 32 bits
                      clock: 33MHz
                      capabilities: storage pm msi pciexpress ahci_1.0 bus_master cap_list rom
                      configuration: driver=ahci latency=0
                      resources: irq:33 ioport:c040(size=8) ioport:c030(size=4) ioport:c020(size=8) ioport:c010(size=4) ioport:c000(size=16) memory:ef220000-ef2201ff memory:ef200000-ef21ffff
              *-pci:2
                   description: PCI bridge
                   product: PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 5
                   bus info: pci@0000:05:05.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:28
              *-pci:3
                   description: PCI bridge
                   product: PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 7
                   bus info: pci@0000:05:07.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:29
              *-pci:4
                   description: PCI bridge
                   product: PEX 8606 6 Lane, 6 Port PCI Express Gen 2 (5.0 GT/s) Switch
                   vendor: PLX Technology, Inc.
                   physical id: 9
                   bus info: pci@0000:05:09.0
                   version: ba
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
                   configuration: driver=pcieport
                   resources: irq:30 memory:ef100000-ef1fffff
                 *-pci
                      description: PCI bridge
                      product: Integrated Technology Express, Inc.
                      vendor: Integrated Technology Express, Inc.
                      physical id: 0
                      bus info: pci@0000:0a:00.0
                      version: 30
                      width: 32 bits
                      clock: 33MHz
                      capabilities: pci pm subtractive_decode bus_master cap_list
                      resources: memory:ef100000-ef1fffff
                    *-firewire
                         description: FireWire (IEEE 1394)
                         product: TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
                         vendor: Texas Instruments
                         physical id: 2
                         bus info: pci@0000:0b:02.0
                         version: 00
                         width: 32 bits
                         clock: 33MHz
                         capabilities: pm ohci bus_master cap_list
                         configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                         resources: irq:16 memory:ef104000-ef1047ff memory:ef100000-ef103fff
        *-pci:4
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 8
             vendor: Intel Corporation
             physical id: 1c.7
             bus info: pci@0000:00:1c.7
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:b000(size=4096) memory:ef400000-ef4fffff
           *-storage
                description: SATA controller
                product: 88SE9172 SATA 6Gb/s Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress ahci_1.0 bus_master cap_list rom
                configuration: driver=ahci latency=0
                resources: irq:35 ioport:b040(size=8) ioport:b030(size=4) ioport:b020(size=8) ioport:b010(size=4) ioport:b000(size=16) memory:ef420000-ef4201ff memory:ef400000-ef41ffff
        *-usb:2
             description: USB controller
             product: 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ef637000-ef6373ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.8.0-32-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=2 speed=480Mbit/s
              *-usb
                   description: USB hub
                   product: Integrated Rate Matching Hub
                   vendor: Intel Corp.
                   physical id: 1
                   bus info: usb@2:1
                   version: 0.00
                   capabilities: usb-2.00
                   configuration: driver=hub slots=8 speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: Z77 Express Chipset LPC Controller
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
             product: 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:32 ioport:f090(size=8) ioport:f080(size=4) ioport:f070(size=8) ioport:f060(size=4) ioport:f020(size=32) memory:ef636000-ef6367ff
        *-serial UNCLAIMED
             description: SMBus
             product: 7 Series/C210 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:ef635000-ef6350ff ioport:f000(size=32)
     *-scsi
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: INTEL SSDSC2CW18
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 400i
             serial: CVCV204406BL180EGN
             size: 167GiB (180GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=000536e4
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: b7dbd4b1-d953-4e03-a238-3288465b9c7d
                size: 165GiB
                capacity: 165GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2016-12-29 13:39:15 filesystem=ext4 lastmountpoint=/ modified=2016-12-29 16:52:36 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2016-12-29 16:48:03 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                size: 1905MiB
                capacity: 1905MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1905MiB
                   capabilities: nofs
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.1
       logical name: wlx94dbc950f458
       serial: 94:db:c9:50:f4:58
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.8.0-32-generic firmware=0.29 link=no multicast=yes wireless=IEEE 802.11
```

---

### Post by allenc28 on 2017-12-17
The 90 second delay is caused by a network interface naming conflict that happens due to a flaw in the BIOS of your motherboard.  Some Intel motherboards with multiple integrated NICs have this problem.  Two motherboards that I know of are the Intel DZ77GA-70K (your case) and the DZ77RE-75K (mine.)

Note: there are a number of failure modes that will cause a long delay during boot leading to wasted effort while seeking solutions.  This specific case is related to network interface conflicts and can be detected by running the following command described here: [https://bugzilla.redhat.com/show_bug.cgi?id=1102135](https://bugzilla.redhat.com/show_bug.cgi?id=1102135)

```
# grep . /sys/class/net/*/device/{index,acpi_index}
/sys/class/net/eth0/device/index:1
/sys/class/net/eth1/device/index:1
grep: /sys/class/net/*/device/acpi_index: No such file or directory
```

The two devices have the same "index" value 1 and the ACPI index values are missing.  There should be distinct APCI index values assigned by the BIOS.  Due to these conflicting values the "Predictable Network Interface Name" policy ([https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames)) that appeared in udev v197 causes the network interfaces to somehow not initialize properly on boot and a 90 second timeout is observed.

Another way to detect this is to apply the "debug ignore_loglevel" arguments to the kernel command line.  With these arguments in place during boot (and also in dmesg output) you will see a message after 60 seconds from systemd-udevd that some network interface is "taking a long time."

    ```
systemd-udevd[447]: seq 2024 '/devices/pci0000:00/...' is taking a long time
```

There are several ways to work around this problem.  They are documented on the freedesktop.org link above.  The relevant part is quoted here:

> 1. You disable the assignment of fixed names, so that the unpredictable kernel names are used again. For this, simply mask udev's .link file for the default policy: ln -s /dev/null /etc/systemd/network/99-default.link

2. You create your own manual naming scheme, for example by naming your interfaces "internet0", "dmz0" or "lan0". For that create your own .link files in /etc/systemd/network/, that choose an explicit name or a better naming scheme for one, some, or all of your interfaces. See systemd.link(5) for more information.

3. You pass the net.ifnames=0 on the kernel command line

Speculation: these Z77 boards from Intel appeared just before Intel exited the desktop motherboard business 2013.  The boards never had the benefit of ongoing BIOS updates that might have corrected these issues.  The boards work but there are some glitches, another being the USB "over-current" errors that happen on boot in both Linux and Windows despite there being no USB devices drawing current.

---


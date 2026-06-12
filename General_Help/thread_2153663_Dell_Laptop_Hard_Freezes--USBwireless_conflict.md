---
title: "Dell Laptop Hard Freezes--USB/wireless conflict?"
date: 2013-06-11
forum: General Help
---

### Post by thenanodude on 2013-06-11
Hello,

I have been having a problem with my Dell Latitute E6420 freezing for several months.  My symptoms are similar to those posted here:  [http://ubuntuforums.org/showthread.php?t=1969300](http://ubuntuforums.org/showthread.php?t=1969300)  but no solution has been suggested that helps.  Furthermore, I have collected some information that seems to point to a conflict involving the wireless card / wireless card driver and possibly USB mouse, so I decided to start a new post.

I discovered that the computer only freezes when the wireless network card is active.  Furthermore, it appears to happen sooner when I have a wireless USB mouse plugged in.  It always seems to lock when I'm in the midst of moving the mouse (either with the wireless or the trackpad) or if I leave the computer idle for awhile and return.  The video will still be on, but the computer does not respond to anything.  I cannot even Ctrl-Alt-F1 to open up a text terminal.  It is absolutely locked solid and freezes so quickly that no crash reports are generated, nor does anything seem to be written to the logs.  If left on long enough with the wireless card on, the computer will freeze every time.  If I disable wireless by un-checking "enable wireless" in the control panel, the computer will remain on indefinitely without freezing.  

Here is some system configuration info:
Ubuntu version: xubuntu 12.04.2 LTS
kernel version: 3.5.0-25-generic     (Note: I was previously running a 3.2.x kernel, but read that upgrading it might help.  it does not)
wireless card: Broadcom Corporation BCM43228 802.11a/b/g/n
wireless card driver: bcmwl-kernel-source  6.20.155.1+bdcom-0ubuntu0.0.1   Broadcom 802.11 Linux STA wireless driver source

for more hardware info, below is the output of lshw, lsusb, and lspci.

lshw: 
```
nspc40
    description: Laptop
    product: Latitude E6420 ()
    vendor: Winbond Electronics
    version: 01
    serial: 2WK5DS1
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=laptop uuid=44454C4C-5700-104B-8035-B2C04F445331
  *-core
       description: Motherboard
       product: 038C0K
       vendor: Winbond Electronics
       physical id: 0
       version: A00
       serial: /2WK5DS1/CN129612550157/
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A08
          date: 10/18/2011
          size: 64KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2540M CPU @ 2.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-2540M CPU @ 2.60GH
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 41
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: HMT325S6CFR8C-H9
             vendor: Hynix/Hyundai
             physical id: 0
             serial: 024FE539
             slot: ChannelA-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: HMT325S6CFR8C-H9
             vendor: Hynix/Hyundai
             physical id: 1
             serial: 28CBC6A2
             slot: ChannelB-DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-pci
          description: Host bridge
          product: 2nd Generation Core Processor Family DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:4000(size=4096) memory:e4000000-e50fffff ioport:d0000000(size=301989888)
           *-display
                description: VGA compatible controller
                product: GF119 [Quadro NVS 4200M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:e4000000-e4ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:4000(size=128) memory:e5000000-e507ffff
           *-multimedia
                description: Audio device
                product: HDMI Audio stub
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:e5080000-e5083fff
        *-communication
             description: Communication controller
             product: 6 Series/C200 Series Chipset Family MEI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei latency=0
             resources: irq:44 memory:e67b0000-e67b000f
        *-network
             description: Ethernet interface
             product: 82579LM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 04
             serial: d4:be:d9:2b:cd:3d
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=0.13-3 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:43 memory:e6700000-e671ffff memory:e6780000-e6780fff ioport:5040(size=32)
        *-usb:0
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:e6770000-e67703ff
        *-multimedia
             description: Audio device
             product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:45 memory:e6760000-e6763fff
        *-pci:1
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16
        *-pci:2
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:e6600000-e66fffff
           *-network
                description: Wireless interface
                product: BCM43228 802.11a/b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth2
                version: 00
                serial: c0:18:85:8d:a6:89
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.0.108 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:17 memory:e6600000-e6603fff
        *-pci:3
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:3000(size=4096) memory:e5b00000-e64fffff ioport:e2b00000(size=10485760)
        *-pci:4
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:2000(size=4096) memory:e5100000-e5afffff ioport:e2100000(size=10485760)
        *-pci:5
             description: PCI bridge
             product: 6 Series/C200 Series Chipset Family PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:e6500000-e65fffff
           *-generic
                description: SD Host controller
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 0
                bus info: pci@0000:0b:00.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:17 memory:e6520000-e65201ff
           *-storage UNCLAIMED
                description: Mass storage controller
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 0.1
                bus info: pci@0000:0b:00.1
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:e6510000-e6510fff memory:e6500000-e65007ff
        *-usb:1
             description: USB controller
             product: 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:17 memory:e6750000-e67503ff
        *-isa
             description: ISA bridge
             product: QM67 Express Chipset Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: RAID bus controller
             product: 82801 Mobile SATA Controller [RAID mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:42 ioport:5090(size=8) ioport:5080(size=4) ioport:5070(size=8) ioport:5060(size=4) ioport:5020(size=32) memory:e6740000-e67407ff
        *-serial UNCLAIMED
             description: SMBus
             product: 6 Series/C200 Series Chipset Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:e6730000-e67300ff ioport:5000(size=32)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: ST9500423AS
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 0003
             serial: 6WR1269V
             size: 465GiB (500GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=4ac145c9
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 6c1005ba-d445-6243-8ac0-c047241496d3
                size: 139GiB
                capacity: 139GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2010-09-14 12:59:54 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 326GiB
                capacity: 326GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 9536MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /boot
                   capacity: 476MiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,stripe=4,data=ordered state=mounted
              *-logicalvolume:2
                   description: Linux filesystem partition
                   physical id: 7
                   logical name: /dev/sda7
                   logical name: /
                   capacity: 316GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD+-RW TS-U633J
             vendor: TSSTcorp
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom4
             logical name: /dev/cdrw4
             logical name: /dev/dvd4
             logical name: /dev/dvdrw4
             logical name: /dev/sr0
             version: D800
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom4
  *-battery
       product: DELL FKYCH17
       vendor: Sanyo
       physical id: 1
       version: 07/27/2011
       serial: 09E5
       slot: Sys. Battery Bay
       capacity: 86580mWh
       configuration: voltage=11.1V

```

output of lsusb:
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 001 Device 004: ID 1bcf:2802 Sunplus Innovation Technology Inc. 
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 004: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor

```

output of lspci:
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [Quadro NVS 4200M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation HDMI Audio stub (rev a1)
03:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n
0b:00.0 SD Host controller: O2 Micro, Inc. Device 8221 (rev 05)
0b:00.1 Mass storage controller: O2 Micro, Inc. Device 8231 (rev 03)

```

Thanks for any help!

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by thenanodude on 2013-06-11
Hello again,
I realized I said that nothing seems to be written to the logs at the time of the crash, and I thought I ought to post something to back that up.  So, below are the last few lines from the /var/log/kern.log from just before two recent crashes:

```

Jun  3 22:02:14 nspc40 kernel: [ 6335.555280] PM: resume of drv:scsi dev:host0 complete after 2741.944 msecs
Jun  3 22:02:14 nspc40 kernel: [ 6335.555289] PM: resume of drv:ata_port dev:ata1 complete after 2176.066 msecs
Jun  3 22:02:14 nspc40 kernel: [ 6335.555341] PM: resume of drv:scsi dev:target0:0:0 complete after 2741.642 msecs
Jun  3 22:02:14 nspc40 kernel: [ 6335.555359] PM: resume of drv:scsi_host dev:host0 complete after 2741.971 msecs
Jun  3 22:02:14 nspc40 kernel: [ 6335.555389] PM: resume of drv:sd dev:0:0:0:0 complete after 2741.689 msecs
Jun  3 22:02:14 nspc40 kernel: [ 6335.555402] sd 0:0:0:0: [sda] Starting disk
Jun  3 22:02:14 nspc40 kernel: [ 6335.579697] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2766.009 msecs
Jun  3 22:02:14 nspc40 kernel: [ 6335.580062] PM: resume of devices complete after 2767.464 msecs
Jun  3 22:02:14 nspc40 kernel: [ 6335.580968] PM: resume devices took 2.768 seconds
Jun  3 22:02:14 nspc40 kernel: [ 6335.581247] PM: Finishing wakeup.
Jun  3 22:02:14 nspc40 kernel: [ 6335.581250] Restarting tasks ... done.
Jun  3 22:02:15 nspc40 kernel: [ 6335.999216] video LNXVIDEO:00: Restoring backlight state
Jun  3 22:02:16 nspc40 kernel: [ 6337.484074] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Jun  3 22:02:16 nspc40 kernel: [ 6337.587540] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
Jun  3 22:02:16 nspc40 kernel: [ 6337.588803] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  3 22:02:20 nspc40 kernel: [ 6341.140917] cfg80211: Found new beacon on frequency: 5785 MHz (Ch 157) on phy0
Jun  3 22:05:41 nspc40 kernel: [ 6541.623993] cfg80211: Found new beacon on frequency: 5765 MHz (Ch 153) on phy0




Jun  4 10:15:02 nspc40 kernel: [   24.026993] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
Jun  4 10:15:03 nspc40 kernel: [   24.130695] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
Jun  4 10:15:03 nspc40 kernel: [   24.131087] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  4 10:15:03 nspc40 kernel: [   24.131465] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun  4 10:15:03 nspc40 kernel: [   25.029971] NVRM: Your system is not currently configured to drive a VGA console
Jun  4 10:15:03 nspc40 kernel: [   25.029975] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
Jun  4 10:15:03 nspc40 kernel: [   25.029977] NVRM: requires the use of a text-mode VGA console. Use of other console
Jun  4 10:15:03 nspc40 kernel: [   25.029979] NVRM: drivers including, but not limited to, vesafb, may result in
Jun  4 10:15:03 nspc40 kernel: [   25.029981] NVRM: corruption and stability problems, and is not supported.
Jun  4 10:15:06 nspc40 kernel: [   27.516318] cfg80211: Found new beacon on frequency: 5785 MHz (Ch 157) on phy0
Jun  4 10:15:06 nspc40 kernel: [   27.516324] cfg80211: Found new beacon on frequency: 5785 MHz (Ch 157) on phy0
Jun  4 10:15:24 nspc40 kernel: [   46.441785] audit_printk_skb: 33 callbacks suppressed
Jun  4 10:15:24 nspc40 kernel: [   46.441789] type=1400 audit(1370355324.846:23): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1105 comm="cupsd" pid=1105 comm="c
upsd" capability=36  capname="block_suspend"

```

Here are the last few lines from the syslog at the same times:
```

Jun  3 22:02:37 nspc40 ntpdate[4000]: adjust time server 91.189.94.4 offset 0.086311 sec
Jun  3 22:02:42 nspc40 NetworkManager[1032]: <info> (eth2): IP6 addrconf timed out or failed.
Jun  3 22:02:42 nspc40 NetworkManager[1032]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  3 22:02:42 nspc40 NetworkManager[1032]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  3 22:02:42 nspc40 NetworkManager[1032]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  3 22:05:41 nspc40 kernel: [ 6541.623993] cfg80211: Found new beacon on frequency: 5765 MHz (Ch 153) on phy0
Jun  3 22:17:01 nspc40 CRON[4163]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)


Jun  4 10:15:24 nspc40 kernel: [   46.441785] audit_printk_skb: 33 callbacks suppressed
Jun  4 10:15:24 nspc40 kernel: [   46.441789] type=1400 audit(1370355324.846:23): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1105 comm="cupsd" pid=1105 comm="c
upsd" capability=36  capname="block_suspend"
Jun  4 10:15:25 nspc40 dbus[998]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Jun  4 10:15:25 nspc40 blueman-mechanism: Starting blueman-mechanism 
Jun  4 10:15:25 nspc40 dbus[998]: [system] Successfully activated service 'org.blueman.Mechanism'
Jun  4 10:15:25 nspc40 blueman-mechanism: loading Config 
Jun  4 10:15:25 nspc40 blueman-mechanism: loading Ppp 
Jun  4 10:15:25 nspc40 blueman-mechanism: loading RfKill 
Jun  4 10:15:25 nspc40 blueman-mechanism: loading Network 
Jun  4 10:15:28 nspc40 NetworkManager[1035]: <info> (eth2): IP6 addrconf timed out or failed.
Jun  4 10:15:28 nspc40 NetworkManager[1035]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  4 10:15:28 nspc40 NetworkManager[1035]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  4 10:15:28 nspc40 NetworkManager[1035]: <info> Activation (eth2) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  4 10:15:55 nspc40 blueman-mechanism: Exiting 
Jun  4 10:17:01 nspc40 CRON[2383]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

and here are the last few lines from /var/log/syslog from just before a crash several months ago (I saved these logs when I first started experiencing the problem--I guess that was at least back in February):
```

Feb 14 14:51:06 nspc40 wpa_supplicant[1276]: WPA: Group rekeying completed with 98:fc:11:6c:e1:3a [GTK=TKIP]
Feb 14 14:55:38 nspc40 dbus[861]: [system] Activating service name='org.blueman.Mechanism' (using servicehelper)
Feb 14 14:55:38 nspc40 blueman-mechanism: Starting blueman-mechanism 
Feb 14 14:55:38 nspc40 dbus[861]: [system] Successfully activated service 'org.blueman.Mechanism'
Feb 14 14:55:38 nspc40 blueman-mechanism: loading Config 
Feb 14 14:55:38 nspc40 blueman-mechanism: loading Ppp 
Feb 14 14:55:38 nspc40 blueman-mechanism: loading RfKill 
Feb 14 14:55:38 nspc40 blueman-mechanism: loading Network 
Feb 14 14:55:38 nspc40 kernel: [  399.752765] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
Feb 14 14:56:08 nspc40 blueman-mechanism: Exiting 
Feb 14 14:56:53 nspc40 bluetoothd[896]: HCI dev 0 down
Feb 14 14:56:53 nspc40 bluetoothd[896]: Adapter /org/bluez/896/hci0 has been disabled
Feb 14 14:56:53 nspc40 bluetoothd[896]: HCI dev 0 unregistered
Feb 14 14:56:53 nspc40 bluetoothd[896]: Stopping hci0 event socket
Feb 14 14:56:53 nspc40 bluetoothd[896]: Unregister path: /org/bluez/896/hci0
Feb 14 14:56:53 nspc40 kernel: [  474.768360] usb 1-1.4: USB disconnect, device number 3
Feb 14 15:17:01 nspc40 CRON[2505]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

I could be wrong, but I don't see any problems in here that are repeated and could be causing the crash.

---

### Post by thenanodude on 2013-06-11
ahallubuntu:

the same thought (nvidia issues) crossed my mind as well.  from dpkg, this is the nvidia package I have installed:

      nvidia-current  304.88-0ubuntu0.0.2   NVIDIA binary Xorg driver, kernel module and VDPAU library

however, unless it is the nvidia driver conflicting with the broadcomm driver, I don't think nvidia is the problem.  the system will work all day long as long as the wireless is deactivated.

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by thenanodude on 2013-06-11
ahallubuntu,

thanks for the suggestion.  I do [sadly] still have windows on the machine (it's a work machine, so I cannot get rid of it entirely), so I'll try updating the EFI and BIOS.  I'll also get my hands on another wireless card and check that out--an excellent suggestion that I feel silly for not having tried.  It'll take me a few days, but I'll get back and post the results of the test.  thanks, again!

---

### Post by thenanodude on 2013-07-01
I'm not quite ready to call this one "solved," but I have an update on the situation.  I pulled an old Broadcomm BCM4311 802.11b/g wireless card out of an old notebook and swapped it for the BCM43228 802.11a/b/g/n that was in there.  I also uninstalled the Broadcomm driver from bcm-kernel-source and installed the older one with b43-fwcutter.  That was two weeks ago, and the freezing issue has not returned.  When I have a chance, I am going to purchase an Intel wireless card, so I can get rid of the Broadcomm cards altogether.  Once I do that and can verify that the problem is fixed, I will mark this thread "solved."

For anybody reading this post, I noticed that all of ahallubuntu's helpful posts have been replaced by "~".  Not sure what happened there, but the particularly helpful thing he suggested doing was replacing the wireless card with an Intel one.  Though your helpful words have disappeared, ahallubuntu, I still want to gratefully acknowledge you!

---


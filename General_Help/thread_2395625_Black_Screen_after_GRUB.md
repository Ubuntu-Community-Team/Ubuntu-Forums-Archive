---
title: "Black Screen after GRUB"
date: 2018-07-04
forum: General Help
---

### Post by phosphide on 2018-07-04
Hey everyone,

I recently switched to Ubuntu Mate and having an issue when booting up. I get stuck in a black screen for quite some time before eventually getting to the login and everything works just fine. I've tried the following solutions:

1. Edited /etc/default/grub to put nomodeset. It didn't work and somehow distorted the view (couldn't change screen resolution and it was super zoomed in). Reverted back.
2. Tried editing at GRUB menu by selecting 'e' and putting nomodeset. No effect.
3. Checked to see if xserver-xorg was installed. Already installed and updated.
4. Checked for additional drivers. Says 'No additional drivers available."

Have I missed any other options? I was using Ubuntu 16.04 previously without issue. Appreciate any insight.

System specs:

```
laptop
    description: Notebook
    product: HP ProBook 6460b (XU050UT#ABA)
    vendor: Hewlett-Packard
    version: A0001D02
    serial: CNU1381ZB5
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 smp vsyscall32
    configuration: boot=normal chassis=notebook family=103C_5336AN sku=XU050UT#ABA uuid=4AE8018A-CF31-E111-B543-70C25F06C0CA
  *-core
       description: Motherboard
       product: 161D
       vendor: Hewlett-Packard
       physical id: 0
       version: KBC Version 97.4C
       serial: PCCKB00QE1KA6P
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: b
          version: 68SCE Ver. F.28
          date: 09/17/2012
          size: 64KiB
          capacity: 2496KiB
          capabilities: pci pcmcia upgrade shadowing cdboot bootselect edd int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          slot: CPU 1
          size: 2843MHz
          capacity: 2900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm epb pti ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid xsaveopt dtherm ida arat pln pts cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L3 cache
             physical id: 4
             slot: Unknown
             size: 3KiB
             capacity: 3KiB
             capabilities: asynchronous internal write-back instruction
             configuration: level=3
        *-cache:1
             description: L2 cache
             physical id: 3
             slot: Unknown
             size: 256KiB
             capacity: 256KiB
             capabilities: asynchronous internal write-back instruction
             configuration: level=2
        *-cache:2
             description: L1 cache
             physical id: 2
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
             configuration: level=1
     *-cache
          description: L1 cache
          physical id: 1
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 5
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5173CB0-YK0
             vendor: Samsung
             physical id: 0
             serial: 8706F496
             slot: Bottom-Slot 1(top)
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
             product: M471B5273CH0-CK0
             vendor: Samsung
             physical id: 1
             serial: E1F99DA3
             slot: Bottom-Slot 2(under)
             size: 4GiB
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
        *-display
             description: VGA compatible controller
             product: 2nd Generation Core Processor Family Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:30 memory:d4000000-d43fffff memory:c0000000-cfffffff ioport:4000(size=64) memory:c0000-dffff
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
             configuration: driver=mei_me latency=0
             resources: irq:31 memory:d4724000-d472400f
        *-network
             description: Ethernet interface
             product: 82579V Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: enp0s25
             version: 04
             serial: 10:1f:74:e9:db:da
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.13-4 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:29 memory:d4700000-d471ffff memory:d472a000-d472afff ioport:4060(size=32)
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
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d4729000-d47293ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.15.0-24-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.15
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
                 *-usb UNCLAIMED
                      description: Generic USB device
                      product: VFS471 Fingerprint Reader
                      vendor: Validity Sensors, Inc.
                      physical id: 1
                      bus info: usb@1:1.1
                      version: 0.86
                      serial: 00200acc7989
                      capabilities: usb-1.10
                      configuration: maxpower=100mA speed=12Mbit/s
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
             resources: irq:33 memory:d4720000-d4723fff
        *-pci:0
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
             resources: irq:24 memory:d4600000-d46fffff
        *-pci:1
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
             resources: irq:25 ioport:2000(size=8192) memory:d0000000-d3ffffff ioport:bfb00000(size=2097152)
        *-pci:2
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
             resources: irq:26 memory:d4500000-d45fffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:23:00.0
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=0
                resources: irq:18 memory:d4500000-d45007ff memory:d4505000-d45050ff
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:23:00.1
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=sdhci-pci latency=0
                resources: irq:18 memory:d4504000-d45040ff memory:d4508000-d450ffff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:23:00.2
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:d4503000-d45030ff
        *-pci:3
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
             resources: irq:27 memory:d4400000-d44fffff
           *-network
                description: Wireless interface
                product: Centrino Advanced-N 6205 [Taylor Peak]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:24:00.0
                logical name: wlo1
                version: 34
                serial: 10:0b:a9:40:97:68
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-24-generic firmware=18.168.6.1 ip= latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:32 memory:d4400000-d4401fff
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
             configuration: driver=ehci-pci latency=0
             resources: irq:16 memory:d4728000-d47283ff
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 4.15.0-24-generic ehci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.15
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
                   configuration: driver=hub slots=6 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: USB Receiver
                      vendor: Logitech
                      physical id: 2
                      bus info: usb@2:1.2
                      version: 29.00
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
                 *-usb:1
                      description: Video
                      product: HP HD Webcam [Fixed]
                      vendor: Chicony Electronics Co., Ltd.
                      physical id: 4
                      bus info: usb@2:1.4
                      version: 99.89
                      serial: SN0001
                      capabilities: usb-2.00
                      configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
        *-isa
             description: ISA bridge
             product: HM65 Express Chipset Family LPC Controller
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
             product: 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:28 ioport:4088(size=8) ioport:4094(size=4) ioport:4080(size=8) ioport:4090(size=4) ioport:4040(size=32) memory:d4727000-d47277ff
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 840
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: CB6Q
             serial: S1D5NSAFB34881R
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=2933118b
           *-volume
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 0040ed0b-b73a-477a-a5dc-318d4aba1ce5
                size: 111GiB
                capacity: 111GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink 64bit extents ext4 ext2 initialized
                configuration: created=2018-07-02 14:58:50 filesystem=ext4 lastmountpoint=/ modified=2018-07-04 11:36:50 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2018-07-03 19:41:43 state=mounted
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Samsung SSD 850
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sdb
             version: 1B6Q
             serial: S21TNXAG540321X
             size: 111GiB (120GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=a58b927b
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sdb1
                version: 3.1
                serial: 769e-be79
                size: 98MiB
                capacity: 100MiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2016-01-16 03:31:04 filesystem=ntfs label=System Reserved state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sdb2
                version: 3.1
                serial: 52cccea4-b519-b045-9d9c-b60e3c2e6ef7
                size: 111GiB
                capacity: 111GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2016-01-16 03:31:04 filesystem=ntfs state=clean
  *-battery
       product: CC06055
       vendor: 12-42
       physical id: 1
       slot: Primary
       capacity: 55080mWh
       configuration: voltage=10.8V
```

---

### Post by Xian on 2018-07-04
When I've encountered this it's often been a wrong UUID in the either the /boot/grub/grub.cfg or /etc/fstab file.

---

### Post by NM5TF on 2018-07-04
kind of sounds like it's waiting for a start job to finish.....edit the kernel at boot and remove [COLOR="#FF0000"]quiet[/COLOR] 
to see any error messages in red stating "waiting for start job xxxxx to finish"....they usually wait 1 min 30 secs
before they time-out 

if nothing found, compare UUIDs in fstab to what your "system specs" above show as suggested by Xian....have had that
problem before...

good luck

tommy

---

### Post by phosphide on 2018-07-05
The uuid in the lshw output doesn't match the fstab, but updating fstab and/or the grub.cfg file crashes and doesn't let me boot at all. I'll try to remove quiet and see if that works.

---

### Post by phosphide on 2018-07-05
Removing quiet from grub didn't change anything. 

Also, apologize, should have noticed this earlier. I actually do get to the Ubuntu Mate load menu first (the dots that are filling up). So it's making it past grub but then loads and gets stuck, eventually letting me get to the login screen. So something is getting hung up after the initial load.

---

### Post by NM5TF on 2018-07-06
To view system and application logs, you can use the "Log File Viewer" application. Hit F2 to open your dash, then type log and select the Log File Viewer application.

or in a terminal go to [COLOR="#FF0000"]/var/log/syslog[/COLOR] and look for error messages...

tommy

---

### Post by apeitheo2 on 2018-07-06
It looks like you're running kernel 4.15.0-24, which currently has an issue where some systems hang for a while right before getting to the login screen. I don't know if that's the issue you're having but you could give this a try:

```
sudo apt install haveged
sudo systemctl enable haveged
```

More information is available here: [https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140](https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140)

If it's not the issue, it's easy to uninstall haveged.

---

### Post by bodhin2 on 2018-07-06
i read that ubuntu did release an fix for this and advised everyone to runs updates etc. maybe it was on slashdot or most likely tuxmaxhines.

---

### Post by bodhin2 on 2018-07-06
sorry ben really busy and exhausted...

[https://news.softpedia.com/news/canonical-fixes-ubuntu-14-04-lts-regression-causing-boot-failures-on-amd-pcs-521868.shtml](https://news.softpedia.com/news/canonical-fixes-ubuntu-14-04-lts-regression-causing-boot-failures-on-amd-pcs-521868.shtml)
hope this is helpful

---

### Post by bodhin2 on 2018-07-06
[https://lists.ubuntu.com/archives/ubuntu-security-announce/2018-July/004482.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2018-July/004482.html)

---

### Post by phosphide on 2018-07-07
> **apeitheo2 said:**
> It looks like you're running kernel 4.15.0-24, which currently has an issue where some systems hang for a while right before getting to the login screen. I don't know if that's the issue you're having but you could give this a try:

```
sudo apt install haveged
sudo systemctl enable haveged
```

More information is available here: [https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140](https://ubuntuforums.org/showthread.php?t=2395459&page=2&p=13781140#post13781140)

If it's not the issue, it's easy to uninstall haveged.

This did it. Thank you!

Just curious, if you know. Why does installing haveged fix this issue? Seems odd that a random number generator would be the solution.

---


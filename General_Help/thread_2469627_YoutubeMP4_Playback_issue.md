---
title: "Youtube/MP4 Playback issue"
date: 2021-12-04
forum: General Help
---

### Post by iain_crane on 2021-12-04
Hello,

Using a Gigabyte GB-BXBT-2807 (Intel Celeron N2807) on 20.04.

Youtube (Firefox): choppy playback.

MP4: using "Videos" Ubuntu application - choppy. Using VLC - black screen (sound OK).

Any advice appreciated.

Thank you.
[h=1][/h]

---

### Post by Autodave on 2021-12-04
Did you install the "Ubuntu restricted extras"?

---

### Post by iain_crane on 2021-12-04
Hello - I did, but haven't yet rebooted since doing so, if that makes any difference. Thx.

---

### Post by jimmy-frydkaer on 2021-12-04
I never reboot after installing Restricted Exras, that shoukd nor be nessecery.

---

### Post by pqwoerituytrueiwoq on 2021-12-05
have you tried using [youtube-dl]("https://github.com/ytdl-org/youtube-dl") then opening the file is other video players? sometimes smplayer works when vlc does not

i think the issue may be the system lacks the modern instruction sets for cpu decoding and is unable to brute force it being a entry level cpu, but if you can get a video player to use hardware acceleration it should be able to play at least at lower resolutions, usually this trick works with stuff from the ~2005 erra

also possible vlc is not working cause the installed youtube plugin is too old and needs a update 
[https://addons.videolan.org/p/1154080/](https://addons.videolan.org/p/1154080/)

---

### Post by mIk3_08 on 2021-12-05
> **iain_crane said:**
> Hello,

Using a Gigabyte GB-BXBT-2807 (Intel Celeron N2807) on 20.04.
Youtube (Firefox): choppy playback.
MP4: using "Videos" Ubuntu application - choppy. Using VLC - black screen (sound OK).
Any advice appreciated.

Thank you.


Can you show us the result of this command below paste it wrap with code here in thread.
```
sudo lshw
```
and this
```
hostnamectl status
```
Cheers

---

### Post by ActionParsnip on 2021-12-05
Did you try changing the video output method in VLC settings? This can help

---

### Post by iain_crane on 2021-12-05
Hello mike_08,

I have run sudo lshw but the problem is I cannot  copy and paste from XTerm. I'm still searching for a solution to this.  The only thing I can do is paste using Shift-Insert. Any ideas on  that...?

Thanks...

---

### Post by ActionParsnip on 2021-12-05
> **iain_crane said:**
> Hello mike_08,

I have run sudo lshw but the problem is I cannot  copy and paste from XTerm. I'm still searching for a solution to this.  The only thing I can do is paste using Shift-Insert. Any ideas on  that...?

Thanks...

Try
```
 
sudo apt install pastebinit; sudo lshw | pastebinit

```
Then you can type the URL easily. Case is important here

---

### Post by iain_crane on 2021-12-05
Hello - try this URL, I checked it [https://paste.ubuntu.com/p/qJGgMWVRZJ/](https://paste.ubuntu.com/p/qJGgMWVRZJ/)

---

### Post by iain_crane on 2021-12-05
Also getting error "gnome-control-center crashed with SIGSEGV in__find_specmb()" - not sure if this is related...

---

### Post by Impavidus on 2021-12-05
> **iain_crane said:**
> Hello mike_08,

I have run sudo lshw but the problem is I cannot  copy and paste from XTerm. I'm still searching for a solution to this.  The only thing I can do is paste using Shift-Insert. Any ideas on  that...?

Thanks...
Any success using select &#8594; right click &#8594; copy?
Or select &#8594; ctrl+shift+c? Or just select and then paste by clicking the middle mouse button?

---

### Post by iain_crane on 2021-12-05
Thanks Impavidus - "Or just select and then paste by clicking the middle mouse button?" - Worked :P


Output from sudo lshw

```


main-gb-bxbt-2807           
    description: Desktop Computer
    product: GB-BXBT-2807 (To be filled by O.E.M.)
    vendor: GIGABYTE
    version: 1.x
    serial: To be filled by O.E.M.
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=780E27BD-A172-E311-A771-7C00607E0C00
  *-core
       description: Motherboard
       product: MZBAYAP-00
       vendor: GIGABYTE
       physical id: 0
       version: 1.x
       serial: To be filled by O.E.M.
       slot: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: F3
          date: 06/18/2014
          size: 64KiB
          capacity: 5MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: DIMM DDR3 1600 MHz (0.6 ns)
             product: CMSO8GX3M1C1600C11
             vendor: Corsair
             physical id: 0
             serial: 00000000
             slot: A1_DIMM0
             size: 8GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-02-05 00:26+0000Last-Translator: Andi Chandler <Unknown>Language-Team: English (United Kingdom) <en_GB@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2021-08-02 16:47+0000X-Generator: Launchpad (build 8bd362bf86c4b35e805f897f03c203e3576a7006) [empty]
             product: Array1_PartNumber1
             vendor: A1_Manufacturer1
             physical id: 1
             serial: A1_SerNum1
             slot: A1_DIMM1
     *-cache:0
          description: L1 cache
          physical id: 32
          slot: CPU Internal L1
          size: 112KiB
          capacity: 112KiB
          capabilities: internal write-back
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 33
          slot: CPU Internal L2
          size: 1MiB
          capacity: 1MiB
          capabilities: internal write-back unified
          configuration: level=2
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU  N2807  @ 1.58GHz
          vendor: Intel Corp.
          physical id: 34
          bus info: cpu@0
          version: Intel(R) Celeron(R) CPU N2807 @ 1.58GHz
          slot: SOCKET 0
          size: 1999MHz
          capacity: 2400MHz
          width: 64 bits
          clock: 83MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch epb pti ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat md_clear cpufreq
          configuration: cores=2 enabledcores=2 threads=2
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
             resources: irq:95 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f080(size=8) memory:c0000-dffff
        *-sata
             description: SATA controller
             product: Atom Processor E3800 Series SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 0e
             width: 32 bits
             clock: 66MHz
             capabilities: sata msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:92 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:d0815000-d08157ff
        *-usb
             description: USB controller
             product: Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 0e
             width: 64 bits
            clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:91 memory:d0800000-d080ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 5.4.0-91-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 5.04
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb:0
                   description: Bluetooth wireless interface
                   product: Bluetooth Radio
                   vendor: Realtek
                   physical id: 2
                   bus info: usb@1:2
                   version: 2.00
                   serial: 00e04c000001
                   capabilities: bluetooth usb-2.10
                   configuration: driver=btusb maxpower=500mA speed=12Mbit/s
              *-usb:1
                   description: Keyboard
                   product: USB Keyboard
                   vendor: Logitech
                   physical id: 3
                   bus info: usb@1:3
                   version: 64.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=90mA speed=2Mbit/s
              *-usb:2
                   description: Mouse
                   product: USB Optical Mouse
                   vendor: Primax Electronics, Ltd
                   physical id: 4
                   bus info: usb@1:4
                   version: 2.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=2Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 5.4.0-91-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 5.04
                capabilities: usb-3.00
                configuration: driver=hub slots=1 speed=5000Mbit/s
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
             resources: irq:94 memory:d0500000-d05fffff memory:d0400000-d04fffff
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
             resources: irq:96 memory:d0810000-d0813fff
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
             resources: irq:87 ioport:1000(size=4096)
        *-pci:1
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:88 ioport:e000(size=4096) memory:d0700000-d07fffff
           *-network
                description: Wireless interface
                product: RTL8723BE PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                serial: 40:e2:30:03:d8:23
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8723be driverversion=5.4.0-91-generic firmware=N/A ip=192.168.1.80 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:17 ioport:e000(size=256) memory:d0700000-d0703fff
        *-pci:2
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
             resources: irq:89 ioport:d000(size=4096) memory:d0600000-d06fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 0c
                serial: fc:aa:14:16:1f:61
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII
                resources: irq:18 ioport:d000(size=256) memory:d0604000-d0604fff memory:d0600000-d0603fff
        *-pci:3
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
            resources: irq:90 ioport:2000(size=4096)
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
        *-serial
             description: SMBus
             product: Atom Processor E3800 Series SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=i801_smbus latency=0
             resources: irq:18 memory:d0814000-d081401f ioport:f000(size=32)
     *-pnp00:00
          product: PnP device PNP0b00
          physical id: 1
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:01
          product: PnP device PNP0c02
          physical id: 2
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: 3
          capabilities: pnp
          configuration: driver=system
     *-pnp00:03
          product: PnP device PNP0c02
          physical id: 4
          capabilities: pnp
          configuration: driver=system
     *-scsi
          physical id: 5
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SanDisk SDSSDXPS
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 00RL
             serial: 154092401204
             size: 223GiB (240GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=00026ab0
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: abfcbfb1-7d9b-4d62-a414-f955bb5e13e5
                size: 215GiB
                capacity: 215GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2016-04-02 20:13:18 filesystem=ext4 lastmountpoint=/ modified=2021-12-04 17:27:53 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2021-12-04 17:27:54 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 8084MiB
                capacity: 8084MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap volume
                   physical id: 5
                   logical name: /dev/sda5
                   version: 1
                   serial: c8e73d84-8834-4ea9-add3-6d1125eeae56
                   size: 8084MiB
                   capacity: 8084MiB
                   capabilities: nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: virbr0-nic
       serial: 52:54:00:84:b5:1a
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s


```

Output of hostnamectl status

```


 Static hostname: main-GB-BXBT-2807
         Icon name: computer-desktop
           Chassis: desktop
        Machine ID: 3127a8a235ac90737a6422f057001ca3
           Boot ID: d173a599dcfc472fa15537f5d6774ee2
  Operating System: Ubuntu 20.04.3 LTS
            Kernel: Linux 5.4.0-91-generic
      Architecture: x86-64


```

Thanks...

---


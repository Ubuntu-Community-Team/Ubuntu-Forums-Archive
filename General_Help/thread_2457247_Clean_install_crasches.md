---
title: "Clean install crasches"
date: 2021-01-28
forum: General Help
---

### Post by Cadryc on 2021-01-28
I thought I would try to make file a server out of an old computer I have laying around for backing up family photos, important documents, storing ripped cd for play on my reciever over lan, and so on. But it seems my old compi be a wee bit cranky, suppose it might come with old age, or a hardware fault or maybe a software mishap. Back in the the day I assembled 3 identical computer and my parents still run theirs updated to 20.04 without any problems. But the one i kept for myself has been in a cupboard for some years.

I chose the regular Ubuntu 20.04 for ease of use. I am a long time Ubuntu user, I have done my fair share of googling and copypasting terminal commands so I have a basic understanding of the terminal (like not to copy and paste without contemplating the consequences) but gnome is where I live. And now my google skills fail me...

I have done a clean install and immediately on login I am greeted with error reports. After getting all the updates the behavior is still the same, sometimes the gui crashes and I am brought to the login screen (thou I have chosen autologin)

Could anyone here possibly point me in a direction to identify the fault?

How would I go about copying the text of a crash report? I'll just write the Title text here for 3 reports
1 apt_check.py crashed with SIGSEGV in PyTuple_new()
2 gnome-shell assert failure: corrupted double-linked list
3 apport-checkreports crashed with SIGSEGV in PyGC_Collect()

The output from lshw, if you wonder why the pata the answer is I'm saving the sata for plain storage drives (planning 4 drives in raid 5 )
Perhaps there is a fancy terminal command to get the output in english, but i don't think the swedish will slow you savvy people down
```
 beskrivning: Stationär dator
    produkt: G41M-ES2L
    tillverkare: Gigabyte Technology Co., Ltd.
    bredd: 64 bits
    förmågor: smbios-2.4 dmi-2.4 smp vsyscall32
    konfiguration: boot=normal chassis=desktop uuid=00000000-0000-0000-0000-6CF049617977
  *-core
       beskrivning: Moderkort
       produkt: G41M-ES2L
       tillverkare: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x
     *-firmware
          beskrivning: BIOS
          tillverkare: Award Software International, Inc.
          physical id: 0
          version: F9
          date: 06/21/2010
          storlek: 128KiB
          kapacitet: 1MiB
          förmågor: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          beskrivning: Processor
          produkt: Pentium(R) Dual-Core  CPU      E6500  @ 2.93GHz
          tillverkare: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Pentium(R) Dual-Core CPU E6500 @
          plats: Socket 775
          storlek: 2345MHz
          kapacitet: 4GHz
          bredd: 64 bits
          klocka: 266MHz
          förmågor: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl cpuid aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm pti tpr_shadow vnmi flexpriority vpid dtherm cpufreq
        *-cache:0
             beskrivning: L1 cache
             physical id: a
             plats: Internal Cache
             storlek: 64KiB
             kapacitet: 64KiB
             förmågor: synchronous internal write-back
             konfiguration: level=1
        *-cache:1
             beskrivning: L2 cache
             physical id: b
             plats: External Cache
             storlek: 2MiB
             kapacitet: 2MiB
             förmågor: synchronous internal write-back
             konfiguration: level=2
     *-memory
          beskrivning: Systemminne
          physical id: 19
          plats: System board or motherboard
          storlek: 2GiB
        *-bank:0
             beskrivning: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-03-18 21:55+0000Last-Translator: Daniel Nylander <yeager@ubuntu.com>Language-Team: Swedish <sv@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2021-01-21 18:43+0000X-Generator: Launchpad (build 2d1d5e352f0d063d660df2300e31f66bed027fa5) 800 MHz (1,2 ns)
             physical id: 0
             plats: A0
             storlek: 1GiB
             bredd: 64 bits
             klocka: 800MHz (1.2ns)
        *-bank:1
             beskrivning: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-03-18 21:55+0000Last-Translator: Daniel Nylander <yeager@ubuntu.com>Language-Team: Swedish <sv@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2021-01-21 18:43+0000X-Generator: Launchpad (build 2d1d5e352f0d063d660df2300e31f66bed027fa5) [tom]
             physical id: 1
             plats: A1
        *-bank:2
             beskrivning: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-03-18 21:55+0000Last-Translator: Daniel Nylander <yeager@ubuntu.com>Language-Team: Swedish <sv@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2021-01-21 18:43+0000X-Generator: Launchpad (build 2d1d5e352f0d063d660df2300e31f66bed027fa5) 800 MHz (1,2 ns)
             physical id: 2
             plats: A2
             storlek: 1GiB
             bredd: 64 bits
             klocka: 800MHz (1.2ns)
        *-bank:3
             beskrivning: DIMMProject-Id-Version: lshwReport-Msgid-Bugs-To: FULL NAME <EMAIL@ADDRESS>PO-Revision-Date: 2012-03-18 21:55+0000Last-Translator: Daniel Nylander <yeager@ubuntu.com>Language-Team: Swedish <sv@li.org>MIME-Version: 1.0Content-Type: text/plain; charset=UTF-8Content-Transfer-Encoding: 8bitX-Launchpad-Export-Date: 2021-01-21 18:43+0000X-Generator: Launchpad (build 2d1d5e352f0d063d660df2300e31f66bed027fa5) [tom]
             physical id: 3
             plats: A3
     *-pci
          beskrivning: Host bridge
          produkt: 4 Series Chipset DRAM Controller
          tillverkare: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          bredd: 32 bits
          klocka: 33MHz
        *-display
             beskrivning: VGA compatible controller
             produkt: 4 Series Chipset Integrated Graphics Controller
             tillverkare: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             bredd: 64 bits
             klocka: 33MHz
             förmågor: msi pm vga_controller bus_master cap_list rom
             konfiguration: driver=i915 latency=0
             resurser: irq:16 memory:fd800000-fdbfffff memory:d0000000-dfffffff ioport:ff00(storlek=8) memory:c0000-dffff
        *-multimedia
             beskrivning: Audio device
             produkt: NM10/ICH7 Family High Definition Audio Controller
             tillverkare: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             bredd: 64 bits
             klocka: 33MHz
             förmågor: pm msi pciexpress bus_master cap_list
             konfiguration: driver=snd_hda_intel latency=0
             resurser: irq:27 memory:fdff8000-fdffbfff
        *-pci:0
             beskrivning: PCI bridge
             produkt: NM10/ICH7 Family PCI Express Port 1
             tillverkare: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             bredd: 32 bits
             klocka: 33MHz
             förmågor: pci pciexpress msi pm normal_decode bus_master cap_list
             konfiguration: driver=pcieport
             resurser: irq:24 ioport:1000(storlek=4096) memory:7bd00000-7befffff ioport:80000000(storlek=2097152)
        *-pci:1
             beskrivning: PCI bridge
             produkt: NM10/ICH7 Family PCI Express Port 2
             tillverkare: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             bredd: 32 bits
             klocka: 33MHz
             förmågor: pci pciexpress msi pm normal_decode bus_master cap_list
             konfiguration: driver=pcieport
             resurser: irq:25 ioport:d000(storlek=4096) memory:fdd00000-fddfffff ioport:fde00000(storlek=1048576)
           *-network
                beskrivning: Ethernet interface
                produkt: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                tillverkare: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logiskt namn: enp2s0
                version: 02
                serienummer: 6c:f0:49:61:79:77
                storlek: 100Mbit/s
                kapacitet: 1Gbit/s
                bredd: 64 bits
                klocka: 33MHz
                förmågor: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                konfiguration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.8.0-40-generic duplex=full ip=192.168.1.149 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
                resurser: irq:17 ioport:de00(storlek=256) memory:fdeff000-fdefffff memory:fdee0000-fdeeffff memory:fdd00000-fdd0ffff
        *-usb:0
             beskrivning: USB controller
             produkt: NM10/ICH7 Family USB UHCI Controller #1
             tillverkare: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             bredd: 32 bits
             klocka: 33MHz
             förmågor: uhci bus_master
             konfiguration: driver=uhci_hcd latency=0
             resurser: irq:23 ioport:fe00(storlek=32)
           *-usbhost
                produkt: UHCI Host Controller
                tillverkare: Linux 5.8.0-40-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logiskt namn: usb2
                version: 5.08
                förmågor: usb-1.10
                konfiguration: driver=hub slots=2 speed=12Mbit/s
              *-usb:0
                   beskrivning: Mus
                   produkt: USB Receiver
                   tillverkare: Logitech
                   physical id: 1
                   bus info: usb@2:1
                   version: 5.00
                   förmågor: usb-2.00
                   konfiguration: driver=usbhid maxpower=98mA speed=12Mbit/s
              *-usb:1
                   beskrivning: Tangentbord
                   produkt: USB Keyboard
                   tillverkare: NOVATEK
                   physical id: 2
                   bus info: usb@2:2
                   version: 1.12
                   förmågor: usb-1.10
                   konfiguration: driver=usbhid maxpower=100mA speed=1Mbit/s
        *-usb:1
             beskrivning: USB controller
             produkt: NM10/ICH7 Family USB UHCI Controller #2
             tillverkare: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             bredd: 32 bits
             klocka: 33MHz
             förmågor: uhci bus_master
             konfiguration: driver=uhci_hcd latency=0
             resurser: irq:19 ioport:fd00(storlek=32)
           *-usbhost
                produkt: UHCI Host Controller
                tillverkare: Linux 5.8.0-40-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logiskt namn: usb3
                version: 5.08
                förmågor: usb-1.10
                konfiguration: driver=hub slots=2 speed=12Mbit/s
        *-usb:2
             beskrivning: USB controller
             produkt: NM10/ICH7 Family USB UHCI Controller #3
             tillverkare: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             bredd: 32 bits
             klocka: 33MHz
             förmågor: uhci bus_master
             konfiguration: driver=uhci_hcd latency=0
             resurser: irq:18 ioport:fc00(storlek=32)
           *-usbhost
                produkt: UHCI Host Controller
                tillverkare: Linux 5.8.0-40-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logiskt namn: usb4
                version: 5.08
                förmågor: usb-1.10
                konfiguration: driver=hub slots=2 speed=12Mbit/s
        *-usb:3
             beskrivning: USB controller
             produkt: NM10/ICH7 Family USB UHCI Controller #4
             tillverkare: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             bredd: 32 bits
             klocka: 33MHz
             förmågor: uhci bus_master
             konfiguration: driver=uhci_hcd latency=0
             resurser: irq:16 ioport:fb00(storlek=32)
           *-usbhost
                produkt: UHCI Host Controller
                tillverkare: Linux 5.8.0-40-generic uhci_hcd
                physical id: 1
                bus info: usb@5
                logiskt namn: usb5
                version: 5.08
                förmågor: usb-1.10
                konfiguration: driver=hub slots=2 speed=12Mbit/s
        *-usb:4
             beskrivning: USB controller
             produkt: NM10/ICH7 Family USB2 EHCI Controller
             tillverkare: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             bredd: 32 bits
             klocka: 33MHz
             förmågor: pm ehci bus_master cap_list
             konfiguration: driver=ehci-pci latency=0
             resurser: irq:23 memory:fdfff000-fdfff3ff
           *-usbhost
                produkt: EHCI Host Controller
                tillverkare: Linux 5.8.0-40-generic ehci_hcd
                physical id: 1
                bus info: usb@1
                logiskt namn: usb1
                version: 5.08
                förmågor: usb-2.00
                konfiguration: driver=hub slots=8 speed=480Mbit/s
        *-pci:2
             beskrivning: PCI bridge
             produkt: 82801 PCI Bridge
             tillverkare: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             bredd: 32 bits
             klocka: 33MHz
             förmågor: pci subtractive_decode cap_list
        *-isa
             beskrivning: ISA bridge
             produkt: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             tillverkare: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             bredd: 32 bits
             klocka: 33MHz
             förmågor: isa bus_master cap_list
             konfiguration: driver=lpc_ich latency=0
             resurser: irq:0
        *-ide:0
             beskrivning: IDE interface
             produkt: 82801G (ICH7 Family) IDE Controller
             tillverkare: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             bredd: 32 bits
             klocka: 33MHz
             förmågor: ide isa_compat_mode pci_native_mode bus_master
             konfiguration: driver=ata_piix latency=0
             resurser: irq:18 ioport:1f0(storlek=8) ioport:3f6 ioport:170(storlek=8) ioport:376 ioport:f800(storlek=16)
        *-ide:1
             beskrivning: IDE interface
             produkt: NM10/ICH7 Family SATA Controller [IDE mode]
             tillverkare: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             bredd: 32 bits
             klocka: 66MHz
             förmågor: ide pm isa_compat_mode pci_native_mode bus_master cap_list
             konfiguration: driver=ata_piix latency=0
             resurser: irq:19 ioport:f700(storlek=8) ioport:f600(storlek=4) ioport:f500(storlek=8) ioport:f400(storlek=4) ioport:f300(storlek=16)
        *-serial
             beskrivning: SMBus
             produkt: NM10/ICH7 Family SMBus Controller
             tillverkare: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             bredd: 32 bits
             klocka: 33MHz
             konfiguration: driver=i801_smbus latency=0
             resurser: irq:19 ioport:500(storlek=32)
     *-pnp00:00
          produkt: PnP device PNP0c02
          physical id: 1
          förmågor: pnp
          konfiguration: driver=system
     *-pnp00:01
          produkt: PnP device PNP0b00
          physical id: 2
          förmågor: pnp
          konfiguration: driver=rtc_cmos
     *-pnp00:02
          produkt: PnP device PNP0501
          physical id: 3
          förmågor: pnp
          konfiguration: driver=serial
     *-pnp00:03
          produkt: PnP device PNP0501
          physical id: 5
          förmågor: pnp
          konfiguration: driver=serial
     *-pnp00:04
          produkt: PnP device PNP0400
          physical id: 6
          förmågor: pnp
          konfiguration: driver=parport_pc
     *-pnp00:05
          produkt: PnP device PNP0c02
          physical id: 7
          förmågor: pnp
          konfiguration: driver=system
     *-pnp00:06
          produkt: PnP device PNP0c02
          physical id: 8
          förmågor: pnp
          konfiguration: driver=system
     *-pnp00:07
          produkt: PnP device PNP0c01
          physical id: 9
          förmågor: pnp
          konfiguration: driver=system
     *-scsi:0
          physical id: a
          logiskt namn: scsi0
          förmågor: emulated
        *-disk
             beskrivning: ATA Disk
             produkt: ST3120026A
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logiskt namn: /dev/sda
             version: 3.06
             serienummer: 3JT2ES2X
             storlek: 111GiB (120GB)
             förmågor: gpt-1.00 partitioned partitioned:gpt
             konfiguration: ansiversion=5 guid=9b8c9692-9bc0-4430-ba90-75e20f1776ec logicalsectorsize=512 sectorsize=512
           *-volume:0
                beskrivning: Linux swap volym
                tillverkare: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logiskt namn: /dev/sda1
                version: 1
                serienummer: 056e27ee-a0dd-46d5-ae26-f04670f55df4
                storlek: 4095MiB
                kapacitet: 4095MiB
                förmågor: nofs swap initialized
                konfiguration: filesystem=swap pagesize=4095
           *-volume:1
                beskrivning: EXT4-volym
                tillverkare: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logiskt namn: /dev/sda2
                logiskt namn: /
                version: 1.0
                serienummer: daec6397-a553-4b39-9ddd-c83c6f222ecf
                storlek: 107GiB
                kapacitet: 107GiB
                förmågor: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                konfiguration: created=2020-12-13 18:29:14 filesystem=ext4 lastmountpoint=/ modified=2021-01-28 18:30:27 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2021-01-28 18:30:33 state=mounted

```

---

### Post by Cadryc on 2021-01-29
I can add this pequliar thing which I get when running sudo apt update && apt upgrade first thing after boot

```
sudo apt update && apt upgrade
[sudo] lösenord för ###########: 
...
...
...
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?


```

---


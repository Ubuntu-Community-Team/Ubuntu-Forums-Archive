---
title: "update install problems"
date: 2017-06-12
forum: General Help
---

### Post by oldsoundguy on 2017-06-12
Yesterday (Sunday-11th) I updated my 14.04 to 16.04 and now am having issues.  Mostly with poor response with my Logitech wireless trackball and with screens FREEZING and washing to GREY! (requiring the three finger salute and re-booting!)

Would a re-install clean this up or am i SCREWED?

---

### Post by ajgreeny on 2017-06-12
With the info you have given us there is no way to know how to help you.

What hardware do you have?
Tell us as much detail as you can and we may have some suggestions, however you can also try a live system of 16.04 to see if that runs without problems; if so then your upgrade may be the problem and a clean install may solve this for you.

---

### Post by oldsoundguy on 2017-06-12
Running an old semi home brew HP.  It worked great on 14.04 and 12.04 and 10.04.  This 16.04 is dodgy right now.  It works and then it just STOPS, screen turns to grey overcast, and sometimes comes back but occasionally freezes requiring the old 3 finger salute.  And it takes FOREVER (it seems) to launch anything from the dock!

This is my primary machine and I have a lot of "stuff" set up on it ... would hate to lose and have to re-do everything .. and not sure of how to get the info of every thing I have on it ..  Printers (3 of them) and I would need a list of everything I have before I could wipe and start over.  I have become complacent with the stability over the years and the thought of starting all over is a tad daunting.

---

### Post by oldsoundguy on 2017-06-12
Looks to be a SCRIPTING problem .. it does not like some scripts, especially on EBAY! ..... but here is the lshw:

```
dave-desktop-mediaroom    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2005MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.20GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          size: 3200MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82915G/P/GV/GL/PL/910GL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 04
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:cfd00000-cfd7ffff ioport:3800(size=8) memory:e0000000-efffffff memory:cfd80000-cfdbffff
        *-pci:0
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:4000(size=4096) memory:f0000000-f01fffff ioport:f0500000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:7000(size=4096) memory:f0200000-f04fffff ioport:f0700000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:40:00.0
                logical name: eth1
                version: 01
                serial: 00:13:21:00:1f:f3
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5751-v3.29a ip=10.0.0.2 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
                resources: irq:17 memory:f0400000-f040ffff
        *-usb:0
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:3440(size=32)
        *-usb:1
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:3460(size=32)
        *-usb:2
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:3480(size=32)
        *-usb:3
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:34a0(size=32)
        *-usb:4
             description: USB controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:20 memory:cfdc0000-cfdc03ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:1000(size=4096)
           *-multimedia
                description: Multimedia audio controller
                product: SB Live! EMU10k1
                vendor: Creative Labs
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=snd_emu10k1 latency=32 maxlatency=20 mingnt=2
                resources: irq:16 ioport:1000(size=32)
           *-input
                description: Input device controller
                product: SB Live! Game Port
                vendor: Creative Labs
                physical id: 4.1
                bus info: pci@0000:05:04.1
                version: 07
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Emu10k1_gameport latency=32
                resources: irq:0 ioport:1020(size=8)
        *-isa
             description: ISA bridge
             product: 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:34e0(size=16)
        *-ide:1
             description: IDE interface
             product: 82801FB/FW (ICH6/ICH6W) SATA Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:3818(size=8) ioport:3830(size=4) ioport:3820(size=8) ioport:3834(size=4) ioport:34f0(size=16)
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-cdrom:0
             description: DVD reader
             product: COMBO SOHC-4832K
             vendor: LITE-ON
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: OQKB
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
        *-cdrom:1
             description: DVD writer
             product: DVDRW SHW-160H6S
             vendor: LITE-ON
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr1
             version: CS08
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
  *-scsi
       physical id: 1
       bus info: scsi@4
       logical name: scsi4
       capabilities: scsi-host
       configuration: driver=usb-storage
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
dave@dave-desktop-mediaroom:~$
```

---

### Post by oldsoundguy on 2017-06-13
Now, IT APPEARS that the problem has fixed itself!  Have NO IDEA what was amiss, but a couple of re-boots and there is the indication that normalcy has re-appeared.  Will NOT hold my breath, but, as of right now, things seem OK .. with the minor exception that the track ball has become super sensitive.

I DO like the fact that the scroll bars are now COLORED!

---


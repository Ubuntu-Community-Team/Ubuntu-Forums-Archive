---
title: "i've installed a fresh ubuntu (16.10) and it's freezing often"
date: 2017-03-24
forum: General Help
---

### Post by ronjjjg8885 on 2017-03-24
maybe it is because of the new chrome update?

anyhow
it is freezing my whole desktop for long periods

edit:
it is not because of chromium (title edited)

---

### Post by ronjjjg8885 on 2017-03-25
any help?
it is so annoying

---

### Post by howefield on 2017-03-25
You could try going into Chromium settings > Show Advanced Settings and then deselect "*Use hardware acceleration when available*"

---

### Post by ronjjjg8885 on 2017-03-25
i will wait to see if it has helped

---

### Post by howefield on 2017-03-25
I'm sure you already have, just make sure that you have now restarted the browser after deselecting that option so that it can take effect..

---

### Post by ronjjjg8885 on 2017-03-25
yes. chromium told me to do so
thanks,

---

### Post by ronjjjg8885 on 2017-03-25
heyy again
the problem persist.
my computer still freezing often. i think it is only while chromium opened
how can i fix this?

in 16.04 it was fine with many opened tabs

edit:
it happens when minimizing the chromium window

---

### Post by mörgæs on 2017-03-26
Which hardware are you using?

---

### Post by ronjjjg8885 on 2017-03-26
ideapad 510S

---

### Post by RobGoss on 2017-03-26
Please post the specs for your machine it will others give you the best possible advice in order to see what the problem may be


-Brand name and model
-CPU
-RAM (size)
-Graphics chip/card
-Wifi chip/card

---

### Post by ronjjjg8885 on 2017-03-26
it's a laptop
it's the Lenovo Ideapad 510S-14 80TK00B3IV

i don't know the specifications

---

### Post by RobGoss on 2017-03-26
Please try runing the following command this will display your hardware information it will help us trouble shoot your issue. When you run this command** CCP** the output and use the **code tags** to post your results

Command: 
```
 lshw 
```

---

### Post by ronjjjg8885 on 2017-03-26
```
ron@ron-Lenovo-ideapad-510S:~$ sudo lshw[sudo] password for ron: 
ron-lenovo-ideapad-510s     
    description: Notebook
    product: 80TK (LENOVO_MT_80TK_BU_idea_FM_Lenovo ideapad 510S-14ISK)
    vendor: LENOVO
    version: Lenovo ideapad 510S-14ISK
    serial: MP15XVWU
    width: 64 bits
    capabilities: smbios-2.8 dmi-2.8 smp vsyscall32
    configuration: administrator_password=enabled boot=normal chassis=notebook family=IDEAPAD frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=LENOVO_MT_80TK_BU_idea_FM_Lenovo ideapad 510S-14ISK uuid=492A932F-AB80-E611-B27E-1C3947ED8EAD
  *-core
       description: Motherboard
       product: Lenovo ideapad 5
       vendor: LENOVO
       physical id: 0
       version: SDK0J40709 WIN
       serial: MP15XVWU
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 0VCN21WW(V1.05)
          date: 08/31/2016
          size: 128KiB
          capacity: 6080KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i3-6100U CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i3-6100U CPU @ 2.30GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 2300MHz
          capacity: 4005MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 6
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 7
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 8
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-cache
          description: L1 cache
          physical id: 5
          slot: L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 26
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous 2133 MHz (0.5 ns)
             product: M471A1K43BB0-CPB
             vendor: Samsung
             physical id: 0
             serial: 22111059
             slot: ChannelA-DIMM0
             size: 8GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:1
             description: [empty]
             physical id: 1
             slot: ChannelA-DIMM1
        *-bank:2
             description: [empty]
             physical id: 2
             slot: ChannelB-DIMM0
        *-bank:3
             description: [empty]
             physical id: 3
             slot: ChannelB-DIMM1
     *-pci
          description: Host bridge
          product: Skylake Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 08
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: HD Graphics 520
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:126 memory:b1000000-b1ffffff memory:a0000000-afffffff ioport:5000(size=64) memory:c0000-dffff
        *-usb
             description: USB controller
             product: Sunrise Point-LP USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:122 memory:b3300000-b330ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.8.0-41-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.08
                capabilities: usb-2.00
                configuration: driver=hub slots=12 speed=480Mbit/s
              *-usb:0
                   description: Keyboard
                   product: RAPOO 5G Wireless Device
                   vendor: RAPOO
                   physical id: 2
                   bus info: usb@1:2
                   version: 10.01
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=200mA speed=12Mbit/s
              *-usb:1
                   description: Bluetooth wireless interface
                   vendor: Atheros Communications, Inc.
                   physical id: 7
                   bus info: usb@1:7
                   version: 0.01
                   capabilities: bluetooth usb-2.01
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.8.0-41-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.08
                capabilities: usb-3.00
                configuration: driver=hub slots=6 speed=5000Mbit/s
        *-generic
             description: Signal processing controller
             product: Sunrise Point-LP Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:b332a000-b332afff
        *-communication
             description: Communication controller
             product: Sunrise Point-LP CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:127 memory:b332b000-b332bfff
        *-storage
             description: SATA controller
             product: Sunrise Point-LP SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:123 memory:b3328000-b3329fff memory:b332e000-b332e0ff ioport:5080(size=8) ioport:5088(size=4) ioport:5060(size=32) memory:b332c000-b332c7ff
        *-pci:0
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #5
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:4000(size=4096) memory:b3200000-b32fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: enp1s0
                version: 15
                serial: 1c:39:47:ed:8e:ad
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:125 ioport:4000(size=256) memory:b3204000-b3204fff memory:b3200000-b3203fff
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 memory:b3000000-b31fffff
           *-network
                description: Wireless interface
                product: QCA9377 802.11ac Wireless Network Adapter
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 30
                serial: cc:b0:da:f6:3b:cb
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath10k_pci driverversion=4.8.0-41-generic firmware=WLAN.TF.1.0-00267-1 ip=192.168.1.137 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:128 memory:b3000000-b31fffff
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #9
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:3000(size=4096) memory:b2000000-b2ffffff ioport:b0000000(size=16777216)
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:124 memory:b2000000-b2000fff
        *-isa
             description: ISA bridge
             product: Sunrise Point-LP LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory
             description: Memory controller
             product: Sunrise Point-LP PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             configuration: driver=intel_pmc_core latency=0
             resources: irq:0 memory:b3324000-b3327fff
        *-multimedia
             description: Audio device
             product: Sunrise Point-LP HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:129 memory:b3320000-b3323fff memory:b3310000-b331ffff
        *-serial UNCLAIMED
             description: SMBus
             product: Sunrise Point-LP SMBus
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 21
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b332d000-b332d0ff ioport:5040(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: SAMSUNG MZYTY256
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 1L1Q
             serial: S30XNYAH719283
             size: 238GiB (256GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=19881920-1dd3-4349-95c4-7fcd1c5e6bd9 logicalsectorsize=512 sectorsize=512
           *-volume:0
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot/efi
                version: FAT32
                serial: 4018-390e
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro name=EFI System Partition state=mounted
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: 9842091b-5e1d-49ea-846e-d80cb88f5ec9
                size: 230GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2017-03-24 19:40:09 filesystem=ext4 lastmountpoint=/ modified=2017-03-25 15:53:54 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-03-25 15:53:54 state=mounted
           *-volume:2
                description: Linux swap volume
                vendor: Linux
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 1
                serial: 88e60f6e-741e-49d2-adae-5f966fe891f3
                size: 8043MiB
                capacity: 8044MiB
                capabilities: nofs precious readonly hidden nomount swap initialized
                configuration: filesystem=swap pagesize=4095
  *-battery
       description: Zinc Air Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 08/08/2010
       serial: Battery 0
       slot: Fake
  *-power UNCLAIMED
       description: OEM Define 1
       product: OEM Define 5
       vendor: OEM Define 2
       physical id: 2
       version: OEM Define 6
       serial: OEM Define 3
       capacity: 75mWh



```

---

### Post by vasa1 on 2017-03-26
> **ronjjjg8885 said:**
> heyy again
the problem persist.
my computer still freezing often. i think it is only while chromium opened
how can i fix this?

in 16.04 it was fine with many opened tabs

edit:
it happens when minimizing the chromium windowDoes it happen **only** when minimizing the chromium window?

---

### Post by ronjjjg8885 on 2017-03-26
yesterday it even happened with firefox too. and mostly when trying to minimize

so no

---

### Post by dragonfly41 on 2017-03-26
For some time I have been plagued with freezing in Ubuntu 14.04.
Often freezing several times daily requiring reboot.

I read advice from @howefield in post#3 and on checking I realised that I had hardware acceleration on.
I thought that it was off.
I unchecked this and so far after a day of usage I have had no further freezes.  
Time will tell. Thanks @howefield.

Now to OP's freezing problem.

In searching around for solutions to my previous freeze problem I had listed a few experiments to try.

Here is one I found ...

[https://github.com/l3ib/nitrogen/issues/51](https://github.com/l3ib/nitrogen/issues/51)

Install dconf editor

Launch dconf editor and navigate to /org/gnome/desktop/background/show-desktop-icons true

Check that this is set to true.

...

Sometimes a workaround to get out of freeze without reboot is to hit Ctrl+Alt+F1 to get into terminal.
Then immediately switch back to Ctrl+Alt+F7 to restore desktop.

...

[Later edit]

OP can try using gnome flashback instead of Unity.

[http://www.debugpoint.com/2016/04/install-classic-gnome-flashback-in-ubuntu-16-04-replacing-unity/#](http://www.debugpoint.com/2016/04/install-classic-gnome-flashback-in-ubuntu-16-04-replacing-unity/#)


See this reference to Unity bug ... I don't know if it has been fixed or still valid.
[URL="https://www.linuxonlinehelp.de/2016/01/ubuntu-unity-bug-minimize-windows-freeze-unity-desktop-15-04/"]
https://www.linuxonlinehelp.de/2016/01/ubuntu-unity-bug-minimize-windows-freeze-unity-desktop-15-04/[/URL]

---

### Post by vasa1 on 2017-03-26
> **ronjjjg8885 said:**
> yesterday it even happened with firefox too. ...
In that case, you may want to get a better idea of what all is affected so that people don't focus on one thing (which may be an effect rather than the cause) exclusively.

You may also consider another title for your thread. If you want to change it but don't know how to do so, please click the report button and make your suggestion known there.

---

### Post by ronjjjg8885 on 2017-03-27
ok
i will change the title
today my ubuntu havn't froze so maybe i should wait and see what's happening later

thank you forr the help until now

---


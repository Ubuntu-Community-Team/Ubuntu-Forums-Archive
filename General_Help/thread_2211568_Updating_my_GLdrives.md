---
title: "Updating my GLdrives"
date: 2014-03-16
forum: General Help
---

### Post by duckfeeder105.5 on 2014-03-16
Hello,

I have already posted this before but I want to bring it up, again.

I have a TOSHIBA laptop and I am trying to play garry's mod.

The GL verison I have is this: OpenGL version string: 1.4 Mesa 9.2.1. Is there any way to update this? My friend said I have to atleast have openGL 3.0 or something...

Oh and I have xubuntu installed.

Please tell me if i need to acquire more information. Thanks.

---

### Post by slooksterpsv on 2014-03-16
What kind of Toshiba laptop - what's the graphics on the system?

EDIT: I think I found where you got the GL Version from was it from glxinfo? If so that's not relevent to what your graphics card may or may not support. You can run **glxgears -info | grep VERSION** to see what verson your graphics is running.

e.g.
```

shawn@shawn-Satellite-C75D-A:~$ glxgears -info | grep VERSION
GL_VERSION    = 4.3.12795 Compatibility Profile Context 13.35.1005

```

---

### Post by duckfeeder105.5 on 2014-03-16
Shall I post the output(s) here?

Edit: This gear popped up and this is all what showed up in terminal after waiting a few...

GL_VERSION    = 1.4 Mesa 9.2.1
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 19906 requests (19906 known processed) with 0 events remaining.

---

### Post by slooksterpsv on 2014-03-16
Yeah just put it in the code brackets where code is between the braces []. I don't know how to type it out without it trying to render it.

EDIT: [_code_]<content here>[_/code_] - remove the underscores but put the content where it says <content here>

---

### Post by duckfeeder105.5 on 2014-03-16
Hello,

All I get is :

```
fonzie@Fonzie:~$ glxgears -info | grep VERSIONGL_VERSION    = 1.4 Mesa 9.2.1
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1518 requests (1518 known processed) with 0 events remaining.
fonzie@Fonzie:~$ 
```

---

### Post by slooksterpsv on 2014-03-16
What kind of toshiba laptop?

Try: lspci | grep VGA

EDIT: Have you checked for additional drivers in Software Center under Edit -> Software Sources... -> Additional Drivers tab

---

### Post by duckfeeder105.5 on 2014-03-16
Hello,

Here is the output:

```
fonzie@Fonzie:~$ lspci | grep VGA00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
```

edit: Also, my friend has the exact same laptop (sort of), he can run garrys mod, but mine can't

---

### Post by slooksterpsv on 2014-03-16
If you could tell me the specific Toshiba laptop you have that'd be great.

---

### Post by slooksterpsv on 2014-03-16
I suspect it has a GMA3150 graphics chipset, which only supports OpenGL 1.4. Which won't run OpenGL 3.0 software.

---

### Post by duckfeeder105.5 on 2014-03-16
It's a small laptop... That's basically all the info I can give you, sorry!

---

### Post by duckfeeder105.5 on 2014-03-16
Hello,

I had a family member come over(who is good with Computers, luckily!)

He told me to do this...

Here is the output:

```
fonzie@Fonzie:~$ sudo lshw[sudo] password for fonzie: 
fonzie                    
    description: Notebook
    product: TOSHIBA NB255 (012345678912345678912345678)
    vendor: TOSHIBA
    version: PLL2PU-00901L
    serial: 5A374840K
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=1 family=ABCDEFGHIJKLMNOPQRSTUVWXYZ sku=012345678912345678912345678 uuid=12E2D017-604D-11DF-BD78-88AE1D3FAF70
  *-core
       description: Motherboard
       product: PAV10 DDR2
       vendor: TOSHIBA
       physical id: 0
       version: 1.00
       serial: 0123456789AB
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.90
          date: 07/09/2012
          size: 99KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppytoshiba int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Atom(TM) CPU N455   @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.12.10
          serial: 0001-06CA-0000-0000-0000-0000
          slot: U2E1
          size: 1GHz
          capacity: 2048MHz
          width: 64 bits
          capabilities: x86-64 boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm dtherm cpufreq
          configuration: cores=1 enabledcores=1 id=0 threads=2
        *-cache
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: M1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR Synchronous 667 MHz (1.5 ns) [empty]
             physical id: 1
             slot: M2
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:f0200000-f027ffff ioport:18d0(size=8) memory:d0000000-dfffffff memory:f0000000-f00fffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0280000-f02fffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:f0300000-f0303fff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:3000(size=4096) memory:80000000-801fffff ioport:80200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:4000(size=4096) memory:f0100000-f01fffff ioport:80400000(size=2097152)
           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Qualcomm Atheros
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlan0
                version: 01
                serial: 00:26:4d:b0:06:f8
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.11.0-18-generic firmware=N/A ip=192.168.1.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f0100000-f010ffff
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:80600000-809fffff ioport:f0500000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 05
                serial: 88:ae:1d:3f:af:70
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:2000(size=256) memory:f050c000-f050cfff memory:f0508000-f050bfff
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:80a00000-80a003ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
        *-isa
             description: ISA bridge
             product: NM10 Family LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: NM10/ICH7 Family SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:18e8(size=8) ioport:18dc(size=4) ioport:18e0(size=8) ioport:18d8(size=4) ioport:18c0(size=16) memory:80a00400-80a007ff
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18a0(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MK2565GS
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: GJ00
             serial: 30CBB227B
             size: 232GiB (250GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=00053a21
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: e78a3573-706a-493f-a6ad-8f6582c187c6
                size: 230GiB
                capacity: 230GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2014-03-03 12:49:32 filesystem=ext4 lastmountpoint=/ modified=2014-03-16 16:26:02 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-03-16 16:26:02 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 2036MiB
                capacity: 2036MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 2036MiB
                   capabilities: nofs
  *-battery
       description: Lithium Ion Battery
       product: PA3395U
       vendor: TOSHIBA
       physical id: 1
       version: 12/01/2005
       serial: 3658Q
       slot: 1st Battery
       capacity: 31500mWh
       configuration: voltage=14.8V

```

---

### Post by slooksterpsv on 2014-03-16
Not a problem. It looks like your system only supports opengl 1.4 which won't run Garry's Mod AFAIK. Sorry.

---

### Post by duckfeeder105.5 on 2014-03-16
Ah, well... damn. Luckly my B-day is comin' up and I'm getting a custom built PC...

Thanks for the help

---

### Post by pqwoerituytrueiwoq on 2014-03-16
> **duckfeeder105.5 said:**
> Ah, well... damn. Luckly my B-day is comin' up and I'm getting a custom built PC...

Thanks for the helpcongrats on that, i would like to build it, it is fun
latest OpenGL is version 4.4
```
$ glxinfo | grep -i VERSION
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
OpenGL core profile version string: 4.3.0 NVIDIA 331.20
OpenGL core profile shading language version string: 4.30 NVIDIA via Cg compiler
OpenGL version string: 4.4.0 NVIDIA 331.20
OpenGL shading language version string: 4.40 NVIDIA via Cg compiler
```
if you are going to build it your self if you tell me your budget and intended use i can pick parts out at newegg

---

### Post by duckfeeder105.5 on 2014-03-17
Hi,

No thank you. But thanks for asking. :)

---


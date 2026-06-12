---
title: "Touch screen not working on Lenovo Ideapad Yoga 11s with fresh install 18.04.1 LTS"
date: 2019-02-02
forum: General Help
---

### Post by gtwboogie on 2019-02-02
Hello,

I've just got an old Yoga without a system so I've figured that Ubuntu would be the way to go. Most of the stuff worked out of the box more or less but I can't get touchscreen to work...

I've tried to follow instructions found on the wiki - they are for an older distro and didn't do much... - [https://wiki.ubuntu.com/Touchscreen](https://wiki.ubuntu.com/Touchscreen). Searching this forum didn't give me any real answers.

Maybe someone here could guide me through this problem?

lsusb gives me:
```

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 2047:0855 Texas Instruments Invensense Embedded MotionApp HID Sensor
Bus 002 Device 003: ID 0bda:1724 Realtek Semiconductor Corp. RTL8723AU 802.11n WLAN Adapter
Bus 002 Device 002: ID 04f2:b35e Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lspci:
```

0:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Device 0a1e (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:04.0 Signal processing controller: Intel Corporation Haswell-ULT Thermal Subsystem (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 8 Series Thermal (rev 04)

```

xinput
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera: Lenovo EasyC             id=9    [slave  keyboard (3)]
    &#8627; Ideapad extra buttons                       id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

```

sudo lshw
```

    description: Notebook
    product: 20246 (LENOVO_MT_20246)
    vendor: LENOVO
    version: Lenovo IdeaPad Yoga 11S
    serial: 1010896401984
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=IDEAPAD frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=LENOVO_MT_20246 uuid=8260FC45-8867-E311-AC66-28D24447F5B4
  *-core
       description: Motherboard
       product: Yoga2
       vendor: LENOVO
       physical id: 0
       version: 31900058STD
       serial: YB01719466
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 8FCN36WW(V1.03)
          date: 10/08/2013
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-4210Y CPU @ 1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i5-4210Y CPU @ 1.50GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 1772MHz
          capacity: 1900MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid xsaveopt dtherm ida arat pln pts flush_l1d cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: b
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back instruction
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: c
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: d
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-cache
          description: L1 cache
          physical id: a
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-back data
          configuration: level=1
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 0
             serial: Empty
             slot: DIMM0
        *-bank:1
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 1
             serial: Empty
             slot: DIMM1
        *-bank:2
             description: SODIMM DDR3 Synchronous 1600 MHz (0,6 ns)
             product: RMT3170EB68F9W1600
             vendor: Unknown
             physical id: 2
             serial: 40E0CC5F
             slot: DIMM2
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:3
             description: DIMM [empty]
             product: Empty
             vendor: Empty
             physical id: 3
             serial: Empty
             slot: DIMM3
     *-pci
          description: Host bridge
          product: Haswell-ULT DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0b
          width: 32 bits
          clock: 33MHz
          configuration: driver=hsw_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0b
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:b0000000-b03fffff memory:a0000000-afffffff ioport:3000(size=64) memory:c0000-dffff
        *-multimedia:0
             description: Audio device
             product: Haswell-ULT HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0b
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:55 memory:b0418000-b041bfff
        *-generic:0
             description: Signal processing controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 0b
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:b0410000-b0417fff
        *-usb:0
             description: USB controller
             product: 8 Series USB xHCI HC
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:40 memory:b0400000-b040ffff
        *-communication
             description: Communication controller
             product: 8 Series HECI #0
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:43 memory:b0420000-b042001f
        *-multimedia:1
             description: Audio device
             product: 8 Series HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:54 memory:b041c000-b041ffff
        *-usb:1
             description: USB controller
             product: 8 Series USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:b0424000-b04243ff
        *-isa
             description: ISA bridge
             product: 8 Series LPC Controller
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
             product: 8 Series SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:41 ioport:3088(size=8) ioport:3094(size=4) ioport:3080(size=8) ioport:3090(size=4) ioport:3060(size=32) memory:b0423000-b04237ff
        *-serial UNCLAIMED
             description: SMBus
             product: 8 Series SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b0421000-b04210ff ioport:3040(size=32)
        *-generic:1
             description: Signal processing controller
             product: 8 Series Thermal
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:b0422000-b0422fff
     *-scsi
          physical id: 1
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA THNSNH12
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: N103
             serial: X3NS102TTZUY
             size: 119GiB (128GB)
             capabilities: gpt-1.00 partitioned partitioned:gpt
             configuration: ansiversion=5 guid=7dc2ed83-ac63-4395-bfc8-a7d8da4f8d49 logicalsectorsize=512 sectorsize=512
           *-volume:0 UNCLAIMED
                description: Windows FAT volume
                vendor: mkfs.fat
                physical id: 1
                bus info: scsi@1:0.0.0,1
                version: FAT32
                serial: 865a-32eb
                size: 510MiB
                capacity: 511MiB
                capabilities: boot fat initialized
                configuration: FATs=2 filesystem=fat name=EFI System Partition
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: 09c8d2d1-5831-444e-80c6-d0c4d79b3041
                size: 118GiB
                capabilities: journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2019-02-01 12:07:17 filesystem=ext4 lastmountpoint=/ modified=2019-02-02 16:15:01 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2019-02-02 16:15:02 state=mounted
  *-battery
       description: Lithium Ion Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 07/07/2010
       serial: Battery 0
       slot: Fake
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:5
       logical name: wlx40f02fafeb66
       serial: 40:f0:2f:af:eb:66
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8xxxu driverversion=4.15.0-45-generic firmware=N/A ip=192.168.1.108 link=yes multicast=yes wireless=IEEE 802.11

```

Thanks!

---

### Post by gtwboogie on 2019-02-04
*Bump*

---

### Post by William_Klee on 2019-02-04
I know this isn't going to be helpful, but it looks like your system doesn't realize it has a touchscreen. I've installed linux on 3 or 4 touchscreen laptops, and xinput on one of them always showed the touchscreen under virtual core pointer.

---

### Post by gtwboogie on 2019-02-05
Well it helps even if you don't think so :) Now I know that I should see something in xinput (this is my first linux install on a machine with touch screen - I didn't know what to seek even). As I see it I must find out what type of device is in it and work on having it discovered by os - maybe it's connected in some unusual way...
Thanks a lot!

---

### Post by William_Klee on 2019-02-12
I had a couple free minutes, and was googling a similar issue I'm having with a different system, and found a note that I could download the driver I needed, but I'd also have to install device-specific firmware. If you don't have the firmware for your Yoga 11S touchscreen, that might be why it's not showing up under xinput. Just a thought, something to check out.

---

### Post by wg-racing on 2019-03-01
Not sure where we are with this thread as it is quite old but I can say with some confidence that this is no longer an issue. Just imaged a Lenovo IdeaPad Yoga 11S with the latest ISO of Ubuntu 18.04 LTS and touch screen works out of the box as does WiFi (which is more than can be said for the flakey Windows driver). It's the OS this device was built for. Beautiful! as soon as you touch the screen in a the login box the on-screen keyboard pops up. Awesome. Better than Windows. So basically, if you have a Lenovo IdeaPad Yoga 11S do yourself a favour and stick Ubuntu 18.04 LTS on it. :P

---


---
title: "Suspend/Hibernate causes screen color bleeding after reboot in 8.04"
date: 2008-06-17
forum: General Help
---

### Post by Maaack on 2008-06-17
I have a problem using suspend or hibernate on my laptop, also started on my desktop since 8.04 despite working in 7.10.  Both modes seem to shut the laptop off correctly and reboot up to a point without incident.  Alas, when I expect to see a box for my log in I instead get this strange result for both hibernation and suspend.  My screen will begin to bleed colors typically starting from the bottom with green, white, violet, and then black.  If it weren't for the fact that my computer becomes completely unresponsive and I have to hard reboot, I would say that its actually kind of intriguing to watch, even pleasing to the eye.

Some hardware information about the laptop:
```

    description: Portable Computer
    product: Inspiron 8600
    vendor: Dell Computer Corporation
    serial: 8FS5G51
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-4600-1053-8035-B8C04F473531
  *-core
       description: Motherboard
       product: 0Y4572
       vendor: Dell Computer Corporation
       physical id: 0
       serial: .8FS5G51.CN1296147R2201.
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A08 (04/26/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1500MHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.9.5
          slot: Microprocessor
          size: 1500MHz
          capacity: 1700MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 0
             slot: DIMM_A
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             physical id: 1
             slot: DIMM_B
             size: 256MiB
             width: 64 bits
             clock: 266MHz (3.8ns)

```

I can post system logs as well, it is just that there is a lot and I don't know which are likely to be the most relevant.

---

### Post by ranran on 2008-11-14
ME TOO bandwagon! :)

Inspiron 8600c (I love this laptop!) and just did a clean install of Ubuntu 8.1

After days of configuration I'm now at a point where I could actually start using this (except that Crossover Pro - <thanks Lameduck> still stinks with MS Office, especially 2007) but with a laptop an essential feature is suspend.

I shut/open my laptop all the time and this is really an essential feature.

I get the **EXACT** same behaviour.  It seems to suspend ok, goes to blinking green light, but upon resume, I  get the same "pretty"(?) bleeding colours and a completely unresponsive system.

So, what can we do to fix this?  Nvidia driver problem?  ACPI problem?  What what what? :) :)

_Hardware info:_
Dell Inspiron 8600c
Pentium M 1.5Mhz Dothan
333Mhz FSB
2GB DDR1
Nvidia Go5200 64mb 4X AGP
160GB WD Scorpio HD

---


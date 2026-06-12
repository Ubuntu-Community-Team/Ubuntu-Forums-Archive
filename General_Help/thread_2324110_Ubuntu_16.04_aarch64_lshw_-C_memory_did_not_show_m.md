---
title: "Ubuntu 16.04 aarch64 lshw -C memory did not show memory banks info correctly"
date: 2016-05-10
forum: General Help
---

### Post by scuttimmy on 2016-05-10
Dear all,

I installed Ubuntu 16.04 aarch64(ARM64) version with network installation method in an ARM64 board (**UEFI enabled**).
When I tried to get memory bank information with *lshw -C memory*, it shows:
```
root@Ubuntu:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
root@Ubuntu:~# lshw -C memory
  *-memory                
       description: System memory
       physical id: 11
       size: 7956MiB
```

However, if I get lshw source with *apt-get source lshw* and build it with make(Tried both cross compile in Ubuntu 16.04 x86_64  and native build in the Ubuntu 16.04 aarch64), it could show correct info:
```

root@Ubuntu:~# lshw-02.17/src/lshw -C memory
  *-firmware              
       description: BIOS
       vendor: Huawei Corp.
       physical id: 1
       version: Bios Version
       date: 04/29/2016
       size: 366KiB
       capacity: 3008KiB
       capabilities: pci upgrade shadowing cdboot bootselect edd  int13floppynec int13floppytoshiba int13floppy360 int13floppy1200  int13floppy720 int13floppy2880 int9keyboard int10video acpi usb  biosbootspecification uefi
  *-memory
       description: System Memory
       physical id: 7
       slot: System board or motherboard
       size: 8GiB
     *-bank:0
          description: DIMM Synchronous [empty]
          product: NO DIMM
          vendor: NO DIMM
          physical id: 0
          serial: NO DIMM
          slot: DIMM000 J1
     *-bank:1
          description: DIMM Synchronous [empty]
          product: NO DIMM
          vendor: NO DIMM
          physical id: 1
          serial: NO DIMM
          slot: DIMM001 J2
     *-bank:2
          description: DIMM DDR3 Synchronous 1600 MHz (0.6 ns)
          product: RMS6101ME68FAF1600
          vendor: Ramaxel
          physical id: 2
          serial: 0x414C32EB
          slot: DIMM010 J3
          size: 8GiB
          width: 64 bits
          clock: 1600MHz (0.6ns)
     *-bank:3
          description: DIMM Synchronous [empty]
          product: NO DIMM
          vendor: NO DIMM
          physical id: 3
          serial: NO DIMM
          slot: DIMM011 J4
  *-cache:0
       description: L1 cache
       physical id: d
       slot: L1 Instruction Cache
       size: 768KiB
       capacity: 768KiB
       capabilities: synchronous internal write-back instruction
  *-cache:1
       description: L1 cache
       physical id: e
       slot: L1 Data Cache
       size: 512KiB
       capacity: 512KiB
       capabilities: synchronous internal write-back data
  *-cache:2
       description: L2 cache
       physical id: f
       slot: L2 Cache
       size: 4MiB
       capacity: 4MiB
       capabilities: synchronous internal varies unified
  *-cache:3
       description: L3 cache
       physical id: 10
       slot: L3 Cache
       size: 16MiB
       capacity: 16MiB
       capabilities: synchronous internal varies unified

```

Could anyone give some suggestion about the difference of the original lshw and the built one?

Best Regards,

---

### Post by scuttimmy on 2016-09-12
It turns to that one ubuntu lshw patch will affect lshw functionality in ARM64, which is preventing application to access /dev/mem directly (OK in x86, but will cause crash in some ARM64 platforms).

In ARM64 + UEFI enabled platform, upstream lshw has added support for reading memory info from sysfs (Not in Ubuntu 16.04 yet).

---

### Post by mörgæs on 2016-09-12
Thanks for posting.
If you have the time to do a live boot it would be interesting to see how 16.10 behaves (whether or not the fix has made it to here).

---


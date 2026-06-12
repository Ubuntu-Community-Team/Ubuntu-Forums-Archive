---
title: "Ubuntu 18.04 not recognizing full RAM"
date: 2019-07-21
forum: General Help
---

### Post by jyeti on 2019-07-21
I recently installed Ubuntu 18.04 on a laptop and have noticed that upon opening Settings and going to Details, it only shows as having 5.8 GiB instead of 8. lshw -class memory shows the full 8 GiB, but free, top and System Monitor all recognize the smaller amount.

---

### Post by TheFu on 2019-07-21
Just a thought, could the onboard GPU take it?

---

### Post by jyeti on 2019-07-21
Upon running lspci -v, the integrated graphics card is shown to only be using 256MB of RAM.

---

### Post by TheFu on 2019-07-22
Sometimes there is a misinterpretation of the output.  Any chance of posting the actual commands used AND the output?  Perhaps someone else would read it differently.

---

### Post by jyeti on 2019-07-22
Command: lspci
Result:
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15d0
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Device 15d1
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:01.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15d3
00:01.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15d3
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15db
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 15dc
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 61)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15e8
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15e9
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ea
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15eb
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ec
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ed
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ee
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 15ef
01:00.0 Network controller: Intel Corporation Wireless 8265 / 8275 (rev 78)
02:00.0 Non-Volatile memory controller: Sandisk Corp Device 5003 (rev 01)
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Picasso (rev c2)
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 15de
03:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 15df
03:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15e0
03:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Device 15e1
03:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Device 15e2
03:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Device 15e3
03:00.7 Non-VGA unclassified device: Advanced Micro Devices, Inc. [AMD] Device 15e6
04:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 61)
```
Command: lspci -v -s 03:00.0
Result:
```
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Picasso (rev c2) (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 1821
    Flags: bus master, fast devsel, latency 0, IRQ 255
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=2M]
    I/O ports at f000 [disabled] [size=256]
    Memory at fe700000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>
```

---

### Post by QIII on 2019-07-22
Would you please show the actual commends and results of 
```
free
``` and ```
top
``` and ```
lshw -class memory 
```

It is always best to show all commands and their outputs when seeking support.

---

### Post by jyeti on 2019-07-22
Command: free
Result: ```
              total        used        free      shared  buff/cache   available
Mem:        6112076     5395684      334012      189200      382380      303900
Swap:       7812092      401152     7410940
```
The applicable part of the output of top: ```
KiB Mem :  6112076 total,   266932 free,  5406216 used,   438928 buff/cache
KiB Swap:  7812092 total,  7410940 free,   401152 used.   275512 avail Mem
```
Command: sudo lshw -class memory
Result: ```
  *-firmware                
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: X512DA.302
       date: 03/08/2019
       size: 64KiB
       capacity: 8128KiB
       capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
  *-memory
       description: System Memory
       physical id: a
       slot: System board or motherboard
       size: 8GiB
     *-bank:0
          description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
          product: M471A5244CB0-CRC
          vendor: Samsung
          physical id: 0
          serial: 00000000
          slot: DIMM 0
          size: 4GiB
          width: 64 bits
          clock: 2400MHz (0.4ns)
     *-bank:1
          description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2400 MHz (0.4 ns)
          product: M471A5244CB0-CRC
          vendor: Samsung
          physical id: 1
          serial: 98CF3A3A
          slot: DIMM 0
          size: 4GiB
          width: 64 bits
          clock: 2400MHz (0.4ns)
  *-cache:0
       description: L1 cache
       physical id: c
       slot: L1 - Cache
       size: 384KiB
       capacity: 384KiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=1
  *-cache:1
       description: L2 cache
       physical id: d
       slot: L2 - Cache
       size: 2MiB
       capacity: 2MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=2
  *-cache:2
       description: L3 cache
       physical id: e
       slot: L3 - Cache
       size: 4MiB
       capacity: 4MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=3
```

---

### Post by QIII on 2019-07-22
Is this a recent observation that was not the case some time ago?

How much memory is indicated by your BIOS?

---

### Post by jyeti on 2019-07-22
The computer was purchased very recently and Ubuntu was installed on it immediately, and this has been the case for the entirety of the time since then.

---

### Post by jyeti on 2019-07-22
Oh, and the BIOS reports 8GB of RAM.

---

### Post by TheFu on 2019-07-22
On my systems, 
```
glxinfo | egrep -i 'device|memory'
```
shows different results than **lspci -v** for GPU RAM use.

lspci for the video adapter says 
```
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
```
but
```
$ glxinfo | egrep -i 'device|memory'
    Device: Mesa DRI Intel(R) UHD Graphics 620 (Kabylake GT2)  (0x5917)
    Video memory: 3072MB
    Unified memory: yes
```
```

$ more /proc/meminfo 
MemTotal:        8048140 kB
MemFree:         4111844 kB
MemAvailable:    5492476 kB
...
```

Found some posts that refer to GPU specific tools which I don't have loaded.
```
intel_gpu_tools
aticonfig --odgc --odgt
nvidia-smi
```
[https://askubuntu.com/questions/276039/how-can-i-find-the-memory-usage-on-my-gpu](https://askubuntu.com/questions/276039/how-can-i-find-the-memory-usage-on-my-gpu)

Not encouraging when different methods don't provide the same answer.

---

### Post by jyeti on 2019-07-22
Whoa, ```
glxinfo | egrep -i 'device|memory'
``` says that I have 5968MB of video memory, which also doesn't make sense...

---

### Post by TheFu on 2019-07-22
For RAM, I'd trust /proc/meminfo  contents.
For video RAM use, I don't know who to trust, but I *suspect* there is a maximum limitation and normal use values. I am relatively clueless on video card stuff.

---

### Post by jyeti on 2019-07-22
/proc/meminfo indicates 5.8GiB of RAM.

---

### Post by QIII on 2019-07-22
proc/meminfo indicates what the motherboard is reporting to the kernel.  As a double-check, it might be worth just verifying that in your BIOS menu.

lshw in this case is just asking the memory for some info.  If it's nominally a 4GB module, that's what you'll get.

You are getting mixed messages about what the hardware says it is and the amount of memory the OS (and possibly the mobo) can address.

Do you have an inkling of the next step in diagnosis?

---

### Post by QIII on 2019-07-26
Was hoping someone would bite ...

My next step in diagnosis would be to run memtest to see if you have a problem with the memory modules.

---


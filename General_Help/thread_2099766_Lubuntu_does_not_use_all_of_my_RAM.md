---
title: "Lubuntu does not use all of my RAM"
date: 2012-12-30
forum: General Help
---

### Post by dikdirk on 2012-12-30
I am running Lubuntu 12.10 64bit on my hp nx7400 laptop.
I recently upgraded my RAM to 4GB (2x2GB memory modules), however sysinfo only displays 3.3GB of available RAM.

In the bios I can clearly see 4GB of ram installed and I can also run a diagnosis check on the memory in the bios. So it seems to be operating system related.

So, I am wondering what happened to the rest of it.

In this post: [http://ubuntuforums.org/showthread.php?p=12429300#post12429300](http://ubuntuforums.org/showthread.php?p=12429300#post12429300)
it is suggested that it might have something to do with shared video memory, however it is not posted how to verify that.

Does someone know how to:

[LIST]
[*] check the amount shared video memory?
[*]change the amount of shared video memory?
[*]find out what else might be the cause?
[/LIST]

---

### Post by matt_symes on 2012-12-30
HI

This question keeps coming up.

[http://unix.stackexchange.com/questions/15256/why-does-my-system-show-only-3-2-gib-of-ram-when-i-definitely-have-4-0-gib](http://unix.stackexchange.com/questions/15256/why-does-my-system-show-only-3-2-gib-of-ram-when-i-definitely-have-4-0-gib)

Kind regards

---

### Post by dikdirk on 2012-12-30
> **matt_symes said:**
> HI

This question keeps coming up.

[http://unix.stackexchange.com/questions/15256/why-does-my-system-show-only-3-2-gib-of-ram-when-i-definitely-have-4-0-gib](http://unix.stackexchange.com/questions/15256/why-does-my-system-show-only-3-2-gib-of-ram-when-i-definitely-have-4-0-gib)

Kind regards

Thank your for the response. Your link, however, seems to be related to 32 bit operating system and architecture. My operating system and architecture is 64 bit:

for example


[LIST]
[*]unem -a gives: Linux martin-HPnx7400 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64 x86_64 **x86_64** GNU/Linux
[*]sudo lshw |grep cpu, gives: *-cpu
          bus info: cpu@0
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx **x86-64** constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm tpr_shadow cpufreq
[/LIST]
Accoring to [wikipedia x86-64]("https://en.wikipedia.org/wiki/X86-64") means 64 bit and thus the cause should be something else!

---

### Post by Cheesemill on 2012-12-30
Is there a setting in your BIOS for allocating shared video memory? On my motherboard I can adjust how much RAM the onboard video adapter uses.

---

### Post by dikdirk on 2012-12-31
> **Cheesemill said:**
> Is there a setting in your BIOS for allocating shared video memory? On my motherboard I can adjust how much RAM the onboard video adapter uses.

No, unfortunately not.

---

### Post by fdrake on 2012-12-31
did you try reinstallin the kernel after the RAM upgrade? RAM sometimes doesn't get configured automatically

```

sudo apt-get install linux-image && sudo apt-get update 

```

---

### Post by dikdirk on 2012-12-31
> **fdrake said:**
> did you try reinstallin the kernel after the RAM upgrade? RAM sometimes doesn't get configured automatically

```

sudo apt-get install linux-image && sudo apt-get update 

```

Thank you for the suggestion, I tried it, but it didn work.
I upgraded from 1GB ram to 4GB, so part of it is also actually visible.

---

### Post by 3rdalbum on 2012-12-31
Something in your BIOS is set to only address in 32-bit mode.

---

### Post by fdrake on 2012-12-31
> **3rdalbum said:**
> Something in your BIOS is set to only address in 32-bit mode.
but he said he is running ubunut 64bit.

@OP
can you provide us with the ```
uname -a
sudo apt-get install dmidecode
sudo dmidecode --type memory
free -mh

```

---

### Post by matt_symes on 2012-12-31
Hi

Yes, that article was for 32 bit. 

Can we take a look at what Ubuntu is actually seeing ? 

Open a terminal and type (these are all case sensitive)

```
dmesg | grep Mem 
```

```
grep MemTotal /proc/meminfo
```

```
free -m
```

```
sudo dmidecode -t 6
```

Please post the results back here.

Kind regards

---

### Post by fdrake on 2012-12-31
also 
to check the memeory of the videocard:
```
lspci -v -s $(lspci | grep VGA | cut -d " " -f 1)
```

---

### Post by dikdirk on 2012-12-31
> **fdrake said:**
> but he said he is running ubunut 64bit.

@OP
can you provide us with the ```
uname -a
sudo apt-get install dmidecode
sudo dmidecode --type memory
free -mh

```

This is the output:

```
uname -a
Linux martin-HPnx7400 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
``````
sudo dmidecode --type memory
# dmidecode 2.11
SMBIOS 2.4 present.

Handle 0x000A, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 4 GB
    Error Information Handle: No Error
    Number Of Devices: 2

Handle 0x000B, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM #1
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 975 MHz
    Manufacturer: 7F7F9E0000000000
    Serial Number: 00000000
    Asset Tag: Not Specified
    Part Number: VS2GSDS800D2      

Handle 0x000C, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000A
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: None
    Locator: DIMM #2
    Bank Locator: Not Specified
    Type: DDR2
    Type Detail: Synchronous
    Speed: 975 MHz
    Manufacturer: 7F7F9E0000000000
    Serial Number: 00000000
    Asset Tag: Not Specified
    Part Number: VS2GSDS800D2
``````
free -mh
             total       used       free     shared    buffers     cached
Mem:          3.3G       1.5G       1.8G         0B       100M       574M
-/+ buffers/cache:       843M       2.5G
Swap:         4.7G         0B       4.7G
``````
cat /proc/meminfo 
MemTotal:        3462244 kB
MemFree:         1820584 kB
Buffers:          104636 kB
Cached:           591624 kB
SwapCached:            0 kB
Active:           914628 kB
Inactive:         529276 kB
Active(anon):     754284 kB
Inactive(anon):    56484 kB
Active(file):     160344 kB
Inactive(file):   472792 kB
Unevictable:       31260 kB
Mlocked:           31260 kB
SwapTotal:       4881404 kB
SwapFree:        4881404 kB
Dirty:               320 kB
Writeback:             0 kB
AnonPages:        778912 kB
Mapped:           116680 kB
Shmem:             57304 kB
Slab:              97716 kB
SReclaimable:      77064 kB
SUnreclaim:        20652 kB
KernelStack:        2648 kB
PageTables:        16824 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     6612524 kB
Committed_AS:    2145120 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      356884 kB
VmallocChunk:   34359373584 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       71488 kB
DirectMap2M:     3459072 kB
```I also tried booting up from a lubuntu 12.04 64 bit live usb (this was what I initially installed a while ago, then I upgraded to 12.10, after that I upgraded the memory from 1GB to 4GB). There was no difference in memory usage, also only 3.3GB was used.

---

### Post by dikdirk on 2012-12-31
> **fdrake said:**
> also 
to check the memeory of the videocard:
```
lspci -v -s $(lspci | grep VGA | cut -d " " -f 1)
```

This is the result:

```
lspci -v -s $(lspci | grep VGA | cut -d " " -f 1)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 30a2
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f4400000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 4000 [size=8]
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Memory at f4480000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
```

As far as I understand this, the video card is using 256MB right? 
But I have no idea whether this is shared memory or not....

---

### Post by dikdirk on 2012-12-31
> **matt_symes said:**
> Hi

Yes, that article was for 32 bit. 

Can we take a look at what Ubuntu is actually seeing ? 

Open a terminal and type (these are all case sensitive)

```
dmesg | grep Mem 
``````
grep MemTotal /proc/meminfo
``````
free -m
``````
sudo dmidecode -t 6
```Please post the results back here.

Kind regards

This is the result:

```
dmesg | grep Mem
[    0.000000] Memory: 3443856k/3530560k available (6718k kernel code, 452k absent, 86252k reserved, 6452k data, 932k init)

``````
 grep MemTotal /proc/meminfo
MemTotal:        3462244 kB

``````
free -m
             total       used       free     shared    buffers     cached
Mem:          3381       1618       1763          0        103        585
-/+ buffers/cache:        928       2452
Swap:         4766          0       4766
``````
 sudo dmidecode -t 6
# dmidecode 2.11
SMBIOS 2.4 present.
```

---

### Post by dikdirk on 2012-12-31
I found out another interesting detail. I  have a second laptop (a hp nc6320, which has almost the same specs as my hp nx7400). This laptop runs linux mint 10.4 64 bit (based on the ubuntu lucid LTS).
The same problem arised there!

---

### Post by fdrake on 2012-12-31
show us also the rest of the per memory
```

lspci -v |grep Memory

```

---

### Post by dikdirk on 2012-12-31
> **fdrake said:**
> show us also the rest of the per memory
```

lspci -v |grep Memory

```

This is the output:

```
lspci -v |grep Memory
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
    Memory at f4400000 (32-bit, non-prefetchable) [size=512K]
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    Memory at f4480000 (32-bit, non-prefetchable) [size=256K]
    Memory at f4500000 (32-bit, non-prefetchable) [size=512K]
    Memory at f4580000 (64-bit, non-prefetchable) [size=16K]
    Memory behind bridge: d7800000-d79fffff
    Memory behind bridge: f4000000-f40fffff
    Memory behind bridge: f0000000-f3ffffff
    Memory at f4584000 (32-bit, non-prefetchable) [size=1K]
    Memory behind bridge: f4100000-f43fffff
    Memory at f4585000 (32-bit, non-prefetchable) [size=1K]
    Memory at f4100000 (32-bit, non-prefetchable) [size=4K]
    Memory window 0: d8000000-dbffffff (prefetchable)
    Memory window 1: dc000000-dfffffff
    Memory at f4101000 (32-bit, non-prefetchable) [size=2K]
    Memory at f4104000 (32-bit, non-prefetchable) [size=16K]
    Memory at f4108000 (32-bit, non-prefetchable) [size=8K]
    Memory at f4000000 (32-bit, non-prefetchable) [size=4K]
```

---

### Post by matt_symes on 2013-01-02
Hi
 
It looks like your video card may be pinching the missing memory.
 
Please post the output of
 
```
 
head -n 150 /var/log/dmesg

```
 
Kind regards

---

### Post by dikdirk on 2013-01-02
> **matt_symes said:**
> Hi
 
It looks like your video card may be pinching the missing memory.
 
Please post the output of
 
```
 
head -n 150 /var/log/dmesg

```Kind regards


This is the output!
I must say I understand very little of this one, what does it do?


```
head -n 150 /var/log/dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-21-generic (buildd@allspice) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 (Ubuntu 3.5.0-21.32-generic 3.5.7.1)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-21-generic root=UUID=9a1ec54f-9bb5-462e-b832-6c3160785aca ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000d77cffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000d77d0000-0x00000000d77e55ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000d77e5600-0x00000000d77f7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000d77f8000-0x00000000d77fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed20000-0x00000000fed9afff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feda0000-0x00000000fedbffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffbfffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Hewlett-Packard HP Compaq nx7400 (RU425ET#ABH)/30A2, BIOS 68YGU Ver. F.0E 08/27/2008
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0xd77d0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FF0000000 write-back
[    0.000000]   3 base 0D0000000 mask FF8000000 write-back
[    0.000000]   4 base FD7800000 mask FFF800000 uncachable
[    0.000000]   5 base 0FEDA0000 mask FFFFE0000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3328MB, range: 128MB, type WB
[    0.000000] reg 4, base: 64888MB, range: 8MB, type UC
[    0.000000] reg 5, base: 4175488KB, range: 128KB, type UC
[    0.000000] total RAM covered: 3456M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3456MB, range: 128MB, type UC
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xd77cffff]
[    0.000000]  [mem 0x00000000-0xd75fffff] page 2M
[    0.000000]  [mem 0xd7600000-0xd77cffff] page 4k
[    0.000000] kernel direct mapping tables up to 0xd77cffff @ [mem 0x1fffa000-0x1fffffff]
[    0.000000] RAMDISK: [mem 0x362e4000-0x37169fff]
[    0.000000] ACPI: RSDP 00000000000f7c00 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 00000000d77e57c4 00074 (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
[    0.000000] ACPI: FACP 00000000d77e5684 000F4 (v04 HP     30A2     00000003 HP   00000001)
[    0.000000] ACPI: DSDT 00000000d77e5ac0 0F9C8 (v01 HP       nx7400 00010000 MSFT 0100000E)
[    0.000000] ACPI: FACS 00000000d77f7e80 00040
[    0.000000] ACPI: SLIC 00000000d77e5838 00176 (v01 HPQOEM SLIC-MPC 00000001 HP   00000001)
[    0.000000] ACPI: HPET 00000000d77e59b0 00038 (v01 HP     30A2     00000001 HP   00000001)
[    0.000000] ACPI: APIC 00000000d77e59e8 00068 (v01 HP     30A2     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 00000000d77e5a50 0003C (v01 HP     30A2     00000001 HP   00000001)
[    0.000000] ACPI: TCPA 00000000d77e5a8c 00032 (v02 HP     30A2     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 00000000d77f5488 00326 (v01 HP       HPQSAT 00000001 MSFT 0100000E)
[    0.000000] ACPI: SSDT 00000000d77f5fc1 0025F (v01 HP      Cpu0Tst 00003000 INTL 20060317)
[    0.000000] ACPI: SSDT 00000000d77f6220 000A6 (v01 HP      Cpu1Tst 00003000 INTL 20060317)
[    0.000000] ACPI: SSDT 00000000d77f62c6 004D7 (v01 HP        CpuPm 00003000 INTL 20060317)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000000d77cffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0xd77cffff]
[    0.000000]   NODE_DATA [mem 0xd77cc000-0xd77cffff]
[    0.000000]  [ffffea0000000000-ffffea00035fffff] PMD -> [ffff8800d3800000-ffff8800d6dfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xd77cffff]
[    0.000000] On node 0 totalpages: 882527
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3913 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13728 pages used for memmap
[    0.000000]   DMA32 zone: 864816 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] e820: [mem 0xd7800000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800d7400000 s83584 r8192 d22912 u1048576
[    0.000000] pcpu-alloc: s83584 r8192 d22912 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 868729
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-21-generic root=UUID=9a1ec54f-9bb5-462e-b832-6c3160785aca ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3443856k/3530560k available (6718k kernel code, 452k absent, 86252k reserved, 6452k data, 932k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 14155776 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1828.836 MHz processor.
```

I also tried a different brand memory modules by switching them with the laptop of someone else... it made no difference and again only 3.3GB was visible!

---

### Post by dikdirk on 2013-01-05
Does anyone have a clue, the problem still persists....

What I especially  want to figure out is how much shared video memory is taken away from the RAM.

---

### Post by oldgraf on 2013-01-05
Same heer with toshiba tecra a8. Years ago read in tech forum that is bios problem. Yes bios say 4gb but nor Windows not Linux can oparate with all of them

---

### Post by MoebusNet on 2013-01-05
Speculation here, since I don't know any better:

```
head -n 150 /var/log/dmesg

*snip*
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3456MB, range: 128MB, type UC
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
*snip*
```

When variable MTRRs were remapped, doesn't it look like reg1 and reg2 were reserved for the video card? It looks like 4GB minus 636MB gets pretty close to your memory available, doesn't it?

If anyone else has a better explanation, please correct me!

---

### Post by 1clue on 2013-01-05
> **oldgraf said:**
> Same heer with toshiba tecra a8. Years ago read in tech forum that is bios problem. Yes bios say 4gb but nor Windows not Linux can oparate with all of them

This is a hardware issue, not a Linux or Windows issue.

I have 12g on my Ubuntu, and an external video card that has its own memory instead of robbing from the system RAM.  My system doesn't show nearly that much missing, everything can be accounted for by the lspci memory trick.

---

### Post by dikdirk on 2013-01-06
> **MoebusNet said:**
> Speculation here, since I don't know any better:

```
head -n 150 /var/log/dmesg

*snip*
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3456MB, range: 128MB, type UC
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
*snip*
```When variable MTRRs were remapped, doesn't it look like reg1 and reg2 were reserved for the video card? It looks like 4GB minus 636MB gets pretty close to your memory available, doesn't it?

If anyone else has a better explanation, please correct me!

Thank you all for the explaination. I agree, and also with that this is probably related to mapping the memory.

The thing I still don't understand is that the video card only uses 256MB of extra memory... (see the output of the lspci stuff) so still about 500MB is "missing". Well it get's mapped into someting... but is it clear that that is bios related and does this mean it is unusable?

Another way to put it, the memory is mapped into reg0, reg1, reg2. Does this mean that is then automatically unavailable for as ram?

---

### Post by axel668 on 2013-01-15
had a similar issue with my Asus 1215N when I upgraded from 2 to 3 GB RAM - I had to do a BIOS update so the additional RAM would be recongnized at all. if it's not that, probably the "missing" RAM is indeed reserved for your onboard GPU, if you can't set it in the BIOS it will be the max amount the GPU can handle (like 512 or 768M for the usual Intel HD chipsets)

---

### Post by kernel2 on 2013-09-13
I have the same problem.

BIOS Detected 8 GB! Work, Nvidia Shared 256 MB


8 GB,not recognizing Lubuntu 64 bit amd motherboard asrock N68-S3 FX

 two memory 4 GB(Corsair Vengeance 1x 4 Gb ddr3 1600) 

------
> uname -a
Linux kernel-desktop 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:52:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

  >  NVIDIA Corporation C61 [GeForce 7025 / nForce 630a] (rev a2) (prog-if 00 [VGA controller])    Subsystem: ASRock Incorporation Device 03d6
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ed000000 (64-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at effc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia  

> free -m             total       used       free     shared    buffers     cached
Mem:          3701       3023        678          0        137        802
-/+ buffers/cache:       2083       1618
Swap:         3839          0       3839
kernel@kernel-desktop:~$ free -mh
             total       used       free     shared    buffers     cached
Mem:          3,6G       3,0G       674M         0B       137M       805M
-/+ buffers/cache:       2,0G       1,6G
Swap:         3,7G         0B       3,7G




> sudo dmidecode -t 6# dmidecode 2.11
SMBIOS 2.6 present.




> cat /proc/cpuinfo | grep paeflags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr hw_pstate npt lbrv svm_lock nrip_save
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr hw_pstate npt lbrv svm_lock nrip_save
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr hw_pstate npt lbrv svm_lock nrip_save
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt nodeid_msr hw_pstate npt lbrv svm_lock nrip_save


Not boot with 8 GB, black screen loading... not loaded full :/

boot 4 GB more no detect 4 GB memory :/

help :/

---

### Post by kernel2 on 2013-09-13
is there any way to use Lubuntu 13 64-bit memory of 8 GB?

---

### Post by kernel2 on 2013-09-14
Well, come to detail, something I should have done from the beginning.


Motherboard asrock N68-S3-fx
2 memories 1X 4GB DDR3 1600.


Sata 160 gb HD.


In bios I provides the total memory 8 GB shared 256
with nvidia onboard.




Systems tested Lubuntu 13:04 64 and 32 bits.




The installation of both works only with 1 stick of memory connected.


And in Sees Maximum 3 GB, both 64-bit and 32.


When I add another comb memory, the boot screen is dark. Blank Screen.


In 32-bit system the only kernel that worked with 2 sticks Memory was the generic 3.2.40 for ubuntu.


But I only view 3 GB of memory.


I installed kernel-pae, gave me black screen again, Blank Screen, it stop there.


In the 64-bit, even compiling the kernel 3.2.40, still blank screen, the thing is when I put the other comb 4 GB, 8 GB total, is in blank Screen and not out there.


The I modified grub also for possible problems blank screen, changing the grub splash quiet to modonoset.


Only works with one memory of 4 GB, which displays only 3 Gb


The OS was installed via USB stick.
Yet this does not influence.


Anyone can say what I can do for my Lubuntu use 8 GB?

---

### Post by oldos2er on 2013-09-14
You'd be much better off starting a new thread for your questions.

---

### Post by mishi2 on 2013-09-18
> **axel668 said:**
> had a similar issue with my Asus 1215N when I upgraded from 2 to 3 GB RAM - I had to do a BIOS update so the additional RAM would be recongnized at all. if it's not that, probably the "missing" RAM is indeed reserved for your onboard GPU, if you can't set it in the BIOS it will be the max amount the GPU can handle (like 512 or 768M for the usual Intel HD chipsets)

I have literally the same issue as dirkdirk. Only 3.2GB RAM when I have 4GBs installed, despite having the x64 bit architecture. Since my Windows 7 partition utilizes all of my memory I'm going to guess it's not an BIOS issue and it's just memory the system reserves. If this is the case, is there anyway to tell my graphics card to use less memory for my Ubuntu partition only?

---

### Post by TenPlus1 on 2013-09-19
Gfx memory usage is setup in the bios which you would have to change each time, their is no automatic way of doing this...

So long as your system works ok even with 3.3gb of memory available hold on for some future updates either for Ubuntu itself through the kernel or your laptop bios and I'm sure one of these will fix the memory available for you...

---

### Post by rasos on 2014-04-15
Same issue here on a HP-Compaq nc6320. Flipping both 2GB RAMs did not help. BIOS shows 4 GB, no switch for video-RAM in latest BIOS Version 1.24 (upgraded).
Interesting: even Memtest can test only 3319 MB, but it shows both 2GB RAMs built in (when pressing c-5).
Has anyone filed this as a bug report?

---


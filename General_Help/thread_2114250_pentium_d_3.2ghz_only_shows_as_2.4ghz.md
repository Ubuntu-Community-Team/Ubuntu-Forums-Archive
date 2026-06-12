---
title: "pentium d 3.2ghz only shows as 2.4ghz"
date: 2013-02-09
forum: General Help
---

### Post by wingnut2626 on 2013-02-09
I recently bought a pentium d 3.2ghz with 4 mb l2 cache and when i type in lscpu it tells me that the clock speed is 2400 mhz and i only have a 2 mb l2 cache.  any ideas?

---

### Post by ibjsb4 on 2013-02-09
Whats this say?

```
cat /proc/cpuinfo
```

---

### Post by tgalati4 on 2013-02-09
Sounds like the sticker on the box does not match the processor under the heat sink.  Sounds like somebody switched it.

---

### Post by wingnut2626 on 2013-02-09
No.  I put the processor in myself.  I just bought it.  It is a 3.2Ghz pentium D.

```
here is the readout on the /proc/cpuinfo

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 6
model name	: Intel(R) Pentium(R) D CPU 3.20GHz
stepping	: 4
microcode	: 0x4
cpu MHz		: 2400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl vmx est cid cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 6400.49
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 6
model name	: Intel(R) Pentium(R) D CPU 3.20GHz
stepping	: 4
microcode	: 0x4
cpu MHz		: 2400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl vmx est cid cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 6400.49
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

```

---

### Post by rnerwein on 2013-02-09
> **wingnut2626 said:**
> I recently bought a pentium d 3.2ghz with 4 mb l2 cache and when i type in lscpu it tells me that the clock speed is 2400 mhz and i only have a 2 mb l2 cache.  any ideas?
hi
the cpu-freq. is scheduled (by default) on demand. have a look at:
/sys/devices/system/cpu//sys/devices/cpu0/cpufreq
in /sys/devices/system/cpu you will find cpu0 ... cpun. in cpufreq you find:
cpuinfo_cur_freq, cpuinfo_min_freq, cpuinfo_max_freq .. cat these files and you will see what' possible for your cpu. 
just give some load on your box and you will see that the ghz goes up to 3.2.
don't worry - be happy
cheers

---

### Post by wingnut2626 on 2013-02-09
So why is the L2 cache size wrong?

---

### Post by tgalati4 on 2013-02-09
Check the stamping on the chip itself and do a search on intel's website.  What is the chipset on the motherboard?

---

### Post by Doug S on 2013-02-09
I think the command "lscpu" lists the l2 cache as per core.
I think you will find the command:```
sudo lshw | more
```will list the total l2 cache size.
Here is what I found on my i7 computer:```
sudo lshw | more
...
        *-cache:1
             description: L2 cache
             physical id: 6
             [COLOR=red]slot: L2-Cache[/COLOR]
[COLOR=red]            size: 1MiB[/COLOR]
             capacity: 1MiB
             capabilities: internal varies unified
...
doug@s15:~/sguide-1304/serverguide-lp1077494-2$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    2
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 42
Stepping:              7
CPU MHz:               1600.000
BogoMIPS:              6822.07
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
[COLOR=red]L2 cache:              256K[/COLOR]
L3 cache:              8192K
NUMA node0 CPU(s):     0-7
 

```

---

### Post by prodigy_ on 2013-02-09
> **wingnut2626 said:**
> So why is the L2 cache size wrong?
It's not wrong. Pentium D 940 is a dual-core CPU with 2x2MB cache (2MB per core which is exactly what you see in the output). It idles at 2400MHz because you have EIST enabled in BIOS. Do something CPU-intensive (watch video for example) and you'll see 3200.

---

### Post by Yellow Pasque on 2013-02-09
^Yeah, what prodigy_ said. More specifically, the Pentium D 940 has a 400MHz base clock and an 8x multiplier (8 * 400 = 3200 MHz). Speedstep puts the mulitplier down to 6 to save energy when the CPU is idle (6 * 400 = 2400 MHz).

You could disable SpeedStep to make the CPU run at 3.2 GHz all the time, but that's a waste of electricity, especially when you have a 130W CPU...

---

### Post by wingnut2626 on 2013-02-10
Ok thanks guys. I appreciate the help.

---


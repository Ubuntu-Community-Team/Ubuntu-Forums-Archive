---
title: "UBUNTU 12.04 LTS: system is running in low graphics mode"
date: 2014-01-26
forum: General Help
---

### Post by itsankur on 2014-01-26
Hi
I have ubuntu 12.04 lts and after some updates I am getting this error, as like many others:

**The system is running in low graphics mode...**

According to the suggestions, I entered in the **recovery** mode, then selected **failsafex**.

Then after choosing **yes**  I get the following message at the bottom of the screen:
 
[B]fsck from util-linux 2.20.1
/dev/sda3 contains a file system with errors, check forced[/B]

After some time again the following occurs

[B]The system is running in low graphics mode...
[/B]
Now when I try to open a terminal by pressing **ctrl+alt+F1**

It stays at

**Loading extension GLX**

forever. Terminal can not be initiated...

What do I do? Please help...

---

### Post by QIII on 2014-01-26
Hello!

It would be very helpful if you could give us some details about your hardware.  More is better, but please at least provide information on your graphics.

Cheers!

---

### Post by itsankur on 2014-01-26
Thanks for the response.

Here's some of the details of my hardware, if you need more please tell me the instructions to know those...

[B]1. sudo lshw -C display
[/B]  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:e080(size=8)

[B]2. sudo lshw -C cpu
[/B]  *-cpu                   
       description: CPU
       product: Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 6.5.2
       serial: 0002-0652-0000-0000-0000-0000
       slot: N/A
       size: 933MHz
       capacity: 2133MHz
       width: 64 bits
       clock: 133MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq

...

[B]3. sudo lshw -short -C memory
[/B]H/W path         Device      Class          Description
=======================================================
/0/0                         memory         64KiB BIOS
/0/4/5                       memory         128KiB L1 cache
/0/4/6                       memory         512KiB L2 cache
/0/4/7                       memory         3MiB L3 cache
/0/9                         memory         2GiB System Memory
/0/9/0                       memory         2GiB SODIMM DDR3
/0/9/1                       memory         SODIMM [empty]


Thanks again...

---

### Post by itsankur on 2014-01-27
Hi QIII and others,
I am still waiting for your answer...

---


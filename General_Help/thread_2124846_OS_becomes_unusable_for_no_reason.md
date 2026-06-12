---
title: "OS becomes unusable for no reason"
date: 2013-03-12
forum: General Help
---

### Post by danielgomes on 2013-03-12
Hey guys,

I installed Ubuntu a few days ago, and it works fine, but every now and then (as in, it happened 3 times since I installed it) the OS just gets totally unresponsive out of nowhere. This last time, for instance, I was working on Eclipse and did a search on Chrome, and suddenly nothing worked anymore. It doesn't totally freeze up, I can see the mouse moving a little bit (and much later than the actual mouse movement), but I can't even Ctrl-Alt-F1 to jump to a terminal. One of the previous times this happened I did manage to get to a terminal, and "top" didn't show any crazy memory/CPU hogging processes, everything seemed normal, but it was super slow and I was forced to reboot.

I had a look at the syslog right after I rebooted and I can see this line showing up many many times:

Mar 12 13:38:09 dgomes kernel: [15861.202889] m9x: CreateSurface Failed !m_poBrdgDirectRequester->RequestSurfaceCreation() !!

By "many times" I really mean A LOT: the file had 1,195,993 lines, from which 1,194,918 were that error...

I'm running Ubuntu 12.04.2 LTS and this is my cpuinfo:

```
processor    : 0vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
stepping    : 7
microcode    : 0x25
cpu MHz        : 1600.000
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 4
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6185.95
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
stepping    : 7
microcode    : 0x25
cpu MHz        : 1600.000
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 1
cpu cores    : 4
apicid        : 2
initial apicid    : 2
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6185.95
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
stepping    : 7
microcode    : 0x25
cpu MHz        : 1600.000
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 4
apicid        : 4
initial apicid    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6185.95
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:


processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 42
model name    : Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
stepping    : 7
microcode    : 0x25
cpu MHz        : 1600.000
cache size    : 6144 KB
physical id    : 0
siblings    : 4
core id        : 3
cpu cores    : 4
apicid        : 6
initial apicid    : 6
fpu        : yes
fpu_exception    : yes
cpuid level    : 13
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6185.95
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```

Feel free to ask for more info

---

### Post by ibjsb4 on 2013-03-12
Never dealt with this, but got some hits that may help you out.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=CreateSurface+Failed&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=CreateSurface+Failed&sa=Search&cof=FORID:9)

---

### Post by ceggers on 2013-04-10
I've the same problem under openSUSE 12.2. It appeared first after replacing my graphics adapter with a Matrox M9148 LP.

Via SSH I could see that Xorg was consuming about 30% of all available memory. After some time (depending on the available swap space), Xorg gets killed by the OOM killer. After this, some memory is available again, but most is still allocated. So I usually I've to reboot after this.

---

### Post by solarghost on 2013-04-10
I sometimes get this issue using Chrome, when I open a couple of tabs everything freezes for about 20 seconds and then back to normal.

---


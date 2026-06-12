---
title: "Run out of inodes"
date: 2012-10-22
forum: General Help
---

### Post by asus701user on 2012-10-22
I have run out of inodes (again). This was caused I think by running Update Manager which then had some reason not to complete and must have created 1000s of empty files (I am guessing). This may have been caused by Ubuntu Tweak (I am guessing).

The result is I have plenty of space (via df -k) but 100% use of inodes.

I have found that there are lots of files in /proc. I run Nautilus as a user and I see many directories named, 1,2,3, 4, up to very many but I cannot delete them. If I run Nautilus as root (sudo nautilus) when I go to /proc the machine hangs ? and just says 'loading'. At least as root I stand a chance of deleting them (guessing that I can delete all the numbered directories). Should I wait  however long and hope that nautilus opens /proc or give up.

How can I get rid of these files from the failed update and regain the inodes?

Many thanks

---

### Post by Cheesemill on 2012-10-22
The files in /proc are nothing to do with a failed upgrade, you can't actually delete anything in /proc, and even if you could it wouldn't free any inodes.

/proc doesn't live in your hard drive, none of the files it contains actually exist. It is a virtual filesystem that presents information about running processes and other system information.

For example:
```
rob@raring:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
stepping    : 5
microcode    : 0x2
cpu MHz        : 1197.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6133.18
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
stepping    : 5
microcode    : 0x2
cpu MHz        : 1197.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 2
apicid        : 4
initial apicid    : 4
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6133.18
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 2
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
stepping    : 5
microcode    : 0x2
cpu MHz        : 1197.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 0
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6133.18
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 3
vendor_id    : GenuineIntel
cpu family    : 6
model        : 37
model name    : Intel(R) Core(TM) i3 CPU         540  @ 3.07GHz
stepping    : 5
microcode    : 0x2
cpu MHz        : 1197.000
cache size    : 4096 KB
physical id    : 0
siblings    : 4
core id        : 2
cpu cores    : 2
apicid        : 5
initial apicid    : 5
fpu        : yes
fpu_exception    : yes
cpuid level    : 11
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips    : 6133.18
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:
```This information isn't actually stored in a file, even though it appears like it is. Instead it is read directly from the CPU via the kernel.

Another example:
```
rob@raring:~$ cat /proc/1/status 
Name:    init
State:    S (sleeping)
Tgid:    1
Pid:    1
PPid:    0
TracerPid:    0
Uid:    0    0    0    0
Gid:    0    0    0    0
FDSize:    64
Groups:    
VmPeak:       24544 kB
VmSize:       24540 kB
VmLck:           0 kB
VmPin:           0 kB
VmHWM:        2488 kB
VmRSS:        2488 kB
VmData:        1072 kB
VmStk:         136 kB
VmExe:         152 kB
VmLib:        2608 kB
VmPTE:          64 kB
VmSwap:           0 kB
Threads:    1
SigQ:    0/61648
SigPnd:    0000000000000000
ShdPnd:    0000000000000000
SigBlk:    0000000000000000
SigIgn:    0000000000001000
SigCgt:    00000001a0016623
CapInh:    0000000000000000
CapPrm:    ffffffffffffffff
CapEff:    ffffffffffffffff
CapBnd:    ffffffffffffffff
Cpus_allowed:    ff
Cpus_allowed_list:    0-7
Mems_allowed:    00000000,00000001
Mems_allowed_list:    0
voluntary_ctxt_switches:    1369
nonvoluntary_ctxt_switches:    496
```This gives you the status of the process with PID 1. Again this information doesn't exist in a file, it is reported directly by the kernel.

Just like /dev, /proc exists to support the Linux philosophy of 'everything is a file'.

---


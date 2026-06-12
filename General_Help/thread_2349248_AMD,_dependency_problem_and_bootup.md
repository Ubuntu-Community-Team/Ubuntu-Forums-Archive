---
title: "AMD, dependency problem and bootup"
date: 2017-01-12
forum: General Help
---

### Post by Mark_in_Hollywood on 2017-01-12
The 'puter has some problem and I cannot form an intelligent question so as to isolate it well to ask for help here. None the less, here goes:

Powerup time shows multiple iteration lines showing **amd** and some **pre-dependency** problem for many multiple library objects (I believe I am saying this correctly). I have an AMD cpu.

The log file, is so very long it's viewable at:

[http://pastebin.com/4az3eLYb](http://pastebin.com/4az3eLYb)

Having said all this, the computer boots and seems to run OK, until power off. Then it won't power off. The system hangs and I have to use the power button. When I have to use the power button, on powerup there are even more dire sounding lines about orphaned inodes.

I have tried Ubuntu Recovery, running, fsck, update grub and dpkg.

---

### Post by geeksmith on 2017-01-12
Looks like you have packages installed for more than one CPU architecture. Is this a 32-bit or 64-bit CPU? You can post the contents of /proc/cpuinfo if you're not sure.

The messages you're seeing are package dependency problems. I'd suggest trying this:
```
sudo apt-get update; sudo apt-get dist-upgrade; sudo apt-get -f install
```

If that doesn't fix it, please paste the output of those commands.

---

### Post by Yellow Pasque on 2017-01-12
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

> Looks like you have packages installed for more than one CPU architecture.
This is not a problem. It's common to have 32-bit libs on a 64-bit system, especially because of wine.

---

### Post by geeksmith on 2017-01-12
> **Temüjin said:**
> [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)


This is not a problem. It's common to have 32-bit libs on a 64-bit system, especially because of wine.

I never said it was a problem -- I have a similar setup. Just trying to gather info.

---

### Post by Mark_in_Hollywood on 2017-01-12
Thank you, again, Linux Community. You are the best.

Running dist-upgrade brought a new (or only) version of dbus. About 497kb.

Running apt-get install -f returned:

mark@Lexington:~$ sudo apt-get install -f
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Bashing-om on 2017-01-12
Mark_in_Hollywood: Hello again;

Hey the target here is a text file:
> 
sysop@x1604:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
<snip>


: My bit to try and help

---

### Post by Mark_in_Hollywood on 2017-01-12
POSTED merely as an FYI. Case closed.
```

mark@Lexington:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-6300 Six-Core Processor
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 3500.000
cache size	: 2048 KB
physical id	: 0
siblings	: 6
core id		: 0
cpu cores	: 3
apicid		: 16
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb cpb hw_pstate vmmcall bmi1 arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bugs		: fxsave_leak sysret_ss_attrs
bogomips	: 6999.93
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-6300 Six-Core Processor
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 6
core id		: 1
cpu cores	: 3
apicid		: 17
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb cpb hw_pstate vmmcall bmi1 arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bugs		: fxsave_leak sysret_ss_attrs
bogomips	: 6999.93
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-6300 Six-Core Processor
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 2500.000
cache size	: 2048 KB
physical id	: 0
siblings	: 6
core id		: 2
cpu cores	: 3
apicid		: 18
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb cpb hw_pstate vmmcall bmi1 arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bugs		: fxsave_leak sysret_ss_attrs
bogomips	: 6999.93
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-6300 Six-Core Processor
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 6
core id		: 3
cpu cores	: 3
apicid		: 19
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb cpb hw_pstate vmmcall bmi1 arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bugs		: fxsave_leak sysret_ss_attrs
bogomips	: 6999.93
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 4
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-6300 Six-Core Processor
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 1400.000
cache size	: 2048 KB
physical id	: 0
siblings	: 6
core id		: 4
cpu cores	: 3
apicid		: 20
initial apicid	: 4
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb cpb hw_pstate vmmcall bmi1 arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bugs		: fxsave_leak sysret_ss_attrs
bogomips	: 6999.93
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

processor	: 5
vendor_id	: AuthenticAMD
cpu family	: 21
model		: 2
model name	: AMD FX(tm)-6300 Six-Core Processor
stepping	: 0
microcode	: 0x6000822
cpu MHz		: 2500.000
cache size	: 2048 KB
physical id	: 0
siblings	: 6
core id		: 5
cpu cores	: 3
apicid		: 21
initial apicid	: 5
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 popcnt aes xsave avx f16c lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 tce nodeid_msr tbm topoext perfctr_core perfctr_nb cpb hw_pstate vmmcall bmi1 arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
bugs		: fxsave_leak sysret_ss_attrs
bogomips	: 6999.93
TLB size	: 1536 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm 100mhzsteps hwpstate cpb eff_freq_ro

```

---


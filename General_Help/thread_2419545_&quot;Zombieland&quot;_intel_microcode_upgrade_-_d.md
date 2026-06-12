---
title: "&quot;Zombieland&quot; intel microcode upgrade - did this work?"
date: 2019-05-23
forum: General Help
---

### Post by bobnn on 2019-05-23
So I've done all my upgrades, but am unsure what this is supposed to look like.  Dell Inspiron, Ubuntu 14.04 LTS

```

# uname -a
Linux srvr1 3.13.0-170-generic #220-Ubuntu SMP Thu May 9 12:40:49 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

# apt-cache policy intel-microcode 
intel-microcode:
  Installed: 3.20190514.0ubuntu0.14.04.1
  Candidate: 3.20190514.0ubuntu0.14.04.2
  Version table:
     3.20190514.0ubuntu0.14.04.2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
 *** 3.20190514.0ubuntu0.14.04.1 0
        100 /var/lib/dpkg/status
     2.20140122.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages



# dmesg | grep microcode
[    0.000000] CPU0 microcode updated early to revision 0x2f, date = 2019-02-17
[    0.077989] CPU1 microcode updated early to revision 0x2f, date = 2019-02-17
[    0.799985] microcode: CPU0 sig=0x206a7, pf=0x2, revision=0x2f
[    0.799992] microcode: CPU1 sig=0x206a7, pf=0x2, revision=0x2f
[    0.799999] microcode: CPU2 sig=0x206a7, pf=0x2, revision=0x2f
[    0.800008] microcode: CPU3 sig=0x206a7, pf=0x2, revision=0x2f
[    0.800055] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba

```
That stuff out of dmesg is what I'm curious about, is this right?


```

# cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
stepping	: 7
microcode	: 0x2f
cpu MHz		: 1600.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer xsave avx lahf_lm epb xsaveopt ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid dtherm arat pln pts md_clear flush_l1d
bogomips	: 6186.08
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
stepping	: 7
microcode	: 0x2f
cpu MHz		: 1600.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer xsave avx lahf_lm epb xsaveopt ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid dtherm arat pln pts md_clear flush_l1d
bogomips	: 6186.08
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


```
The CPU stuff repeats 3 more times: 2 cores w/ hyperthreads looks like 4 CPUs as I understand it

---

### Post by deadflowr on 2019-05-23
The microcode updates has a limited affect for a only a select few processor families.
You can run
```
cat /sys/devices/system/cpu/vulnerabilities/mds
```
To see where you stand.
See:
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/MDS]("https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/MDS")
[https://www.kernel.org/doc/html/latest/admin-guide/hw-vuln/mds.html#mds-system-information]("https://www.kernel.org/doc/html/latest/admin-guide/hw-vuln/mds.html#mds-system-information")


Also: You haven't applied all updates as the Installed and Candidate don't match:
```
# apt-cache policy intel-microcode 
intel-microcode:
  Installed: 3.20190514.0ubuntu0.14.04.1
  Candidate: 3.20190514.0ubuntu0.14.04.2
```

---

### Post by mikewhatever on 2019-05-25
Hasn't Ubuntu 14.04 standard support ended in April 2019? If you are worried about security, it is time to upgrade to a supported release.

---

### Post by yetimon_64 on 2019-05-25
> **deadflowr said:**
> ...
Also: You haven't applied all updates as the Installed and Candidate don't match:
```
# apt-cache policy intel-microcode 
intel-microcode:
  Installed: 3.20190514.0ubuntu0.14.04.1
  Candidate: 3.20190514.0ubuntu0.14.04.2
```

I don't think that will even be possible to match those up with Trusty now being EOL, at least not without switching the sources.list file to "old-releases.ubuntu.com".

However as mikewhatever notes ...
> If you are worried about security, it is time to upgrade to a supported release. +1, that would be the way to go OP.

Because trusty is now "end of life" it will probably be easier to do a fresh install, I suspect an upgrade may be a bit problematic with an EOL release like Trusty.
I always do fresh installs for myself; others here would be better off advising you on upgrades if you choose that option.

---

### Post by bobnn on 2019-05-27
OK, I failed to notice the mismatch on that apt-cache policy output.

```
intel-microcode:
  Installed: 3.20190514.0ubuntu0.14.04.2
  Candidate: 3.20190514.0ubuntu0.14.04.2


```

**I'll go check the documents that deadflowr referred to.**

Updates, upgrades, installs are still working for 14.04 - I actually installed darktable yesterday on a 14.04 machine - but you're right it's time to switch.




Now I see 

```
\# dmesg | grep microcode
[    0.000000] CPU0 microcode updated early to revision 0x2f, date = 2019-02-17
[    0.077851] CPU1 microcode updated early to revision 0x2f, date = 2019-02-17
[    0.682932] microcode: CPU0 sig=0x206a7, pf=0x2, revision=0x2f
[    0.682938] microcode: CPU1 sig=0x206a7, pf=0x2, revision=0x2f
[    0.682946] microcode: CPU2 sig=0x206a7, pf=0x2, revision=0x2f
[    0.682955] microcode: CPU3 sig=0x206a7, pf=0x2, revision=0x2f
[    0.683001] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba

```

---


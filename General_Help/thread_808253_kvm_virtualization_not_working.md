---
title: "kvm virtualization not working"
date: 2008-05-26
forum: General Help
---

### Post by strattonbrazil on 2008-05-26
I can't seem to get kvm to work with virtualization.  I went into my BIOS and enabled Intel virtualization, but I still can't see any /dev/kvm being created, and get an error trying to run kvm without hardware acceleration.  I'm running Ubuntu 8.04.  

`modprobe kvm` works and is displayed with lsmod.  Here are my CPU details
details (omitting processor 1-3):

```


processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Xeon(R) CPU            5140  @ 2.33GHz
stepping	: 6
cpu MHz		: 2333.415
cache size	: 4096 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall lm constant_tsc arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips	: 4670.60
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


```

---


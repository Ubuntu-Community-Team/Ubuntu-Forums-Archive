---
title: "how to recognise the sse3 instruction set?"
date: 2008-05-13
forum: General Help
---

### Post by azzamite on 2008-05-13
Hi there, I have a Turion 64 x2 processor (k8 ) and it is supposed
to implement the sse3 instruction set or so I'm told by cpuz.

But I look in /proc/cpuinfo and that doesn't appear, I understand
those instructions help to improve the performance of the games...

I tries installing the linux-*-amd64-k8 packages but nothing, the
packages says that they are dummies.

Any ideas?
```
 cat /proc/cpuinfo  | grep -i sse
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch

```

---


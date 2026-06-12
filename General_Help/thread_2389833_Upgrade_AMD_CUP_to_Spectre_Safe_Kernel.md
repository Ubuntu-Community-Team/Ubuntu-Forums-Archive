---
title: "Upgrade AMD CUP to Spectre Safe Kernel"
date: 2018-04-22
forum: General Help
---

### Post by Mark_in_Hollywood on 2018-04-22
Per:

How To Check For Meltdown And Spectre Vulnerabilities And Patch Them In Linux

 [https://www.ostechnix.com/check-meltdown-spectre-vulnerabilities-patch-linux/]("https://www.ostechnix.com/check-meltdown-spectre-vulnerabilities-patch-linux/")

```
grep CONFIG_PAGE_TABLE_ISOLATION=y /boot/config-`uname -r` && echo "patched :)" || echo "unpatched :("
```

or

```
grep cpu_insecure /proc/cpuinfo && echo "patched :)" || echo "unpatched :("
```

or
```

dmesg | grep "Kernel/User page tables isolation: enabled" && echo "patched :)" || echo "unpatched :("
```

and 

```
mark@Lexington:~$ uname -r
4.13.0-38-generic
```

this 'puter needs to have it's kernel updated. Per the same, I did

sudo apt-get update

then

mark@Lexington:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

so, I can't upgrade the kernel via the above.

How can I install the most recent kernel?

---

### Post by deadflowr on 2018-04-22
There is a really good meltdown/spectre checking tool you can grab from here:
[https://github.com/speed47/spectre-meltdown-checker]("https://github.com/speed47/spectre-meltdown-checker")

Is this 64-bit or 32-bit?
I ask becaue 64-bit has more patches and 32-bit has limited patches.
See: [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown#Current_Status]("https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/SpectreAndMeltdown#Current_Status")

---

### Post by HermanAB on 2018-04-22
Note that you can get the latest kernel source code from kernel.org and compile it yourself.

---

### Post by Yellow Pasque on 2018-04-22
> Note that you can get the latest kernel source code from kernel.org and compile it yourself. 
If a user want the latest mainline kernel, it would be easier to get kernel 4.16.3 following instructions here:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

I thought Ubuntu enabled KPTI patches in January though :?

---

### Post by Mark_in_Hollywood on 2018-04-22
deadflowr

This is an AMD 64bit CPU

HermanAB

Years ago, I had to upgrade. I recall that there were three separate files and that each had to be installed in a certain order.

Temüjin

Is this the kernel you are referring to?

v3.4.16 mainline build

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.16-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.16-quantal/)

---

### Post by Yellow Pasque on 2018-04-22
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16.3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.16.3/)

---

### Post by deadflowr on 2018-04-22
Run and post the output from the meltdown-spectre-checker script.
I believe AMD doesn't need the pti mitigation.
But the checker script output will give fairly useful info.

---

### Post by Mark_in_Hollywood on 2018-04-22
Spectre and Meltdown mitigation detection tool v0.37+

```
Checking for vulnerabilities on current system
Kernel is Linux 4.13.0-38-generic #43~16.04.1-Ubuntu SMP Wed Mar 14 17:48:43 UTC 2018 x86_64
CPU is AMD FX(tm)-6300 Six-Core Processor

Hardware check
* Hardware support (CPU microcode) for mitigation techniques
  * Indirect Branch Restricted Speculation (IBRS)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates IBRS capability:  NO 
    * CPU indicates preferring IBRS always-on:  NO 
    * CPU indicates preferring IBRS over retpoline:  NO 
  * Indirect Branch Prediction Barrier (IBPB)
    * PRED_CMD MSR is available:  NO 
    * CPU indicates IBPB capability:  NO 
  * Single Thread Indirect Branch Predictors (STIBP)
    * SPEC_CTRL MSR is available:  NO 
    * CPU indicates STIBP capability:  NO 
    * CPU indicates preferring STIBP always-on:  NO 
  * CPU microcode is known to cause stability problems:  NO  (model 2 stepping 0 ucode 0x6000822 cpuid 0x600f20)
* CPU vulnerability to the three speculative execution attack variants
  * Vulnerable to Variant 1:  YES 
  * Vulnerable to Variant 2:  YES 
  * Vulnerable to Variant 3:  NO 

CVE-2017-5753 [bounds check bypass] aka 'Spectre Variant 1'
* Mitigated according to the /sys interface:  YES  (Mitigation: OSB (observable speculation barrier, Intel v6))
* Kernel has array_index_mask_nospec (x86):  NO 
* Kernel has the Red Hat/Ubuntu patch:  YES 
* Kernel has mask_nospec64 (arm):  NO 
> STATUS:  NOT VULNERABLE  (Mitigation: OSB (observable speculation barrier, Intel v6))

CVE-2017-5715 [branch target injection] aka 'Spectre Variant 2'
* Mitigated according to the /sys interface:  YES  (Mitigation: Full AMD retpoline)
* Mitigation 1
  * Kernel is compiled with IBRS support:  YES 
    * IBRS enabled and active:  NO 
  * Kernel is compiled with IBPB support:  YES 
    * IBPB enabled and active:  NO 
* Mitigation 2
  * Kernel has branch predictor hardening (arm):  NO 
  * Kernel compiled with retpoline option:  YES 
    * Kernel compiled with a retpoline-aware compiler:  YES  (kernel reports full retpoline compilation)
> STATUS:  NOT VULNERABLE  (Full retpoline is mitigating the vulnerability)
IBPB is considered as a good addition to retpoline for Variant 2 mitigation, but your CPU microcode doesn't support it

CVE-2017-5754 [rogue data cache load] aka 'Meltdown' aka 'Variant 3'
* Mitigated according to the /sys interface:  YES  (Not affected)
* Kernel supports Page Table Isolation (PTI):  YES 
  * PTI enabled and active:  NO 
  * Reduced performance impact of PTI:  NO  (PCID/INVPCID not supported, performance impact of PTI will be significant)
* Running as a Xen PV DomU:  NO 
> STATUS:  NOT VULNERABLE  (your CPU vendor reported your CPU model as not vulnerable)
```

---


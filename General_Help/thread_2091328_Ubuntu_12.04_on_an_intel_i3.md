---
title: "Ubuntu 12.04 on an intel i3"
date: 2012-12-04
forum: General Help
---

### Post by badnack on 2012-12-04
Hi at all, it is a very long time that i don't post anything; but this time i need help for an annoying issue.
I've installed ubuntu 12.04 on my MSI laptop (using an i3 with 4 gb of RAM); but I've very bad performances.
Particularly it takes a lot of time to start from the login screen (about 1 min) and also the performances of the OS are not so good.
Moreover when i try to move windows it is not so smooth. I've thought it was be due to video driver but launching glxinfo | grep rendering i get "yes".

I've used since yesterday ubuntu 11.10 and it was simple perfect and fast for my laptop, the 12.04 is a disaster. What could be? 

It is unbelievable that an O.S. is unable to be correctly ran on a dual-core machine with 4 gb of RAM.

p.s.
I use gnome-shell since it is a faster; use unity is quite impossible.

---

### Post by badnack on 2012-12-05
I just now realized that the real problem is about moving objects.
I experience lags every time I've to move windows/icons etc. It is not so smooth and the mouse pointer precedes annoyingly the object moved.
As I said I thought it was due to video driver, but it does not seems to be; what am I supposed to do?

---

### Post by rg4w on 2012-12-05
Which Core i3 model?

I'm running 12.10 on a first-gen i3 (330M) and it runs remarkably well.  I would imagine later generations would do even better with the much-improved integrated graphics.

If you post the CPU model I'll see if I can track down any known issues.  May also be good to see the output from lshw to get the full picture.

---

### Post by badnack on 2012-12-05
This is the output of lshw about my processor:

```
description: CPU
       product: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 933MHz
          capacity: 4GHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=1 threads=2
        
```
This is cat /proc/cpuinfo
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 37
model name	: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
stepping	: 5
microcode	: 0x2
cpu MHz		: 933.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt lahf_lm arat dtherm tpr_shadow vnmi flexpriority ept vpid
bogomips	: 4787.84
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```
Honestly I don't know exactly what version of processor is; i just know that it is a Intel Core i3-350M 2.26GHz. If you need more infos just ask :)
My pc is this: [http://www.msimobile.com/level3_productpage.aspx?id=224](http://www.msimobile.com/level3_productpage.aspx?id=224).
I've also tried to use ubuntu 12.04 v. 32 bit; but I've the same (bad) performances.

---

### Post by rg4w on 2012-12-05
Thanks for that info, but offhand I don't see anything that would cause the issues you described.  In fact, you and I have the same generation of i3, just yours is a slightly faster model, but I believe the graphics engine in both is identical, yet I'm seeing pretty good performance here.

Hopefully someone more experienced with diagnosing these sorts of issues will chime in here.  I look forward to seeing what they come up with.

---

### Post by badnack on 2012-12-06
Thanks anyway, tell me just one more thing; when you perform a login how much time your ubuntu tooks to be ready? Mine it tooks about 1 min sometimes.

---

### Post by rg4w on 2012-12-06
For boot times I cheat:  I replaced the HD with an SSD, and also moved /tmp to RAM, so boot times for me are about 10 seconds.

---

### Post by badnack on 2012-12-06
Lol I like it ;)

---

### Post by badnack on 2012-12-06
No one else has any idea? Anyway, rg4w how did you use RAM instead of /tmp ?

---

### Post by rg4w on 2012-12-06
It's been a while since I made the change, but I think I learned which changes to make to fstab from this thread:

[http://ubuntuforums.org/showthread.php?t=1531783](http://ubuntuforums.org/showthread.php?t=1531783)

WARNING: fstab is easy to edit, but not easy to recover from if you mess it up. ;)  You probably know this, but for anyone else who may come across this thread, edit fstab with great care and make a backup of it first.

---


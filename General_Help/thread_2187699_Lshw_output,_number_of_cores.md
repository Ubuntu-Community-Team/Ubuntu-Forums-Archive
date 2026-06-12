---
title: "Lshw output, number of cores"
date: 2013-11-13
forum: General Help
---

### Post by Japhering on 2013-11-13
I have said laptop running  13.04, Raring Ringtail.   

Running lshw shows the following for processor

     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GH
          serial: To Be Filled By O.E.M.
          slot: Socket 989
          size: 933MHz
          capacity: 4GHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
[COLOR=#ff0000]          configuration: cores=4 enabledcores=1 threads=2
[/COLOR]
So Linux thinks I have 4 cores .. but what does enabledcores mean  ?   Shouldn't  cores equal enabledcores  and if so,  where do I start looking to fix this?

---

### Post by efflandt on 2013-11-15
**enabledcores** should normally be same as **cores**. **threads** may be more than that due to hyperthreading. For some reason it looks like you are using only 1 core with hyperthreading (2 threads). I installed 13.10 on a new laptop I got with i7 4700MQ and it shows:

[COLOR=#ff0000]configuration: cores=4 enabledcores=4 threads=8[/COLOR]

My old i5 650 shows enabledcores=2 threads=4

Following should also show number of threads (a speed for each thread): **grep MHz /proc/cpuinfo**

---

### Post by nerdtron on 2013-11-15
[COLOR=#ff0000]configuration: cores=4 enabledcores=1 threads=2[/COLOR]
Does it stay like that even under heavy load? Or are you using battery power? In that case, maybe the computer itself is disabling the other cores in order to save power.

---

### Post by Doug S on 2013-11-15
Interesting. Mine shows the same as the OP, even under load on all 8 cpus. I know that all cores / cpus are working.```
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1155
          size: 1600MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          [COLOR=#ff0000]configuration: cores=4 enabledcores=1 threads=2[/COLOR]
``````
top - 08:07:40 up 20:12,  4 users,  load average: 5.33, 1.95, 0.74
Tasks: 150 total,   8 running, 142 sleeping,   0 stopped,   0 zombie
Cpu0  : 84.8%us,  0.0%sy,  0.0%ni, 15.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  : 84.7%us,  0.0%sy,  0.0%ni, 15.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  : 84.8%us,  0.0%sy,  0.0%ni, 15.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  : 84.9%us,  0.0%sy,  0.0%ni, 15.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu4  : 85.0%us,  0.0%sy,  0.0%ni, 15.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu5  : 85.0%us,  0.0%sy,  0.0%ni, 15.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu6  : 85.0%us,  0.0%sy,  0.0%ni, 15.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu7  : 85.5%us,  0.0%sy,  0.0%ni, 14.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  16004104k total,  4473068k used, 11531036k free,   503684k buffers
Swap:  8294396k total,        0k used,  8294396k free,  2552172k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7353 doug      20   0  4168   92    0 R   85  0.0   1:21.72 waiter
 7355 doug      20   0  4168   92    0 R   85  0.0   1:21.47 waiter
 7349 doug      20   0  4168   92    0 S   85  0.0   1:21.87 waiter
 7354 doug      20   0  4168   92    0 R   85  0.0   1:21.61 waiter
 7352 doug      20   0  4168   92    0 R   84  0.0   1:21.75 waiter
 7351 doug      20   0  4168   92    0 R   84  0.0   1:21.76 waiter
 7356 doug      20   0  4168   92    0 R   84  0.0   1:21.24 waiter
 7350 doug      20   0  4168   92    0 R   84  0.0   1:21.80 waiter
 4259 libvirt-  20   0 12.4g 1.1g 6936 S    4  7.0   2:39.33 kvm
   52 root      25   5     0    0    0 S    1  0.0   4:46.30 ksmd
```

---

### Post by Japhering on 2013-11-15
Even under load my system still reports  

configuration: cores=4 enabledcores=1 threads=2

with htop reporting  all 4 cores with both threads active ..


I'm beginning to wonder if this is a mother board issue...

---

### Post by SeijiSensei on 2013-11-15
If you run "top" and hit the "1" key, you'll see all the cores display like Doug shows above.  How many do you see?

Even my dinky ASUS 1201n netbook with a dual-core Atom shows four cores in use.

---

### Post by Japhering on 2013-11-16
*-cpu
          description: CPU
          product: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GH
          serial: To Be Filled By O.E.M.
          slot: Socket 989
          size: 933MHz
          capacity: 4GHz
          width: 64 bits
          clock: 133MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=4 enabledcores=1 threads=2

top - 00:15:31 up 2 days, 16:23,  6 users,  load average: 0.93, 0.74, 0.48
Tasks: 296 total,   2 running, 293 sleeping,   0 stopped,   1 zombie
%Cpu0  : 29.1 us,  0.7 sy,  0.0 ni, 70.2 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu1  :  5.0 us,  5.7 sy,  0.0 ni, 89.0 id,  0.0 wa,  0.0 hi,  0.3 si,  0.0 st
%Cpu2  :  4.3 us,  8.3 sy,  0.0 ni, 87.4 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu3  : 11.1 us,  2.7 sy,  0.0 ni, 86.2 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu4  : 20.3 us,  0.0 sy,  0.0 ni, 79.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu5  :  0.3 us,  3.0 sy,  0.0 ni, 96.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu6  :  0.3 us, 39.3 sy,  0.0 ni, 21.3 id, 38.7 wa,  0.0 hi,  0.3 si,  0.0 st
%Cpu7  :  0.0 us,  0.7 sy,  0.0 ni, 99.3 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  10165036 total,  7617000 used,  2548036 free,    82568 buffers
KiB Swap:        0 total,        0 used,        0 free,  1626356 cached

---

### Post by SeijiSensei on 2013-11-16
Top shows all eight CPU cores are recognized, and all were in use.

---

### Post by Japhering on 2013-11-16
Yes,  everything seems to be working ... other than lshw ... what does it actually mean ?    

[COLOR=#000000]configuration: cores=4 enabledcores=1 threads=2

and would it work any better if  enabledcores=4 ?[/COLOR]

---

### Post by Doug S on 2013-11-16
I think this is just a case of what we see reported by lshw is not what is really the situation.

---

### Post by mörgæs on 2013-11-16
If this is a bug in lshw it would be good to [report]("http://ezix.org/project/query?status=new&status=assigned&status=reopened&component=lshw&order=priority") it to the developer.

---

### Post by Doug S on 2013-11-16
> **mörgæs said:**
> If this is a bug in lshw it would be good to [report]("http://ezix.org/project/query?status=new&status=assigned&status=reopened&component=lshw&order=priority") it to the developer.I don't think it is a bug in lshw, here is the code fragment:```
            if (data[0x23] != 0)
                newnode.setConfig("cores", data[0x23]);
            if (data[0x24] != 0)
                newnode.setConfig("[COLOR=#ff0000]enabledcores[/COLOR]", data[0x24]);
            if (data[0x25] != 0)
                newnode.setConfig("threads", data[0x25]);
            if (data[0x26] & 0x4)
                newnode.addCapability("x86-64", "64bits extensions (x86-64)");
```I think the issue is in the BIOS, where it is not returning the correct value. See also [http://dmtf.org/sites/default/files/standards/documents/DSP0134_2.7.1.pdf](http://dmtf.org/sites/default/files/standards/documents/DSP0134_2.7.1.pdf) section 7.5.7 (page 50) and Table 20 (page 42). I have never observed any negative operational effect.

Edit: I forgot to mention: Yesterday, I updated by BIOS to the most recent (which turned into a saga), same result.

---


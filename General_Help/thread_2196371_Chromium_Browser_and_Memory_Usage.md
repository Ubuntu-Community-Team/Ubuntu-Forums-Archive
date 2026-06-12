---
title: "Chromium Browser and Memory Usage"
date: 2013-12-29
forum: General Help
---

### Post by amjjawad on 2013-12-29
Hi,

```
Xubuntu 12.04.3 amd64 - 3.2.0-57-generic
```

```
description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3898MiB
     *-cpu
          product: Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq


```

```
Chromium: Version 31.0.1650.63 Ubuntu 12.04 (31.0.1650.63-0ubuntu0.12.04.1~20131204.1)



```
I was on Twitter using Chromium with 2-3 opened tabs. I had Firefox version 26.0 with 8 opened tabs.

While I was uploading a picture to tweet it, my machine became frozen O_o
I was shocked because this is the VERY FIRST time it happens with me on this machine. It is Core i5 2nd generation wit 4GB RAM and 4GB SWAP Partition and I have never ever faced such issue before. Today, it happened 3 times and I managed to access System Monitor and take some screenshots:

[ATTACH=CONFIG]248989[/ATTACH]

[ATTACH=CONFIG]248988[/ATTACH]

Usually, such thing happens with me when I am on my P4 with 512MB RAM and while I use Facebook and Gmail on Chromium, the machine will give me hard time and [Chromium will eventually crash]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1096603"). 

But on such powerful machine that I was using? I am really shocked. For a second, I thought there is a hacker or something but then, I realized it is Chromium that is doing all that.

I have closed all the tabs and kept only one:

[ATTACH=CONFIG]248990[/ATTACH]

[ATTACH=CONFIG]248991[/ATTACH]


Once I closed Chromium Browser, I felt the machine became better.

Have you ever seen something like this before?
No matter how many tabs I open on Firefox, my machine works like a charm. Do you think this is a bug? note that I am using Xubuntu which should be light on resources, I am not using Ubuntu.

Thank you in advance :)

---

### Post by amjjawad on 2013-12-29
I am sorry, I should have mentioned this:

While it is true that I was opening few tabs on Twitter, but I was uploading a picture to retweet it.

I just did a test and the Physical RAM usage jumped 1.5 GB when I was uploading and dropped the 1.5 GB right after the upload is done.

While I was uploading, I was opening tabs (Twitter). 

After I finish the upload, I close the current tab and open new one and re-upload the very same image.

Repeated that several times and my machine was totally frozen for few seconds, even my mouse wasn't moving. Had to wait more seconds until I managed to move it.

I also got the "Wait or Kill" pop-up error message. 

[Chromium didn't crash]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1096603") because SWAP was not yet full.

On Old Machines, it is super easy to produce that but with a machine like mine, I would be hard.

I am doing my best to make it crash. I will keep trying and if I managed to do it then it is 1000% a Chromium related bug and I think Ubuntu has nothing to do with it. But, I could be wrong though :)

P.S.
Also, as far as I can tell, it does not matter whether you have old machine or new, Chromium will act the same way. I think I can prove it if I didn't already ;)

---


---
title: "quad cpu: reports only 1 core available"
date: 2008-06-22
forum: General Help
---

### Post by darco on 2008-06-22
Not sure whats happening here....I just rebooted my pc after I added Conky and Virtualbox. First I lost my screen resolution. I used the recovery mode but had to reinstall the nvida drivers via Envy. Thats ok now. System monitor reports only 1 core functioning instead of the 4 cores that I have w/my Quad Core. Conky reports I am attempting to access more cores than I have and refuses to open.... I have lost audio as gstreamer is saying no audio devices found. I have updated my pc OS (Mint) and have not made any other recent changes I can think of.
Help please!
darco

---

### Post by cariboo on 2008-06-22
A couple of things you can do. First in a terminal type:

```
uname -a
```

You should see something like this:

```
Linux intrepid 2.6.26-2-generic #1 **SMP** Thu Jun 19 15:49:49 UTC 2008 x86_64 GNU/Linux
```

Note the **SMP** that stands for symmetric multiprocessing if that isn't in the output of uname -a then you have the wrong kernel.

The next thing to try, is in a terminal type:

```
cat /proc/cpuinfo > cpuinfo.txt
```

that will output to a file called cpuinfo.txt, listing of a lot of info about your cpu it should show you 4 cpu's.

Jim

---

### Post by darco on 2008-06-22
I think you are correct. I am showing a 386 kernel instead of the i686. How the heck did that happen? Just today I saw on Conky that my Kernel was 686.

```
uname -a
Linux dar-mint 2.6.24-16-386 #1 Thu Apr 10 12:50:06 UTC 2008 i686 GNU/Linux

```

```
 sudo cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
stepping	: 11
cpu MHz		: 1596.000
cache size	: 4096 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4779.53
clflush size	: 64

```

What do I need to do now?
thxs
darco

---

### Post by darco on 2008-06-22
Ok i was able to boot from the -16 generic kernel fine. I then edited the menu.lst to move this kernel to the top. Rebooted and all looks good. i normally dont notice but is this the latest kernel version I should be running?:

```
Linux dar-mint 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

```

thxs
darco

---


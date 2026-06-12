---
title: "How do I identify my processor?"
date: 2007-12-01
forum: General Help
---

### Post by scottnadeau on 2007-12-01
Hi all,
I know I have an AMD Sempron 2800+, but I don't know if it's a 32bit or 64 bit - they made both.  Is there a command line utility that will tell me what I have?  I'm on Ubuntu 6 - if I navigate to System> Preferences> Hardware Information> Processor, the left side of the screen displays the processor as "AMD Sempron 2800+", but the right side displays all the details as "Unknown".

Any thoughts?

Thanks!
Scott

---

### Post by zvacet on 2007-12-01
```
lshw
```

---

### Post by stroyan on 2007-12-01
You can look for a "lm" value in the flags: line from running "cat /proc/cpuinfo".
That "lm" flag is long mode, 64-bit addressing.  It will only be present on cpus that
can handle 64-bit mode.

---

### Post by zvacet on 2007-12-01
```
lspci
```

---

### Post by mysticrider92 on 2007-12-01
According to a website I found, any socket 754, 939, and AM2 Semprons are 64 bit. So if you have a socket A it is 32 bit. The 64 bit AMD processors have '64' in the name (e.g. AMD Sempron 64 2800+), but I don't know if that helps you at all.

[edit] guess you beat me to it...

---

### Post by prodezigner on 2007-12-01
uname -a

if it says x86_64 it's 64 bit... if it's iX86 then it's 32-bit (where X is the platform)

---

### Post by mysticrider92 on 2007-12-01
> **prodezigner said:**
> uname -a

if it says x86_64 it's 64 bit... if it's iX86 then it's 32-bit (where X is the platform)

That would only tell you what your kernel is. But the uname -a also prints out your processor name, which if it says Sempron 64, it is 64 bit capable.

---

### Post by skymera on 2007-12-01
try

cat /proc/cpuinfo

---

### Post by scottnadeau on 2007-12-01
Here's the output I get from a few commands:

$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 28
model name      : AMD Sempron(tm) Processor 2800+
stepping        : 0
cpu MHz         : 1603.813
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt 3dnowext 3dnow up lahf_lm ts ttp
bogomips        : 3211.38
clflush size    : 64

$ uname -a
Linux ubuntu 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux


I see the flag lahf_lm in the flags section - is this a possible 64 bit flag?  I also see just plain i686 (with no _64 suffix) - this leads me to believe it's 32 bit.  

Can I identify the socket type by pulling the cover and visually looking at it?  Maybe it's screen printed on the PCB?  I'd rather not remove the processor to see the pin layout, and I know I won't be able too see the label due to the fan...

Thanks very much for the fast responses so far!

Scott

---

### Post by stroyan on 2007-12-01
[http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/25481.pdf](http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/25481.pdf) and
the kernel source in /arch/x86_64/kernel/setup.c indicate that lahf_lm indicates whether the LAHF and SAHF instructions are available when in 64-bit mode.  But a processor that really supported 64-bit mode really should have the "lm" flag set.  It definitely looks like you have a 32-bit only CPU.

---

### Post by scottnadeau on 2007-12-01
Thank you very much ladies and gentlemen.  I really appreciate the quick help.

Have a great night and a Merry Christmas!
Scott

---

### Post by bbaaxx on 2008-01-09
Yo Scott,

I'm sorry to tell you that Stroyan is right, only I didn't knew about the im flag, so i did something different (a lot more troublesome but maybe someone can find this helpful):

I found this tool on the AMD website:

[http://products.amd.com/en-us/DesktopCPUFilter.aspx](http://products.amd.com/en-us/DesktopCPUFilter.aspx)

Using this tool and the information i got from running: cat /proc/cpuinfo I was able to identify my processor, here:

[http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=167](http://products.amd.com/en-us/DesktopCPUDetail.aspx?id=167)

On this page it explicitly says that the 64bit operation mode is not available.

Ohh, and I knew that yours is 32bit only because it seems that I have the same CPU as you, here is the output of my /proc/cpuinfo file:

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 28
model name      : AMD Sempron(tm) Processor 2800+
stepping        : 0
cpu MHz         : 1608.005
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up lahf_lm ts ttp
bogomips        : 3217.71
clflush size    : 64


I hope it helped ;)

---


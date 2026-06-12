---
title: "No more dual core with new Edgy kernel"
date: 2007-02-25
forum: General Help
---

### Post by Talon2 on 2007-02-25
An Edgy kernel update flowed into my system via Software Updates recently.  I'm not sure exactly when it happened but I saw a couple of things that make me look into the matter.  Here is what "uname -a" gives me:

 2.6.17-11-386

Here is what "cat /proc/cpuinfo" gives me now:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
stepping        : 9
cpu MHz         : 3200.589
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
bogomips        : 6406.06

--- This indicates to me that HT is now not being used which accounts for some of the behavior I was seeing.

The previous Edgy kernel was  "2.6.17-10-generic".  This kernel did support HT.

What is going on and how to I get my HT support back?

---

### Post by Vivix729 on 2007-02-25
try 

```
sudo apt-get install linux-i686-smp
```

---

### Post by Ramses de Norre on 2007-02-25
You're on linux-386 which doesn't support smp (and never did in older versions neither), on edgy i686(-smp) is deprecated, you need to install linux-generic.

---

### Post by eggdeng on 2007-02-25
You can still boot with your generic kernel by choosing that option from the grub menu. If you want to set it as default, find the line ```
 default 0
``` in /boot/grub/menu.lst. This sets the default option as the first option in the list so just replace the 0 with the number that corresponds to the position of your old kernel in the list & reboot.

---

### Post by Talon2 on 2007-02-25
> **Ramses de Norre said:**
> You're on linux-386 which doesn't support smp (and never did in older versions neither), on edgy i686(-smp) is deprecated, you need to install linux-generic.

You are telling what I thought to be what has happened with development:  That the specific kernels had been replaced by the "generic" version starting with Edgy.

When I installed (clean) Edgy on this box after release last year the kernel that was installed was the "generic" kernel and HT was supported.  Everything was great.  Why is it that the Software Updates utility changed my system to a "-386" kernel?  I haven't played around on this box, the kernel was changed for me.  This seems strange.

Also, I didn't think specific kernels were available for Edgy, just "generic."  

I'm installing the generic kernel as I write.  Something just seems mucked up and I'm not sure what it is.

Thanks for the replies.

---

### Post by russell.h on 2007-02-25
My edgy install the 386 kernel when I installed the nvidia binary driver.

---

### Post by Ramses de Norre on 2007-02-27
When you don't want the 386 kernel you need to uninstall linux-386, that should stop it from installing/upgrading it.

---


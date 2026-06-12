---
title: "[SOLVED] Kernel advice - dual core - 386 or 686"
date: 2008-06-08
forum: General Help
---

### Post by jimmy the saint on 2008-06-08
I was poking around the interwebs the other day and I came across an article that gave advice on what to do immediately after installing Ubuntu.  I cannot find the article again for some reason, but I believe it was at linux.com.  Anyway, the article suggested that if you have a newere processor (i.e. Anything more than 5 years old) you should ditch the default i386 kernel and install the i686 kernel via synaptic.  It goes on to explain that this will enable Ubuntu to use the modern instruction sets that the i386 kernel is not capable of using.  Is the 686 kernel 64bit?  Can anyone explain what the difference is and if it is indeed recommended?  I have never came across that particular advice before so I would really like your input before I attempt it.  

Thanks

JTS

---

### Post by steveneddy on 2008-06-08
If you have a dual core processor, you really should run the 64 bit version of Ubuntu. You'll be much happier.

---

### Post by jimmy the saint on 2008-06-08
is that what i686 is?  Since I have a lot of programs and such installed, is it as simple as installing the 686 kernel, or do I need to start with a fresh install from scratch?

---

### Post by jimmy the saint on 2008-06-08
Ok, I got my questions answered. i found a page that details how choose the right kernel.  The only problem is that it was written a few years ago and says that the package "linux-686-smp" is required for multi-core and hyper-threading.  There are several packages in synaptic that relate to linux-686, but none have the smp part.  Have these features been incorporated?  should I install the other packages as well?  these include the "image," the "headers," and a special restricted modules package.

---

### Post by housam on 2008-06-08
Edit : before Edgy this was required to get the dual core processor identified . but the newer versions of ubuntu has it now . so you don't need to install it. the generic kernel versions detect the dual boot processors.

---

### Post by jimmy the saint on 2008-06-08
ok, I installed the package "linux-686" and restarted.  There are no new kernels listed in the grub menu.  I confirmed through synaptic that the package is installed.  i cannot find a good guide that goes into detail about this.  what have i missed here?

Update:  Now I have installed all 4 of those packages and still no new kernel showing up.  i must be doing something wrong, but I can't figure out what it is

---

### Post by housam on 2008-06-08
open you grub menu.lst to see if it has it or not.
```
 gksudo gedit /boot/grub/menu.lst
```

---

### Post by steveneddy on 2008-06-08
Back up your data and do a complete reinstall to the 64 bit version.

---

### Post by jimmy the saint on 2008-06-08
Its not on the grub list.  "Ubuntu 8.04, kernel 2.6.24-18-generic"  is the most recent kernel listed.

---

### Post by jocko on 2008-06-08
There is no point installing the "linux-686" package.
It's just a metapackage which will install the "-generic" kernel.
The instructions you have found were written for an old version of ubuntu, where the -386 kernel was default and to get full support for anything better than a pentium II processor you had to install optimized kernels for specific processors families (686 for pentium III or better intel processors, -k7 for duron and better amd processors).
The "-generic" kernel will detect which processor you have and load the optimizations that are needed.

But if you have a 64 bit processor (I don't think all dual core processors are 64 bit), you will get support for more memory and get better performance if you install a 64 bit os.

---

### Post by housam on 2008-06-08
in the grub menu.lst you will find a similar to the following part 
> ### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_[COLOR="Red"]686[/COLOR]=root=/dev/hdc2 ro
# kopt=root=UUID=fde58ebd-aee0-485e-8e61-58b739d00877 ro

---

### Post by housam on 2008-06-08
you can also type in the terminal 
```
cat /proc/cpuinfo
```
if you got infos about your dual core as processor 0 and processor 1, then you don't need to do any installation for dual core.

here is mine 
> housam@housam-laptop:~$ cat /proc/cpuinfo
[COLOR="Red"]processor	: 0[/COLOR]
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping	: 8
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr
bogomips	: 3994.75
clflush size	: 64

[COLOR="Red"]processor	: 1[/COLOR]
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping	: 8
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts pni monitor vmx est tm2 xtpr
bogomips	: 3990.28
clflush size	: 64


---


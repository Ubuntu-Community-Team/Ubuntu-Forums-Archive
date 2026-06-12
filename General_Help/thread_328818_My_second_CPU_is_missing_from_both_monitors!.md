---
title: "My second CPU is missing from both monitors!"
date: 2006-12-31
forum: General Help
---

### Post by wilberfan on 2006-12-31
I installed GKrellM a couple of weeks ago, used it for awhile, then went back to gdesklets.  Today I decided to give GKrellM another chance, but when I started it up, it's not showing both CPU's of my AMD 64x2 (I'm running Edgy-32).

I have another desktop monitor (by chilehardware) running on my Kubuntu desktop and it's 2nd CPU graph is flatlined at zero...

What could have changed, and how can I restore those readings?

---

### Post by bulldog on 2006-12-31
Which kernel do you use?
You should have the generic smp kernel which supports two multiple CPU's

---

### Post by MetalMusicAddict on 2006-12-31
Check the kernel like bulldog said and some monitors (ie: gDesklets ones) show both CPU averages as one average. ie: 50% usage = 100% usage of one CPU.

---

### Post by wilberfan on 2006-12-31
> **bulldog said:**
> Which kernel do you use?
You should have the generic smp kernel which supports two multiple CPU's

Uh oh.   How do I check that?   If I DON'T have it--how do I get it?

---

### Post by ZylGadis on 2006-12-31
```
cat /proc/cpuinfo
```
If you see just one cpu there, you need another kernel. If you see two, you are fine, no matter what the monitor tells you.

---

### Post by wilberfan on 2006-12-31
> **ZylGadis said:**
> ```
cat /proc/cpuinfo
```
If you see just one cpu there, you need another kernel. If you see two, you are fine, no matter what the monitor tells you.

Looks like I'm missing something!

> wilberfan@AMD64:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 35
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
stepping        : 2
cpu MHz         : 1000.000
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni lahf_lm cmp_legacy ts fid vid ttp
bogomips        : 2012.48

How do I get another kernel?   (Are we talking about the ***Linux*** kernel??)

> wilberfan@AMD64:~$ uname -r
2.6.17-10-386

---

### Post by bulldog on 2006-12-31
```
sudo aptitude install linux-generic meta-package
```should do the trick if I'm not mistaken.

---

### Post by wilberfan on 2006-12-31
> **bulldog said:**
> ```
sudo aptitude install linux-generic meta-package
```should do the trick if I'm not mistaken.

Hmmm.....

> wilberfan@AMD64:~$ sudo aptitude install linux-generic meta-package
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
[COLOR="Red"]Couldn't find any package matching "meta-package"[/COLOR].  However, the following
packages contain "meta-package" in their description:
  cdd-doc xubuntu-at-mag bacula-server libsope4.4-dev php4 php5 
  xfce4-goodies gforge xfce4 linux-image-2.6.17-10-386 rancid-installer 
  linux-image-2.6.17-10-generic gforge-theme-starterpack pythoncard 
  linux-image-2.6.17-10-server-bigiron sylpheed-claws-plugins kst bacula 
  bacula-client xubuntu-at-speech linux-image-2.6.17-10-server r-base 
  nagios-plugins xmltv hotswap 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

:-k

---

### Post by bulldog on 2006-12-31
Go into synaptic and search for linux-generic meta-package and you will see the kernel you want.
I was thinking it could be done with aptitude,but I was wrong I guess :(

---

### Post by David Corrales on 2006-12-31
The package meta-package doesn't exist :) I think you meant that kernel-generic is itself a meta package.

---

### Post by wilberfan on 2006-12-31
Huzzah!

I HAD the generic kernel installed, but it was the *second one listed *in my GRUB menu!   I had no idea!!   I've reconfigured menu.lst to make the generic kernel the default and now GKrellM has TWO CPU's listed!    :mrgreen: 

What is that "non-generic" kernel, and how did it get first-in-line??

[Edit ]   Gawd!!! Everything is so much FASTER now!!  :cool:  :D

---

### Post by MetalMusicAddict on 2006-12-31
You can remove the -386 kernels and that should do it. You could also remove the entries for the -386 kernels from the menu.lst

---

### Post by MasterZ on 2007-02-02
Hello, 

I have the same 'issue' as wilberfan here, but I installed lots of drivers (nvidia, evdev,...) on the 386 kernel. 
The generic kernel is listed in grub but I fear that I'll be losing my drivers and modules if I use it. 
Am I wrong ? 

What will be the gain if I use the generic kernel ? Is it just a matter of "seeing" the second CPU or do I currently only use one (which mean I could run much faster with the other kernel ? ) ??

MasterZ

---

### Post by wilberfan on 2007-02-02
> **MasterZ said:**
>  

What will be the gain if I use the generic kernel ? Is it just a matter of "seeing" the second CPU or do I currently only use one (which mean I could run much faster with the other kernel ? ) ??

MasterZ

I have a feeling you'll see much faster speeds.  I'm pretty sure that only ONE of my CPUs were being used before I switched kernels.  (I have a post somewhere about how "creaky" Amarok was on this blazing fast PC.   That problem was solved after I started loading the "proper" (generic) kernel...

Anyone know how to 'remove' the kernel I'm not using anymore?  (ie, the non-generic one?)

---

### Post by JoxBG on 2007-03-23
> **wilberfan said:**
> 
Anyone know how to 'remove' the kernel I'm not using anymore?  (ie, the non-generic one?)

Use Synaptic, look in base group, you should find the installed kernels.  Choose those you want removed. Synaptic will also adjust your grub menu.

Or if you know the exact package name including version number, e.g. 2.6.15-28-386, you can use command line:

    sudo aptitude remove <package name>

The  xxx-686 modules are generally SMP enabled, xxx-386 for single CPU.


Jox

---


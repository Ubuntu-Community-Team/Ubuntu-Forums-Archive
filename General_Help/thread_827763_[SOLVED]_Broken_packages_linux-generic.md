---
title: "[SOLVED] Broken packages linux-generic"
date: 2008-06-13
forum: General Help
---

### Post by birdySi on 2008-06-13
Hi, when I try 

```
sudo apt-get -y install linux-generic
```

I got problem with broken packages

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-generic: Depends: linux-image-generic (= 2.6.24.18.20) but 2.6.24.19.21 is to be installed
E: Broken packages
```

I already tried in Synaptic Package Manager to Fix Broken Packages, but it didn't help. 

Does anybody has an idea how to solve the problem.

---

### Post by denham2010 on 2008-06-13
Hi,

It appears from the readout you have posted that the package linux-generic depends on an earlier version of linux-image-generic.

You may need to check for a more recent version of linux-generic.

The easiest way I know of would be to open synaptic and search linux-generic and see if there is a version there that matches the version of linux-image-generic that is going to be installed. They should both have the same version numbers.

The other solution is to force synaptic, or apt-get if you prefer using the command line, to install the earlier version of linux-image-generic.

You can do this in synaptic by right clicking the linux-image-generic package and selecting force version.

Beware though, these are kernel images you are playing with here. Forcing a downgrade may cause many issues with other installed packages and can break your system, to the point where you may have to re-install from scratch.

You really need to know and understand what you are doing before proceeding. At the very least, make a backup of your entire system so you can recover should the worst happen.

Cheers.

---

### Post by iaculallad on 2008-06-13
What about:

```
sudo apt-get install -f
```

---

### Post by birdySi on 2008-06-13
When I try to reslove problem in Synaptic Package Manager I got problem (see attached image).

When I try to run command:

```
sudo apt-get -f install linux-generic
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-generic: Depends: linux-image-generic (= 2.6.24.18.20) but 2.6.24.19.21 is to be installed
E: Broken packages
```


So, nothing realy helped. Any other suggestion? I must admit I'm realy disapointed with 8.04! I have also problem with nvidia driver. I can't belevie they released so bad version. This should be BETA version and not real version. And almost every day there are 10+ updates. This remindes me on some other OS....

---

### Post by plucky on 2008-06-13
>  linux-generic: Depends: linux-image-generic (= 2.6.24.18.20) but 2.6.24.19.21 is to be installed
E: Broken packages


Can you post output of ```
uname -a
``` For some reason it is saying that 2.6.24.19.21 is to be installed,but the current kernel is 2.6.24.18.20.

Do you have the proposed and backport repositories enabled?

---

### Post by birdySi on 2008-06-13
uname -a gives result:

```
Linux gkkista 2.6.24-19-386 #1 Wed Jun 4 15:54:02 UTC 2008 i686 GNU/Linux
```

And about repositories. I have enabled backports, but disabled proposed. What should I do? Both disable?

---

### Post by birdySi on 2008-06-13
Ok, I have enabled proposed and backports. After several updates I finaly managed to solve Broken packages problem. But main reason why I started to upgrading linux-generic is that I have Dual core proccessor, but Ubuntu runs only on one, it does not recognize dual core. My /proc/cpuinfo looks like:

```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
stepping	: 6
cpu MHz		: 1596.000
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4269.88
clflush size	: 64
```

Does anybody have idea how to solve this promblem. Tnx

---

### Post by plucky on 2008-06-13
> Linux gkkista 2.6.24-19-386 #1 Wed Jun 4 15:54:02 UTC 2008 i686 GNU/Linux


The problem is you have that kernel installed.

I just enabled backports and didn't find that kernel ,but did when I enabled proposed.So that kernel will probably get installed sometime in the future.

I suppose you could use **Synaptic Package Manager** to remove it,but you do so at your own risk.I have never tried to downgrade a kernel.

Do you have any previous kernels in your GRUB menu?

Is there a reason for using that kernel? Just saw your previous response

That is definitely not the correct kernel,I would boot into a previous kernel and do the upgrade from there.Then remove that kernel.I think you do need the generic kernel.


Good LUck

---

### Post by birdySi on 2008-06-13
Well yes, the reason why I used 386 kernel is that I had some problem with nvidia drivers. In Synaptic Package Manager I removed 386 kernel and made an upgrade of generic kernel. It seems that now works fine.

Tnx for help

---


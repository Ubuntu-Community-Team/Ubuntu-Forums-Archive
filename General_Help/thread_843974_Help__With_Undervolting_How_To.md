---
title: "Help  With Undervolting How To"
date: 2008-06-29
forum: General Help
---

### Post by SyntheticShield on 2008-06-29
First, let me say that there is a tutorial already in the forums for undervolting, however it is geared more towards the Indel Dual Core processors.  So I started searching for a way to do so on my AMD Sempron processor for my laptop.

I was hitting a brick wall so I checked with the #ubuntu IRC channel and ran across a person that pointed me to this How To:

[https://wiki.ubuntu.com/UndervoltingHowto](https://wiki.ubuntu.com/UndervoltingHowto)

I tried following those directions and ran into the issues and so I searched for more info regarding the problem I was having.  I ran across this How To:

[https://www.dedigentoo.org/trac/linux-phc/wiki/phc_howto_ubuntu_001](https://www.dedigentoo.org/trac/linux-phc/wiki/phc_howto_ubuntu_001)

Both are basically the same but I thought I would post them just in case there are any questions regarding the process.  However I am running into an issue with one of the commands that is supposed to be run.

Each how to says to run this command:

```

patch -p1 < ../linux-phc-0.3.0/kernel-patch/linux-phc-0.3.0-kernel-ubuntu-2.6.20.patch

```

But when I do that I get the following:

```

:~/undervolt/linux-2.6.24$ patch -p1 < linux-phc-0.3.0-kernel-vanilla-2.6.23rc3.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --new-file -a --unified=5 --recursive linux-2.6.23-rc3/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.c linux-source-2.6.23-rc3/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.c
|--- linux-2.6.23-rc3/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.c	2007-08-13 06:25:24.000000000 +0200
|+++ linux-source-2.6.23-rc3/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.c	2007-08-14 15:33:30.000000000 +0200
--------------------------
File to patch: 

```

I dont know which file it should be patching.  Im assuming the kernel file, but Im not really sure and hoped that someone here could help me out with some guidance.  Im trying to find the answers and googling and searching but not coming up with much.

I would appreciate any assistance.

---

### Post by PmDematagoda on 2008-06-29
Is the patch file in the kernel source folder?

---

### Post by SyntheticShield on 2008-06-29
Yes, I copied it over there as part of the how to steps, but also confirmed it is there by navigating to that folder.

---

### Post by PmDematagoda on 2008-06-29
It seems that you have the wrong kernel version since the patch is made for 2.6.23rc3 and the source you have is 2.6.24, so in order to use it you would have to find a new patch that is made for the particular kernel you want to patch or you will have to edit it(this is really risky).

---

### Post by SyntheticShield on 2008-06-29
Well crap.  I keep hitting brick walls trying to undervolt my AMD Sempron processor.  I feel so left out, LOL.

---

### Post by PmDematagoda on 2008-06-29
> **SyntheticShield said:**
> Well crap.  I keep hitting brick walls trying to undervolt my AMD Sempron processor.  I feel so left out, LOL.

Uhm, I don't think patching the kernel would have helped if you have an AMD:-
> AMD processors are currently not supported. But some work is in progress on a patch for the powernow-k8 cpufreq driver. We plan to include this patch in the next major release of Linux-PHC.

---

### Post by SyntheticShield on 2008-06-29
Well double crap.  I had read information here and there that suggested getting it to work with the AMD processor was a shot in the dark more or less and well obviously I decided to take that shot.

I guess I'll just put that little project aside until there is support for the AMD processor.

---


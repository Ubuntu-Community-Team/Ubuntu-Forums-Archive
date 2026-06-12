---
title: "Can my laptop run KVM (plus is it 32- or 64-bit)?"
date: 2013-06-18
forum: General Help
---

### Post by vasa1 on 2013-06-18
I'm not at all hardware-savvy so please excuse me :(

I have a Dell Inspiron 1545 laptop (2009 vintage). And have read (a very little) about KVM and about how it can be used to test pre-release versions of Ubuntu.

According to [http://acidborg.wordpress.com/2010/02/18/how-to-create-virtual-machines-using-kvm-kernel-based-virtual-machine/](http://acidborg.wordpress.com/2010/02/18/how-to-create-virtual-machines-using-kvm-kernel-based-virtual-machine/) , 
```
egrep '(vmx|svm)' --color=always /proc/cpuinfo 
```

should tell me if I can run KVM. I just get the prompt back indicating that my laptop isn't fit for KVM.

According to [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation) ,
>  To see if your processor supports one of these, you can review the output from this command:

```
egrep -c '(vmx|svm)' /proc/cpuinfo
```

If **0** it means that your CPU doesn't support hardware virtualization.

If **1 or more** it does - but you still need to make sure that virtualization is enabled in the BIOS.

I get **2**.

So I'm confused.

Also, how do I know if my computer is 32- or 64-bit? I somehow took it for granted that it is 32-bit and have always installed 32-bit versions of Ubuntu. I have 4GB RAM and can't install more than that according to the little booklet that came with my laptop.

With **lscpu**, I get the following:
```
[11:07 AM] ~ $ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              10
CPU MHz:               2000.000
BogoMIPS:              3990.10
L1d cache:             32K
L1i cache:             32K
L2 cache:              2048K

```

PS: I use my laptop for light stuff: browsing, watching videos, spreadsheets.

---

### Post by ahallubuntu on 2013-06-18
~

---

### Post by vasa1 on 2013-06-18
Hi, this is what I got:
```
product: Intel(R) Core(TM)2 Duo CPU     T6400  @ 2.00GHz
```
So I guess it's no KVM for me :(. I'm not up for upgrading the CPU. If anything when my laptop dies, I'll try to get a more capable one. 

Thanks for replying and clearing my doubts!

---

### Post by vasa1 on 2013-06-18
Thanks to ahallubuntu, I found [http://ubuntuforums.org/showthread.php?t=1225346](http://ubuntuforums.org/showthread.php?t=1225346) and [http://ark.intel.com/products/40479/](http://ark.intel.com/products/40479/). But the first link, if I read it correctly, implies that it's possible to use VirtualBox (instead of KVM) to virtualize 32-bit operating systems:
>  If you run a platform such as Virtual Box in support of 32 bit guest systems you also will not see the problem.

---


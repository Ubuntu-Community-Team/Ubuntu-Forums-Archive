---
title: "Install new Kernel"
date: 2006-12-07
forum: General Help
---

### Post by ghepardo on 2006-12-07
Hi, I have a pentium 4 and I want to install a new kernel right for my machine.
On this forum I found that I should install this:

sudo apt-get install linux-686-smp

I did it but in grub I dont have the option to start with this kernel. What can I do!?

---

### Post by ghepardo on 2006-12-07
up plz

---

### Post by amo-ej1 on 2006-12-07
```

e@lap:~$ apt-cache search linux-686-smp
linux-686-smp - Obsoleted by: linux-image-generic
e@lap:~$ apt-cache search linux-image-generic
linux-image-686 - Obsoleted by: linux-image-generic
linux-image-generic - Generic Linux kernel image
linux-image-k7 - Obsoleted by: linux-image-generic
linux-686-smp - Obsoleted by: linux-image-generic

```

could you do a *dpkg -l | grep kernel* that will show you some pacakges containing which contain a kernel than use * dpkg -L linux-image-2.6.17-10-386  * where (linux-image-....) is the package name to check which files are included in that package. Probably you installed some dummy package which contained nothing ...

---

### Post by ghepardo on 2006-12-07
This means the package linux-686-smp is included into linux-image-generic !?

So I dont need to install a 686-smp kernel image because the generic-image is already 686-smp!?

---

### Post by amo-ej1 on 2006-12-07
what does your uname -a say you ?

---

### Post by ghepardo on 2006-12-07
Linux manu-desktop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

So I think I am already with a 686-smp kernel, right?

---

### Post by amo-ej1 on 2006-12-07
that's what SMP means in that response ;-)

take a look at the /proc/cpuinfo file to see information on the detected cpu's

---


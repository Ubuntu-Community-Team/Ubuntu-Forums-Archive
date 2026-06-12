---
title: "Fan at maximum speed after suspend on HP laptop with kernel &gt;3.17"
date: 2015-09-14
forum: General Help
---

### Post by FizzBuntu on 2015-09-14
Hello
I'm trying to find a better fix to a problem.
I'm using an HP 2510p laptop (a bit aging but working great).
Everything works OK until you use suspend mode. When it wakes up, the fan spins at maximum speed and never stops regardless of activity or temperature.
The problem happens on Ubuntu, Xubuntu and UbuntuStudio for sure and seems to be related to the kernel. I've tested a Manjaro distrib using a 4.1 kernel and the problem was the same (but the fan was running always max, even without suspend).
I've tested it with an older kernel (3.17) and the problem doesn't show. From what I gathered, the problem begins with 3.18 kernels.

Is there any other ways to fix this problem ?

thx

---

### Post by dino99 on 2015-09-14
3.17 is not a supported ubuntu kernel

---

### Post by FizzBuntu on 2015-09-14
> **dino99 said:**
> 3.17 is not a supported ubuntu kernel

Apparently it is:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by FizzBuntu on 2015-09-16
Anyone ?

---

### Post by gorthx on 2015-10-31
I just upgraded to Vivid Vervet + 3.19.0-26 from Trusty Tahr + 3.16 (I think) and am having the same issue. 

I'm trying this as a temporary workaround: [https://bugzilla.redhat.com/show_bug.cgi?id=895276#c18](https://bugzilla.redhat.com/show_bug.cgi?id=895276#c18), but I really don't like mucking about with the cooling on this machine as it does get quite warm.  (I am also on a 2510p - they are great little machines & I am trying to keep this one going as long as I can.)

---


---
title: "trying to get ATI drivers to work with linux-rt kernel"
date: 2008-03-18
forum: General Help
---

### Post by el_ricardo on 2008-03-18
hi all, I'm currently trying to get the ATI 8.3 drivers (off the ATI website, not repos) to install with linux-rt. I did the buildpkg method for my generic kernel, in which everything works just fine, but when i try to do it while i'm booted in rt, dpkg tells me that i need to do a dkms build on linux-rt. I've tried fiddling about with dkms and can't figure out how to make it work, I gave the command

```

dkms build -k linux-rt -v 2.6.22-14

```

but it says that there's an incorrect number of parameters, despite me following the instructions in dkms -- help.

I installed the kernel headers, and dpkg tells me the same thing, i rebuilt the .deb files while booted into the rt kernel, and still the same thing.

anyway, I'm probably missing something obvious, as i'm still new to all this in all honesty, here's some specs if it's any help:

ATI card: radeon 2900XT
driver version: 8.3
kernel version: 2.6.22-14 i686 (generic and rt)
CPU: p4 3.4GHz

please help, I need linux-rt to be fully functional for a couple of my programs to run properly!

thanks in advance!

---

### Post by el_ricardo on 2008-03-19
bump?

---

### Post by el_ricardo on 2008-03-21
oh come on!!!!! bump!!!!

---

### Post by sonicmaker on 2008-06-08
Patience is a virtue...

Did you ever try to install linux-rt from the Ubuntu repository and the ATI drivers using Envy? I've just switched to Ubuntu Studio which uses the linux-rt kernel (2.6.24-18), and my ATI drivers which were installed before I switched still work (albeit with a few artifacts, but not enough to render it unusable, and strangely there are fewer artifacts every time I start up :P). That might be a simpler solution for you, if you haven't already fixed it...

---

### Post by sonicmaker on 2008-07-21
Eating humble pie is also a virtue :-P

Have you found a solution to your problem? I'm having the same problem now... I've found that people have had the same problem with Nvidia drivers and have found a workaround, but I haven't found (yet) any solutions for ATI...

---


---
title: "linux-source: no .config ?"
date: 2007-09-09
forum: General Help
---

### Post by rihad on 2007-09-09
How do I know how linux-source was configured and built in 7.0.4? I installed it with aptitude in /usr/src/linux-source-2.6.20.tar.bz2 but there's no .config inside when unpacked.  My intention is to just set CPU optimizations to amd64 from "make menuconfig", while retaining any tailored settings.

---

### Post by jocko on 2007-09-09
You could copy the config from your running kernel and use it to configure your source.
Run these commands in the directory where you have unpacked the source:
```
cp /boot/config-`uname -r` .config
make oldconfig
```(If you don't have write permission to the directory you need to add "sudo" before both commands)
[More help here]("http://ubuntuforums.org/showthread.php?t=311158")

---

### Post by rihad on 2007-09-10
Oh no, I somehow forgot to look there... thanks a lot! BTW, description of linux-source package states that "The Ubuntu patches have been applied." What are the Ubuntu patches? Anything improving server stability/performance?

---

### Post by rihad on 2007-09-11
Anyone?

---

### Post by mcduck on 2007-09-11
Don't waste your time with that. Ubuntu's kernels enable correct optimizations for your CPU at boot time..

---

### Post by rihad on 2007-09-11
You mean by rewriting assembly code on the fly? :) I'm talking about flags being passed to gcc when compiling the kernel.

---

### Post by mcduck on 2007-09-11
> **rihad said:**
> You mean by rewriting assembly code on the fly? :) I'm talking about flags being passed to gcc when compiling the kernel.
Here's some discussion from Ubuntu devs about not building separate kernels for every different CPU, and if you follow the posts you'll also find some test data that shows that there is no important difference in performance between the generic build and build specifically made for the CPU used. 

[https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-August/019983.html")

> Since Linux has always offered CPU-specific optimizations, it's been taken
for granted that this offered enough of a performance benefit to make all of
this maintenance effort worthwhile.  A lot has happened to the kernel since
the early days, though, and for some time, it has been capable of loading
these optimizations at runtime.  Even when you use the -386 kernel, you get
the benefit of many CPU-specific optimizations automatically.
.
.
.
Having read over it, I think the numbers are fairly compelling.  The
difference in performance between -386 and -686 is insigificant; the
measurements are all within a reasonable error range, and within that range,
-686 was slower as often as it was faster.


Anyway, if you really wish to make your system faster you'd probably spend your  time better turning off services you don't need..

---


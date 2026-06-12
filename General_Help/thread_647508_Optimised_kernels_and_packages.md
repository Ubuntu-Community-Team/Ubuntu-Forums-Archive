---
title: "Optimised kernels and packages?"
date: 2007-12-22
forum: General Help
---

### Post by andrewcmcardle on 2007-12-22
Hi, i read that ubuntu linux is slower than some other distros because it uses a non optimized kernel, ie one which fits many different architectures. Are there any benefits to getting a kernel which better fits your architecture, and if so how would one go about finding and installing a better kernel. On a similar note is there any difference in building architecture optimized programmes from source, as opposed to installing binary packages.

Basically is it possible and benifitial to optimize kernels and programmes for my processor architecture, and if it is, how do I go about doing so.

---

### Post by TidusBlade on 2007-12-22
Not sure what your getting at, but theres a 64Bit version of Ubuntu and a version for Sun UltraSPARC...

---

### Post by jespdj on 2007-12-22
It is possible to [compile your own kernel]("https://help.ubuntu.com/community/Kernel/Compile"), however I wouldn't really recommend it unless you like to tinker with the innermost details of the operating system and if you know what you're doing.

The performance benefit you'll get from this is most likely unnoticeably small, so probably it's not really worth the effort.

There are Linux distributions such as [Gentoo]("http://www.gentoo.org/") which are completely installed from source - i.e., you just get the source code, and the setup program compiles the kernel and (almost) all software specifically tailored to your system. The advantage is that the OS and the software will be optimal for your system, but the downside is that it's difficult to install, it has a steep learning curve, and installation takes a long time.

---

### Post by jeffus_il on 2007-12-22
I used Gentoo for quite a while and always built a tailored kernel, 686 instead of 386 or 486 and other optimizations, I noticed no benefits and no speed , performance advantage. You may find some benchmark differences but for day to day use, there is really no difference, on the other hand the software updates are extremely heavy, taking a much longer time and uses lots of cpu for the builds. Also the install process is much more complex, you have to deal with all the package building options and also dependencies between packages which can be complex. ...

---

### Post by andrewcmcardle on 2007-12-23
So what it appears people are saying is that its possible to do it, but it is difficult and not worth the effort.

---


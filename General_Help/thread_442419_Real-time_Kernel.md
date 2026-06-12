---
title: "Real-time Kernel"
date: 2007-05-13
forum: General Help
---

### Post by naptastic on 2007-05-13
I'm running feisty 7.04 64-bit Desktop, and I love it.

I need fairly desperately to get a real-time preemptible kernel running. I followed the instructions at [https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime) and apt-get gave me this error:

E: Couldn't find package linux-realtime

The new repository is installed... I 'updated'... I can see that it did actually download some repo data from texware.it... but the package isn't there.

What should I do now?

---

### Post by stateq2 on 2007-05-14
try to update again and search for any realtime packages.  This is what I get:

> 
stateq@stateq-laptop:~$ apt-cache search linux-realtime
linux-image-2.6.20-15-realtime - Linux kernel image for version 2.6.20 on x86/x86_64
linux-image-2.6.20-15-realtime-trace - Linux kernel trace image for version 2.6.20 on x86/x86_64
linux-realtime - Complete real time Linux kernel


---

### Post by _SK_ on 2007-05-14
Sorry, Real-time kernel package is only for 32bit systems.

---


---
title: "[SOLVED] 32bit 4GigaByte Ram"
date: 2008-03-17
forum: General Help
---

### Post by Vevmesteren on 2008-03-17
Hey everyone, I just ordered 4GB RAM for my Dell XPS M1210. I am running 32Bit Gutsy, and am wondering if I will need to upgrade to 64bit, if yes, can this be done directly, or do I need to re-install everything?

thanks

V

---

### Post by Ub1476 on 2008-03-17
You need to reinstall. x86 (32-bit) will only use 3GB, I believe. Anyway, Ubutu Hardy Heron, 8.04, will be released in a month (24.04), so it's a good time to do so then:)

---

### Post by dizzutch on 2008-03-17
The reason for this is that a 32-bit processor has 4GB of addressing space, but needs to allocate some of that space to addresses other than your RAM. Devices such as devices in the PCI bus need to be addressed as well. I have 4GB of RAM, but in a 32-bit OS, the processor will only see 2.75GB because of the video card, and other devices.
This might not be the most scientific explanation, but it makes sense.
If you switch to 64-bit, all your RAM will be used.

---

### Post by jespdj on 2008-03-17
It's possible to use more than 4 GB RAM on a 32-bit system if you're using a kernel that supports [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension).

To enable PAE, you'll have to custom compile your own kernel. The Ubuntu Server edition kernel has PAE enabled by default.

---


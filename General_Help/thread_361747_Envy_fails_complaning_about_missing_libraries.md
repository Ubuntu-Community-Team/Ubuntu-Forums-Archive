---
title: "Envy fails complaning about missing libraries"
date: 2007-02-14
forum: General Help
---

### Post by rafciu123 on 2007-02-14
Hi,

I try to use nvidia driver to get installed on my box. I use envy for that purpose but after driver gets downloaded envy give me the following complaint:
"You do not appear to have header files installed in your system. Please install your distribution's header libc development package."
I tried to fix the problem

I tried to install header files by:

sudo apt-get install linux-headers-generic

but it didn't help. X still doesn't work with nvidia driver and envy returns above error. My kernel ends with 11.

Thanks

---

### Post by Maestro23 on 2007-02-14
Do you have the lib6c packages(dev, etc..) installed?

---

### Post by rafciu123 on 2007-02-14
Synaptic says I got version 2.4-1ubuntu12.3

---

### Post by dcstar on 2007-02-14
> **rafciu123 said:**
> Synaptic says I got version 2.4-1ubuntu12.3

I suspect it is compiling a new driver, you need to install the Development meta-package (sorry, I cannot recall the exact name, do a search for a kernel compilation HOWTO and it should be in one of the posts).

---


---
title: "Need configured kernel sources for compiling a driver"
date: 2005-04-29
forum: General Help
---

### Post by ranarion on 2005-04-29
I intend to switch to Ubuntu, so I don't have a running system handy where I can check this myself.

In order to build the driver for my laptop's winmodem, I need configured kernel sources. Up to now, under Mandrake, I used to solve this by fetching MDK's kernel source RPM and building my own kernel. How would I handle this under Ubuntu? Do I need to go through all the kernel building hassles or is there an easier solution?

Many thanks in advance!

---

### Post by shakin on 2005-04-29
You can just use Synaptic to install the 'linux-source' package. You probably only need to install the 'linux-headers' package for your kernel. Either way it's very easy and you never need to compile your kernel yourself.

---

### Post by az on 2005-04-29
You should use the linux-headers package.  Instead of the whole source, youshould only need the headers for compiling modules.

Lucent modules are inculede in linux-restricted-modules and the drivers for intel/smartlink modems are also available.

---

### Post by ranarion on 2005-04-29
Precompiled smartlink drivers are a very nice thing to have -- I'll give them a try, although up to now (with other distros), I was not lucky in getting my modem to work with precompiled ones.

Otherwise, being able to get configured kernel headers is a nice option, too. Thanks for the hints!

---


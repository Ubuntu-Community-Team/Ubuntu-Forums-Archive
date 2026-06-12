---
title: "restricted manager ubuntu 7.04"
date: 2007-04-20
forum: General Help
---

### Post by rjwboys on 2007-04-20
when my newly updated ubuntu wants me to run the restricted manager i click it and i get this error

You need to install the package

  linux-restricted-modules-2.6.20-ck1

for this program to work.

ive looked everyware this forum couldn't find it
google  no results
please help

---

### Post by johnc4510 on 2007-04-20
The restricted module needs to match your linux image. 
If you have the 2.6.20-15 image installed, you need the 2.6.20-15 restricted-module.
To see the number of your image, type this in a terminal.

uname -r

The terminal is here: Applications>Accessories>Terminal

Write down the info given, then open Synaptic 

Synaptic is here: System>Administration>Synaptic Package Manager

Scroll down to: linux-restricted-modules and match up the number you wrote down with the one in Synaptic. Now install it.

---

### Post by rjwboys on 2007-04-20
yes i have done this allready as i seen something similer but my uname -r comes out to 2.60.20-ck1
and the only things that come up under apt-cache search 2.60.20-ck1 
are 

linux-headers-2.6.20-ck1 - Header files related to Linux kernel, specifically,
linux-image-2.6.20-ck1 - Linux kernel binary image for version 2.6.20-ck1
nvidia-kernel-2.6.20-ck1 - NVIDIA binary kernel module for Linux 2.6.20-ck1

> **johnc4510 said:**
> The restricted module needs to match your linux image. 
If you have the 2.6.20-15 image installed, you need the 2.6.20-15 restricted-module.
To see the number of your image, type this in a terminal.

uname -r

The terminal is here: Applications>Accessories>Terminal

Write down the info given, then open Synaptic 

Synaptic is here: System>Administration>Synaptic Package Manager

Scroll down to: linux-restricted-modules and match up the number you wrote down with the one in Synaptic. Now install it.

---

### Post by rjwboys on 2007-04-23
bump

---

### Post by rjwboys on 2007-04-24
oh yeah if i type apt-cache search restricted-modules

I get this list

notice none of them say 2.6.20-ck1 anywhare

linux-restricted-modules-2.6.20-15-generic - Non-free Linux 2.6.20 modules on x86/x86_64
linux-restricted-modules-amd64-generic - Obsoleted by: linux-restricted-modules-generic
linux-restricted-modules-amd64-k8 - Obsoleted by: linux-restricted-modules-generic
linux-restricted-modules-amd64-xeon - Obsoleted by: linux-restricted-modules-generic
linux-restricted-modules-common - Non-free Linux 2.6.20 modules helper script
linux-restricted-modules-generic - Restricted Linux modules for generic kernels
nvidia-new-kernel-source - NVIDIA binary 'new' kernel module source
avm-fritz-kernel-source - AVM Fritz! binary kernel module source
fglrx-kernel-source - ATI binary kernel module source
linux-restricted-modules-2.6.20-15-lowlatency - Non-free Linux 2.6.20 modules on x86/x86_64
linux-restricted-modules-lowlatency - Restricted Linux modules for low latency kernels
nvidia-legacy-kernel-source - NVIDIA binary 'legacy' kernel module source
xen-restricted-modules-2.6.17-6-generic-xen0 - Non-free Linux 2.6.17 modules on x86_64 generic-xen0
linux-restricted-modules-2.6.17-11-generic - Non-free Linux 2.6.17 modules on x86_64 generic
linux-restricted-modules-2.6.17-10-generic - Non-free Linux 2.6.17 modules on x86_64 generic

---

### Post by kilou on 2007-05-09
Please try suggestion at post #7 here: [http://ubuntuforums.org/showthread.php?p=2622095#post2622095](http://ubuntuforums.org/showthread.php?p=2622095#post2622095)

---

### Post by fragos on 2007-05-09
I don't recognize a 2.6.20-ck1 verson of the kernel.  Which Ubuntu version do you have.  Where did you get it and what hardware are you running it on.  2.6.20-15-generic will run on anything Intel or AMD.

---

### Post by kilou on 2007-05-10
> **fragos said:**
> I don't recognize a 2.6.20-ck1 verson of the kernel.  Which Ubuntu version do you have.  Where did you get it and what hardware are you running it on.  2.6.20-15-generic will run on anything Intel or AMD.

The 2.6.20-ck1 is most probably a 2.6.20 Vanilla kernel patched with the Con Kolivas patch. It is a custom compiled kernel that is designed to be faster than original (Vanilla) or Ubuntu kernels. The vanilla kernels (original linux kernel) and the Con Kolivas patch are available on [www.kernel.org](www.kernel.org). Basically it is a tuned kernel for better performances on desktop computers.

---

### Post by rjwboys on 2007-05-10
thank you kilou for your help

---


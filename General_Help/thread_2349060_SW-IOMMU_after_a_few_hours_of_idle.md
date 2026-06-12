---
title: "SW-IOMMU after a few hours of idle"
date: 2017-01-10
forum: General Help
---

### Post by 98cwitr on 2017-01-10
Im suspecting a driver issue but unsure where to start. I have both a wireless adapter installed as well as an ethernet adapter (wireless doesn't work right and that's another story/thread) enp4s0 is my wired adapter:

[IMG]http://i.imgur.com/6XtSXMq.jpg[/IMG]

So the system become unresponsive, sometimes even failing to reboot without a hard reset. Upon reboot I am always prompted with initramfs where I have to run a fsck to get the system back up and running. This probably started nearly a year ago for me. 

SysInfo:

Kernel: Ubuntu 4.4.0-57.78-generic 4.4.35
Description:    Ubuntu 16.04.1 LTS
Release:    16.04

Thanks in advance!

---

### Post by Yellow Pasque on 2017-01-11
Try a more recent kernel (>= 4.7). Maybe this commit will help: [https://github.com/torvalds/linux/commit/27896c83fe94e2190f121a2fdbffffbf1d83d573](https://github.com/torvalds/linux/commit/27896c83fe94e2190f121a2fdbffffbf1d83d573)

---

### Post by 98cwitr on 2017-01-12
Disabling the wireless completely seemed to work with no errors over a 2 hour idle period. Need to test longer though. Will report back!

---


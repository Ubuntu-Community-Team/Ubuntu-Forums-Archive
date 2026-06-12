---
title: "How can I patch a module? (For current kernel and without compile entire kernel)"
date: 2008-03-23
forum: General Help
---

### Post by Liken on 2008-03-23
Hi. I am trying to make changes in the source of a kernel module. I cannot compile entire kernel each time i want to test those changes.

What I do (And it fails). 

apt-get source linux-image-2.6.24-11-generic
//copy .config from /boot
//copy Module.symvers from /usr/src/linux-headers-generic/
make menuconfig
make modules_prepare

//Now, example to compile module pcspkr (console beep)
make SUBDIRS=drivers/input/misc modules

//Then I have pcspkr.ko module: insmod ./pcspkr.ko  

it loads OK but it fails: 
When I lsmod original module dmesg say:
input: PC Speaker as /devices/platform/pcspkr/input/input15
When I insmod compiled module dmesg say:
input: PC Speaker as /devices/virtual/input/input13

And pcspkr is a example module, I have tryed it because  it seems simple. What I really want to change is a important core module (libata.ko), but when I try my compiled module (without changes) computer hangs.

So, I am lost, How Can I compile a single module (without changes in the source) in order to obtain a clone of a running kernel module.???????

Thx.

---


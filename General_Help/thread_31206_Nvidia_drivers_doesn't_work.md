---
title: "Nvidia drivers doesn't work"
date: 2005-05-02
forum: General Help
---

### Post by cutOff on 2005-05-02
Hi all

i've just compiled my own kernel using an existing configuration (config-2.6.10-5-k7). If I boot my custom kernel, Nvidia drivers doesn't work. However if I boot up an Ubuntu kernel (2.6.10-5-k7) it works fine.

Does anybody know how to solve this?

BTW I have the package 'linux-restricted-modules-2.6.10-5-k7' installed. Do I need other one??

Thanx in advance

---

### Post by shakin on 2005-05-02
I think you need to reinstall the Nvidia driver so it can be compiled against your new kernel's headers.

---

### Post by cutOff on 2005-05-03
[QUOTE=shakin]I think you need to reinstall the Nvidia driver so it can be compiled against your new kernel's headers.[/QUOTE]
Thanx for the reply but it didn't work. I continue having same problem.

Any suggestion??


Regards

---

### Post by crazy-flash on 2005-05-03
you need to compile your own nvidia-module, because when you compile your own kernel the module-path will be anywhere else (just have a look under /lib/modules). you could try to copy the module from the old path to the new one but in most cases this won't work because the module must be compiled under the same compiler version as the kernel was compiled.
so just go the easiest way: go to [www.nvidia.com](www.nvidia.com), download the drivers and install them. during the installation the module will be automatically compiled and installed. (be sure that you have created a symlink /usr/src/linux to your linux-sources)

---

### Post by cutOff on 2005-05-04
[QUOTE=crazy-flash]you need to compile your own nvidia-module, because when you compile your own kernel the module-path will be anywhere else (just have a look under /lib/modules). you could try to copy the module from the old path to the new one but in most cases this won't work because the module must be compiled under the same compiler version as the kernel was compiled.
so just go the easiest way: go to [www.nvidia.com](www.nvidia.com), download the drivers and install them. during the installation the module will be automatically compiled and installed. (be sure that you have created a symlink /usr/src/linux to your linux-sources)[/QUOTE]
Thanks for your help. I'll try it later. I'm a bit busy now. 

Many thanks!

---


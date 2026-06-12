---
title: "Merging 2 Kernel Config Files Into 1"
date: 2006-07-10
forum: General Help
---

### Post by dr_d on 2006-07-10
Hey Folks...

I'm trying to compile a generic Ubuntu kernel that will run on my Microsoft XBOX.

To do this, I have the Ubuntu sources, and the XBOX-Linux patch for the correct kernel version.

After I patch the sources, there is a file called Kernel.config. If I build with this config, then the kernel boots on my XBOX... however the resulting kernel is pretty useless (no iptables, usb support, etc).

I'm not experienced enough to build a kernel with everything I want, so instead I opted for the Ubuntu generic kernel. I have the 686-smp config file from my dual-core laptop. I know that the XBOX is not dual core but I think/hope it won't matter.

So:

cp kernel.config .config
make oldconfig
make menuconfig
  load config-2.6.15-686
make-kpkg clean
make-kpkg --initrd kernel_image modules_image kernel_headers


However this refuses to boot on my XBOX, I've tried many different things, and come to the conclusion that when I load the second config, it is overwriting all the options from the previous kernel.config. I'm guessing that some of those options are essential to allow the XBOX to boot.


So my question is, how can I merge these two configuration files into one?


Any help would be greatly appreciated.
Cheers,
Dr_D

---

### Post by dr_d on 2006-07-12
Surely there is some way to do this... doesn't anybody know?

---

### Post by Rui Pais on 2006-07-12
hi,

a direct answer to your question could be to install a graphical gui for diff, like meld (sudo apt-get install meld), copy the ubuntu config to .config and do:
```
meld Kernel.config .config 
```
and then just add the differences need from Kernel.config to .config using the arrows and redo the make menuconfig to ensure it read it and everything is ok. (btw, may i suggest make xconfig or make gconfig to make thigns easy, menuconfig is hard for someone without experience)

But note that is prone to errors.

A correct approach would be:
Boot from the ubuntu kernel,
patch the sources,
```
make oldconfig
```
answer any questions (accept default is usually good). That will replicate the ubuntu settings!
```
make xconfig
``` (or the one you prefer) 
check if is alright and remove thing not used. See 'Device drivers' section and remove stuff related to hardware that you don't have (as an example, ubuntu has enabled, under Device drivers -> Graphics support, Virtual Frame Buffer support. Thats for testing purposes and shoud not be enabled!)
And then the usual:
```
fakeroot make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-MyXBOX kernel_image kernel_headers modules_image
```

hope that helps

---


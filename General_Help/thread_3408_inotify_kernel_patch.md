---
title: "inotify kernel patch"
date: 2004-11-05
forum: General Help
---

### Post by Enygma on 2004-11-05
I tried to apply the inotify kernel patch that's on the Beagle Install Howto page here:
[http://www.ubuntulinux.org/wiki/BeagleInstallHowto](http://www.ubuntulinux.org/wiki/BeagleInstallHowto)

It compiles fine but when I reboot into the new patched kernel X just doesn't work.
I reconfigured X to use the default 'nv' driver instead of the 'nvidia' driver and that worked.
So I thought if I re-install and reconfigure the 'nvidia' driver I should be sorted.
Nope, same problem doesn't boot. 

So is the nvidia-glx package only compatible with the default warty kernel or something?

Does anyone have any other ideas why this is happening, the X server log says absolutely nothing.

Thanks

---

### Post by p!=f on 2004-11-05
Linux-restricted-modules-2.6.8.1-3-* where * = architecture is a package which contains ATI and NVIDIA drivers but for the default **Ubuntu** kernels only.
 You created your own kernel so there's no nvidia kernel module for it.
 To be short, you have to compile one for you.
 
 There're many ways how to do it. Let's do it **Debian** way. Download and install *module-assistant* package and then run it.
 ```

 sudo module-assistant
 
```
 
 Link you kernel sources to /usr/src/linux (optional).
 Select UPDATE, PREPARE and SELECT. Check nvidia-kernel and ... I'm sure you get the point as soon as you see it. :)
 Note that *module-assistant* will compile modules for currently running kernel until specified by parameter.
 
 The second **Debian** way is also easy. Download and install *kernel-package* and *nvidia-kernel-source* package. Unpack nvidia from /usr/src to /usr/src/modules. 
 ```

 drwxrwxr-x  20 root root    4096 2004-10-30 16:42 linux-image-2.6.9-cko2
 drwxr-xr-x   4 root root    4096 2004-07-29 07:18 modules
 -rw-r--r--   1 root root 1050573 2004-10-18 08:14 nvidia-kernel-source.tar.gz
 
```
 Go to your kernel sources and run:
 ```

 make-kpkg modules_image
 
```
 Both methods will create **Debian** nvidia-kernel package for your custom kernel.
 
 Note that you may use *kernel-package* for creating kernel package itself. Go to clean kernel sources and run something like this (check make-kpkg manpages first to get the point):
 ```

 sudo make-kpkg --initrd --revision=1 --config=menuconfig --added_modules=nvidia-kernel kernel_image modules_image
 
```
 It will run all neccessary steps to compile your brand new kernel image and create a package for it.
 
 Edit: You will still need *nvidia-glx* package.

---

### Post by Enygma on 2004-11-06
Thanks for a very thorough response! I'll give this a go tomorrow, got a hot date right now :)

I'll let you know how I get on.

---

### Post by Enygma on 2004-11-07
First one worked like a charm, Thanks!

---


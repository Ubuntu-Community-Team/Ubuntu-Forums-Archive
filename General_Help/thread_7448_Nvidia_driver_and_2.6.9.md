---
title: "Nvidia driver and 2.6.9"
date: 2004-12-07
forum: General Help
---

### Post by M@t on 2004-12-07
I just compiled the kernel 2.6.9 for my ubuntu hoary box. The kernel boots perfectly, but there is a problem with x. X server doesn't start and displayed following error message: 
  Failed to load module GLcore
  Failed to load module xtt
  Failed to initialize the NVIDIA kernel module
  Screen(s) found, but none have a usable conf

  Fatal server error
    no screens found

Is someone succeed in running nvidia driver with 2.6.9 kernel ?

---

### Post by subterrific on 2004-12-07
When you upgrade kernels, you also have to upgrade any 3rd party modules. So you need to install the nvidia kernel module for your new kernel. Once you do that, it will be located at: /lib/modules/<your kernel version>/nvidia/. <your kernel version> is what is returned by uname -r. Then you can do modprobe nvidia to load it, and X will work. You might also want to add nvidia to /etc/modules to load the module on boot.

---

### Post by p!=f on 2004-12-13
[QUOTE=M@t]I just compiled the kernel 2.6.9 for my ubuntu hoary box. The kernel boots perfectly, but there is a problem with x. X server doesn't start and displayed following error message: 
  Failed to load module GLcore
  Failed to load module xtt
  Failed to initialize the NVIDIA kernel module
  Screen(s) found, but none have a usable conf

  Fatal server error
    no screens found

Is someone succeed in running nvidia driver with 2.6.9 kernel ?[/QUOTE]

There's no package you could easily install to get nvidia module for a custom kernel. You're on your own here. :)

I'm running 2.6.9 with Con Kolivas Overloaded (-cko3) patchset. The following methods work for me flawlessly.
First install build-essential metapackage unless already done so.
```

sudo apt-get install build-essential

```
Install module-assistant package.
```

sudo apt-get install module-assistant
sudo module-assistant

```
The rest is self explaining.

You may also install nvidia-kernel-source package, unpack it to /usr/src/modules (by default), cd to your configured kernel sources and run
```

sudo apt-get install kernel-package
sudo make-kpkg modules_image

```

Both methods will create Debian packages for your running kernel.

---


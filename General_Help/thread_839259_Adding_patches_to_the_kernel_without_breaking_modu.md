---
title: "Adding patches to the kernel without breaking modules-packages"
date: 2008-06-24
forum: General Help
---

### Post by Astaroth_PoD on 2008-06-24
I'm trying to get my USB-stick Ubuntu running smoothly with some kernel enhancements, like e2compr.

However, whenever I make a custom kernel, I inherently break all the hardware support from packages that provide modules to the kernel.

The question is simple: How can I compile a new kernel and still be able to use the "restricted-modules", "ubuntu-modules" etc?

---

### Post by sdennie on 2008-06-24
You can't.  Although, you can build a custom kernel with make-kpkg and it will integrate into your system just as if it were an Ubuntu kernel.  Check this guide: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu).  Note that in the step where you copy the config file from an Ubuntu kernel, it will almost certainly have some of the sound and wifi drivers disabled so, you'll need to explicitly enable them from menuconfig.

---

### Post by Astaroth_PoD on 2008-06-24
Alright thanks, I was afraid of that.

Is there a list available over what's in the Unbuntu-modules and restricted-modules packages? I would like to know what they are since this stick should work flawlessly on most systems it's inserted into.

I'm already using make-kpkg to make the kernels and it works fine, except for all the modules. So if I know which modules there are in the packages, I can enable them in the config...

---

### Post by sdennie on 2008-06-24
If you want a list of files in a package you can use dpkg -L.  For example:

```

dpkg -L linux-image-`uname -r`

```

Will give you a list of all the files in the linux image for the current running kernel (you can do the same with restricted).

However, it sounds like you just need to copy the config from an Ubuntu kernel in your new kernel source directory.  That guide shows how to do that but, here it is in a nutshell:

```

cp /boot/config-`uname -r` ./.config

```

If you run that from the base of your kernel source it will use the Ubuntu kernel config as a base for your kernel (with the caveat I mentioned above about probably needing to turn on some wireless and sound options).

Edit:
The last command assumes you are running an Ubuntu kernel when you type it.

---


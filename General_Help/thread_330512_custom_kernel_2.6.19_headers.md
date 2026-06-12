---
title: "custom kernel 2.6.19 headers"
date: 2007-01-03
forum: General Help
---

### Post by Gujs on 2007-01-03
Hello,

I have a problem with custom build kernel 2.6.19. I build it through manual on ubuntu wiki. And kernel itself works perfect. But I have another similar computer and I installed build packages on it (image and headers), but when I want to build ivtv driver from source, I can't because it doesn't find .h files it needs to build.

How come that for default ubuntu kernel I can have just linux-image and linux-header packages installed and this works, but for custom kernel doesn't.

I build the packages with command:
```

make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

```

When I instal packages i get this warnings:
```

Selecting previously deselected package kernel-image-2.6.19.1-custom.
(Reading database ... 141120 files and directories currently installed.)
Unpacking kernel-image-2.6.19.1-custom(from kernel-image-2.6.19.1-custom_10.00.Custom_i386.deb) ...
Selecting previously deselected package kernel-headers-2.6.19.1-custom.
Unpacking kernel-headers-2.6.19.1-custom(from kernel-headers-2.6.19.1-custom_10.00.Custom_i386.deb) ...
Setting up kernel-image-2.6.19.1-custom(10.00.Custom) ...

 Hmm. There is a symbolic link /lib/modules/2.6.19.1-custom/build
 However, I can not read it: No such file or directory
 Therefore, I am deleting /lib/modules/2.6.19.1-custom/build


 Hmm. The package shipped with a symbolic link /lib/modules/2.6.19.1-custom/source
 However, I can not read it: No such file or directory
 Therefore, I am deleting /lib/modules/2.6.19.1-custom/source

/initrd.img does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.
/vmlinuz does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.19.1-custom
Found kernel: /boot/vmlinuz-2.6.18.5-custom
Found kernel: /boot/vmlinuz-2.6.15.7-ubuntu1-custom
Found kernel: /boot/vmlinuz-2.6.12-10-686-smp
Found kernel: /boot/vmlinuz-2.6.12-10-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up kernel-headers-2.6.19.1-custom(10.00.Custom) ...


```
Please, I would really appreciate help on this issue, because I just don't want every to compile never kernel on both computers if there is the same system on it!

EDIT:
And when I want to compile ivtv driver I get this error:
```

make -C driver all
make[1]: Entering directory `/home/iptv/ivtv/ivtv-0.9.1/driver'
make -C /lib/modules/2.6.19.1-iskratel/build M=/home/iptv/ivtv/ivtv-0.9.1/driver modules
make[2]: Entering directory `/usr/src/kernel-headers-2.6.19.1-iskratel'
Makefile:275: /usr/src/kernel-headers-2.6.19.1-iskratel/scripts/Kbuild.include: No such file or directory
/usr/src/kernel-headers-2.6.19.1-iskratel/arch/i386/Makefile:38: /usr/src/kernel-headers-2.6.19.1-iskratel/arch/i386/Makefile.cpu: No such file or directory
/bin/sh: line 0: [: -lt: unary operator expected
make[2]: *** No rule to make target `/usr/src/kernel-headers-2.6.19.1-iskratel/arch/i386/Makefile.cpu'.  Stop.
make[2]: Leaving directory `/usr/src/kernel-headers-2.6.19.1-iskratel'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/iptv/ivtv/ivtv-0.9.1/driver'
make: *** [all] Error 2

```

Thanks,

Gujs

---

### Post by superm1 on 2007-01-05
> **Gujs said:**
> Hello,

I have a problem with custom build kernel 2.6.19. I build it through manual on ubuntu wiki. And kernel itself works perfect. But I have another similar computer and I installed build packages on it (image and headers), but when I want to build ivtv driver from source, I can't because it doesn't find .h files it needs to build.

How come that for default ubuntu kernel I can have just linux-image and linux-header packages installed and this works, but for custom kernel doesn't.

I build the packages with command:
```

make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

```When I instal packages i get this warnings:
```

Selecting previously deselected package kernel-image-2.6.19.1-custom.
(Reading database ... 141120 files and directories currently installed.)
Unpacking kernel-image-2.6.19.1-custom(from kernel-image-2.6.19.1-custom_10.00.Custom_i386.deb) ...
Selecting previously deselected package kernel-headers-2.6.19.1-custom.
Unpacking kernel-headers-2.6.19.1-custom(from kernel-headers-2.6.19.1-custom_10.00.Custom_i386.deb) ...
Setting up kernel-image-2.6.19.1-custom(10.00.Custom) ...

 Hmm. There is a symbolic link /lib/modules/2.6.19.1-custom/build
 However, I can not read it: No such file or directory
 Therefore, I am deleting /lib/modules/2.6.19.1-custom/build


 Hmm. The package shipped with a symbolic link /lib/modules/2.6.19.1-custom/source
 However, I can not read it: No such file or directory
 Therefore, I am deleting /lib/modules/2.6.19.1-custom/source

/initrd.img does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.
/vmlinuz does not exist. Installing from scratch, eh?
Or maybe you don't want a symbolic link here. Hmm? Lets See.
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.19.1-custom
Found kernel: /boot/vmlinuz-2.6.18.5-custom
Found kernel: /boot/vmlinuz-2.6.15.7-ubuntu1-custom
Found kernel: /boot/vmlinuz-2.6.12-10-686-smp
Found kernel: /boot/vmlinuz-2.6.12-10-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up kernel-headers-2.6.19.1-custom(10.00.Custom) ...


```Please, I would really appreciate help on this issue, because I just don't want every to compile never kernel on both computers if there is the same system on it!

EDIT:
And when I want to compile ivtv driver I get this error:
```

make -C driver all
make[1]: Entering directory `/home/iptv/ivtv/ivtv-0.9.1/driver'
make -C /lib/modules/2.6.19.1-iskratel/build M=/home/iptv/ivtv/ivtv-0.9.1/driver modules
make[2]: Entering directory `/usr/src/kernel-headers-2.6.19.1-iskratel'
Makefile:275: /usr/src/kernel-headers-2.6.19.1-iskratel/scripts/Kbuild.include: No such file or directory
/usr/src/kernel-headers-2.6.19.1-iskratel/arch/i386/Makefile:38: /usr/src/kernel-headers-2.6.19.1-iskratel/arch/i386/Makefile.cpu: No such file or directory
/bin/sh: line 0: [: -lt: unary operator expected
make[2]: *** No rule to make target `/usr/src/kernel-headers-2.6.19.1-iskratel/arch/i386/Makefile.cpu'.  Stop.
make[2]: Leaving directory `/usr/src/kernel-headers-2.6.19.1-iskratel'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/iptv/ivtv/ivtv-0.9.1/driver'
make: *** [all] Error 2

```Thanks,

Gujs
Before going too far into this, is there a good reason why you are using custom built kernels?  
At this point, if there is something in 2.6.19 that you really really need, perhaps you might just be better off grabbing a 2.6.20 kernel from the feisty repositories and using that.  It will save you quite a bit of hassle (especially since feisty includes ivtv drivers now)

---

### Post by Gujs on 2007-01-05
Oh, great. When I was looking there just for 2.6.19, because is latest stable released on kernel.org. And I saw it has many dependencies which breezy can't have. So I thought that all kernels that are build for Feisty are having the same dependencies. 

Thank you for sharing that with me.

But if you know what am I doing wrong, I would still be interested for help, because I would still like to have my own compiled kernel. I will just use for now Feisty kernel, until I find out what am I doing wrong.

Thanks again!

---

### Post by superm1 on 2007-01-05
> **Gujs said:**
> Oh, great. When I was looking there just for 2.6.19, because is latest stable released on kernel.org. And I saw it has many dependencies which breezy can't have. So I thought that all kernels that are build for Feisty are having the same dependencies. 

Thank you for sharing that with me.

But if you know what am I doing wrong, I would still be interested for help, because I would still like to have my own compiled kernel. I will just use for now Feisty kernel, until I find out what am I doing wrong.

Thanks again!
The kernels are usually fairly standalone packages - but you may consider moving up to a newer release of ubuntu if the feisty kernel doesn't work on breezy (it is possible that it might not - a lot of other things have changed since breezy - udev, hotplug, upstart - i was assuming you were on edgy).  Even if you step up to dapper, you are at a new enough kernel that you can setup ivtv through a straightforward process.

I can't comment exactly what you were doing wrong, I stopped compiling kernels by hand when I left gentoo - and for good reason.  Someone else may be able to comment on this.

---

### Post by pseudonym on 2007-01-05
> **Gujs said:**
> But if you know what am I doing wrong, I would still be interested for help, because I would still like to have my own compiled kernel. I will just use for now Feisty kernel, until I find out what am I doing wrong.
I think the reason why linux-image and linux-header works for your purposes but your custom kernel doesn't, has to do with the packaging process. Certain symlinks and directories are created differently in packaged kernels, which is why you got those warnings when you installed the hand-compiled kernel on another machine. It likes to live on the same machine as the source-tree used to create it.

But if you say the second machine is identical to the first, you should just be able to use the same .config on each machine. It means 2 separate compiles, but the second one will be quicker because you don't have to worry about deciding which options you want/don't want.

Unless you're prepared to learn more about the kernel packaging process, this is what you'll need to do, I think.

---


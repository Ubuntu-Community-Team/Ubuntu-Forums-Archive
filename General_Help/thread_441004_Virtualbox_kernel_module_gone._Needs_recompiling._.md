---
title: "Virtualbox kernel module gone. Needs recompiling. Need some serious hel, fast"
date: 2007-05-12
forum: General Help
---

### Post by oliverb4ss on 2007-05-12
help*, typo in the title.
When I try to run my XP virtual machine, Virtualbox displays the following message:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.

VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

Then I run /etc/init.d/vboxdrv setup in terminal, which results in the following:

sudo /etc/init.d/vboxdrv setup
Password:
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                                 
 * Look at /var/lib/vbox-install.log to find out what went wrong

The I looked at the log, which stated:

Makefile:73: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again..  Stop.

And from the I don't know what to do, because I didn't have to run make before as I installed it from precompiled binaries.

Could anyone explain me step by step or is easier to just reinstall Virtualbox and set up XP from the ground up again, which takes a whole lot of time?

Thanks.

---

### Post by oliverb4ss on 2007-05-12
*bump*

It does seem like I'm impatient, doesn't it?

Well, I really need help.

---

### Post by bodhi.zazen on 2007-05-22
LOL, sorry to be so late answering your post, better late then never :)

Install your kernal sources, then re-compile the virtualbox module.

```
sudo aptitude install kernel-header-`uname -r`
```

Note those are back tics, just to the left of the number 1 and not single quotes

back tic `
single quote '

---

### Post by oliverb4ss on 2007-05-25
Yeah, that might work, but I already reinstalled Virtualbox and it's working fine now.

Thanks anyway.

---

### Post by oliverb4ss on 2007-05-30
Okay, I have the same problem again, but I've noticed a pattern.

The last time the module went away, was the time I switched to a low-latency kernel. As of today Virtualbox gives me the same message, module is not install, please recompile, and I can't recompile it view original post).
Then I realized that I had just got a kernel update from the update manager.
It happens when the kernel gets updated.

So how can I recompile it so I wouldn't have to reinstall it and setup Windows again every time?

---

### Post by Vic_Astro on 2007-05-30
Wait until the kernel-headers package is available, install it and re-configure vboxdrv

---

### Post by .adma on 2007-05-30
Will Ubuntu automatically download the kernel headers for me?  As of right now, I can only get VB to work when I run ...20-15 and not the new kernel, 20-16.  Thanks

---

### Post by mijj on 2007-05-30
> **oliverb4ss said:**
> Then I run /etc/init.d/vboxdrv setup in terminal, which results in the following:
...


did you try:```
 ***sudo*** /etc/init.d/vboxdrv setup
```
?

I had probs at first (not the same error as yours tho) which were caused cos i wasnt the root user.  Everything went ok when i prefixed the instruction with "sudo".

---

### Post by oliverb4ss on 2007-05-30
Well, that made me feel stupid :D

I forgot to sudo myself.

Thanks.

---

### Post by art2003 on 2007-05-30
There is an easy fix and probably won't need fixing again next time there is a kernel update...

```
sudo aptitude install xen-headers-2.6.16
```

or open synaptic and install xen-headers-2.6.16


then

```
sudo /etc/init.d/vboxdrv setup
```

and the result is:

```

 * Stopping VirtualBox kernel module vboxdrv                            [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                       [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                             [ OK ]

```

---

### Post by .adma on 2007-05-31
what are the xen headers and why would another update not cause the same?  Thanks for help

---

### Post by .adma on 2007-05-31
```
Setting up xen-headers-2.6.16 (2.6.16-11.1) ...
adma@adma-laptop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                                 
 * Look at /var/lib/vbox-install.log to find out what went wrong

```

:(

---

### Post by bodhi.zazen on 2007-05-31
:(

OK, lets look at what kind of error message we ar getting then ...

```
sudo less /var/lib/vbox-install.log
```

---

### Post by .adma on 2007-05-31
Here Goes:

```
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/tmp/vbox.2 SRCROOT=/tmp/vbox.2 modules
gcc: Internal error: Segmentation fault (program cc1)
Please submit a full bug report.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.

gcc: Internal error: Segmentation fault (program cc1)
Please submit a full bug report.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.

make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.2/.tmp_versions
rm -f /tmp/vbox.2/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.2
  gcc -Wp,-MD,/tmp/vbox.2/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3   -march=i586  -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-i386/mach-default -fomit-frame-pointer -g    -I/lib/modules/2.6.20-16-generic/build/include  -I/tmp/vbox.2/ -I/tmp/vbox.2/include -I/tmp/vbox.2/r0drv/linux -D__KERNEL__ -DMODULE -D__LINUX__ -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DCONFIG_VBOXDRV_AS_MISC -D__X86__   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.2/linux/.tmp_SUPDrv-linux.o /tmp/vbox.2/linux/SUPDrv-linux.c
gcc: Internal error: Segmentation fault (program cc1)
Please submit a full bug report.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-4.1/README.Bugs>.

make[2]: *** [/tmp/vbox.2/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vboxdrv] Error 2
```

---

### Post by bodhi.zazen on 2007-05-31
:lolflag:

You want ?me to translate that mess ???

```
sudo aptitude install linux-headers-2.6.20-16-generic
sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup
```

---

### Post by GandG on 2007-05-31
Same problem. A simple Virtualbox uninstall/re-install using Automatix  worked fine for me.  Picked up the the previously defined Virtual Machine perfectly.

---

### Post by .adma on 2007-05-31
> **bodhi.zazen said:**
> :lolflag:

You want ?me to translate that mess ???

```
sudo aptitude install linux-headers-2.6.20-16-generic
sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup
```

I just have no idea what it means. I am sorry, wasnt trying to get someone else to do all my work  :(

Very frustrated.  Automatix didnt fix it, evidently STILL some issue with my kernel headers when I run:

```
sudo aptitude install linux-headers-2.6.20-16-generic
```

I get 
```
adma@adma-laptop:~$ sudo aptitude install linux-headers-2.6.20-16-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```
So essentially nothing is happening... Sorry to keep asking for help here, just really want this to work .  Thanks so much in advance

---

### Post by bodhi.zazen on 2007-05-31
> **.adma said:**
> I just have no idea what it means. I am sorry, wasnt trying to get someone else to do all my work  :(

:lolflag:

It was a joke :) You are NOT expected to be a programmer or debug the script.

I was not trying to be brash, please accept my apology if I came across that way. What I mean is:

Boy that is one hellacious error message ! :twisted:

Posting error messages is VERY helpful to those of us trying to hep you.

If you like I will translate it to English for you.

gcc = Gnu C Compiler.

so you are seeing the output of the compiler ...

> echo "         include/linux/autoconf.h or include/config/auto.conf are missing."

This is saying, in English, you do not have your kernel headers installed.

Thus, try installing the kernel headers (with the command I gave you) and re-running the vbox install script with :

```
sudo /etc/init.d/vboxdrv setup
```

_Note_: I find I need to run the script twice for some reason. I have not de-bugged the install script, it is on my to-do list ~ NOT.

---

### Post by .adma on 2007-05-31
Thanks so much for your gracious reply!  I edited my post above yours.  My Linux Headers 'Appear' to be in order, at least from the perspective of aptitude.  When I run that command, it basically says it installs nothing.  I went into syanptic and it shows it is already installed.  I clicked to reinstall it.  Still getting same error.  Maybe  I will uninstall the headers, and reboot...

---

### Post by .adma on 2007-05-31
is it possible my compiler is messed up?  I wasnt able to do 'make' files the other day...could this be an issue with my headers?

also remember, to make this more confusing...it works fine in the 20-15 kernel

---

### Post by bodhi.zazen on 2007-05-31
> **.adma said:**
> is it possible my compiler is messed up?  I wasnt able to do 'make' files the other day...could this be an issue with my headers?

also remember, to make this more confusing...it works fine in the 20-15 kernel

Well, to run make you need to install build-essential :

```
sudo aptitude install build-essential
```

Other then that, again it would help to see the exact (make) error ...

I am not sure of how to fix VirtualBox on your new kernel :(

I am wondering if it is a problem with the kernel ? That is just a guess ...

---

### Post by .adma on 2007-06-01
Well, thanks for all the help.  Soon I will be reinstalling Ubuntu from scratch, so I hope it gets fixed then.

---


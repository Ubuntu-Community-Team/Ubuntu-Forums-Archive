---
title: "Nvidia drivers not building after upgrading to new kernal version 6.1.0-1015-oem"
date: 2023-06-30
forum: General Help
---

### Post by eshangray on 2023-06-30
Hi,

After updating my system to the latest kernal version (6.1.0-1015-oem) my nvidia drivers are not able to update to the newest version (535) and I get the error when i try to install it:
```

Warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc-12 (Ubuntu 12.1.0-2ubuntu1~22.04) 12.1.0
  You are using:           cc (Ubuntu 11.3.0-1ubuntu1~22.04.1) 11.3.0
```

On running gcc --version it is showing:
```
[FONT=monospace][COLOR=#000000]gcc (Ubuntu 11.3.0-1ubuntu1~22.04.1) 11.3.0 [/COLOR]
Copyright (C) 2021 Free Software Foundation, Inc. 
This is free software; see the source for copying conditions.  There is NO 
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. 
[/FONT]
```

But, when I try to install gcc 12 it says it is already installed?

Is there a way to force the system to use the newest version of gcc to get the drivers installed?

---

### Post by Holger_Gehrke on 2023-06-30
If you do a 'ls -l /usr/bin/gcc*' you'll see that gcc is a link to gcc-11 which is a link to x86_64-linux-gnu-gcc-11. If apt says gcc-12 is installed, than you probably have a gcc-12 / x86_64-linux-gnu-gcc-12, too. 'cc' is another symbolic link, but that one is under control of the debian-alternatives system. In the end it points to gcc. The reason for this whole thing is to make it possible to have multiple compilers installed and switch between them as needed. Usually you would edit the Makefile and set the variable CC to the compiler to use, but with the way things are with NVidia driver packages that might not be an option - I don't know, I haven't used Nvidia in more than 10 years. If that is indeed the case, you might remove the symlink /usr/bin/gcc and create a new one which points to gcc-12.

Holger

---

### Post by Yellow Pasque on 2023-07-01
It seems like that's only a warning and shouldn't cause a build failure. Is there any other output? Usually, you get something like:
```
Error! Bad return status for module build on kernel
Consult /var/lib/dkms/nvidia/(version number)/build/make.log for more information.
```

---

### Post by eshangray on 2023-07-01
> It seems like that's only a warning and shouldn't cause a build failure.  Is there any other output? Usually, you get something like:
 	Code:
 	Error! Bad return status for module build on kernel
Consult /var/lib/dkms/nvidia/(version number)/build/make.log for more information. 


The only other error I can find in the file is:

cc: error: unrecognized command-line option &#8216;-ftrivial-auto-var-init=zero&#8217;

---

### Post by Yellow Pasque on 2023-07-01
The ftrivial-auto-var-init option was added in gcc 12, so I guess compiler version mismatch is the issue. I generally know how to hack things on a Debian-based system to force compiler versions, but I don't want to give you bad advice that causes other issues for you, so hopefully someone knows a a safe workaround.

---

### Post by itosaygo on 2023-08-08
I encountered a similar situation and found a relatively safe recovery method that I hope you all can consider.
First, check the compiled version using gcc-12:

> cat /proc/version
Linux version 6.1.0-1015-oem (buildd@bos03-amd64-046) (x86_64-linux-gnu-gcc-12 (Ubuntu 12.1.0-2ubuntu1~22.04) 12.1.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #15-Ubuntu SMP PREEMPT_DYNAMIC Fri Jun 16 09:51:49 UTC 2023 (Ubuntu 6.1.0-1015.15-oem 6.1.29)
 

Then, if gcc is pointing to gcc-11, the installation of Nvidia's driver will fail:

> $ ls -l /usr/bin/gcc
gcc            gcc-11         gcc-12 ...
 

You can use update-alternatives to set gcc to 11 and 12, then switch to 12:

> $ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-11 11
$ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-12 12
$ sudo update-alternatives --config gcc
(select gcc-12 here)


After that, install the headers and Nvidia's driver:

> sudo apt install linux-headers-$(uname -r)
sudo ubuntu-drivers autoinstall


I hope this solution helps!

---


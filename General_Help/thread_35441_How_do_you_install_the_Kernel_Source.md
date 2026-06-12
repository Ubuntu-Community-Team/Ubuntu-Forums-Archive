---
title: "How do you install the Kernel Source?"
date: 2005-05-18
forum: General Help
---

### Post by himuraken on 2005-05-18
I have looked in the SYnaptic manager but I am still unable to find out how I can install the kernel source. VMware requires the kernel source in order to compile properly. Does Ubuntu install the kernel source by default? If so where? And if not, how can it be installed? TIA

---

### Post by shakin on 2005-05-18
You probably just need the headers. Searching Synaptic for "headers" should find it. It's probably called linux-i686-headers or something similar depending on which kernel you have installed.

---

### Post by himuraken on 2005-05-18
I checked the Synaptic manager and there aren't any entries for headers. However there is a package call   "kernel-package". The description for this package is:

[COLOR=DarkSlateBlue]A utility for building Linux kernel related Debian packages.
This package provides the capability to create a debian kernel-image
package by just running make-kpkg kernel_image in a kernel source
directory tree.  It can also package the relevant kernel headers into
a kernel-headers package. In general, this package is very useful if
you need to create a custom kernel, if, for example, the default
kernel does not support some of your hardware, or you wish a leaner,
meaner kernel.  It also scripts the steps that need be taken to
compile the kernel, which is quite convenient (forgetting a crucial
step once was the initial motivation for this package). Please look at
/usr/share/doc/kernel-package/Rationale.gz for a full list of advantages
of this package.[/COLOR]

If this is the correct package for the kernel source, what is the default location? I thought it was /usr/lib/linux/include or something similar.

---

### Post by Xian on 2005-05-18
[QUOTE=himuraken]I have looked in the SYnaptic manager but I am still unable to find out how I can install the kernel source. VMware requires the kernel source in order to compile properly. Does Ubuntu install the kernel source by default? If so where? And if not, how can it be installed? TIA[/QUOTE]

Shown below is where you will find the kernel source in Synaptic.
It is installed in the /usr/src directory.

Some programs require that you make a symlink to the actual source folder.
Example:

```
$ cd /usr/src
$ sudo ln -s linux-source-2.6.10 linux
```

[img]http://img.photobucket.com/albums/v469/camplear/forums/synkernel.png[/img]
[img]http://photobucket.com/albums/v469/camplear/forums/[/img]
[img]http://photobucket.com/albums/v469/camplear/forums/[/img]

---

### Post by az on 2005-05-19
Try installing the linux-headers package as mentioned.  You do not have to worry about telling your app where it is.  It makes a symlink in /lib/modules/*****/build so that it should get picked up when you compile.

If it fails, use the full source.  Use the linux-tree package since you do not want to apply all the packages and the configurations yourself.  If you wanted to compile a different (pristine) kernel and configure it to your liking, use linux-source.  That is not what you want to do here.

---

### Post by add1sun on 2005-05-21
I need to install the headers in order to install my modem driver on my laptop.  The problem is, of course, that without a modem driver, I have no internet connection, so I can't apt-get or synaptic to get them...

I do have other computers with internet.  Any ideas on where I could download what I need on to a usb drive and then transfer to the laptop?  Other ideas?

---

### Post by add1sun on 2005-05-22
Well, I found the packages at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and got the headers I needed (linux-headers-2.6.10-5-386 - I aso go the plain 2.6.10-5 since the 386 depends on it).   I have installed them, but still get errors saying they don't match my kernel but that is the correct kernel.  So, now I'm getting really frustrated.  Do I have to do anything else with the headers once I have them installed?

What should I be looking at now?

---

### Post by Xian on 2005-05-22
What kernel source does your sym link in /usr/src point to?

Mine is: /usr/src/linux-source-2.6.10
And this is my running kernel:
```
$ uname -r
2.6.10-5-386
$
```

Directory contents:

[img]http://img.photobucket.com/albums/v469/camplear/forums/2610.png[/img]

---

### Post by add1sun on 2005-05-22
I have the same uname: 2.6.10-5-386

In my /usr/src I have these dirs:
linux-headers-2.6.10-5
linux-headers-2.6.10-5-386
modules
rpm

I also have /lib/modules/2.6.10-5-386
I am trying to install a linuxant modem driver.  The error that I am receiving says:
```
WARNING: the kernel version () defined in /lib/modules/2.6.10-5-386/build/include/linux/version.h does not match the currently running kernel (2.6.10-5-386)
The cause of this problem is an incorrect kernel source path.
Please check that /lib/modules/2.6.10-5-386/build points to right tree.
The cause of this is usually a missing or unconfigured kernel source tree ( and sometimes an incorrect directory or symbolic link).

However, proper /boot/config-2.6.10-5-386 was found.
Would you like to try using it (in temporary kernel tree)?
```

When I say yes to this last bit it still fails.  I get the same error whether pointing to /usr/src or /lib/modules.

This is all gibberish to me.

---

### Post by Xian on 2005-05-22
[QUOTE=add1sun]I have the same uname: 2.6.10-5-386

In my /usr/src I have these dirs:
linux-headers-2.6.10-5
linux-headers-2.6.10-5-386
modules
rpm

I also have /lib/modules/2.6.10-5-386[/QUOTE]
I honestly don't know about that driver you are trying to install, but when I hear packages complaining about kernel sources the things I immediately look for are: (1) That the correct kernel source is unpacked into the /usr/src directory, and (2) That there is a proper symlink present to that source folder. From the information you have provided neither of these exist.

I would suggest that you download and untar the kernel source into the /usr/src path like the image I provided, and then make the symlink with the command listed earlier. Again, I have no experience with your driver installation but am only thinking out loud with other drivers I have used on my box, and their need for the matching kernel source to be located where expected.

---

### Post by add1sun on 2005-05-22
Thanks for all your help Xian.  It's still not working unfortunately.  I went and installed the linux-source-2.6.10, but now it just says that there is no autoconf.h file.  It goes on to say that I should reconfigure doing make menconfig and then compile and install the new kernel.

I think I am going to give up on the modem and look for another way to connect to the internet.  I see a wireless card in my future.

---

### Post by Xian on 2005-05-22
[QUOTE=add1sun]Thanks for all your help Xian.  It's still not working unfortunately.  I went and installed the linux-source-2.6.10, but now it just says that there is no autoconf.h file.  It goes on to say that I should reconfigure doing make menconfig and then compile and install the new kernel.[/QUOTE]
I'm sorry. I really wish I knew more about that driver.

---

### Post by MkIII_Supra on 2005-07-07
Well this is more fun than a barrel of  chimpanzes! When I go to my /usr/src this is what I find in it:

john@jtop:/usr/src$ ls --color
rpm
john@jtop:/usr/src$

And I am pretty darn sure I installed the headers... matter of fact Synaptic states that I have:

"**Linux Kernel Headers for development**
This package provides headers from the Linux kernel.  These headers
are used by the installed headers for GNU glibc and other system libraries."

So once again the kernel headers issue rears it's ugly head. ](*,) 

Any ideas?

---


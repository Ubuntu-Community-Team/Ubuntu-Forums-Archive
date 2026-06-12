---
title: "Segfault after upgrading to 8.42.3 ATi driver in Kubuntu Feisty"
date: 2007-10-23
forum: General Help
---

### Post by srunni on 2007-10-23
Hi,

I updated my graphics driver to the new 8.42.3 release by ATi. I'm running Kubuntu Feisty with a Radeon X300. However, when I try to run fglrxinfo or glxgears now, I'm getting this error: ```
Segmentation fault (core dumped)
``` Any ideas?

---

### Post by srunni on 2007-10-24
Any ideas?

---

### Post by sergio.gameiro on 2007-10-26
I was having this same problem with my installation.

I have a openSUSE 10.3, glxinfo, glxgears, fglrxinfo and fgl_glxgears all seg faulted (mainly, any program that tried using OpenGL was segfaulting on me).

My problem was solved when I didn't use the built-in functionality of the installer that generates a package for the distribution, and used the installer directly.

Here's my steps (don't know how these can apply to Ubuntu):

1 - Prepare kernel (taken from [here]("http://linux.wordpress.com/2007/10/11/opensuse-103-amdati-drivers-installation/")):

```
# cd /usr/src/linux-<version>
# make mrproper
# make cloneconfig
# make modules_prepare
```

and one last command to clean the kernel source:

```
# make clean
```

2 - Remove any previous installations:

```
# rpm -e $(rpm -qa | grep fglrx)
```

3 - Remove any left over:

```
# rm -fR `find /lib /lib64 /usr -name *fglrx*`
```

4 - Run the visual setup for the ATI driver:

```
# sh <LOCATION_OF_ATI_DOWNLOAD>/ati-driver-installer-8.42.3-x86.x86_64.run
```

Follow the steps and then reboot.

I hope it helps.

---

### Post by srunni on 2007-10-26
So it's a kernel issue? I think I'll just wait until I upgrade to Gutsy in that case, because I don't know how aptitude will respond to a manual kernel installation.

---

### Post by sergio.gameiro on 2007-10-27
No dude, it's not a Kernel issue. It's an issue at the installation package from ATI.
The visual setup works, but the distribution package generation is broken.

Those kernel steps are required just to clean/prepare the kernel for building up the kernel module for the ATI's driver. Nothing much. Just precaution.

Don't worry, nothing will change with those steps, and apitude probably won't even notice.

Those first steps are just to clean up your system to ensure that the kernel module compilation performed by ATI's installer works.

Don't worry.

---


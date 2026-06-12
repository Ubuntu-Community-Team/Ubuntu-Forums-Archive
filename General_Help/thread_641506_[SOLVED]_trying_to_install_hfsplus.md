---
title: "[SOLVED] trying to install hfsplus"
date: 2007-12-15
forum: General Help
---

### Post by jmagick07 on 2007-12-15
[http://www.ardistech.com/hfsplus/](http://www.ardistech.com/hfsplus/)

The README file is confusing, I don't know if it's Linux 2.4 or Linux 2.6 or what Kernel it has.  All I know is that it's Ubuntu 7.10

Can you take this README file and break it down as to what I have to do as an Ubuntu 7.10 user, to get hfsplus installed on my computer... so I can read/write to an external hard drive formatted for Mac?

> The HFS+ can be used with Linux 2.4 and 2.6 and can be compiled either
as module or as builtin driver. The driver source requires the
configured kernel source of the target kernel.
This release also include support for HFS, the instructions to compile
the driver are equal to the HFS+ driver, excepts that Linux 2.4 currently
requires the linux-2.4.hfs.diff patch.

Modular driver:

For Linux 2.4.21 and earlier versions it's required to apply the patch
linux-hfsplus.2.4.diff and to recompile the kernel. For Linux 2.5 or
Linux 2.4.22 and later this is not required.
To build the driver go to the hfsplus directory and start make with the
path to the kernel source as argument:

	cd hfsplus
	make KERNELSRC=.../linux-2.x

To install the module type:

	make KERNELSRC=.../linux-2.x install

After a reboot the module can be loaded with 'modprobe hfsplus' or it
will be loaded automatically by the kernel, if the '-t hfsplus' option
is used with mount.


Builtin driver:

Recent kernels already have the hfsplus support integrated, so that
you only need to replace the hfs or hfsplus directory. Otherwise
first the linux-2.4.hfsplus.diff or linux-2.6.hfsplus.diff has to be
applied to the kernel source and the hfsplus directory has to be copied
there:

	patch -p1 -d .../linux-2.x < linux-2.x.hfsplus.diff
	cp -r hfsplus .../linux-2.x/fs

Now you can go to the kernel source, configure the kernel as usual and
rebuild the kernel.

---

### Post by jmagick07 on 2007-12-15
anyone?

---

### Post by r-mo on 2007-12-15
Thought that it was built into ubuntu already, or is it read-only?? 

I've certainly read hfsplus volumes before when I was doing some data recovery from a mac.

---

### Post by r-mo on 2007-12-15
"Configure the kernel as usual and rebuild the kernel."

Oh, they make it sound so easy :lolflag:

---

### Post by jmagick07 on 2007-12-15
> **r-mo said:**
> "Configure the kernel as usual and rebuild the kernel."

Oh, they make it sound so easy :lolflag:


I have to replace "2.x" with either 2.4 or 2.6 (as those are what's in the downloaded archive.

> patch -p1 -d .../linux-2.x < linux-2.x.hfsplus.diff
cp -r hfsplus .../linux-2.x/fs

I believe the question was which is Ubuntu 7.10 using ;)

---

### Post by jmagick07 on 2007-12-15
> **r-mo said:**
> Thought that it was built into ubuntu already, or is it read-only?? 

I've certainly read hfsplus volumes before when I was doing some data recovery from a mac.

It's read-only.  This makes it writable also...

---

### Post by Shazaam on 2007-12-15
Try this in terminal...
```
uname -a
```
This code will print out your kernel version. uname -r works for a simpler printout.

---

### Post by jmagick07 on 2007-12-15
> **Shazaam said:**
> Try this in terminal...
```
uname -a
```
This code will print out your kernel version. uname -r works for a simpler printout.

Thanks :)

---


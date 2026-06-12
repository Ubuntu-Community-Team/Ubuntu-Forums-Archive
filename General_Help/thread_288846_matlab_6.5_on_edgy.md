---
title: "matlab 6.5 on edgy"
date: 2006-10-30
forum: General Help
---

### Post by mehmet on 2006-10-30
Hi,
I have just installed edgy and want to use matlab 6.5 on it. I was using 
it on breezy so did not think I would have a problem. 
The problem is after installation I am executing with 
LD_ASSUME_KERNEL=2.4.1 (as I do with breezy).

But it gives these errors and doesnt start:

/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

libc.so.6 seems to be OK:

$locate libc.so.6
/lib/tls/i686/cmov/libc.so.6
/lib/libc.so.6

If I dont use LD_ASSUME_KERNEL variable then the error is this:

/var/tmp/lm_TMW.ld: relocation error: /var/tmp/lm_TMW.ld: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

Is there a way that I can solve this problem? 

Thank you.

---

### Post by yosefm on 2006-11-02
I've run into a similar problem. LD_ASSUME_KERNEL=2.4.1 no longer works with matlab, as none of the libc versions found in Edgy contain ABI information, as far as I could tell (with readelf). 

I can start Matlab 7 without the LD_... stuff, but then I can't use the Symbolic Math Toolbox, because it needs errno@GLIBC_2.0, which I believe was removed in glibc-2.4 (the Edgy glibc). 

I believe that if someone could offer a package with glibc-2.4 with support for the older symbols, it would solve the problem. older libc probably won't do, as Matlab uses native libs such as libXau that are compiled against libc-2.4.

---

### Post by Faelar on 2006-11-06
I've the same problem too!

This is what I discovered about it!

I wanted to run Matlab7 with Symbolic Toolbox working.
Under Dapper I had to do the well known export command to **fix Symbolic Toolbox issue**.
**This issue isn't caused by the glibc version (I tried to install every version) but owing to the kernel version.**
With the "export LD_ASSUME_KERNEL=2.4.1" call **you simply set the LD_ASSUME_KERNEL global variable to the value "2.4.1"**.
You can try to call the export command without options to watch this.

Now with Kubuntu 6.10 Edgy Eft a**fter I called the export command every further command I try to execute in the shell doesn't work**.
Some examples:
if I try to call "**ls**", bash says that it can't find "**librt.so.1**"
with "**clear**" it can't find "**libdl.so.2**"
**when I call any program** it can't find "**libc.so.6**"

So after the export command you can't open any program in particular you can't open matlab ](*,)

You can check the export command had effect by calling it without options: from the global variables list you can recognize the variable LD_ASSUME_KERNEL you've just set!

**I think that is a kernel problem!** I'm searching a solution in that direction. In fact without the export command I can run matlab7 though the problem with Symbolic Toolbox.

I hope to find a solution soon. If not I'm going to install an older kernel version.

Any help is welcome!

---

### Post by yosefm on 2006-11-12
Not a kernel problem. You might want to read up on LD_ASSUME_KERNEL.

Anyway, as a desperate man I tried with a dapper kernel still left on my system (2.6.15), and of course, no joy.

---

### Post by serxyz on 2007-10-16
SerXYZ:

I have the same problem with Matlab6.5 under Suse10.2 (while Matlab6.5 worked fine under Suse10):

================================
$ export LD_ASSUME_KERNEL=2.4.1
$ lmstart 
/bin/sh: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
$ ls
ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
$ mkdir
mkdir: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
================================

After hours of googleing I've found that some versions of Ubuntu (and also Suse, Fedora, etc) DO NOT support "export LD_ASSUME_KERNEL=2.4.1" anymore:

==========================================
<http://rogue.colorado.edu/Wikipin/index.php/FAQ>

FAQs for Pin:

a) What version of OS do I need to run Pin?

We believe pin works on these platforms:

    * Linux
          o Red Hat 7.1
          o Red Hat 8.0
          o Red Hat 9.0
          o Red Hat Enterprise Linux 2
          o Red Hat Enterprise Linux 3
          o Red Hat Enterprise Linux 4
          o CentOS 3
          o CentOS 4
          o Fedora Core 2
          o Fedora Core 3
          o Fedora Core 4 (statically linked pintools will not work)
          o Suse 9
          o Mandrake 10. 

The following distributions DO NOT come with runtime that allows a LD_ASSUME_KERNEL value of 2.4.1. See directions for how to run pin on these systems.

    * Red Hat Enterprise Linux 5 and later (including clones like CentOs)
    * Fedora Core 5 and later
    * Suse 10 and later
    * Ubuntu 7 and later 

b) My Linux distribution is not on the supported list, how will I know if pin will work on it?

Pin requires that systems allow an LD_ASSUME_KERNEL setting of 2.4.1. To test your Linux system for compatibility with pin, try setting the LD_ASSUME_KERNEL environment variable and executing a program:

 [root@vs-lin64-2 ~]# export LD_ASSUME_KERNEL=2.4.1
 [root@vs-lin64-2 ~]# /bin/ls
 /bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
 [root@vs-lin64-2 ~]#

If you see an error message similar to the one above, then your system does not allow 2.4.1 and pin will not work. The release notes will usually say if the distribution has dropped support for 2.4.1. Note that 2.4.1 is not the version number of glibc, it is the minimum kernel version number that the glibc needs to run. This is controlled by the way the glibc is configured, so you cannot determine the LD_ASSUME_KERNEL value from the glibc version number. See LD_ASSUME_KERNEL ([http://people.redhat.com/drepper/assumekernel.html](http://people.redhat.com/drepper/assumekernel.html)) for more background. 
==========================================

I have not idea of how to resolve this conflict between some versions of Linux and some version of Matlab :(

Regards,

Ser.

---


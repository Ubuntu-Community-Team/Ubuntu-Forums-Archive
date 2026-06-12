---
title: "Bestcrypt"
date: 2005-09-15
forum: General Help
---

### Post by flyingbrass on 2005-09-15
I'm dual booting with XP and want the ability to access my Bestcrypt volumes on my Win partitions.  [Linux version of Bestcrypt](http://www.jetico.com/index.htm#/linux.htm).

uname -r says 2.6.10-5-686

I don't know what all is needed for the modules to be created.  Here are some versions of things installed that might be relevant:

linux-source-2.6.10 (says 2.6.10-34.5)
linux-kernel-headers (2.5.999-test7-bk-17)
linux-headers-2.6.10-5 (2.6.10-34.5)
linux-headers-2.6.10-5-686 (2.6.10-34.5)

I grabbed BestCrypt-1.6-2.tar.gz, uncompressed it, ran make, then checkinstall.  It created and installed a .deb.  Bestcrypt worked after rebooting. However, when logging in a few windows pop up in gnome saying Show Desktop, Window List and Workspace Switcher have quit unexpectedly.  Not good.

From dmesg:
localhost kernel: bc: no version for "struct_module" found: kernel tainted.

I did a search, and it seems this has something to do with modules being compiled with different options than the kernel.  Or something like that.  The message disappeared after I removed the bestcrypt package.

Any ideas how to get this working properly?

---

### Post by flyingbrass on 2005-09-16
I bumbled around and got it working.

I'm not sure what fixed it. I installed a thing or two listed in the first part of kernel compiling instructions. I deviated from those instructions and ran make mrproper in my source directory. Not sure exactly what it does, but a bunch of stuff flashed across the screen. Then make oldconfig, and after that make menuconfig. Since I have two directories of headers for my kernel version in /usr/src, one with 686 appended, I thought maybe that needed to be specified (it was showing Pentium).  I set the cpu type, saved and exited.  I didn't change any other settings.

I compiled and installed Bestcrypt. It works, and I'm not getting any notices about things unexpectedly quitting in gnome.

---

### Post by flyingbrass on 2005-09-16
Argh.  I was wrong and wasted time barking up the wrong tree.  Looks like recent updates are responsible, as mentioned [here](http://ubuntuforums.org/showthread.php?t=65005), not a problem with Bestcrypt.

Oddly, the "quit unexpectedly" warnings don't happen every time I reboot and log in, which is why I was blaming Bestcrypt.

---


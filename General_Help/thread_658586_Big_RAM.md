---
title: "Big RAM?"
date: 2008-01-04
forum: General Help
---

### Post by CarlosinFL on 2008-01-04
My laptop has 4 GB of DDR2 RAM however I only show that 3.5 GB is being used. Is there a kernel that allows Linux to see more RAM? Normally in Debian there is a big RAM kernel to address all 4 GB but I can't find it in Ubuntu.

```
carlos@shark:~$ uname -a 
Linux shark 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
carlos@shark:~$ sudo apt-cache search linux-image-2.6.22-14
virtualbox-ose-modules-2.6.22-14-generic - virtualbox-ose modules for linux-image-2.6.22-14-generic
virtualbox-ose-modules-2.6.22-14-server - virtualbox-ose modules for linux-image-2.6.22-14-server
linux-image-2.6.22-14-386 - Linux kernel image for version 2.6.22 on i386
linux-image-2.6.22-14-generic - Linux kernel image for version 2.6.22 on x86/x86_64
linux-image-2.6.22-14-server - Linux kernel image for version 2.6.22 on x86/x86_64
linux-image-2.6.22-14-virtual - Linux kernel image for version 2.6.22 on x86
linux-image-2.6.22-14-rt - Linux kernel image for version 2.6.22 on RT kernel
linux-image-2.6.22-14-ume - Linux kernel image for version 2.6.22 on Ubuntu Moblie and Embedded
linux-image-2.6.22-14-xen - Linux kernel image for version 2.6.22 on This kernel can be used for Xen dom0 and domU

```

---

### Post by taurus on 2008-01-04
Your best bet right now is to install the x86_64 version.

---

### Post by fjgaude on 2008-01-04
I don't know of any big RAM kernel... maybe your system is reserving about 400 MB for other things, like your video board.

---

### Post by CarlosinFL on 2008-01-04
Nope - there is no sense in installing a 64 bit kernel unless you have a 64 bit CPU. 

I don't have on board video...My laptop uses a Nvidia PCI-E GPU w/ its own RAM.

---

### Post by Sef on 2008-01-04
> My laptop has 4 GB of DDR2 RAM however I only show that 3.5 GB is being used. Is there a kernel that allows Linux to see more RAM? Normally in Debian there is a big RAM kernel to address all 4 GB but I can't find it in Ubuntu.

32-bit systems can only see 3.7 GB of ram.   If you want Ubuntu to see all of your 4 GB, then you will have to get the 64-bit version as suggested by taurus.

---

### Post by CarlosinFL on 2008-01-04
Hmmm... My desktop PC running Debian (Lenny) 32 bit simply because I can't live w/o Flash pligin for Firefox which is not available for AMD64 systems however I have 4 x 1GB modules and I show all 4 GB available in HTOP.

---

### Post by fjgaude on 2008-01-04
> **Carlwill said:**
> Hmmm... My desktop PC running Debian (Lenny) 32 bit simply because I can't live w/o Flash pligin for Firefox which is not available for AMD64 systems however I have 4 x 1GB modules and I show all 4 GB available in HTOP.

If you check the 64-bit forum here you will find it is easy to run x64 and still have Flash. Use a Kliz script. Very easy to do. Both my computers are 64-bit Gutsy running Flash. Works great.

---

### Post by CarlosinFL on 2008-01-04
Actually I forgot that GG has a bug that can't even install Flash in 32 bit systems...

This sucks - No Flash but that is a totally separate issue.

---

### Post by taurus on 2008-01-04
> **Carlwill said:**
> Actually I forgot that GG has a bug that can't even install Flash in 32 bit systems...

This sucks - No Flash but that is a totally separate issue.

You cannot install flashplugin-nonfree from repos right now BUT you can still install it by hand by downloading it either in .deb or .tar.gz.

---

### Post by markusf21 on 2008-01-04
> **Carlwill said:**
> Actually I forgot that GG has a bug that can't even install Flash in 32 bit systems...

This sucks - No Flash but that is a totally separate issue.

What are you talking about? I have 32 bit Gutsy and Flash works great.

---

### Post by oldos2er on 2008-01-04
> **Carlwill said:**
> Hmmm... My desktop PC running Debian (Lenny) 32 bit simply because I can't live w/o Flash pligin for Firefox which is not available for AMD64 systems however I have 4 x 1GB modules and I show all 4 GB available in HTOP.

 Flash runs fine for me in Swiftweasel, 64-bit Gutsy. You might want to visit the x86-64-bit board.

---

### Post by SOULRiDER on 2008-01-04
Im almost certain that if you recompile the kernel with big RAM support you'll be able to see your 4 GB of memory, but dont take my word for it.

---

### Post by Digitallysick on 2008-01-04
you should run 64bit , trust me its worth it.

---

### Post by mrazster on 2008-01-04
You can run 4GB+ ram perfectly fine on a 32bit linux system...you just have to recompile the kernel to support more than 4GB memory allocation.
Wich Ubuntu generic 32bit kernel don't.

---

### Post by CarlosinFL on 2008-01-05
> **mrazster said:**
> You can run 4GB+ ram perfectly fine on a 32bit linux system...you just have to recompile the kernel to support more than 4GB memory allocation.
Wich Ubuntu generic 32bit kernel don't.

Thanks. I was 100% sure that 32 bit OS's can't see or utilize more than 3.5 GB but it simply appears there is no pre-compiled kernel in any repo. Thanks. I will try and recompile a kernel Sunday.

---

### Post by aavaliani on 2008-02-22
I am also using 32bit ubuntu. But installing server kernel solved the problem.

sudo apt-get install linux-server linux-headers-server

archie

---

### Post by jespdj on 2008-02-22
The kernel of the server version of Ubuntu has support for [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension), which is a trick to make a 32-bit system be able to use up to 64 GB RAM.

All new Intel and AMD processors of the past few years have 64-bit extensions, and Flash works on 64-bit Ubuntu just as well as on 32-bit. Performance of 64-bit Linux is a bit higher than 32-bit, especially for processor-intensive applications.

So there's really no reason to not use 64-bit Ubuntu. See the stickies in the x86-64 forum for more information.

---


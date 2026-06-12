---
title: "Questions about kernels"
date: 2012-10-15
forum: General Help
---

### Post by Deucalion29710 on 2012-10-15
I am just interested to know your thoughts about what kernel would be best to use on an AMD quad core phenom configuration.  I currently use 3.5.4 with this, which was listed on a site as being stable, however, users in another forum say that 3.4 is the latest stable kernel.  Is 3.5.4 considered to be stable?  Is this the best kernel to use on an AMD64 based system?  Another thing that really confuses me is that after this kernel was installed, when I opened Update Manager it had files there for 3.2 generic??? :confused:

---

### Post by Doug S on 2012-10-15
I consider [this]("http://www.kernel.org/") to be the "master" reference on kernels.
 
And yes, even if you are running a higher level kernel updates to the 3.2 series kernels will still be applied (at least that is what I found on my 12.04 server system just the other day). If you ever go back to the standard 3.2 series kernel, it will be up to date.
 
I don't know the answer to what is best for your system, I think you need to decide that. There will be many opinions on this subject. Myself, I only deviate from the standard 12.04, 3.2 series kernel for special tests and such.

---

### Post by Deucalion29710 on 2012-10-15
Thanks Doug.  These are tar.bz2 files.  Would that be a compressed file that must be unzipped?  I am used to having to download these in 4 parts.

---

### Post by Doug S on 2012-10-15
Assuming you are referring to the source files from the link I gave, yes they are compressed. Example to extract:```
tar -xjf linux-3.5-rc7.tar.bz2
```
However, then you would have to compile. While I use the link I gave as the "master" reference re-stable or not, when I can I use the [Ubuntu kernel-ppa]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") to get already built Ubuntu kernels (the 4 .deb files that I think you were referring to).

---

### Post by philinux on 2012-10-15
> **Deucalion29710 said:**
> I am just interested to know your thoughts about what kernel would be best to use on an AMD quad core phenom configuration.  I currently use 3.5.4 with this, which was listed on a site as being stable, however, users in another forum say that 3.4 is the latest stable kernel.  Is 3.5.4 considered to be stable?  Is this the best kernel to use on an AMD64 based system?  Another thing that really confuses me is that after this kernel was installed, when I opened Update Manager it had files there for 3.2 generic??? :confused:

Is your machine running ok with the stock kernel? Is this 12.04? Or 12.10?

Have a check with this command to see what older kernels are installed.

```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get --dry-run remove
```

From step five here. [http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by Deucalion29710 on 2012-10-15
Thanks again, Doug.  That is really good information.  Phillip, chances are I will be running Xubuntu tonight, so I will be reloading everything stock.  After that I will look into installing the latest stable kernel using the information that Doug has provided.

---

### Post by Linuxisfast on 2012-10-15
Unless you are having hardware or driver issues, the current Ubuntu kernel which is well tested and patched regularly is the most stable alternative. Ubuntu devs if necessary patch the existing kernel from other kernels to add features or fix regressions. Also since this kernel is well tested, it give the user a stable system. I am running the existing kernel without any hitches on my AMD Bulldozer machine.

---

### Post by Deucalion29710 on 2012-10-17
It is running ok, but just ok.  What I mean is that when I look at additional drivers, there seems to be no drivers active.  It gives me 2 options for FGLRX drivers, but that's all that I see.  No USB, sound, CPU, etc.  Also I am having a problem with connectivity.  It drops out my connection and does not notify me that I am offline.  At this point I have to reboot to get connectivity again.  I am using an android usb tether.  I know that the phone is connected because I can still navigate from it.  It would seem that this could be related to the no apparent drivers issue.  How does one know when it is necessary to switch kernels?  I would rather have a compiled kernel because I'm not all that experienced with Linux.  I have a version 3.5.4 which I acquired from another source, however I'm not real sure that it is best for me, so I have not installed it this time around.  I am now using Xubuntu 12.04 (I switched).  This is a fresh install and I have added Gnome, but I have not really added anything else of significance.

---

### Post by Deucalion29710 on 2012-10-17
My lack of drivers being reported in "Additional Drivers", and connectivity issues seem to have been solved with the 3.5.4 kernel, but I'm still interested to know if there would be a better kernel for me.

---


---
title: "How do you prepare kernel in ubuntu?"
date: 2007-01-03
forum: General Help
---

### Post by fromans4 on 2007-01-03
I know the thread title sounds a bit strange, but I couldn't think of anything that made sence.:confused: 

Let me start by saying that I am new to Ubuntu, I have been running FC3/4/5 for a while in conjunction with MythTV and thought it was time to try something different. So here I am.

I use a Silverstone HTPC case that has an integrated VFD (digital display). This display depends on a driver called "imon_vfd". The driver can be very difficult to install, it requires you have the kernel source configured. I tried installing it with the kernel headers and source files available via apt-get, but it didn't work. I am used to being able to configure the kernel source for a particular architecture. This in conjunction with running the make modules command would usually resolve my issues with installing this driver.

When I try to run the "make modules" command in Ubuntu I get an error that seems to point to the fact that I have not configured the kernel for an architecture yet. I can't seem to find any info about how I go about doing this and the process I used to use in Fedora obviously won't work The directory structure required to build the kernel does not seem to exist. Below is the error I get when I try to run "make modules" -

mythtv@htpc:/usr/src/linux$ sudo make modules
  CHK     include/linux/version.h
make[1]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make: *** [arch/i386/kernel] Error 2

Any help woukd be appreciated.

Thanks,
Brent

---

### Post by pseudonym on 2007-01-03
I'm not 100% sure but I think your problem is caused by the fact that Ubuntu/Debian kernels are built using the 'kernel-package' package, as opposed to the method you're used to in Fedora. I think there's one or two directories that get created differently.

I think it's still possible to use your method, though, but you would have to build the whole kernel for it to work, not just one module. [Here]("http://ubuntuforums.org/printthread.php?t=29885") is an example which you might find useful (esp. steps 6 & 7).

Of course, you could also build your own kernel using kernel-package. The Ubuntu-specific method is [here]("http://www.ubuntuforums.org/showthread.php?t=311158&highlight=kernel+compile"). I don't bother with a separate headers package or the modules_image target, because I've never had a need to build a 3rd-party module that doesn't come with it's own install package (like nvidia drivers). I think in your case the modules_image target might be needed, because it creates the directory /usr/src/modules (but, again, I'm not sure because I don't use that method).

HTH, or at least points you in the right direction. :)

---


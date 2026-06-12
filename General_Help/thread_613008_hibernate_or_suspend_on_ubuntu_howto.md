---
title: "hibernate or suspend on ubuntu howto?"
date: 2007-11-14
forum: General Help
---

### Post by graphicsMan on 2007-11-14
Hi all -

I'm a relative newb to ubuntu, slowly switching over from many years of gentoo use/abuse :)  I've spent several days trying to get my machine to suspend/hibernate without any luck.  I've tried pm-utils, the hibernate package, and gnome-power-manager, all with no luck.  I've also tried to get uswsusp, but although I apt-get it, I can't find s2ram or s2disk on my system.

In general, I've had zero luck with and of the suspend to ram options, meaning that I always get some sort of error message.  In general, all of the hibernate options have managed to shut down my system, but resuming is another story.

My machine is based on  an ASRock K7VT6 with athlon xp 2600+, which is an AGP system.  I have a Geforce 6800.  I've tried following dozens of threads that I found via google, but although I changed my xorg.conf and /etc/default/acpi-support files, I can't seem to make any headway.  I would be happy with either hibernate or suspend to ram, but if I had to choose, I'd go with the ram option.

Some of the errors that I have seen are:

> hibernate-ram 
hibernate-ram: No suitable suspend methods were found on your machine.
hibernate-ram: You need to install a kernel with support for suspending to
hibernate-ram: disk or RAM and reboot, then try again.

and

pm-suspend
Error: kernel cannot suspend to ram.

Thanks for any input anyone can give.  Let me know what log files, etc... would be useful for diagnosing the problem, and I'll grab them.

---

### Post by bingoUV on 2007-11-14
This has tips to identify the part that is causing suspend to fail. [https://fedoraproject.org/wiki/KernelCommonProblems#head-dfdd3eb7cba58cc5643d06f7866dd83cb769db4a](https://fedoraproject.org/wiki/KernelCommonProblems#head-dfdd3eb7cba58cc5643d06f7866dd83cb769db4a)

---


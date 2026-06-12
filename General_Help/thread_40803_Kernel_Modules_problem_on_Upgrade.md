---
title: "Kernel Modules problem on Upgrade"
date: 2005-06-10
forum: General Help
---

### Post by fastluck on 2005-06-10
I had to build alsa to get my sound to work.  To do that, I had to rebuild the kernel source.

And it does.  But I did an apt-get upgrade last night, and it quit working.  When manually mod-probing the driver, I got a bunch of unresolved externals.

I rebuilt alsa again.  The kernel version I'm using is the same version as the kernel-source I'm using.  But not long after I originally set up this system, I downloaded a newer kernel image (so I was running with two).  I had a problem with the new image, so I tried to uninstall it but couldn't find a corresponding name to pass to apt-get to remove it.  So I just removed it from menu.lst.

When I did the upgrade last night, it was re-downloaded and added to my menu.lst file.

There might not be a problem--it might just be that the binary version I'm booting with (2.6.10-5-686) is out of sync with the code I'm using to build the modules.  I'm building linux-source-2.6.10 with linux-headers-2.6.10-5-686.  I'm **not** doing a make install, just make menuconfig and exiting, followed by make. I'm using /boot/config-2.6.10-5-686 and not changing anything.

But I think that the binary kernel image downloaded last also overwrites the modules.  That's a problem.  I like to think I can build a custom kernel and test it, and still be able to boot with the old one if there's a problem.

Are the modules all put in the same place regardless of version?  Is there a soft link called modules or something that points to the current modules? Or does apt put the modules for different kernel versions in different places?

Inquiring minds want to know.

Thanks

---

### Post by wylfing on 2005-06-10
The modules for different kernel images are kept separately. Explore /lib/modules and see for yourself if you have multiple kernels installed. However, for upgrades to the **same** kernel image the modules will be overwritten. So, for example, if you upgrade linux-image-2.6.10-5-386 then all of the modules under /lib/modules/2.6.10-5-386 will be overwritten.

So yes, if you compile your own modules, you may run into this problem whenever you upgrade your kernel image. The best you can do is make a script that "fixes" the modules and run it after upgrading a kernel.

---

### Post by fastluck on 2005-06-11
Thanks--I backed up my modules.

Cheers,

John

---


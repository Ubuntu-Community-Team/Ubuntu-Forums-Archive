---
title: "Vmware Server install fails?"
date: 2007-08-31
forum: General Help
---

### Post by RudolfMDLT on 2007-08-31
Hi there,

I'm trying to install Vmware Server - I have downloaded it from there website. The instlation fails when I set the the path to the kerbel modules:
> 
What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PW
D/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:80:
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected dec                                                                                                   laration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: error: expected dec                                                                                                   laration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config1/vmmon-only/./include/compat_kernel.h:21: warning: type defau                                                                                                   lts to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

rudolf@rh:~/VMware-server-1.0.3-44356/vmware-server-distrib$ uname
Linux
rudolf@rh:~/VMware-server-1.0.3-44356/vmware-server-distrib$ uname -a
Linux rh 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
rudolf@rh:~/VMware-server-1.0.3-44356/vmware-server-distrib$



I know it's in the repo's - though I only found that out after I had downloaded this and read that it was and found a how-to. I would really like this to get to work though! :)


Thanks for any info!

Rudolf

---

### Post by diatribe on 2007-08-31
I believe there is a patch that you have to run called vmware-any-any that will allow you to install vmware with your kernel

---

### Post by RudolfMDLT on 2007-08-31
Thanks! Time ran out for so I settled for a howto from the repos! I'll try the patch on my laptop! thanks!

---

### Post by Krijk on 2007-09-04
Have you tried this?

```
apt-get install linux-headers-`uname -r`
```

[http://ubuntuforums.org/showthread.php?t=542958&highlight=vmware](http://ubuntuforums.org/showthread.php?t=542958&highlight=vmware)

---

### Post by Cryptic1911 on 2007-09-04
you probably need to get the any-any 113 patch

there's a link in this post  [http://ubuntuforums.org/showthread.php?t=476004](http://ubuntuforums.org/showthread.php?t=476004)

I had the same problems, and the 113 patch still didnt fix all the errors I was having. I ended up doing a reinstall of the os and it worked great (still needed 113 patch)

---


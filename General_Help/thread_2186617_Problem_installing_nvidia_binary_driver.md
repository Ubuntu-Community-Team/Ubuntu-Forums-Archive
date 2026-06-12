---
title: "Problem installing nvidia binary driver"
date: 2013-11-08
forum: General Help
---

### Post by jalirious on 2013-11-08
Well, lspci gives "NVIDIA Corporation GT218 [GeForce 210] (rev a2)"

So, from their site I take NVIDIA-Linux-x86_64-319.17.run (12.04 64b. Kernel Linux 3.10.9-031009-generic)

I follow these instructions.. [ubuntuforums.org/showthread.php?t=2063025]("ubuntuforums.org/showthread.php?t=2063025")

First I try with DKMS. No dice. Then without .. still fails.

tail /var/log/nvidia-installer.log

/tmp/selfgz17983/NVIDIA-Linux-x86_64-319.17/kernel/nv-i2c.c:327:14: error: void value not ignored as it ought to be
   make[3]: *** [/tmp/selfgz17983/NVIDIA-Linux-x86_64-319.17/kernel/nv-i2c.o] Error 1
   make[2]: *** [_module_/tmp/selfgz17983/NVIDIA-Linux-x86_64-319.17/kernel] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.

Any suggestions?

---

### Post by SeijiSensei on 2013-11-08
Remove the package you installed and run "sudo apt-get install nvidia-current" to get the appropriate driver from the Ubuntu repositories.

---

### Post by jalirious on 2013-11-08
Thanks. Fixed after purging (++) the configuration files.

---


---
title: "Latest Kernel in Trusty Tahr"
date: 2015-05-22
forum: General Help
---

### Post by jsusanka on 2015-05-22
Running trusty tahr and it seems lately that every kernel update requires multiple reboots.  just this latest kernel required two reboots over two days.  

I am concerned if I am running the right kernel and if I my system is hacked.  

Linux 3.13.0-53-generic #89-Ubuntu SMP Wed May 20 10:34:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

That is the latest kernel I am running and just installed this morning.  Is this the correct kernel for Ubuntu 64 bit? I thought it was #88. 

thanks

---

### Post by coffeecat on 2015-05-22
I've renamed the thread so that those running Ubuntu 14.04 and who are familiar with the current kernel version for Trusty can help you. I've also moved this to General Help as it sounds more of a support request. Normally, a kernel upgrade should require only one reboot. So that forum members can advise, please clarify what you mean by, "required two reboots over two days."

---

### Post by grahammechanical on 2015-05-22
How often do you update?

I run a development version and I update every day. I have known instances where I have received updates to the kernel that require a reboot and then the next day after running the Update Manager to be asked to reboot again. This is normal.

Updates to the kernel do require a restart but they are not the only thing that requires a restart. The second required reboot on the next day could be due to packages related to the kernel being updated. I cannot say for sure but I think that updates to the Xserver and proprietary video drivers will also require a restart.

Regards.

---

### Post by SeijiSensei on 2015-05-22
I upgraded to the current Trusty kernel, 3.16.0-38-generic, the other night.  To install it, I needed to run "sudo apt-get dist-upgrade" rather than just "upgrade".  If you upgrade from the command prompt, you may see that certain packages like new kernels have been "held back."  To install those, use "dist-upgrade".

---

### Post by pfeiffep on 2015-05-22
> **SeijiSensei said:**
> I upgraded to the current Trusty kernel, 3.16.0-38-generic, the other night.  To install it, I needed to run "sudo apt-get dist-upgrade" rather than just "upgrade".  If you upgrade from the command prompt, you may see that certain packages like new kernels have been "held back."  To install those, use "dist-upgrade".Interesting, I just performed, update, dist-upgrade and reboot ...still running ```
uname -a
Linux Dell-Studio 3.13.0-53-generic #89-Ubuntu SMP Wed May 20 10:34:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```My system runs just fine I'm just curious

---

### Post by SeijiSensei on 2015-05-22
3.16.0-38-generic is the "backported" kernel from Utopic.  I think I had to accept linux-generic-lts-utopic when prompted, but I don't recall the details. Vanilla linux-generic is using 3.13.

linux-generic (3.13.0.51.58)
    Complete Generic Linux kernel and headers
linux-generic-lts-utopic (3.16.0.36.28)
    Complete Generic Linux kernel and headers

See [http://packages.ubuntu.com/trusty-updates/kernel/](http://packages.ubuntu.com/trusty-updates/kernel/) for a complete list of all the Trusty kernels.

---

### Post by pfeiffep on 2015-05-22
Thanks SeijiSensei

---

### Post by efflandt on 2015-05-22
Sometimes when a new kernel comes out it may seem like you are getting the same exact kernel for 2 or 3 automatic updates. But maybe they added something to it in the form of modules, or maybe a bug was found that they resolved. So it is not that uncommon to seemingly get the same kernel version update more than once.

---


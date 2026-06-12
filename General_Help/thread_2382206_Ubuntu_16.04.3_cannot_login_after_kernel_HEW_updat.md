---
title: "Ubuntu 16.04.3 cannot login after kernel HEW update"
date: 2018-01-10
forum: General Help
---

### Post by monkeybrain20122 on 2018-01-10
Kernel updated from 4.10.0.42 to 4.13.0.26 and I couldn't boot into the desktop any more, after typing in my login password and enter, the screen goes black for a while and then returns to the login screen. It also takes a lot longer to boot comparing to before.
So I log into 4.10.0.42 and delete the new kernel and everything is back to normal again.

My question is: normally I don't enable HEW, but this is a laptop with Ubuntu preinstalled so HEW is enabled. When removing 4.13.0-26 the package linux-image-hew-xenial was also removed. Will I still get normal kernel security update in the future (in the 4.10.0 series)?


This is the [bug ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742302")report, also [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742095"). It appears that the Nvidia driver doesn't build in this kernel.

---

### Post by mc4man on 2018-01-10
> **monkeybrain20122 said:**
> 

My question is: normally I don't enable HEW, but this is a laptop with Ubuntu preinstalled so HEW is enabled. When removing 4.13.0-26 the package linux-image-hew-xenial was also removed. Will I still get normal kernel security update in the future (in the 4.10.0 series)?


This is the [bug ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742302")report, also [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742095"). It appears that the Nvidia driver doesn't build in this kernel.
No, there will be no more updates for 4.10
There has been an acceleration in hwe, if you open synaptic & search linux-gen you'll notice linux-generic-hwe-16.04 is now at 4.13.0.... where as the other day it was at 4.10.x...
I actually have always used linux-generic-hwe-16.04-edge which gave early access but now it's actually slightly behind at 4.13.0.25.31
If you have either of those packages installed you'll get updates up to the 18.04 hwe kernel, if not then you'll only get 4.4.x updates (if linux-generic package is installed.
Bloody confusing.. see screenshot

As far as nvidia drivers, I was not able to install (re-install) the 381 with either 4.13.0.25 or .26 but the 384 & 387 drivers did. 
Generally after kernel upgrades I re-install the nvidia drivers just to make sure (not always needed

Ex. with 387
```
Unpacking nvidia-387 (387.34-0ubuntu0~gpu16.04.2) over (387.34-0ubuntu0~gpu16.04.2) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Setting up nvidia-387 (387.34-0ubuntu0~gpu16.04.2) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-4.13.0-25-generic
INFO:Enable nvidia-387
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Loading new nvidia-387-387.34 DKMS files...
Building for 4.13.0-25-generic and 4.13.0-26-generic
Building for architecture x86_64
Building initial module for 4.13.0-25-generic
Done.

nvidia_387:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

nvidia_387_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

nvidia_387_drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

nvidia_387_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

depmod....

DKMS: install completed.
Building initial module for 4.13.0-26-generic
Done.

nvidia_387:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-26-generic/updates/dkms/

nvidia_387_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-26-generic/updates/dkms/

nvidia_387_drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-26-generic/updates/dkms/

nvidia_387_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-26-generic/updates/dkms/

depmod....

DKMS: install completed.
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for initramfs-tools (0.122ubuntu8.10) ...
update-initramfs: Generating /boot/initrd.img-4.13.0-26-generic
```
 note that the 387 drivers are not yet spectre patched, the 384 are as will upcoming 390

---

### Post by monkeybrain20122 on 2018-01-10
Hi,

Actually this is Nvidia 387, it is a system76 machine from work which comes with 384 but installing cuda bumped the version to 387.  Did you reinstall the driver after the kernel update but before reboot? since if you reboot first then you don't get to desktop.

---

### Post by mc4man on 2018-01-10
> **monkeybrain20122 said:**
> Hi,

Actually this is Nvidia 387, it is a system76 machine from work which comes with 384 but installing cuda bumped the version to 387.  Did you reinstall the driver after the kernel update but before reboot? since if you reboot first then you don't get to desktop.
Yeah always before rebooting or I switch to intel gpu first.
As far as sys76 - do they use their  own nvidia drivers? what does apt-cache policy nvidia-387 say?
Here I use the ubuntu driver ppa or sometimes what's in Ubuntu repo

Ex. (after switching to 384 to check, I'll go back to 387 as it's better with cuda or nvdec hwdec
```
$ apt-cache policy nvidia-387 nvidia-384
nvidia-387:
  Installed: (none)
  Candidate: 387.34-0ubuntu0~gpu16.04.2
  Version table:
     387.34-0ubuntu0~gpu16.04.2 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
nvidia-384:
  Installed: 384.111-0ubuntu0.16.04.1
  Candidate: 384.111-0ubuntu0.16.04.1
  Version table:
 *** 384.111-0ubuntu0.16.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages
        100 /var/lib/dpkg/status
     384.98-0ubuntu0~gpu16.04.1 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages

```

to check 384 (which comes from Ubuntu at latest version), also installed fine
```
Loading new nvidia-384-384.111 DKMS files...
Building for 4.13.0-25-generic and 4.13.0-26-generic
Building for architecture x86_64
Building initial module for 4.13.0-25-generic
Done.

nvidia_384:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

nvidia_384_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

nvidia_384_drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

nvidia_384_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-25-generic/updates/dkms/

depmod....

DKMS: install completed.
Building initial module for 4.13.0-26-generic
Done.

nvidia_384:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-26-generic/updates/dkms/

nvidia_384_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-26-generic/updates/dkms/

nvidia_384_drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-26-generic/updates/dkms/

nvidia_384_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-26-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up libcuda1-384 (384.111-0ubuntu0.16.04.1) ...
Setting up nvidia-opencl-icd-384 (384.111-0ubuntu0.16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for initramfs-tools (0.122ubuntu8.10) ...
update-initramfs: Generating /boot/initrd.img-4.13.0-26-generic


```

---

### Post by monkeybrain20122 on 2018-01-10
> **mc4man said:**
> Yeah always before rebooting or I switch to intel gpu first.
As far as sys76 - do they use their  own nvidia drivers? what does apt-cache policy nvidia-387 say?
Here I use the ubuntu driver ppa or sometimes what's in Ubuntu repo




There is no intel gpu here, pure nvidia rather than optimus. I think the driver actually comes from Nvidia when I added the cuda repo from Nvidia. I will check when  I go home. Now working on a light intel machine. :)

---

### Post by mc4man on 2018-01-10
> **monkeybrain20122 said:**
> There is no intel gpu here, pure nvidia rather than optimus. I think the driver actually comes from Nvidia when I added the cuda repo from Nvidia. I will check when  I go home. Now working on a light intel machine. :)

Which sys76 laptop?
(- I bought the serval when it first came out, desktop cpu, nvidia with no optimus. Returned 30 min. after unpacking as it ran so hot, hot like scorched palms hot. 
You may have to wait for your driver source to catch up or maybe you could use the graphics driver ppa 387 package??

---

### Post by mc4man on 2018-01-10
Just to note - 
If you have 2 different kernel versions you can boot to the lower one & install nvidia there. Then it will build modules for the kernel you're on & the higher version. At worst you'd get a good build on 4.10 & a fail on 4.13, booting to 4.10 would be ok in that instance.

so in examples I posted I re-installed nvidia from 4.13.25 but notice it built for both, if I had re-installed on 4.13.26 it would have only built for 4.13.26

---

### Post by monkeybrain20122 on 2018-01-10
> **mc4man said:**
> Which sys76 laptop?
(- I bought the serval when it first came out, desktop cpu, nvidia with no optimus. Returned 30 min. after unpacking as it ran so hot, hot like scorched palms hot. 
You may have to wait for your driver source to catch up or maybe you could use the graphics driver ppa 387 package??


The Oryx pro with GTX1070, I don't have a heat problem.

---

### Post by monkeybrain20122 on 2018-01-10
Driver is from Nvidia

```
apt-cache policy nvidia-387
nvidia-387:
  Installed: 387.26-0ubuntu1
  Candidate: 387.26-0ubuntu1
  Version table:
 *** 387.26-0ubuntu1 500
        500 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64  Packages
        100 /var/lib/dpkg/status
```

---

### Post by mc4man on 2018-01-10
> **monkeybrain20122 said:**
> Driver is from Nvidia

```
apt-cache policy nvidia-387
nvidia-387:
  Installed: 387.26-0ubuntu1
  Candidate: 387.26-0ubuntu1
  Version table:
 *** 387.26-0ubuntu1 500
        500 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64  Packages
        100 /var/lib/dpkg/status
```
You could add [this ppa]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") & see if the 387 there works better, it should..
(- edit unless it mucks up your cuda related..

---

### Post by monkeybrain20122 on 2018-01-10
hi, I was in the old kernel, installed the new and reinstalled nvidia, it built in the old kernel but I wasn't sure if it built in the new one (the wall of text disappeared too fast) so I reboot and it didn't work. But now I cannot get to the grub menu to boot back to the old kernel, pressing shift doesn't do anything.

OK nevermind, escape works.

---

### Post by monkeybrain20122 on 2018-01-10
> **mc4man said:**
> You could add [this ppa]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") & see if the 387 there works better, it should..
(- edit unless it mucks up your cuda related..


Well looks like it is a kernel 4.13.x problem from the bug reports so the ppa won't help, and it is a company's computer so I am a bit conservative in messing with system unless have to.. so I took the easy way out. Just booted into the 4.10 again and deleted 4.13.0-26. and linux-image-hew. I think it would be a good idea to get security updates for kernel so I installed 4.4.0-109 (linux-image-generic and accompanied packages) and booted into it, while the Nvidia driver works without any problem wifi doesn't work. So back to 4.10. I guess I will be stuck with the current 4.10 kernel for a while and reinstall the hew kernel when upstream get the problem fixed.

Thanks for the help!

---

### Post by monkeybrain20122 on 2018-01-13
> **mc4man said:**
> You could add [this ppa]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") & see if the 387 there works better, it should..
(- edit unless it mucks up your cuda related..

Someone confirms that upgrading Nvidia driver to 387.34 from the ppa does fix the problem. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742095/comments/29](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1742095/comments/29)
I tested it, it works without messing up the cuda stuffs.

Thanks for the help and I am marking this as solved.

---

### Post by alexgwood on 2018-01-24
Hi same issue with 4.13.0.31 and Nvidia driver 403 were after login the loop sends me back to the login page.

Solved by purging all Nvidia drivers and then installing nvidia-common. Neither did Nvidia 340, 378 or 384 work for me.

```
sudo apt-get purge nvidia-*
sudo apt-get autoremove --purge
sudo add-apt-repository ppa:graphics-drivers
sudo apt-get update
sudo apt-get install nvidia-common nvidia-settings
sudo reboot

```

As one is blocked at the login window, switch to tty ctrl-alt-F1 and authenticated via terminal

That said just tested the driver to see if Nvidia was really installed and turns out graphics driver is "Nouveau", at least I can run in graphical mode. Will investigate to switch back to Nvidia driver

```

lsmod | grep -i nvidia
lsmod | grep -i nouveau

```

---


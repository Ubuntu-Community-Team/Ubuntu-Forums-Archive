---
title: "APT Sources"
date: 2007-04-06
forum: General Help
---

### Post by CarlosinFL on 2007-04-06
Guys - I was wondering if there are any available repos that have more available kernels that what I have. I don't know if I am missing some apt-get repos or what the deal is but I know at work I was able to upgrade my kernel from 2.6.17-10-generic to 2.6.17-11-386. Now I am looking for the same kernel at home and I only find the following:

```
root@tank:/# apt-cache search linux-image
alsa-base - ALSA driver configuration files
linux-image-2.6.17-10-386 - Linux kernel image for version 2.6.17 on i386
linux-image-2.6.17-10-server - Linux kernel image for version 2.6.17 on x86/x86_64
linux-image-2.6.17-10-server-bigiron - Linux kernel image for version 2.6.17 on BigIron Server Equipment
linux-image-386 - Linux kernel image on 386.
linux-image-686 - Obsoleted by: linux-image-generic
linux-image-debug-2.6.17-10-386 - Linux kernel debug image for version 2.6.17 on i386
linux-image-debug-2.6.17-10-generic - Linux kernel debug image for version 2.6.17 on x86/x86_64
linux-image-debug-2.6.17-10-server - Linux kernel debug image for version 2.6.17 on x86/x86_64
linux-image-debug-2.6.17-10-server-bigiron - Linux kernel debug image for version 2.6.17 on BigIron Server Equipment
linux-image-generic - Generic Linux kernel image
linux-image-k7 - Obsoleted by: linux-image-generic
linux-image-server - Linux kernel image on Server Equipment.
linux-image-server-bigiron - Linux kernel image on BigIron Server Equipment.
linux-686-smp - Obsoleted by: linux-image-generic
linux-image-kdump - Linux Kernel Crash Dump Image.
linux-image-2.6.17-10-generic - Linux kernel image for version 2.6.17 on x86/x86_64

```

Is my repo list messed up or missing something? Should I un-comment something or add something to allow for more packages?

Thanks for any help! 

**Here is my source.list file**

[i]deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-security multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
[/i]

---

### Post by tbroderick on 2007-04-06
It's in edgy-security main. 4th from the bottom. You should uncomment that and  edgy-security universe.

---


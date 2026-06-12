---
title: "Ubuntu 12.04 LTS - No more kernels? Affecting multiple servers."
date: 2016-08-12
forum: General Help
---

### Post by mcparty2 on 2016-08-12
Why can i not get the latest kernels via aptitude? I seem to be stuck on Ubuntu 12.04.5 LTS (GNU/Linux 3.13.0-92-generic x86_64)
This is affecting multiple servers on the same build.

I have done the obligatory...

```
apt-get update

apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.


```

No packages are kept back or to install. I have rebooted to no avail.The kernel remains the same. 
The Security Announce messages indicate it needs updating (and due to an old rsyslog issue, i need a more recent kernel without upgrading the disto version to 14.04)
The options given by the Security Announcement indicates I should be able to upgrade to the following...
[SIZE=2]
Ubuntu 12.04 LTS:
  linux-image-3.2.0-107-generic   3.2.0-107.148
  linux-image-3.2.0-107-generic-pae  3.2.0-107.148
  linux-image-3.2.0-107-highbank  3.2.0-107.148
  linux-image-3.2.0-107-omap      3.2.0-107.148
  linux-image-3.2.0-107-powerpc-smp  3.2.0-107.148
  linux-image-3.2.0-107-powerpc64-smp  3.2.0-107.148
  linux-image-3.2.0-107-virtual   3.2.0-107.148[/SIZE]

Are the updates being held back to force users to upgrade to 14.04?

Any ideas/info would be great.

Thanks

---

### Post by grahammechanical on 2016-08-12
When Ubuntu 12.04 was released at the end of April 2012 it came with Linux kernel 3.2. Ubuntu 12.04.5 is the last "point" release of Ubuntu 12.04. It comes with kernel 3.13 which was the kernel that Ubuntu 14.04 had when it was released.

Ubuntu 12.04.5 will get security fixes for the 3.13 kernel up to April 2017. It will not get any kernel newer than 3.13. And this is because 12.04 is now up to date with 14.04 when it was released and the newer kernels have been going into 14.04.

Ubuntu 14.04 is now at the point 5 release (14.04.5) stage and it has kernel 4.4 which is the kernel in Ubuntu 16.04. From this time on Ubuntu 14.04.5 will get security fixes to the kernel until April 2019. And the newer kernels will be going into 16.04.

No one is forced to do anything. We get Ubuntu free to download, install & use. We have no power to force the Ubuntu maintainers to continue supporting a version of Ubuntu any longer than they have already agreed to support it. Upgrading to a newer (longer supported version) is also free to do. It costs money to provide support for Ubuntu. The promise of free 5 years support for certain versions is a very good deal.

---

### Post by mcparty2 on 2016-08-12
Thanks for the clarity that makes sense and seems rather logical.

For the record I do love Ubuntu LTS and the 5 year support - There is nothing wrong with it. I have been trying for the best part of two days (under some pressure) to understand what was happening which is why I maybe sounded so aghast in my post. :) 

Thanks again

---


---
title: "Ubuntu 24.04 is possible update the kernel to an recent version ?"
date: 2024-10-21
forum: General Help
---

### Post by aug7744 on 2024-10-21
Hello.
Thanks for reading my topic.
Ubuntu 24.04 use kernel 6.8.
However kernel current version is 6.11.
Running apt upgrade not update the kernel to new 6.11, but continue the 6.8 with new patches.
Is possible update the kernel version to an new version ? How is possible and where are the links for download ?

Have an nice week.

---

### Post by grahammechanical on 2024-10-22
Linux kernel 6.8 is the latest kernel for Ubuntu 24.04.1 LTS. There are newer Linux kernels available. A person can get very new kernels direct from the Linux kernel development team. 

[https://www.kernel.org/](https://www.kernel.org/)

The issue for the Ubuntu kernel team is stability and Long Term Support (LTS) versions of Ubuntu are designed for stability. Over the five year life time support period an LTS release will get newer Linux kernels. Ubuntu 24.10 has Linux kernel 6.11 but it only has 9 months support. These standard versions are for those using new hardware and for Ubuntu developers to bring in development changes to the software that Ubuntu is built on.

Ubuntu 24.04 will eventually get the Linux kernel 6.11 but I cannot find out when. The method used for selecting kernels has changed. There is a lot of reading to go through and I am not very interested in becoming and expert of this selection process.

[https://discourse.ubuntu.com/t/kernel-version-selection-for-ubuntu-releases/47007](https://discourse.ubuntu.com/t/kernel-version-selection-for-ubuntu-releases/47007)

After a very quick browse through that document I come out with two points. 1) Ubuntu interim releases will possibly get a Linux release candidate kernel if one is available rather than an older stable kernel. 2) Due to this change of policy things have become very complicated and it will not be possible to predict what Linux kernel each future Ubuntu version will get.

Please note that this forum has a section called Ubuntu Development Version. Some folks there test kernels and are getting involved in testing Linux kernel 6.12. I suggest that you ask in the Ubuntu Development Section of the forum for help in learning how to download, compile and install other kernels. Having installed kernels in that way some years ago I would advise against doing this on a working operating system but on an OS installed specifically for this purpose. Expect breakage.

Regards

---


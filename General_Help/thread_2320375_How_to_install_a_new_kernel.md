---
title: "How to install a new kernel?"
date: 2016-04-13
forum: General Help
---

### Post by BulletsWithGPS on 2016-04-13
I want to know, step by step from downloading to boot ubuntu with the new kernel.

I am using 16.04 and I would like to to use kernel 3.18.

I have followed some tutorials and I have failed so I thought I should ask you guys.

---

### Post by grahammechanical on 2016-04-13
Ubuntu 16.04 comes with kernel 4.4 series. That 3.18 kernel is very old. It was released by Linux kernel.org in 2014 and the Linux developers will drop support for it January next year.

[https://www.kernel.org/category/releases.html](https://www.kernel.org/category/releases.html)

This is how you do it

[URL="https://wiki.ubuntu.com/Kernel/MainlineBuilds"]https://wiki.ubuntu.com/Kernel/MainlineBuilds

[/URL]If you are using a 64 bit CPU you need to download files marked B & the file mark AB. But here is the problem that you need to overcome. The Ubuntu kernel team does not provide a 3.18 kernel. Ubuntu 14.04.2 came with kernel 3.16 & Ubuntu 14.04.3 came with kernel 3.19. You will have to find a source for the linux-headers 3.18 ... amd64.deb & linux-headers 3.18 ... all.deb & linux-image 3.18 ... amd64.deb.

You need those 3 files - headers_amd64.deb; headers_all.deb & image_amd64.deb relevant for the kernel you want to install.

Regards

---

### Post by buzzingrobot on 2016-04-13
What problem are you trying to solve here? Why do you want to use 3.18 on 16.04?  Features are not typically deliberately removed from later kernels.

---

### Post by kansasnoob on 2016-04-13
Just looked at your earlier thread, specifically this post:

[http://ubuntuforums.org/showthread.php?t=2319380&p=13465216#post13465216](http://ubuntuforums.org/showthread.php?t=2319380&p=13465216#post13465216)

> When they updated the 14.04 kernel from 3.13 to 4.2 my wifi stopped working and this seems the only way to solve it. 

The best answer is IMHO to reinstall Trusty but this time use [the archived 14.04.1 image]("http://old-releases.ubuntu.com/releases/trusty/") which still uses the 3.13 series kernel and will be supported until April 2019:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support)

Note: that embedded link also includes downloads for the 14.04.2 and 14.04.3 images. You must use the 14.04.1 image to get the 3.13 series kernel and continue to receive support throughout April 2019.

Then I'd wait until the first point release of Xenial (16.04.1) around August of this year and try the live image only to see if wireless works. If not a bug report should be filed so it can be fixed.

---

### Post by BulletsWithGPS on 2016-04-19
> **kansasnoob said:**
> Just looked at your earlier thread, specifically this post:

[http://ubuntuforums.org/showthread.php?t=2319380&p=13465216#post13465216](http://ubuntuforums.org/showthread.php?t=2319380&p=13465216#post13465216)



The best answer is IMHO to reinstall Trusty but this time use [the archived 14.04.1 image]("http://old-releases.ubuntu.com/releases/trusty/") which still uses the 3.13 series kernel and will be supported until April 2019:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support)

Note: that embedded link also includes downloads for the 14.04.2 and 14.04.3 images. You must use the 14.04.1 image to get the 3.13 series kernel and continue to receive support throughout April 2019.

Then I'd wait until the first point release of Xenial (16.04.1) around August of this year and try the live image only to see if wireless works. If not a bug report should be filed so it can be fixed.

Sorry for this "late" reply.

The problem is its not a ubuntu problem. It doesn't what distro I am using. If im using kernel version 4.* I get this problem.

---


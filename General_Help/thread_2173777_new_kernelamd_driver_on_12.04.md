---
title: "new kernel/amd driver on 12.04"
date: 2013-09-11
forum: General Help
---

### Post by josephdavidrich115 on 2013-09-11
I thinking to reinstall ubuntu 12.04 from arch as i need something stable and last a lot longer plus i need a new kernel one from 3.8 or higher as there is a bug in the older kernels the I get I need the proprietary drivers to get better performance of steam 

my problem is plymouth I find it super buggy in arch and with it i seem to not be able to boot up in the desktop interface now again I am movin to ubuntu to it's ubuntu problem with kernel higher then 3.5/ amd driver will not mix at all is there any way to make plymouth behave as it should be?

---

### Post by josephdavidrich115 on 2013-09-11
p.s I don't come here first time I i ve been here and ask a question yet

---

### Post by grahammechanical on 2013-09-11
How old is this version of Ubuntu 12.04? If you downloaded Ubuntu 12.04 within the last few days you would have got Ubuntu 12.04.3. You need that .3 version because it comes with the Linux 3.8.0 kernel that is in Ubuntu 13.04. The original 12.04 had the Linux 3.2.0 kernel, if I remember correctly.

The problems you are having may be due to proprietary video drivers. You may need to experiment with other available video drivers. In Ubuntu we do that with the Additional Drivers utility. You may need to use Recovery Mode>Resume to get to a desktop. That does not load a proprietary video driver and so avoids proprietary video driver issues. And then we are able to open Additional Drivers and make changes.

In 12.04 Recovery Mode was in the Grub menu. In 12.04.3 you may have to open a Grub menu sub menu called Advanced Options for Ubuntu. You see, 12.04 used Grub 1.99 which did not have sub menus but 12.04.3 may have Grub 2.0 which does have sub menus. The Grub boot menu is now easier to understand.


To get a kernel higher than 3.8.0 you will need to install Ubuntu 13.04. That may be at Linux kernel 3.9.0. I know that Ubuntu 13.10 will have Linux kernel 3.11.0.

Regards.

---

### Post by ajgreeny on 2013-09-11
You can in fact get and use the 3.8.0 kernel in 12.04 but you will need to search for it and install it manually, I suggest using synaptic, which you may have to install first.  I am using Xubuntu 12.04 and keep trying the 3.8.0 kernel, but I find that it gives me a few glitches in the plymouth display, whereas 3.5.0 is fine, so I have stuck with that for now.

---


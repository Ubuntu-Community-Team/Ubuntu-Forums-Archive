---
title: "udate kernel"
date: 2008-06-29
forum: General Help
---

### Post by rmvg on 2008-06-29
in an attempt to get my system updated i enabled the universe stuff in the /etc/sources.list and have run apt-get update and apt-get upgrade but i get warnings about think the image one is about the kernel right? do i need to update these i think too.

The following packages have been kept back:
  linux-backports-modules-server linux-image-server


also i run apt-get install linux-headers-server and apt-get install kernel-sources to try and build the drdb package from source.  

However have not done a reboot worried that all these kernel things might break ubuntu on reboot (this machine is far away) just confused have i updated my kernel does the source i downloaded match current kernel?

uname -a
Linux mx1.canmail.org 2.6.15-51-server #1 SMP Tue Feb 12 17:12:18 UTC 2008 i686 GNU/Linux

-rw-r--r--  1 root         root          30983624 2005-12-15 20:23 kernel-source-2.4.27.tar.bz2
drwxr-xr-x 19 root         root              4096 2008-06-29 17:47 linux-headers-2.6.15-52
drwxr-xr-x  4 root         root              4096 2008-06-29 17:47 linux-headers-2.6.15-52-server

---

### Post by kuja on 2008-06-29
Do a "dpkg --list | grep linux-image" and see if you still have a kernel installed ... if so then you should be okay on reboot.

---

### Post by rmvg on 2008-06-29
> **kuja said:**
> Do a "dpkg --list | grep linux-image" and see if you still have a kernel installed ... if so then you should be okay on reboot.

dpkg --list | grep linux-image
ii  linux-image-2.6.15-51-server             2.6.15-51.66                 Linux kernel image for version 2.6.15 on Ser
ii  linux-image-server                       2.6.15.51                    Linux kernel image on Server Equipment.

looks ok right??
does it match with the linux headers i installed?

---

### Post by kuja on 2008-06-29
That looks okay. The linux headers is just source to build kernel modules - unless you need to do that frequently/now that should be a non-issue. I'd be more worried about the linux-backports-modules-server and maybe linux-restricted-modules-* packages. In any rate, unless you need those things in particular, you'll probably be okay.

---


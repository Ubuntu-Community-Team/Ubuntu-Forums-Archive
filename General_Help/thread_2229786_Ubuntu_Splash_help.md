---
title: "Ubuntu Splash help"
date: 2014-06-15
forum: General Help
---

### Post by jimmyh1972 on 2014-06-15
Hi
I created a customized version of ubuntu 14.04 (64bit) using remastersys.
I tried to disable the ubuntu logo right on start (the logo that comes up on the purple background with the redqwhite dots under...)
I removed all the `ubuntu-logo.png` from /lib/plymouth/themes/ubuntu-logo/
yet after creating the iso it steel comes up on boot, in the previous distro's it worked fine withput the logo after creating the iso.
I also changed the /etc/default/grub line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to GRUB_CMDLINE_LINUX_DEFAULT=""
but the ubuntu logo apears in boot.
its assential for me to remove it
any helkp please
thank's ahead - Jimmi

---

### Post by grahammechanical on 2014-06-15
Editing the Grub configuration file will not have any effect because Plymouth loads long after Grub has handed over to the Linux kernel and exited.

As far as I can discover there are two copies of ubuntu_logo.png. One in /lib/plymouth/. The other in /lib/plymouth/themes/ubuntu-logo/. Please confirm that you have deleted both copies.

Regards.

---

### Post by jimmyh1972 on 2014-06-16
Hi grahammechanical
well, yes i did, I deleted both and it steel apears...
what else can i do?

---


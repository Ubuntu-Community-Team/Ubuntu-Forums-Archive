---
title: "Dual Boot question"
date: 2007-10-20
forum: General Help
---

### Post by linuxaz on 2007-10-20
Hello,
I'm testing 7.10 here on my laptop.
Suse 10.3 is installed on sda1, which is partitioned.  I installed Ubuntu 7.10 on a 20gig partition on sda2 and had it install the boot loader to (HD1) instead of HD0 during the install.

I want to keep the Suse Grub menu and chain load to the Ubuntu grub.  That way if there is  kernel update, Ubuntu will update the grub loader.

I tried pointing setting this up in Yast, but could not seem to get the chain loader information correct.  The way it's currently working is that I copied the line from Ubuntu's /boot/grub/menu.lst into the same file in Suse.......

I've posted in the Suse forums, but no answer yet.

Thanks much,

linuxaz

---


---
title: "Linux Kernel updates causes other OS to stop booting. Why, what can I do?"
date: 2013-09-15
forum: General Help
---

### Post by mikodo on 2013-09-15
I like trying different distros. My primary install is Xubuntu. Over the years twice, Debian Stable version (Wheezy recently), wouldn't boot after the kernel was updated in my Xubuntu-primary install. When I ran <sudo update-grub> in my Xubuntu-primary install, it would show the  other installs of (Debian), but like above, it would no longer boot.   Debian Wheezy is not installed anymore, for that reason.

Oh and grub in always installed in /dev/sda.

Shouldn't all mainstream distos accept newer kernels versions, or whatever?

Is there something I can do to help stop this from happening in the future, to the other non-primary distros?


Thanks.

---

### Post by tgalati4 on 2013-09-15
After installing kernel updates, there is a post-installation script that is run.  That script performs a variety of functions including running update-grub to include the new kernel version in your grub boot list.  It's possible that you have different versions of grub on your system and that your older version of grub on your older xubuntu install will not correctly read the newer grub bootloader.

You can work around this situation, but it requires some patience.  You can install grub (and a different version) on each partition and manually edit the grub menu to include a pick for grub on a different partition.  Then you would load xubuntu from that partition and it should boot normally.

And yes, you are correct, in a perfect world, kernel updates should not clobber other distros.  But in reality, mixing older and newer distros on the same machine can cause problems.  Even dual booting Linux and Windows will cause headaches.

---

### Post by mikodo on 2013-09-15
> **tgalati4 said:**
> After installing kernel updates, there is a post-installation script that is run.  That script performs a variety of functions including running update-grub to include the new kernel version in your grub boot list.  It's possible that you have different versions of grub on your system and that your older version of grub on your older xubuntu install will not correctly read the newer grub bootloader.

You can work around this situation, but it requires some patience.  You can install grub (and a different version) on each partition and manually edit the grub menu to include a pick for grub on a different partition.  Then you would load xubuntu from that partition and it should boot normally.

And yes, you are correct, in a perfect world, kernel updates should not clobber other distros.  But in reality, mixing older and newer distros on the same machine can cause problems.  Even dual booting Linux and Windows will cause headaches.

I am going to mark this as solved.  You have confirmed what may indeed be my problem, and offered a way of overcoming it. What I will do will remain unknown for now, but no one else needs to help me out.

Thanks.

---


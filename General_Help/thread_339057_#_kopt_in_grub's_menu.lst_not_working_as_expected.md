---
title: "# kopt in grub's menu.lst not working as expected"
date: 2007-01-15
forum: General Help
---

### Post by MacHamster on 2007-01-15
Hello,

I've just moved from Debian to Kubuntu. The transition has gone flawlessly except for this one issue with the way the # kopt line is treated in /boot/grub/menu.lst

I have machines with several different kernels installed. I need to pass the same kernel boot parameters to each kernel version.

Under Debian, I used to do this by editing menu.lst and adding the parameters to the line starting # kopt. I would then run update-grub and each kernel line would then contain my additions.

This doesn't work under Ubuntu though, my changes to the # kopt line are completely ignored. I've noticed too that the comments in menu.lst state that update-grub ignores the default kernel options, so this appears to be correct behaviour for Ubuntu.

My question is thus: Under Ubuntu, how do I replicate the behaviour of the # kopt line under Debian? How do I get my additions to be added to the kernel line of *every* kernel in my menu.lst?

Thanks!

H.

---


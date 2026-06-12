---
title: "Ubuntu freezes at Boot"
date: 2007-12-02
forum: General Help
---

### Post by Bakuchris on 2007-12-02
Ubuntu freezes after loading nearly 1 segment of the preloader on the boot screen then freezes. This happens on every boot. This happened after I accidentally hit CTRL + ALT + F9 and had to do a hard reboot.

Is there any way to fix this? I've already reinstalled Ubuntu 6 times before this, I don't want to have to reinstall ANY more.

I used Wubi to install Ubuntu. I am running Ubuntu 7.10 Gutsy Gibbon.

Any greatly appreciated! :D

---

### Post by loa on 2007-12-08
Does GRUB come up? Do you have any other kernel options you can boot into? Then you could try some of those.

Otherwise you might boot up with a live-cd, and edit the parameters passed to the kernel with a root=[your root partition here, could be /dev/sda1 for instance].

Then when booted up, try sudo grub-install (or was it maybe install-grub...?) in a terminal. That might fix it.

---


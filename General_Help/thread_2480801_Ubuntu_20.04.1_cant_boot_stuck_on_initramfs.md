---
title: "Ubuntu 20.04.1 cant boot stuck on initramfs"
date: 2022-11-10
forum: General Help
---

### Post by indistress on 2022-11-10
Hello. I am having this problem. After updating and upgrading the new kernel loads up which is 5.15.0-52 and it doesnt boot. Stuck on initramfs. While the old kernel which is 5.15.0-48 still boots up just fine. It is FDE and there is no way to boot i tried everything i find on google. I was hoping someone here can help me out finding a fix for this. Thanks.

Edit. Forgot to add the fstab and crypttab are empty too after update to 5.15.0-52

---

### Post by grahammechanical on 2022-11-10
I cannot advise you how to fix this but I would offer two pieces of advice. 

1) Continue booting the 5.15.0-48 kernel. 

2) Use the terminal to update/upgrade for awhile. When Software Updater installs a new Linux kernel it removes old kernels to that only two Linux kernel are available. This does not happen when we update/upgrade through the terminal. You do not want to lose the 5.15.0-48 kernel. At some point there will be another Linux kernel. Hopefully it will install correctly and will boot. Then when you have two newer and working kernels you can remove both the 5.15.0-52 and the 5.15.0-48 kernels with the autoremove command.

For some reason the installation of the 5.15.0-52 kernel failed to complete.

Regards

---

### Post by indistress on 2022-11-11
Thank you for your reply. I tried booting from old kernel which is 5.15.0-48 which was working. Did update and upgraded. After that rebooted. And old kernel stopped working aswell now. Same initramfs screen on both kernels.

This is what i get when update/upgrade from terminal.

Setting up linux-firmware (20220329.git681281e4-0ubuntu3.6) ...
update-initramfs: Generating /boot/initrd.img-5.15.0-52-generic
cryptsetup: WARNING: target 'dm_crypt-x' not found in /etc/crypttab
W: Couldn't identify type of root file system for fsck hook
update-initramfs: Generating /boot/initrd.img-5.15.0-48-generic
cryptsetup: WARNING: target 'dm_crypt-x' not found in /etc/crypttab
W: Couldn't identify type of root file system for fsck hook

---


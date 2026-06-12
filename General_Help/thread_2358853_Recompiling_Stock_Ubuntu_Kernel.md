---
title: "Recompiling Stock Ubuntu Kernel"
date: 2017-04-18
forum: General Help
---

### Post by nfm on 2017-04-18
Hello,

I have a problem booting stock recompiled kernel. I have followed the instructions here [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel). I'm compiling kernel the "Ubuntu/Debian way".

I'm trying to reuse stock 4.10.0-19-generic  kernel and apply some minor patches on top of it. So far I haven't applied any patches since I'm running into an issue on stock recompile where root device cannot be found midway in the boot process

I receive following message and I'm thrown into busybox:
```
Gave up waiting for root device.
```
However the shell/busybox is unresponsive and I can't type in any commands. I'm not even nusing anything special, no LVM nor mdadm, just regular single ext4 root partition.

Since I'm recompiling a kernel that I'm currently running I'm pretty sure EFI/GRUB2 doesn't need any changes and when I install generated linux-image-4.10.0-19-generic_4.10.0-19.21_amd64.deb that already runs depmod and update-initramfs for you. I don't understand why it doesn't want to boot. To get system back to bootable state I do:
```
apt-get install --reinstall linux-image-4.10.0-19-generic linux-headers-4.10.0-19
``` and reboot...that does it. So what the heck is different between my recompiled kernel that 'fakeroot debian/rules binary-headers binary-generic' generates vs what's in the repos?


I do not have this problem when I compile and install vanilla Linux manually (make, make install, generate ramdisks, edit grub2 by hand etc...), but I do not want vanilla kernel since it doesn't come with AppArmor/ZFS/and misc Ubuntu patches.

---


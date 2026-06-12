---
title: "Kernel update renders system unbootable"
date: 2007-12-24
forum: General Help
---

### Post by dermoth on 2007-12-24
Last night I performed a update for the last two weeks or so of security updates; one of them included the latest Linux Kernel security fixes. This morning I just couldn't boot.

I'm not asking or help here; being an experienced systems administrator I have no doubt I'll find the cause and fix it. At first glance it looks like the initramdisk doesn't have the modules on it or they haven't been depmod'ed.

However, what is beyond my understanding is that Ubuntu don't even keep the last working kernel to boot from. I could just have booted the last kernel and recovered from there but now I'm gonna have to recover from boot CDs.

I'm also wondering how a normal user is  expected to recover from there? Normally he could be asked to boot the last kernel and follow instructions xyz. And even if there's no instructions or they doesn't work, he would still have something to work with.

I'm not sure who's decision was that, but for an OS calling itself "Linux for the human being" it seems ridiculous that they don't even have a simple way to boot from  the last kernel when a kernel update fails. I really hope it'll be addressed in the next release.

---

### Post by oscarsfriend on 2007-12-24
Whether there is a backup or not seems to depend on how significant the version number of the kernel is.  For example I have both 2.6.20-16-generic 2.6.20-15-generic, but I have had numerous minor security updates to both which presumably overwrite the previous version.

EDIT: Does anyone know if the previous versions are still in the repos?

---

### Post by dermoth on 2007-12-24
For the heads up, I just recoveried the system. I have no idea how the broken initramfs were built, but nothing was really broken and I could recover the system just by running initramfs on a chroot.

FYI, the previous backed-up initramdiskfs (built during the upgrade process like the broken one) was broken too. This is on amd64.

If anyone runs into the same problem here's the solution:

1. Boot your Ubuntu install disk
2. Open a terminal window
3. Get r00t
  $ sudo su -
4. Find your root partition and mount it (/dev/sda2 in the example below)
  # fidsk -l
  # mkdir /mnt/hd
  # mount /dev/sda2 /mnt/hd
5. Chroot to your installed Ubuntu system
  # chroot /mnt/hd /bin/bash
6. Run mkinitramfs (Make sure you ure the right initrd.img image, may be different)
  # mkinitramfs -o /boot/initrd.img-2.6.22-14-generic
7. Umount and reboot (use the normal way, or the fast one below)
  # logout
  # umount /mnt/hd
  # sync
  Press ALT-SysRq-B
8. Enjoy your working system.

---


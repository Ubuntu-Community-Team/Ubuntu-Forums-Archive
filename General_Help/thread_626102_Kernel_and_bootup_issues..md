---
title: "Kernel and bootup issues."
date: 2007-11-28
forum: General Help
---

### Post by helix on 2007-11-28
I had issues installing 7.10 or 7.06. I even had issues installing 6.10. I ended up installing 6.04 and upgrading my way to 7.10. Here I am now sitting in the 7.10 but I'm actually using the 2.6.17-12-386 or 2.6.15 kernel. Whenever I boot off a later kernel (2.6.20+) I'm unable to get anywhere meaningful. I always boot into an odd prompt that says "BusyBox" and has a prompt of (initramfs). Usual terminal commands do not work here and I'm unable to locate any help or information on this prompt in my context. 

When I boot off a kernel that will work for me, all goes fine until "mounting root file system". It hangs here for about 3-5 minutes before what appears to be a timeout. A search yielded no meaningful results.

Thanks for the help if you can provide it!

P4 2.6 socket 478
3GB PC3200
Abit IS-7 Mobo
ATI radion x850xt
All IDE disk drives 1x80gb 2x160gb
Dual boot w/ Winblows xp.

---

### Post by helix on 2007-11-28
bump.

---

### Post by helix on 2007-11-28
Final bump - help appreciated.

---

### Post by ruibernardo on 2007-12-05
Hi helix,

did you tried to boot in the recovery mode? On this mode you should be able to see the error that prevents the root partition to be mounted. Wait until the busybox prompt appears and check for an opcode error, then google for what it means.

Also you could boot from a Desktop CD and verify if the UUID of the root partition in /etc/fstab is the same that is in the kernel lines in the file /boot/grub/menu.list. This would prevent the root partition to be mounted by GRUB on boot.

Hope this helps you in some way.

---


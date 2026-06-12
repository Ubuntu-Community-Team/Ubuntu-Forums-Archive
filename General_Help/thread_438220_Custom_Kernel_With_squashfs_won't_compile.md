---
title: "Custom Kernel With squashfs won't compile?"
date: 2007-05-09
forum: General Help
---

### Post by mpetersen42 on 2007-05-09
I downloaded the latest Ubuntu source for kernel 2.6.20-15.  I then copied my existing config from /boot.  I modified a couple of DMA settings, then I set the Ubuntu additional modules squashfs and unionfs to be statically compiled.  I plan to put a kernel and load a squashfs system on CF, so the module won't be available until after the squashfs system is mounted.  I believe this means I need it statically compiled.  Anyway, it fails, here's what I did.

apt-get install linux-source
cd /usr/src
tar xjvf ./linux-source-2.6.20.tar.bz2
cd linux-source-2.6.20
make-kpkg clean
make menuconfig
make-kpkg -initrd -revision=15 --append-to-version=-CF_Compatible kernel_image


I end up with errors below.  If I compile unionfs and squashfs as a module, things go well.

ubuntu/built-in.o: In function `vfs_listxattr':
/usr/src/linux-source-2.6.20/ubuntu/fs/unionfs/xattr.c:57: multiple definition of `vfs_listxattr'
fs/built-in.o:/usr/src/linux-source-2.6.20/fs/xattr.c:147: first defined here

---


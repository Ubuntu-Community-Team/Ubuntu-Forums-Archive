---
title: "initramfs-tools, update-initramfs. problems with update edgy-proposed"
date: 2006-12-02
forum: General Help
---

### Post by aleph_444 on 2006-12-02
Hi guys, i am on kubuntu 6.10. After updating initramfs-tools against edgy-proposed repo yesterday,
update-initramfs is no longer working. 
Of course the package-install process created a buggy initrd-img, which now corrupts booting kubuntu.
Downgrading the package didnt change anything. This is the output for both versions of initramfs-tools: 

root@Knoppix:/# update-initramfs -u -k 2.6.17-10-generic
update-initramfs: Generating /boot/initrd.img-2.6.17-10-generic
ln: creating symbolic link `/tmp/mkinitramfs_Xr6395/lib/tls/i686/cmov/libc.so.6' to `lib/tls/i686/cmov/libc.so.6': File exists
ln: creating symbolic link `/tmp/mkinitramfs_Xr6395/lib/tls/i686/cmov/libc.so.6' to `lib/tls/i686/cmov/libc.so.6': File exists
ln: creating symbolic link `/tmp/mkinitramfs_Xr6395/lib/tls/i686/cmov/libc.so.6' to `lib/tls/i686/cmov/libc.so.6': File exists
ln: creating symbolic link `/tmp/mkinitramfs_Xr6395/lib/tls/i686/cmov/libc.so.6' to `lib/tls/i686/cmov/libc.so.6': File exists
ln: creating symbolic link `/tmp/mkinitramfs_Xr6395/lib/tls/i686/cmov/libc.so.6' to `lib/tls/i686/cmov/libc.so.6': File exists
ln: creating symbolic link `/tmp/mkinitramfs_Xr6395/lib/tls/i686/cmov/libc.so.6' to `lib/tls/i686/cmov/libc.so.6': File exists
cpio: ./lib/tls/i686/cmov/libc.so.6: No such file or directory
cpio: ./lib/tls/i686/cmov/libdl.so.2: No such file or directory
cpio: ./lib/libselinux.so.1: No such file or directory
cpio: ./lib/libsepol.so.1: No such file or directory
cpio: ./lib/libusplash.so: No such file or directory

Booting with that initrd produces messages:
modprobe: error while loading shared libraries: libc.so.6 cannot open shared object file: no such file or directory
/sbin/usplash: error while loading shared libraries: libc.so.6 cannot open shared object file: no such file or directory

Does anyone know how to fix this ? 

Greetings, Aleph

---


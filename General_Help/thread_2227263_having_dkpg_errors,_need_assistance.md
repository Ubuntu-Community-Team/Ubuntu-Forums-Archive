---
title: "having dkpg errors, need assistance"
date: 2014-05-31
forum: General Help
---

### Post by Heeter on 2014-05-31
I seem to be having issues with either dkpg or kernel configuring issues. I have been trying to fix for a couple of days now. My installation of postfix is failing because I cannot gt past this issue. This is for Server 14.04 64bit

```

root@mail:/home/adminpc# dpkg --configure -a
Setting up linux-image-extra-3.13.0-27-generic (3.13.0-27.50) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.14.0-031400-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-27-generic /boot/vmlinuz-3.13.0-27-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-27-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-27-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-27-generic.postinst line 1025.
dpkg: error processing package linux-image-extra-3.13.0-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.13.0-27-generic; however:
  Package linux-image-extra-3.13.0-27-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.14.0-031400-generic (3.14.0-031400.201403310035) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.14.0-031400-generic /boot/vmlinuz-3.14.0-031400-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.14.0-031400-generic /boot/vmlinuz-3.14.0-031400-generic
update-initramfs: Generating /boot/initrd.img-3.14.0-031400-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.14.0-031400-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.14.0-031400-generic.postinst line 1025.
dpkg: error processing package linux-image-3.14.0-031400-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.27.33); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-extra-3.13.0-27-generic
 linux-image-generic
 linux-image-3.14.0-031400-generic
 linux-generic
root@mail:/home/adminpc#

```

I think that my /boot partition is full. I had manually partitioned it at the begining. How can I empty it out?
```

root@mail:/home/adminpc# cd /boot
root@mail:/boot# ls -a
.                             lost+found
..                            memtest86+.bin
abi-3.13.0-24-generic         memtest86+.elf
abi-3.13.0-27-generic         memtest86+_multiboot.bin
abi-3.14.0-031400-generic     System.map-3.13.0-24-generic
config-3.13.0-24-generic      System.map-3.13.0-27-generic
config-3.13.0-27-generic      System.map-3.14.0-031400-generic
config-3.14.0-031400-generic  vmlinuz-3.13.0-24-generic
grub                          vmlinuz-3.13.0-27-generic
initrd.img-3.13.0-24-generic  vmlinuz-3.14.0-031400-generic
initrd.img-3.13.0-27-generic
root@mail:/boot# 

```

Anyone got any ideas?

Heeter

---

### Post by Heeter on 2014-06-01
UPDATE:

I gave up trying to find a solution and whipped out my gparted CD, and resized my /boot partition.

Although I am now getting different errors, the kernel upgrade did go through now.


Heeter

---


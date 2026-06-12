---
title: "Need help cleaning boot - 100% full after failed update"
date: 2015-05-11
forum: General Help
---

### Post by mark-lamorey on 2015-05-11
My boot got to be 100% full and the latest kernel is corrupt.
I boot to the older kernel but, I cannot remove any packages from boot as it is 100% full.

I have tried a few command line moves to clean but I consistently get something like the below :
-----------------------
mark@TINY:~$ sudo apt-get remove --purgeReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwxbase3.0-0 libwxsqlite3-2.8-0 linux-image-generic qt4-qmake wx-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-extra-3.13.0-46-generic
0 upgraded, 0 newly installed, 1 to remove and 44 not upgraded.
8 not fully installed or removed.
After this operation, 152 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 268009 files and directories currently installed.)
Removing linux-image-extra-3.13.0-46-generic (3.13.0-46.79) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-46-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-46-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-46-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
mark@TINY:~$ sudo apt-get autoremove --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libwxbase3.0-0* libwxsqlite3-2.8-0* linux-image-extra-3.13.0-46-generic
  linux-image-generic* qt4-qmake* wx-common*
0 upgraded, 0 newly installed, 6 to remove and 44 not upgraded.
8 not fully installed or removed.
After this operation, 161 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 268009 files and directories currently installed.)
Removing linux-image-extra-3.13.0-46-generic (3.13.0-46.79) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-46-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-46-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-46-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
mark@TINY:~$ ^C
mark@TINY:~$

---

### Post by SeijiSensei on 2015-05-11
See: [http://ubuntuforums.org/showthread.php?t=2276860](http://ubuntuforums.org/showthread.php?t=2276860)

---

### Post by mark-lamorey on 2015-05-11
Thanks SeijiSensei,
The simply sudo commands could not fix as I had a failed install / update that got me to 100% full.
Key to be able to run "sudo apt-get autoremove" was the below - from the thread you pointed me too.

Cheers 

cd /boot
sudo rm -f *-4[3-8]*

---


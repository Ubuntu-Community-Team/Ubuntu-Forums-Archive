---
title: "Errors when updating programs through terminal"
date: 2013-04-05
forum: General Help
---

### Post by Bladeforce on 2013-04-05
Hi, Firstly sorry about the long post but this is the error I am getting when updating programs using either terminal or software updater. The programs actaully update themselves but I always get this error...

Setting up linux-image-3.7.0-7-generic (3.7.0-7.15) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.7.0-7-generic /boot/vmlinuz-3.7.0-7-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.7.0-7-generic /boot/vmlinuz-3.7.0-7-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.7.0-7-generic /boot/vmlinuz-3.7.0-7-generic
update-initramfs: Generating /boot/initrd.img-3.7.0-7-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.7.0-7-generic /boot/vmlinuz-3.7.0-7-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.7.0-7-generic /boot/vmlinuz-3.7.0-7-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.7.0-7-generic /boot/vmlinuz-3.7.0-7-generic
Generating grub.cfg ...
/usr/sbin/grub-probe: error: failed to get canonical path of /boot/grub/unicode.pf2GRUB_GFXMODE=1280x1024.
/usr/sbin/grub-probe: error: cannot find a GRUB drive for .  Check your device.map.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.7.0-7-generic.postinst line 1010.
dpkg: error processing linux-image-3.7.0-7-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.8.5-030805-generic (3.8.5-030805.201303281651) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.5-030805-generic /boot/vmlinuz-3.8.5-030805-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.5-030805-generic /boot/vmlinuz-3.8.5-030805-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.5-030805-generic /boot/vmlinuz-3.8.5-030805-generic
update-initramfs: Generating /boot/initrd.img-3.8.5-030805-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.5-030805-generic /boot/vmlinuz-3.8.5-030805-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.5-030805-generic /boot/vmlinuz-3.8.5-030805-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.5-030805-generic /boot/vmlinuz-3.8.5-030805-generic
Generating grub.cfg ...
/usr/sbin/grub-probe: error: failed to get canonical path of /boot/grub/unicode.pf2GRUB_GFXMODE=1280x1024.
/usr/sbin/grub-probe: error: cannot find a GRUB drive for .  Check your device.map.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.5-030805-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.5-030805-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.7.0-7-generic:
 linux-image-extra-3.7.0-7-generic depends on linux-image-3.7.0-7-generic; however:
  Package linux-image-3.7.0-7-generic is not configured yet.

dpkg: error processing linux-image-extra-3.7.0-7-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.7.0-7-generic; however:
  Package linux-image-3.7.0-7-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.7.0-7-generic; however:
  Package linux-image-extra-3.7.0-7-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.

dpkg: error processing linux-geneNo apport report written because the error message indicates it's a follow-up error from a previous failure.
                                         No apport report written because MaxReports has already been reached
         No apport report written because MaxReports has already been reached
                                                                             No apport report written because MaxReports has already been reached
                                             ric (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.8.5-030805-generic:
 linux-image-extra-3.8.5-030805-generic depends on linux-image-3.8.5-030805-generic; however:
  Package linux-image-3.8.5-030805-generic is not configured yet.

dpkg: error processing linux-image-extra-3.8.5-030805-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.7.0-7-generic
 linux-image-3.8.5-030805-generic
 linux-image-extra-3.7.0-7-generic
 linux-image-generic
 linux-generic
 linux-image-extra-3.8.5-030805-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help would be very much appreciated, using 12.10 64bit

---

### Post by d0006 on 2013-04-05
[http://ubuntuforums.org/showthread.php?t=1946145](http://ubuntuforums.org/showthread.php?t=1946145)

---

### Post by Bladeforce on 2013-04-19
I had a backup of my 12.04 install using clonezilla and went back to that where it was working fine

---


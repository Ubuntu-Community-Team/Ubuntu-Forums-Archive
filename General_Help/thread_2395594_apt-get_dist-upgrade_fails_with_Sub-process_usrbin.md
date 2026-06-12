---
title: "apt-get dist-upgrade fails with Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2018-07-04
forum: General Help
---

### Post by alfredballe on 2018-07-04
Brand new Ubuntu 18.04 LTS minimal fails when running:

apt-get update (works)
apt-get upgrade (works)
apt-get dist-upgrade (fails)

Setting up linux-image-4.15.0-24-generic (4.15.0-24.26) ...
Processing triggers for linux-image-4.15.0-24-generic (4.15.0-24.26) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-24-generic
I: The initramfs will attempt to resume from /dev/xvdb1
I: (UUID=e11ffda0-6b10-4924-b542-f3598dfd8820)
I: Set the RESUME variable to override this.
/etc/kernel/postinst.d/x-grub-legacy-ec2:
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
uuid not supported. update 'groot' in /boot/grub/menu.lst


groot must be grub root device (ie '(hd0)'). not 'LABEL=cloudimg-rootfs'


run-parts: /etc/kernel/postinst.d/x-grub-legacy-ec2 exited with return code 1
dpkg: error processing package linux-image-4.15.0-24-generic (--configure):
 installed linux-image-4.15.0-24-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-4.15.0-24-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by schaparro on 2018-07-16
Hi,


I think that you're trying to update an VSI deployed on a Cloud Provider:

Follow these steps and let me know if it works for you:

-Check where the root partition is with the following command:
**df /**
Under "Filesystem" you'll find the /dev/xxx disk.

-Get the disk from above step and replace it in /boot/grub/menu.lst in the groot section. Make a backup copy before edit  (And be sure to don't uncomment it):
[COLOR=#454545][FONT=&amp]## default grub root device[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]## e.g. groot=(hd0)[/FONT][/COLOR]
[COLOR=#454545][FONT=&amp]# groot=/your/diskhere

[/FONT][/COLOR]
## default grub root device
## e.g. groot=(hd0)
# groot=/dev/xvda2Save the file and reboot.

---

### Post by raulg on 2019-01-11
Hi, thank you very much worked for me.

---


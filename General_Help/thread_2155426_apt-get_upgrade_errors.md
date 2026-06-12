---
title: "apt-get upgrade errors"
date: 2013-06-18
forum: General Help
---

### Post by Headcase_Fargone on 2013-06-18
I'm currently running Ubuntu 10.04 and when I try to run apt-get upgrade it gets down to the depmod portion and I get:

> 
Setting up linux-image-3.0.0-32-generic (3.0.0-32.51) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled
(3.0.0-32.50 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(3.0.0-32.50 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-32-generic /boot/vmlinuz-
3.0.0-32-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-32-generic /bo
ot/vmlinuz-3.0.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-32-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-32-generic /boot/vmli
nuz-3.0.0-32-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-32-generic /bo
ot/vmlinuz-3.0.0-32-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-32-generic /boo
t/vmlinuz-3.0.0-32-generic
Generating grub.cfg ...
/etc/grub.d/00_header: 241: Syntax error: "fi" unexpected (expecting "}")
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0
-32-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-i
mage-3.0.0-32-generic-pae (3.0.0-32.51) ...
Running depmod.update-initramfs: deferring update (hook will be called
Not updating initrd symbolic links since we are being up
(3.0.0-32.50 was configured last, according to dpkg)
Not updating image symbolic links since we are being upd
(3.0.0-32.50 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-3
nuz-3.0.0-32-generic-pae
run-parts: executing /etc/kernel/postinst.d/initramfs-to
 /boot/vmlinuz-3.0.0-32-generic-pae
update-initramfs: Generating /boot/initrd.img-3.0.0-32-g
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0
vmlinuz-3.0.0-32-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notif
 /boot/vmlinuz-3.0.0-32-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-gr
/boot/vmlinuz-3.0.0-32-generic-pae
Generating grub.cfg ...
/etc/grub.d/00_header: 241: Syntax error: "fi" unexpecte
run-parts: /etc/kernel/postinst.d/zz-update-grub exited
Failed to process /etc/kernel/postinst.d at /var/lib/dpk
-32-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.0.0-32-generic-pae
 subprocess installed post-installation script returned
No apport report written because MaxReports is reached a


tered while processing:
 linux-image-3.0.0-32-generic
 linux-image-3.0.0-32-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm currently unable to use apt-get as a result.  Any pointers?

---

### Post by Headcase_Fargone on 2013-06-18
It looks like this might be an issue with 10.04 not being support anymore.  Can someone confirm?

---

### Post by Cheesemill on 2013-06-18
> **Headcase_Fargone said:**
> It looks like this might be an issue with 10.04 not being support anymore.  Can someone confirm?

That won't be a problem. Even though support for 10.04 on the desktop has ended the repositories are still online as the server packages are still being updated. The 10.04 repositories won't get taken off-line until server support ends in April 2015.

---

### Post by Impavidus on 2013-06-18
It would complain that it couldn't download the .debs, but the problem is installing. And indeed, I see kernel updates, which are packages also in the server edition, so still available. I also notice they are related to kernel 3.0. Ubuntu 10.04 used kernel 2.6.something, kernel 3.0 was used by 11.10, so that's a bit peculiar. Or did 10.04.one-of-the-last come with 3.0? 

But that may not be related to the problem at hand. Your problem seems to be a syntax error in /etc/grub.d/00_header. This file is included in the package grub-common. Reinstalling that package may help.

---

### Post by mörgæs on 2013-06-19
10.04 stayed (and stays) with kernel 2.6, so a 3.0-kernel is strange. 
Isn't it time for a clean install of 12.04 or 13.04?

---


---
title: "My ubuntu won't update"
date: 2013-03-26
forum: General Help
---

### Post by egr7 on 2013-03-26
Any help would be appreciated ... I am new to linux.

I think there is something wrong with my grub setting, or maybe it is something all together different, I not sure. When I modify /etc/default/grub and run sudo update-grub I get the error message:

i7@bruce:~$ sudo update-grub
: not foundrub-mkconfig: 5: /etc/default/grub:

This is my grub file:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


I get the following errors when running the software update:

installArchives() failed: Setting up linux-image-3.2.0-40-generic (3.2.0-40.63) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
/usr/sbin/grub-mkconfig: 5: /etc/default/grub: 
: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-40-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-40-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-40-generic; however:
  Package linux-image-3.2.0-40-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.40.48); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 linux-image-3.2.0-40-generic
 linux-image-generic
 linux-generic
Setting up linux-image-3.2.0-40-generic (3.2.0-40.63) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
/usr/sbin/grub-mkconfig: 5: /etc/default/grub: 
: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-40-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-40-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-40-generic; however:
  Package linux-image-3.2.0-40-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.40.48); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured


Thanks in advance for any help.

---

### Post by schragge on 2013-03-26
Try running *grub-mkconfig* manually:
```

sudo grub-mkconfig

```
It should output generated grub.cfg on the screen. Notice the line where the error occurs.

---

### Post by egr7 on 2013-03-26
When I run that command I get the message: 

i7@bruce:~$ sudo grub-mkconfig
[sudo] password for i7: 
: not foundrub-mkconfig: 5: /etc/default/grub:

---

### Post by schragge on 2013-03-26
Then try
```
sudo bash -x /usr/sbin/grub-mkconfig
```

---

### Post by egr7 on 2013-03-26
Thanks for the help. 

It didn't work so I just uninstalled grub then reinstalled. It seems to be working now and I am able to update.

---


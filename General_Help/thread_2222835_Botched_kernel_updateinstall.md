---
title: "Botched kernel update/install"
date: 2014-05-08
forum: General Help
---

### Post by r1ft2 on 2014-05-08
Hello, I am running v14.04 amd64 on my C2D laptop, dualbooting it with Windows.

I downloaded the 3.14.1 kernel from the [kernel-ppa/mainline location]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/") and tried to install it. The following is the output from gnome-terminal:

```
r1ft2@laptop:~/Downloads$ sudo dpkg -i *.deb
[sudo] password for r1ft2:
(Reading database ... 176053 files and directories currently installed.)
Preparing to unpack linux-headers-3.14.1-031401-generic_3.14.1-031401.201404141220_amd64.deb ...
Unpacking linux-headers-3.14.1-031401-generic (3.14.1-031401.201404141220) over (3.14.1-031401.201404141220) ...
Preparing to unpack linux-image-3.14.1-031401-generic_3.14.1-031401.201404141220_amd64.deb ...
Examining /etc/kernel/preinst.d/
Done.
Unpacking linux-image-3.14.1-031401-generic (3.14.1-031401.201404141220) over (3.14.1-031401.201404141220) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.14.1-031401-generic /boot/vmlinuz-3.14.1-031401-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.14.1-031401-generic /boot/vmlinuz-3.14.1-031401-generic
dpkg: dependency problems prevent configuration of linux-headers-3.14.1-031401-generic:
 linux-headers-3.14.1-031401-generic depends on linux-headers-3.14.1-031401; however:
  Package linux-headers-3.14.1-031401 is not installed.

dpkg: error processing package linux-headers-3.14.1-031401-generic (--install):
 dependency problems - leaving unconfigured
Setting up linux-image-3.14.1-031401-generic (3.14.1-031401.201404141220) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.14.1-031401-generic
) points to /boot/initrd.img-3.14.1-031401-generic
 (/boot/initrd.img-3.14.1-031401-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.14.1-031401-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.14.1-031401-generic
) points to /boot/vmlinuz-3.14.1-031401-generic
 (/boot/vmlinuz-3.14.1-031401-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.14.1-031401-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.14.1-031401-generic /boot/vmlinuz-3.14.1-031401-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.14.1-031401-generic /boot/vmlinuz-3.14.1-031401-generic
update-initramfs: Generating /boot/initrd.img-3.14.1-031401-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.14.1-031401-generic /boot/vmlinuz-3.14.1-031401-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.14.1-031401-generic /boot/vmlinuz-3.14.1-031401-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.14.1-031401-generic /boot/vmlinuz-3.14.1-031401-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.14.1-031401-generic.postinst line 1025.
dpkg: error processing package linux-image-3.14.1-031401-generic (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-headers-3.14.1-031401-generic
 linux-image-3.14.1-031401-generic


```

Please help!

---

### Post by ian-weisser on 2014-05-08
Well, the first problem seems pretty clear...

> **r1ft2 said:**
> 
dpkg: dependency problems prevent configuration of linux-headers-3.14.1-031401-generic:
 linux-headers-3.14.1-031401-generic depends on linux-headers-3.14.1-031401; however:
  [COLOR=#ff0000]Package linux-headers-3.14.1-031401 is not installed.[/COLOR]


---


---
title: "Once again kernel upgrade problems?"
date: 2014-01-03
forum: General Help
---

### Post by Psil0cybin on 2014-01-03
I ran the command 
> sudo apt-get dist-upgrade

got the following results, after I attempted to upgrade.
After reading online, it seems like I have been having this issue along with other people, alot of people suggest to jut remove the problematic kernel and have heard this before, but I feel like this is not proper security practice. 

Is there anything I can do in order to fix this driver? and get it working with the kernel that got upgraded?

```
Unpacking linux-image-3.2.0-58-generic-pae (from .../linux-image-3.2.0-58-generic-pae_3.2.0-58.88_i386.deb) ...Done.
Preparing to replace linux-generic-pae 3.2.0.57.68 (using .../linux-generic-pae_3.2.0.58.69_i386.deb) ...
Unpacking replacement linux-generic-pae ...
Preparing to replace linux-image-generic-pae 3.2.0.57.68 (using .../linux-image-generic-pae_3.2.0.58.69_i386.deb) ...
Unpacking replacement linux-image-generic-pae ...
Selecting previously unselected package linux-headers-3.2.0-58.
Unpacking linux-headers-3.2.0-58 (from .../linux-headers-3.2.0-58_3.2.0-58.88_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-58-generic-pae.
Unpacking linux-headers-3.2.0-58-generic-pae (from .../linux-headers-3.2.0-58-generic-pae_3.2.0-58.88_i386.deb) ...
Preparing to replace linux-headers-generic-pae 3.2.0.57.68 (using .../linux-headers-generic-pae_3.2.0.58.69_i386.deb) ...
Unpacking replacement linux-headers-generic-pae ...
Selecting previously unselected package linux-headers-3.2.0-58-generic.
Unpacking linux-headers-3.2.0-58-generic (from .../linux-headers-3.2.0-58-generic_3.2.0-58.88_i386.deb) ...
Preparing to replace linux-headers-generic 3.2.0.57.68 (using .../linux-headers-generic_3.2.0.58.69_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Setting up linux-image-3.2.0-58-generic-pae (3.2.0-58.88) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-58-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.12.0-031200-generic
Found initrd image: /boot/initrd.img-3.12.0-031200-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-57-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-57-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-56-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-56-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Setting up linux-image-generic-pae (3.2.0.58.69) ...
Setting up linux-headers-3.2.0-58 (3.2.0-58.88) ...
Setting up linux-headers-3.2.0-58-generic-pae (3.2.0-58.88) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-58-generic-pae /boot/vmlinuz-3.2.0-58-generic-pae
Setting up linux-headers-generic-pae (3.2.0.58.69) ...
Setting up linux-generic-pae (3.2.0.58.69) ...
Setting up linux-headers-3.2.0-58-generic (3.2.0-58.88) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-58-generic /boot/vmlinuz-3.2.0-58-generic
Error! Bad return status for module build on kernel: 3.2.0-58-generic (i686)
Consult /var/lib/dkms/cedarview-drm/20120717/build/make.log for more information.



```

Looking at make.log

I see

```
  GNU nano 2.2.6                File: /var/lib/dkms/cedarview-drm/20120717/build/make.log                                      

DKMS make.log for cedarview-drm-20120717 for kernel 3.2.0-58-generic (i686)
Fri Jan  3 01:07:23 EST 2014
Makefile:5: /boot/config-3.2.0-58-generic: No such file or directory
make: *** No rule to make target `/boot/config-3.2.0-58-generic'.  Stop.



```

What can I do to fix this, so I do not have to wait for another working kernel? 

I keep having this problem every other kernel,
eventually, I get an update that works...but If there is not one, I start to worry and panic..
I know the kernels I use are outdated! BUT!!!
I use an Acer Aspire Netbook, and it is the only way I can get linux working on here.
again,
thanks guys.

---


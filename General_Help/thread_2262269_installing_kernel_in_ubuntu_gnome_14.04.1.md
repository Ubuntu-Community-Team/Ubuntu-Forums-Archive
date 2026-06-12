---
title: "installing kernel in ubuntu gnome 14.04.1"
date: 2015-01-23
forum: General Help
---

### Post by Jessie_James_A._At on 2015-01-23
im installing linux kernel 3.18.3 in ubuntu gnome 14.04.1 but there was an error, please check




 ```
xsoultribex@xsoultribex-Aspire-V3-571G:~$ sudo dpkg -i linux-headers-3.18.3*.deb linux-image-3.18.3*.deb
 [sudo] password for xsoultribex: 
 (Reading database ... 308792 files and directories currently installed.)
 Preparing to unpack linux-headers-3.18.3-031803_3.18.3-031803.201501161810_all.deb ...
 Unpacking linux-headers-3.18.3-031803 (3.18.3-031803.201501161810) over (3.18.3-031803.201501161810) ...
 Preparing to unpack linux-headers-3.18.3-031803-generic_3.18.3-031803.201501161810_amd64.deb ...
 Unpacking linux-headers-3.18.3-031803-generic (3.18.3-031803.201501161810) over (3.18.3-031803.201501161810) ...
 Preparing to unpack linux-image-3.18.3-031803-generic_3.18.3-031803.201501161810_amd64.deb ...
 Done.
 Unpacking linux-image-3.18.3-031803-generic (3.18.3-031803.201501161810) over (3.18.3-031803.201501161810) ...
 Examining /etc/kernel/postrm.d .
 run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
 run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
 Setting up linux-headers-3.18.3-031803 (3.18.3-031803.201501161810) ...
 Setting up linux-headers-3.18.3-031803-generic (3.18.3-031803.201501161810) ...
 Examining /etc/kernel/header_postinst.d.
 run-parts: executing /etc/kernel/header_postinst.d/dkms 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
 ERROR (dkms apport): kernel package linux-headers-3.18.3-031803-generic is not supported
 Error! Bad return status for module build on kernel: 3.18.3-031803-generic (x86_64)
 Consult /var/lib/dkms/i915-3.16-3.13/1/build/make.log for more information.
 ERROR (dkms apport): kernel package linux-headers-3.18.3-031803-generic is not supported
 Error! Bad return status for module build on kernel: 3.18.3-031803-generic (x86_64)
 Consult /var/lib/dkms/i915-3.15-3.13/0.01/build/make.log for more information.
 Setting up linux-image-3.18.3-031803-generic (3.18.3-031803.201501161810) ...
 Running depmod.
 update-initramfs: deferring update (hook will be called later)
 Not updating initrd symbolic links since we are being updated/reinstalled 
 (3.18.3-031803.201501161810 was configured last, according to dpkg)
 Not updating image symbolic links since we are being updated/reinstalled 
 (3.18.3-031803.201501161810 was configured last, according to dpkg)
 Examining /etc/kernel/postinst.d.
 run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
 run-parts: executing /etc/kernel/postinst.d/dkms 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
 ERROR (dkms apport): kernel package linux-headers-3.18.3-031803-generic is not supported
 ERROR (dkms apport): kernel package linux-headers-3.18.3-031803-generic is not supported
 Error! Bad return status for module build on kernel: 3.18.3-031803-generic (x86_64)
 Consult /var/lib/dkms/i915-3.16-3.13/1/build/make.log for more information.
 Error! Bad return status for module build on kernel: 3.18.3-031803-generic (x86_64)
 Consult /var/lib/dkms/i915-3.15-3.13/0.01/build/make.log for more information.
 run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
 update-initramfs: Generating /boot/initrd.img-3.18.3-031803-generic
 run-parts: executing /etc/kernel/postinst.d/pm-utils 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
 run-parts: executing /etc/kernel/postinst.d/update-notifier 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
 run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.18.3-031803-generic /boot/vmlinuz-3.18.3-031803-generic
 Generating grub configuration file ...
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
 Found linux image: /boot/vmlinuz-3.18.3-031803-generic
 Found initrd image: /boot/initrd.img-3.18.3-031803-generic
 Found linux image: /boot/vmlinuz-3.13.0-44-generic
 Found initrd image: /boot/initrd.img-3.13.0-44-generic
 Found linux image: /boot/vmlinuz-3.13.0-43-generic
 Found initrd image: /boot/initrd.img-3.13.0-43-generic
 Found linux image: /boot/vmlinuz-3.13.0-35-generic
 Found initrd image: /boot/initrd.img-3.13.0-35-generic
 Adding boot menu entry for EFI firmware configuration
 done
 xsoultribex@xsoultribex-Aspire-V3-571G:~$
```

---

### Post by Doug S on 2015-01-24
That kernel installs fine for me. I would suggest to make sure your computer is running kernel 3.13.0-44 (the most recent one already installed), and purge the one you are trying to install, and start again.

---

### Post by Yellow Pasque on 2015-01-24
It looks like you have a module (i915) using dkms and not being compatible with the newer kernel. i915 is the intel gpu kernel module, and it's open source, so I have no idea why it's registered with dkms.

---


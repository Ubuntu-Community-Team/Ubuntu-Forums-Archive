---
title: "Missing /lib/modules when installing kernel"
date: 2018-03-05
forum: General Help
---

### Post by somas on 2018-03-05
Good day!
I'm a linux newbie and I have been trying to install a different kernel version to the one that came with my ubuntu distribution (16.04.4 LTS).
Configuring and building the kernel (4.15.7) both go smoothly but when I try to install it (sudo make install) I always get the following warnings and I wind up not being able to boot into the new kernel. I have searched the internet and tried the suggested solutions but still could not solve it.
This is what I get when I run sudo make install
> 
sh ./arch/x86/boot/install.sh 4.15.7 arch/x86/boot/bzImage \
    System.map "/boot"
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.15.7 /boot/vmlinuz-4.15.7
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.15.7 /boot/vmlinuz-4.15.7
update-initramfs: Generating /boot/initrd.img-4.15.7
WARNING: missing /lib/modules/4.15.7
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.15.7: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_VgOuon/lib/modules/4.15.7/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_VgOuon/lib/modules/4.15.7/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.15.7 /boot/vmlinuz-4.15.7
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.15.7 /boot/vmlinuz-4.15.7
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.15.7 /boot/vmlinuz-4.15.7
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.15.7 /boot/vmlinuz-4.15.7
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.7
Found initrd image: /boot/initrd.img-4.15.7
Found linux image: /boot/vmlinuz-4.15.7.old
Found initrd image: /boot/initrd.img-4.15.7
Found linux image: /boot/vmlinuz-4.9.75
Found linux image: /boot/vmlinuz-4.9.75.old
Found linux image: /boot/vmlinuz-4.4.0-116-generic
Found initrd image: /boot/initrd.img-4.4.0-116-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done

This is the output of uname -r
> 
4.4.0-31-generic


---


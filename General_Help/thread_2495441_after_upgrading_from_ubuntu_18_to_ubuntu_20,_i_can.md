---
title: "after upgrading from ubuntu 18 to ubuntu 20, i cannot install or upgrade further"
date: 2024-02-19
forum: General Help
---

### Post by zarosath on 2024-02-19
im trying to install a package or upgrade via apt-get

but this.

```
william@william-Nitro-AN515-55:~$ sudo apt install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  boot-sav boot-sav-extra glade2script glade2script-python3 pastebinit
Suggested packages:
  boot-info cryptsetup dmraid lvm2 mdadm os-uninstaller zfsutils-linux
  gir1.2-appindicator3-0.1
The following packages will be REMOVED:
  linux-image-5.4.0-149-generic
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra glade2script glade2script-python3
  pastebinit
0 upgraded, 6 newly installed, 1 to remove and 4 not upgraded.
9 not fully installed or removed.
Need to get 742 kB of archives.
After this operation, 10.4 MB disk space will be freed.
Get:1 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal/main amd64 glade2script-python3 all 3.2.4~ppa23 [35.9 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu focal/main amd64 pastebinit all 1.5.1-1 [14.2 kB]
Get:3 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal/main amd64 glade2script all 3.2.4~ppa23 [2,204 B]
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal/main amd64 boot-sav all 4ppa2075 [526 kB]
Get:5 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal/main amd64 boot-repair all 4ppa2075 [17.4 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu focal/main amd64 boot-sav-extra all 4ppa2075 [147 kB]
Fetched 742 kB in 3s (220 kB/s)          
(Reading database ... 343123 files and directories currently installed.)
Removing linux-image-5.4.0-149-generic (5.4.0-149.166) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-149-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-171-generic
Found initrd image: /boot/initrd.img-5.4.0-171-generic
Found linux image: /boot/vmlinuz-5.4.0-169-generic
Found initrd image: /boot/initrd.img-5.4.0-169-generic
Found linux image: /boot/vmlinuz-5.4.0-150-generic
Found initrd image: /boot/initrd.img-5.4.0-150-generic
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 323
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.4.0-149-generic (--remove):
 installed linux-image-5.4.0-149-generic package post-removal script subprocess 
returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.4.0-149-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i dont know that there are many users here willing to help with this, i dont remember what kind of hacks i did to the os but i may have done so to install g 8+ on ubuntu 18, i upgraded from ubuntu 18 to ubuntu 20 but now i cannot install any packages or upgrade further.

 can you provide any assistance?

---

### Post by zarosath on 2024-02-19
heres more output doing sudo dpkg --configure -a

> william@william-Nitro-AN515-55:~$  sudo dpkg --configure -a 
Setting up memtest86+ (5.01-3.1ubuntu2.1) ...
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-171-generic
Found initrd image: /boot/initrd.img-5.4.0-171-generic
Found linux image: /boot/vmlinuz-5.4.0-169-generic
Found initrd image: /boot/initrd.img-5.4.0-169-generic
Found linux image: /boot/vmlinuz-5.4.0-150-generic
Found initrd image: /boot/initrd.img-5.4.0-150-generic
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 323
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
dpkg: error processing package memtest86+ (--configure):
 installed memtest86+ package post-installation script subprocess returned error exit status 1
Setting up linux-image-5.4.0-169-generic (5.4.0-169.187) ...
Setting up grub-pc (2.04-1ubuntu26.17) ...
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-171-generic
Found initrd image: /boot/initrd.img-5.4.0-171-generic
Found linux image: /boot/vmlinuz-5.4.0-169-generic
Found initrd image: /boot/initrd.img-5.4.0-169-generic
Found linux image: /boot/vmlinuz-5.4.0-150-generic
Found initrd image: /boot/initrd.img-5.4.0-150-generic
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 323
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 1
Setting up friendly-recovery (0.2.41ubuntu0.20.04.1) ...
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-171-generic
Found initrd image: /boot/initrd.img-5.4.0-171-generic
Found linux image: /boot/vmlinuz-5.4.0-169-generic
Found initrd image: /boot/initrd.img-5.4.0-169-generic
Found linux image: /boot/vmlinuz-5.4.0-150-generic
Found initrd image: /boot/initrd.img-5.4.0-150-generic
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 323
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
dpkg: error processing package friendly-recovery (--configure):
 installed friendly-recovery package post-installation script subprocess returned error exit status 1
Setting up linux-image-5.4.0-171-generic (5.4.0-171.189) ...
Setting up linux-image-5.4.0-150-generic (5.4.0-150.167) ...
dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
 grub-efi-amd64-signed depends on grub-efi-amd64 | grub-pc; however:
  Package grub-efi-amd64 is not installed.
  Package grub-pc is not configured yet.

dpkg: error processing package grub-efi-amd64-signed (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed (>= 1.187.2~) | grub-efi-arm64-signed (>= 1.187.2~); however:
  Package grub-efi-amd64-signed is not configured yet.
  Package grub-efi-arm64-signed is not installed.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
Processing triggers for linux-image-5.4.0-169-generic (5.4.0-169.187) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-169-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-169-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-171-generic
Found initrd image: /boot/initrd.img-5.4.0-171-generic
Found linux image: /boot/vmlinuz-5.4.0-169-generic
Found initrd image: /boot/initrd.img-5.4.0-169-generic
Found linux image: /boot/vmlinuz-5.4.0-150-generic
Found initrd image: /boot/initrd.img-5.4.0-150-generic
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 323
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.4.0-169-generic (--configure):
 installed linux-image-5.4.0-169-generic package post-installation script subprocess returned error exit status 1
Processing triggers for linux-image-5.4.0-171-generic (5.4.0-171.189) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-171-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-171-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-171-generic
Found initrd image: /boot/initrd.img-5.4.0-171-generic
Found linux image: /boot/vmlinuz-5.4.0-169-generic
Found initrd image: /boot/initrd.img-5.4.0-169-generic
Found linux image: /boot/vmlinuz-5.4.0-150-generic
Found initrd image: /boot/initrd.img-5.4.0-150-generic
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 323
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.4.0-171-generic (--configure):
 installed linux-image-5.4.0-171-generic package post-installation script subprocess returned error exit status 1
Processing triggers for linux-image-5.4.0-150-generic (5.4.0-150.167) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-150-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-150-generic
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-171-generic
Found initrd image: /boot/initrd.img-5.4.0-171-generic
Found linux image: /boot/vmlinuz-5.4.0-169-generic
Found initrd image: /boot/initrd.img-5.4.0-169-generic
Found linux image: /boot/vmlinuz-5.4.0-150-generic
Found initrd image: /boot/initrd.img-5.4.0-150-generic
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 323
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.4.0-150-generic (--configure):
 installed linux-image-5.4.0-150-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 memtest86+
 grub-pc
 friendly-recovery
 grub-efi-amd64-signed
 shim-signed
 linux-image-5.4.0-169-generic
 linux-image-5.4.0-171-generic
 linux-image-5.4.0-150-generic


---


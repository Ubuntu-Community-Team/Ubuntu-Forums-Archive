---
title: "Boot Partition space 2 MB - freeing space /remove old kernel"
date: 2015-06-22
forum: General Help
---

### Post by Mohit_Jiindal on 2015-06-22
Hi!

  My boot partition seems to be running out of space - it often pop up a warning message every now and then it has only around 2 mb of space left with it. In order to resolve this error/problem , I tried the following:

1)** Run the command :** ```
uname -a
```

**Output of the command:** ```
3.19.0-22-generic #22-Ubuntu SMP Tue Jun 16 17:14:22 UTC 2015 i686 i686 i686 GNU/Linux
```

2) **Run the command : **```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d'
```

**Output of the command:** ```
linux-headers-3.19.0-16
linux-headers-3.19.0-16-generic
linux-headers-3.19.0-17
linux-headers-3.19.0-17-generic
linux-headers-3.19.0-18
linux-headers-3.19.0-18-generic
linux-headers-3.19.0-20
linux-headers-3.19.0-20-generic
linux-headers-3.19.0-21
linux-headers-3.19.0-21-generic
linux-image-3.13.0-51-generic
linux-image-3.19.0-16-generic
linux-image-3.19.0-17-generic
linux-image-3.19.0-18-generic
linux-image-3.19.0-20-generic
linux-image-3.19.0-21-generic
linux-image-extra-3.13.0-51-generic
linux-image-extra-3.19.0-16-generic
linux-image-extra-3.19.0-17-generic
linux-image-extra-3.19.0-18-generic
linux-image-extra-3.19.0-20-generic
```

3) **Run the command :**```
sudo apt-get -y purge linux-headers-3.19.0-16
```

**Output of the command:**```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.19.0-16* linux-headers-3.19.0-16-generic*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 79.8 MB disk space will be freed.
(Reading database ... 371678 files and directories currently installed.)
Removing linux-headers-3.19.0-16-generic (3.19.0-16.16) ...
Removing linux-headers-3.19.0-16 (3.19.0-16.16) ...
Setting up linux-image-extra-3.19.0-22-generic (3.19.0-22.22) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-22-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.19.0-22-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.19.0-22-generic; however:
  Package linux-image-extra-3.19.0-22-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.19.0.22.21); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-extra-3.19.0-21-generic (3.19.0-21.21) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                    run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-21-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.19.0-21-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-21-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.19.0-22-generic
 linux-image-generic
 linux-generic
 linux-image-extra-3.19.0-21-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

4) **Run the command**: ```
fdisk -l /dev/sda
```
**Output of the command :** ```
fdisk: cannot open /dev/sda: Permission denied
```

Please help resolve this issue. Thanks

---

### Post by Bucky Ball on 2015-06-22
The easiest way I've found is using Synaptic Package Manager. Search for 'linux image'> click the 'Installed' column twice> mark for complete removal the kernels you don't want> hit 'Apply'. 

```
sudo update-grub
```

Reboot.

---

### Post by Mohit_Jiindal on 2015-06-22
> **Bucky Ball said:**
> The easiest way I've found is using Synaptic Package Manager. Search for 'linux image'> click the 'Installed' column twice> mark for complete removal the kernels you don't want> hit 'Apply'. 

```
sudo update-grub
```

Reboot.

HI Bucky

  Thank you so very much for your assistance. Well I visited the Synaptic and searched for the 'linux image' as advised but I couldn't proceed with the selection and removal of the stuff from there because I am afraid that i might remove something which is warranted and thus mess up everything. I tried copying the results so as to paster here as plain text but couldn't. Can you please help me further on this?

Thanks again

---

### Post by Mohit_Jiindal on 2015-06-22
Ok after reading elsewhere this is what I did:

1) **Run the command : **```
df
```

**Output of the command :** ```

Filesystem                  1K-blocks      Used Available Use% Mounted on
udev                           950068         0    950068   0% /dev
tmpfs                          192196      9396    182800   5% /run
/dev/mapper/ubuntu--vg-root 305348864 187808328 102006664  65% /
tmpfs                          960964       220    960744   1% /dev/shm
tmpfs                            5120         4      5116   1% /run/lock
tmpfs                          960964         0    960964   0% /sys/fs/cgroup
/dev/sda1                      240972    226321      2210 100% /boot
tmpfs                          192196        60    192136   1% /run/user/1000
```

and then in order to resolve the problem that I had posted above, I

2) **Run the command:** ```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

**Output of the command:** ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.19.0-17* linux-headers-3.19.0-17-generic* linux-headers-3.19.0-18* linux-headers-3.19.0-18-generic* linux-headers-3.19.0-20*
  linux-headers-3.19.0-20-generic* linux-headers-3.19.0-21* linux-headers-3.19.0-21-generic* linux-image-3.13.0-51-generic*
  linux-image-3.19.0-16-generic* linux-image-3.19.0-17-generic* linux-image-3.19.0-18-generic* linux-image-3.19.0-20-generic*
  linux-image-3.19.0-21-generic* linux-image-extra-3.13.0-51-generic* linux-image-extra-3.19.0-16-generic*
  linux-image-extra-3.19.0-17-generic* linux-image-extra-3.19.0-18-generic* linux-image-extra-3.19.0-20-generic*
  linux-image-extra-3.19.0-21-generic*
0 upgraded, 0 newly installed, 20 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 1,246 MB disk space will be freed.
(Reading database ... 346626 files and directories currently installed.)
Removing linux-image-extra-3.19.0-21-generic (3.19.0-21.21) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-17-generic
Found initrd image: /boot/initrd.img-3.19.0-17-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.19.0-21-generic (3.19.0-21.21) ...
Removing linux-headers-3.19.0-17-generic (3.19.0-17.17) ...
Removing linux-headers-3.19.0-17 (3.19.0-17.17) ...
Removing linux-headers-3.19.0-18-generic (3.19.0-18.18) ...
Removing linux-headers-3.19.0-18 (3.19.0-18.18) ...
Removing linux-headers-3.19.0-20-generic (3.19.0-20.20) ...
Removing linux-headers-3.19.0-20 (3.19.0-20.20) ...
Removing linux-headers-3.19.0-21-generic (3.19.0-21.21) ...
Removing linux-headers-3.19.0-21 (3.19.0-21.21) ...
Removing linux-image-extra-3.13.0-51-generic (3.13.0-51.84) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-51-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-17-generic
Found initrd image: /boot/initrd.img-3.19.0-17-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.13.0-51-generic (3.13.0-51.84) ...
Removing linux-image-3.13.0-51-generic (3.13.0-51.84) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-17-generic
Found initrd image: /boot/initrd.img-3.19.0-17-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.13.0-51-generic (3.13.0-51.84) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-51-generic /boot/vmlinuz-3.13.0-51-generic
Removing linux-image-extra-3.19.0-16-generic (3.19.0-16.16) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-17-generic
Found initrd image: /boot/initrd.img-3.19.0-17-generic
Found linux image: /boot/vmlinuz-3.19.0-16-generic
Found initrd image: /boot/initrd.img-3.19.0-16-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.19.0-16-generic (3.19.0-16.16) ...
Removing linux-image-3.19.0-16-generic (3.19.0-16.16) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-16-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-17-generic
Found initrd image: /boot/initrd.img-3.19.0-17-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.19.0-16-generic (3.19.0-16.16) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-16-generic /boot/vmlinuz-3.19.0-16-generic
Removing linux-image-extra-3.19.0-17-generic (3.19.0-17.17) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-17-generic /boot/vmlinuz-3.19.0-17-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-17-generic /boot/vmlinuz-3.19.0-17-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-17-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-17-generic /boot/vmlinuz-3.19.0-17-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-17-generic /boot/vmlinuz-3.19.0-17-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-17-generic /boot/vmlinuz-3.19.0-17-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-17-generic /boot/vmlinuz-3.19.0-17-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found linux image: /boot/vmlinuz-3.19.0-17-generic
Found initrd image: /boot/initrd.img-3.19.0-17-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.19.0-17-generic (3.19.0-17.17) ...
Removing linux-image-3.19.0-17-generic (3.19.0-17.17) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-17-generic /boot/vmlinuz-3.19.0-17-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-17-generic /boot/vmlinuz-3.19.0-17-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.19.0-17-generic (3.19.0-17.17) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-17-generic /boot/vmlinuz-3.19.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-17-generic /boot/vmlinuz-3.19.0-17-generic
Removing linux-image-extra-3.19.0-18-generic (3.19.0-18.18) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-18-generic
Found initrd image: /boot/initrd.img-3.19.0-18-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.19.0-18-generic (3.19.0-18.18) ...
Removing linux-image-3.19.0-18-generic (3.19.0-18.18) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-18-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.19.0-18-generic (3.19.0-18.18) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-18-generic /boot/vmlinuz-3.19.0-18-generic
Removing linux-image-extra-3.19.0-20-generic (3.19.0-20.20) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-20-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.19.0-20-generic (3.19.0-20.20) ...
Removing linux-image-3.19.0-20-generic (3.19.0-20.20) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-21-generic
Found initrd image: /boot/initrd.img-3.19.0-21-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.19.0-20-generic (3.19.0-20.20) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-20-generic /boot/vmlinuz-3.19.0-20-generic
Removing linux-image-3.19.0-21-generic (3.19.0-21.21) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.19.0-21-generic (3.19.0-21.21) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic
Setting up linux-image-extra-3.19.0-22-generic (3.19.0-22.22) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-22-generic /boot/vmlinuz-3.19.0-22-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic (3.19.0.22.21) ...
Setting up linux-generic (3.19.0.22.21) ...

```

**For Re check **

3) **Run the command:**```
df
``` again

Ouput of the command:```
Filesystem                  1K-blocks      Used Available Use% Mounted on
udev                           950068         0    950068   0% /dev
tmpfs                          192196      9412    182784   5% /run
/dev/mapper/ubuntu--vg-root 305348864 186418096 103396896  65% /
tmpfs                          960964       220    960744   1% /dev/shm
tmpfs                            5120         4      5116   1% /run/lock
tmpfs                          960964         0    960964   0% /sys/fs/cgroup
/dev/sda1                      240972     40727    187804  18% /boot
tmpfs                          192196        60    192136   1% /run/user/1000

```

So in my opinion the problem seems to be resolved as now boot partition seems to be showing up some more free space. As advised , lastly I:

4) **Run the command:**```
sudo update-grub
```
and got the following as the 
[B]
output of the command:[/B] ```
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done

```

---

### Post by Mohit_Jiindal on 2015-06-22
I would appreciate if someone could please let me know if I need to anything else/more here? Thanks

---

### Post by Bucky Ball on 2015-06-22
Doesn't look like it. You have one kernel installed. I personally leave the current kernel and the one before in case the current breaks.

In Synaptic, yes, you could have gone ahead and removed the images, you were just reluctant to. If you don't remove the kernel you are using, then you're fine. Removing a Linux image doesn't remove anything else, just the image. The kernel alone doesn't have any default apps. It's just a kernel. 

Please mark the thread as solved by following instructions in my second signature link. Thanks.

---

### Post by Mohit_Jiindal on 2015-06-22
> **Bucky Ball said:**
> Please mark the thread as solved by following instructions in my second signature link. Thanks.

Thank you so very much for all your help. I am really grateful. As advised this thread is being marked as 'SOLVED'.

---


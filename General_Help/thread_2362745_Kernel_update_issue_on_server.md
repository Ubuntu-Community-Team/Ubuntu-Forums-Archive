---
title: "Kernel update issue on server"
date: 2017-06-01
forum: General Help
---

### Post by bongoboy on 2017-06-01
[center]*****
*split off from [https://ubuntuforums.org/showthread.php?t=2357099](https://ubuntuforums.org/showthread.php?t=2357099) to its own thread*
*****[/center]

Hey there, I've got the exact same problem. As this system is a server, managed by 5 people, I'm not sure who did something wrong - maybe I've done it in a dark sleepless night :-k

Now I need to fix it and can't get any further for the last two days. Could somebody please help me? I'd wish to learn. :)

Current state:
```

# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-4.4.0-66-generic linux-image-extra-4.4.0-66-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 219 MB disk space will be freed.
Do you want to continue? [Y/n]
(Reading database ... 130589 files and directories currently installed.)
Removing linux-image-extra-4.4.0-66-generic (4.4.0-66.87) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-66-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic
WARNING: missing /lib/modules/4.4.0-66-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-66-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_fma86B/lib/modules/4.4.0-66-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_fma86B/lib/modules/4.4.0-66-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
/usr/sbin/grub-probe: error: failed to get canonical path of `/dev/mapper/cl--1--b--prod--vg-root'.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-66-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-66-generic (4.4.0-66.87) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-66-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
/usr/sbin/grub-probe: error: failed to get canonical path of `/dev/mapper/cl--1--b--prod--vg-root'.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-66-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-66-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.4.0-66-generic
 linux-image-4.4.0-66-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Version: Ubuntu 16.04
uname -r: 4.4.0-64-generic

```
# dpkg -l |grep linux-image-.*-generic
rc  linux-image-3.19.0-47-generic       3.19.0-47.53~14.04.1                       amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-51-generic       3.19.0-51.58~14.04.1                       amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-59-generic       3.19.0-59.66~14.04.1                       amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-22-generic        4.4.0-22.40                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-59-generic        4.4.0-59.80                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-64-generic        4.4.0-64.85                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-66-generic        4.4.0-66.87                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-77-generic        4.4.0-77.98                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-78-generic        4.4.0-78.99                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-47-generic 3.19.0-47.53~14.04.1                       amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-51-generic 3.19.0-51.58~14.04.1                       amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-59-generic 3.19.0-59.66~14.04.1                       amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-22-generic  4.4.0-22.40                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-59-generic  4.4.0-59.80                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-64-generic  4.4.0-64.85                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-66-generic  4.4.0-66.87                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-77-generic  4.4.0-77.98                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-78-generic  4.4.0-78.99                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
```

Got it. Had to fix this issue and now everything works fine again. Thanks :D

```

/usr/sbin/grub-probe: error: failed to get canonical path of `/dev/mapper/cl--1--b--prod--vg-root'.

```

---


---
title: "apt kernel removal failure"
date: 2015-08-13
forum: General Help
---

### Post by mattdawolf on 2015-08-13
Everytime I try to install/remove software now, apt insists on removing these outdated kernels. 

Any idea how to fix this? 

```
(synaptic:21067): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 410291 files and directories currently installed.)
Removing linux-image-extra-3.13.0-24-generic (3.13.0-24.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-runlilo 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
/usr/sbin/grub-mkconfig: 36: /etc/default/grub: color: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.13.0-24-generic.postrm line 328.
dpkg: error processing package linux-image-extra-3.13.0-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-24-generic (3.13.0-24.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-runlilo 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
/usr/sbin/grub-mkconfig: 36: /etc/default/grub: color: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-24-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.13.0-57-generic (3.13.0-57.95) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-57-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-57-generic
grep: /boot/config-3.13.0-57-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_BN0eXf/lib/modules/3.13.0-57-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_BN0eXf/lib/modules/3.13.0-57-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
/usr/sbin/grub-mkconfig: 36: /etc/default/grub: color: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.13.0-57-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-57-generic (3.13.0-57.95) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-57-generic
run-parts: executing /etc/kernel/postrm.d/zz-runlilo 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
/usr/sbin/grub-mkconfig: 36: /etc/default/grub: color: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-57-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-57-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-3.13.0-58-generic (3.13.0-58.97) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-58-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-58-generic
grep: /boot/config-3.13.0-58-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_mxL5Xt/lib/modules/3.13.0-58-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_mxL5Xt/lib/modules/3.13.0-58-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
/usr/sbin/grub-mkconfig: 36: /etc/default/grub: color: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.13.0-58-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.13.0-58-generic (3.13.0-58.97) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-58-generic
run-parts: executing /etc/kernel/postrm.d/zz-runlilo 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
/usr/sbin/grub-mkconfig: 36: /etc/default/grub: color: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-58-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-58-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-3.13.0-59-generic (3.13.0-59.98) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-59-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-59-generic
grep: /boot/config-3.13.0-59-generic: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_bqhShO/lib/modules/3.13.0-59-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_bqhShO/lib/modules/3.13.0-59-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
/usr/sbin/grub-mkconfig: 36: /etc/default/grub: color: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.13.0-59-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.13.0-59-generic (3.13.0-59.98) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-59-generic
run-parts: executing /etc/kernel/postrm.d/zz-runlilo 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
/usr/sbin/grub-mkconfig: 36: /etc/default/grub: color: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-59-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-59-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing flashplugin-installer (11.2.202.468ubuntu0.14.04.1) ...
Processing triggers for update-notifier-common (0.154.1ubuntu1) ...
Errors were encountered while processing:
 linux-image-extra-3.13.0-24-generic
 linux-image-3.13.0-24-generic
 linux-image-extra-3.13.0-57-generic
 linux-image-3.13.0-57-generic
 linux-image-extra-3.13.0-58-generic
 linux-image-3.13.0-58-generic
 linux-image-extra-3.13.0-59-generic
 linux-image-3.13.0-59-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

---

### Post by v3.xx on 2015-08-13
Have you tried to remove kernels with the autoremove command?
```
sudo apt-get autoremove
```

Also have a look here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=%2Fboot+full&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=%2Fboot+full&sa=Search&cof=FORID:9)

---


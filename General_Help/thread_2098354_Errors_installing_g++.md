---
title: "Errors installing g++"
date: 2012-12-26
forum: General Help
---

### Post by LyTningB0LT on 2012-12-26
I was trying to install g++ on ubuntu (running off a live usb), so I used sudo apt-get install g++ in the terminal, but got the following output:

> Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main libstdc++6-4.6-dev i386 4.6.3-1ubuntu5 [1,643 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main g++-4.6 i386 4.6.3-1ubuntu5 [6,745 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main g++ i386 4:4.6.3-1ubuntu5 [1,444 B]
Fetched 8,389 kB in 1min 8s (123 kB/s)                                         
Selecting previously unselected package libstdc++6-4.6-dev.
(Reading database ... 176476 files and directories currently installed.)
Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++-4.6.
Unpacking g++-4.6 (from .../g++-4.6_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.6.3-1ubuntu5_i386.deb) ...
Processing triggers for man-db ...
Setting up linux-image-3.2.0-35-generic-pae (3.2.0-35.55) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic-pae
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-35-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-35-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-35-generic-pae; however:
  Package linux-image-3.2.0-35-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.35.40); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Errors were encountered while processing:
 linux-image-3.2.0-35-generic-pae
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)As you can see it contains several errors/warnings.  I'm new to ubuntu so could someone please explain what's causing them and how to fix them? Thanks in advance!

EDIT: Oh and I'm using 12.04, if that makes a difference

---


---
title: "&quot;[Solved]&quot;- Unable to install any Package due Kernel issue"
date: 2015-02-05
forum: General Help
---

### Post by shankar41592213 on 2015-02-05
I'm unable to install any package & i'm not sure how to get around the problem. I'm noticing following error
```
root@croods-GT60:/boot# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.13.0-45-generic linux-image-extra-3.13.0-45-generic
0 upgraded, 0 newly installed, 2 to remove and 4 not upgraded.
2 not fully installed or removed.
After this operation, 194 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 297499 files and directories currently installed.)
Removing linux-image-extra-3.13.0-45-generic (3.13.0-45.74) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-45-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-45-generic
grep: /boot/config-3.13.0-45-generic: No such file or directory
WARNING: missing /lib/modules/3.13.0-45-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-45-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_Zf2Xbi/lib/modules/3.13.0-45-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_Zf2Xbi/lib/modules/3.13.0-45-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: i915.semaphores=1: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.13.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.13.0-45-generic (3.13.0-45.74) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-45-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-45-generic /boot/vmlinuz-3.13.0-45-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: i915.semaphores=1: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.13.0-45-generic.postrm line 328.
dpkg: error processing package linux-image-3.13.0-45-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-45-generic
 linux-image-3.13.0-45-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I went through numerous help line forums & tried removing the newly installed Kernel in vain. I'm getting the same error when i run any of the following command 

```
apt-get purge -y linux-headers-3.13.0-45 linux-headers-3.13.0-45-generic linux-image-3.13.0-45-generic linux-image-extra-3.13.0-45-generic linux-signed-image-3.13.0-45-generic
sudo apt-get autoremove && apt-get autoclean
apt-get update && apt-get dist-upgrade
apt-get install -f linux-image-3.13.0-45-generic

```

Kindly advise how I can re-install or Purge the kernel

---

### Post by ian-weisser on 2015-02-05
It's not a kernel issue.
It's not a package manager issue.
It is a missing files and directory issue.

This happens most often when an admin 'helps' by manually deleting directories and files that were installed by packages...and that the package manager expects to find in place during an uninstall.


The easiest way easy way is to simply reinstall the package (thereby restoring the missing files), then uninstall it. **sudo apt-get install --reinstall linux-image-extra-3.13.0-45-generic**

A slightly more manual way is to create empty (dummy) files/directories in  those expected locations for the package manager to slavishly remove.

If those don't work, a more dangerous way is to force dpkg to 'forget' about the damaged package...leaving all the files in place for you to manually remove. Backup your system first.


Er, looks like 3.0.13.45 is the current kernel on Trusty. Any particular reason why you want to delete it? Your system will promptly start pestering you to reinstall it....

---

### Post by shankar41592213 on 2015-02-05
Ok.. I finally solved this issue with really CRUDE way which no way is recommended for Noobs.. I would recommend first try recourse suggest by [**[COLOR=#000000]ian-weisser[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841707") from previous post followed by steps suggested here -> [http://ubuntuforums.org/showthread.php?t=2258756&page=3](http://ubuntuforums.org/showthread.php?t=2258756&page=3) and [http://askubuntu.com/questions/419095/unable-to-remove-old-kernels](http://askubuntu.com/questions/419095/unable-to-remove-old-kernels)

Make sure you back-up all your data before you attempt. Here is what I did to resolve the issue

the problem of a broken package still exist the solution is to edit the **dpkg status** file manually

  > `sudo gedit /var/lib/dpkg/status`    (you can use vi or gedit instead of nano)

 
****Observe Caution while removing entry**************

Locate the corrupt package (in my case it was paragraph with entry ' 3.13.0-45'), and remove the whole block of information about it and save the file. Basically these are about 10-12 line entry which should look like this. I noticed about 3-4 such entry which I had to remove

> Package: linux-libc-dev
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 3763
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: same
Source: linux
Version: 3.13.0-45.74
Replaces: dvb-dev (<< 1.0.1-6), libc6-dev (<< 2.3.2.ds1-6), libc6.1-dev (<< 2.3.2.ds1-6), libdrm-dev, linux-kernel-headers
Provides: linux-kernel-headers
Conflicts: amd64-libs-dev (<= 1.1), dvb-dev (<< 1.0.1-6), libc6-dev (<< 2.3.2.ds1-6), libc6.1-dev (<< 2.3.2.ds1-6), linux-kernel-headers
Description: Linux Kernel Headers for development
 This package provides headers from the Linux kernel.  These headers
 are used by the installed headers for GNU glibc and other system
 libraries. They are NOT meant to be used to build third-party modules for
 your kernel. Use linux-headers-* packages for that.

After I had to run > apt-get -f install to fix some broken package 'linux-libc-dev'. This basically fixed the issue for me

******I also manually cleaned up the file dropped by the Kernel package. Again NOT RECOMMENDED but worked for me***

> rm -rf /lib/modules/3.13.0-45-generic
rm -rf /boot/*3.13.0-45*

Voila! the package manager is UP & RUNNING

---

### Post by ian-weisser on 2015-02-05
dpkg has a --force-remove-reinstreq command that will do all that mucking about in the status file for you.
Thanks for mentioning that it's the *last* thing you should try. I call it the nuclear option, and I try all my other hammers and spanners and tricks first. The apt database is unforgiving of typos..

---


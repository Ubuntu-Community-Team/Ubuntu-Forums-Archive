---
title: "Can't install/remove/update packages errors on row."
date: 2017-03-29
forum: General Help
---

### Post by sdelta on 2017-03-29
I have been trying to rectify this issue since a while now, but i cant seem to find a solution to this issue. Not even sure what the issue is.
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-4.4.0-64-generic linux-image-extra-4.4.0-66-generic
0 upgraded, 0 newly installed, 2 to remove and 66 not upgraded.
4 not fully installed or removed.
After this operation, 226 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 232993 files and directories currently installed.)
Removing linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-64-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Error! echo
Your kernel headers for kernel 4.4.0-64-generic cannot be found at
/lib/modules/4.4.0-64-generic/build or /lib/modules/4.4.0-64-generic/source.
Error! echo
Your kernel headers for kernel 4.4.0-64-generic cannot be found at
/lib/modules/4.4.0-64-generic/build or /lib/modules/4.4.0-64-generic/source.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
depmod: WARNING: could not open /lib/modules/4.4.0-64-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/4.4.0-64-generic/modules.builtin: No such file or directory
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-64-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-66-generic (4.4.0-66.87) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-66-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
Error! echo
Your kernel headers for kernel 4.4.0-66-generic cannot be found at
/lib/modules/4.4.0-66-generic/build or /lib/modules/4.4.0-66-generic/source.
Error! echo
Your kernel headers for kernel 4.4.0-66-generic cannot be found at
/lib/modules/4.4.0-66-generic/build or /lib/modules/4.4.0-66-generic/source.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-66-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-66-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.4.0-64-generic
 linux-image-extra-4.4.0-66-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-4.4.0-64-generic linux-image-extra-4.4.0-66-generic
0 upgraded, 0 newly installed, 2 to remove and 66 not upgraded.
4 not fully installed or removed.
After this operation, 226 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 232993 files and directories currently installed.)
Removing linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-64-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
Error! echo
Your kernel headers for kernel 4.4.0-64-generic cannot be found at
/lib/modules/4.4.0-64-generic/build or /lib/modules/4.4.0-64-generic/source.
Error! echo
Your kernel headers for kernel 4.4.0-64-generic cannot be found at
/lib/modules/4.4.0-64-generic/build or /lib/modules/4.4.0-64-generic/source.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-64-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-66-generic (4.4.0-66.87) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-66-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
Error! echo
Your kernel headers for kernel 4.4.0-66-generic cannot be found at
/lib/modules/4.4.0-66-generic/build or /lib/modules/4.4.0-66-generic/source.
Error! echo
Your kernel headers for kernel 4.4.0-66-generic cannot be found at
/lib/modules/4.4.0-66-generic/build or /lib/modules/4.4.0-66-generic/source.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-66-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-66-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.4.0-64-generic
 linux-image-extra-4.4.0-66-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

```
sudo dpkg --configure -a
Setting up initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-firmware (1.157.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-59-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-59-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-firmware
 initramfs-tools


```

```
sudo dpkg --configure -a
Setting up initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-firmware (1.157.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-59-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-59-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-firmware
 initramfs-tools


```

A solution to fix this error flows, please any one who can help with this.

---

### Post by ian-weisser on 2017-03-29
Did you perhaps manually delete kernel image and header files? Possibly to free up space? If so, stop. Break that habit.

Reinstall kernel 4.4.0-64 so it can be removed properly.
Reinstall kernel headers for 4.4.0-64-generic, so they can also be removed properly.

That's a start....

---

### Post by sdelta on 2017-04-01
> **ian-weisser said:**
> Did you perhaps manually delete kernel image and header files? Possibly to free up space? If so, stop. Break that habit.

Reinstall kernel 4.4.0-64 so it can be removed properly.
Reinstall kernel headers for 4.4.0-64-generic, so they can also be removed properly.

That's a start....

I'm a new user and i don't even know where the kernel image or the header files are. And why would i even have to fiddle with those which can halt the progress of the system entirelly. I cant install packages nor uninstall them. can't even update any thing now. I cant get to install the given kernal packages as well not from the terminal nor from the kernel update manager.

---

### Post by RobGoss on 2017-04-01
> I'm a new user and i don't even know where the kernel image or the header files are. And why would i even have to fiddle with those which can halt the progress of the system entirelly  

You would be surprise what people not knowingly do to systems while learning the fundamentals of Linux, no pun intended we all do it :)

I believe the question was asked because looking at the output you posted it looks like the kernel image was removed

---

### Post by ian-weisser on 2017-04-01
> **sdelta said:**
> I'm a new user and i don't even know where the kernel image or the header files are. 

Your system looks like it can be fixed, but it won't be fast nor simple. So you have a decision to make:

Question: Do you wish to learn? We can spend a few days teaching you the details of the problem, and show you -step by step- how to understand the problem and fix it. At the end, you will have a much better grasp of your system.

Alternately, do you NOT want to spend some time learning, but simply want your system to work again? If the latter, then back up your data and reinstall.

---


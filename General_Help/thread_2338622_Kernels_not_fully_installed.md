---
title: "Kernels not fully installed"
date: 2016-09-30
forum: General Help
---

### Post by Jasper_Haller on 2016-09-30
Dear all,

when trying to upgrade to kernel version 4.4.0-38, and I receive a lot of error messages. Here they are:

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up initramfs-tools (0.122ubuntu8.1) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-4.4.0-34-generic (4.4.0-34.53) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-4.4.0-38-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-34-generic
cp: cannot stat '/sbin/rmmod': No such file or directory
E: /usr/share/initramfs-tools/hooks/kmod failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-34-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-34-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-34-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-4.4.0-38-generic (4.4.0-38.57) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-4.4.0-34-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-38-generic /boot/vmlinuz-4.4.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-38-generic
cp: cannot stat '/sbin/rmmod': No such file or directory
E: /usr/share/initramfs-tools/hooks/kmod failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-38-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-38-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-38-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-34-generic:
 linux-image-extra-4.4.0-34-generic depends on linux-image-4.4.0-34-generic; however:
  Package linux-image-4.4.0-34-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-34-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-38-generic:
 linux-image-extra-4.4.0-38-generic depends on linux-image-4.4.0-38-generic; however:
  Package linux-image-4.4.0-38-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-38-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                                Processing triggers for initramfs-tools (0.122ubuntu8.1) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
cp: cannot stat '/sbin/rmmod': No such file or directory
E: /usr/share/initramfs-tools/hooks/kmod failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-36-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-4.4.0-34-generic
 linux-image-4.4.0-38-generic
 linux-image-extra-4.4.0-34-generic
 linux-image-extra-4.4.0-38-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I now also can no longer boot into the current kernel, and I have to select an older kernel (4.4.0-36) in GRUB to boot successfully.

I am sure someone has had a similar problem before, but I am finding it hard to google for it because of the many, many error messages, and I don't know which ones are the key ones. If anyone could give me some pointers where to look, I would much appreciate it.

---

### Post by ajgreeny on 2016-09-30
I wonder if you have a separate /boot partition which has filled up; do you use encryption or LVM partitions?

Show us the terminal output of command ```
df -h
```
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by ian-weisser on 2016-09-30
> **Jasper_Haller said:**
> cp: cannot stat '/sbin/rmmod': No such file or directory
E: /usr/share/initramfs-tools/hooks/kmod failed with return 1.

Does the file /sbin/rmmod exist?
If it exists as a link, does the target exist?

For example, here is mine:
```
$ ls -l /sbin/rmmod
lrwxrwxrwx 1 root root 9 Mar 13  2016 /sbin/rmmod -> /bin/kmod

$ ls -l /bin/kmod
-rwxr-xr-x 1 root root 154696 Mar 13  2016 /bin/kmod
```

If either file is missing, simply reinstall the 'kmod' package (using dpkg, since apt is broken)

---

### Post by Jasper_Haller on 2016-09-30
> **ian-weisser said:**
> Does the file /sbin/rmmod exist?

It did not exist; that was the problem. I followed your advice and all is running normally now. Thank you.

---

### Post by ajgreeny on 2016-09-30
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---


---
title: "broken apt"
date: 2018-02-05
forum: General Help
---

### Post by kpierce on 2018-02-05
when I try to install packages I get the following error: 

The following packages have unmet dependencies:
 linux-image-extra-4.10.0-40-generic : Depends: linux-image-4.10.0-40-generic but it is not going to be installed
 linux-image-generic-hwe-16.04 : Depends: linux-image-4.10.0-40-generic but it is not going to be installed
 x2goclient : Depends: nxproxy but it is not going to be installed
              Recommends: openssh-server
              Recommends: rdesktop but it is not going to be installed or
                          freerdp-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


When I looked at installed kernels, I saw that 4.10.0-38 has status "iF". The active kernel is 4.10.0-37. I suppose I need to remove 38 and reinstall: can anyone help me do this? I'm not super confident I'll manage it without killing my machine

---

### Post by Frogs Hair on 2018-02-05
Hello and Welcome

Did you try the suggestion in the output ? If not post the entire output. 

```
sudo apt-get -f install
```

---

### Post by kpierce on 2018-02-06
Hi, thanks for the welcome! 

Running your suggestion I get: 

> 

kpierce@dw7mhal3:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.10.0-35 linux-headers-4.10.0-35-generic
  linux-headers-4.10.0-40 linux-headers-4.10.0-40-generic
  linux-headers-4.8.0-36 linux-headers-4.8.0-36-generic
  linux-image-4.10.0-35-generic linux-image-4.10.0-40-generic
  linux-image-4.8.0-36-generic linux-image-extra-4.10.0-35-generic
  linux-image-extra-4.10.0-40-generic linux-image-extra-4.8.0-36-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-generic-hwe-16.04 linux-headers-4.13.0-32
  linux-headers-4.13.0-32-generic linux-headers-generic-hwe-16.04
  linux-image-4.10.0-40-generic linux-image-4.13.0-32-generic
  linux-image-extra-4.13.0-32-generic linux-image-generic-hwe-16.04
Suggested packages:
  fdutils linux-tools
The following packages will be REMOVED:
  linux-image-extra-4.10.0-38-generic
The following NEW packages will be installed:
  linux-headers-4.13.0-32 linux-headers-4.13.0-32-generic
  linux-image-4.10.0-40-generic linux-image-4.13.0-32-generic
  linux-image-extra-4.13.0-32-generic
The following packages will be upgraded:
  linux-generic-hwe-16.04 linux-headers-generic-hwe-16.04
  linux-image-generic-hwe-16.04
3 upgraded, 5 newly installed, 1 to remove and 228 not upgraded.
7 not fully installed or removed.
Need to get 0 B/83.7 MB of archives.
After this operation, 234 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 411620 files and directories currently installed.)
Removing linux-image-extra-4.10.0-38-generic (4.10.0-38.42~16.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.10.0-38-generic /boot/vmlinuz-4.10.0-38-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.10.0-38-generic /boot/vmlinuz-4.10.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.10.0-38-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.10.0-38-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.10.0-38-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.10.0-38-generic
needrestart is being skipped since dpkg has failed
E: Sub-process /usr/bin/dpkg returned an error code (1)
kpierce@dw7mhal3:~$ 


    


So it seems /boot is full. Any recommendation as to how to clean it up?

---

### Post by Frogs Hair on 2018-02-06
Try the following as in the output.

```
sudo apt autoremove 
```

```
sudo apt update && sudo apt upgrade
```

---


---
title: "Conflicting device node, lvm and udev, after installing git lvm"
date: 2015-05-01
forum: General Help
---

### Post by gmoutso on 2015-05-01
Hi,
I installed lvm2 v2_02_118 from upstream ([https://www.sourceware.org/lvm2/](https://www.sourceware.org/lvm2/))  because v2_02_111 has had many bugfixes related to lvmcache. Installation was 
```
./configure ; make; sudo make install 
```
No errors. BTW, I tried checkinstall but that didn't work.

I was able to install lvmcache for my HDD+SSD (see [http://ubuntuforums.org/showthread.php?t=2247232](http://ubuntuforums.org/showthread.php?t=2247232)) an everything works fine. 

I have though a problem, which is not important in the sense that everything works anyway. Everytime I boot, I get messages like
```
Apr 29 23:41:11 Miro systemd-udevd[391]: conflicting device node '/dev/mapper/LinuxVG-rootLV' found, link to '/dev/dm-4' will not be created

```
for each and every of my logical volumes.

I suspect this is udev and lvm not playing well together during boot, after I have installed lvm from git. Ubuntu's standard lvm package must solve this issue. How can I also do the same? Thanks!

---

### Post by gmoutso on 2015-05-03
A better question: how to install lvm2 from git source? 

./configure gives many options and I am not sure what is the right options that would play well with udev. For instance there are the options (to name only a few that might be relevant)
```
  --disable-devmapper     disable LVM2 device-mapper interaction
  --enable-lvmetad        enable the LVM Metadata Daemon
  --disable-udev-systemd-background-jobs
                          disable udev-systemd protocol to instantiate a
                          service for background job
  --enable-udev_sync      enable synchronisation with udev processing
  --enable-udev_rules     install rule files needed for udev synchronisation
  --enable-udev-rule-exec-detection
                          enable executable path detection in udev rules
  --disable-ioctl         disable ioctl calls to device-mapper in the kernel

```

---


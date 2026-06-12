---
title: "[SOLVED] /boot full and Synapics &amp;quot;report dpkg was interrupted&amp;quot;"
date: 2008-06-23
forum: General Help
---

### Post by ThomThom on 2008-06-23
I can't update Ubuntu any more.

```

thomas@DEV01-UBUNTU:~$ sudo dpkg --configure -a
[sudo] password for thomas: 
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-ubuntu-modules-2.6.24-18-generic (2.6.24-18.26) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic
gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
dpkg: subprocess post-installation script returned error exit status 1

```

My /boot partition is full

```

thomas@DEV01-UBUNTU:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             25576624   4338952  19938420  18% /
varrun                  517412       244    517168   1% /var/run
varlock                 517412         0    517412   0% /var/lock
udev                    517412        52    517360   1% /dev
devshm                  517412        48    517364   1% /dev/shm
lrm                     517412     38176    479236   8% /lib/modules/2.6.24-18-generic/volatile
/dev/sda5                93307     87019      1471  99% /boot
/dev/sda1             29294492   8556052  20738440  30% /media/sda1
/dev/sda2             29294588  16139640  13154948  56% /media/sda2
/dev/sdb1            293049664 173513156 119536508  60% /media/sdb1

```

The GRUB menu lists many old Kernel images. I found this, [http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/) , describing how to remove old kernel images. But it demands that I use Synapic, and when I try to run Synapic it says:
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

So, now what?

---

### Post by avtolle on 2008-06-23
At the terminal (Applications>>Accessories>>Terminal)```
sudo dpkg --configure -a
```

---

### Post by ThomThom on 2008-06-23
> **avtolle said:**
> At the terminal (Applications>>Accessories>>Terminal)```
sudo dpkg --configure -a
```

That's the commend I typed in the first example I gave. It stops because the boot partition is full. I'm stuck in this loop of errors. I can't fix one unless I fix the other.

---

### Post by ThomThom on 2008-06-23
Could I...

...move some of the old Kernel files to a different location, run the command again? Then hopefully Synapics will work again and I can uninstall some of the other old Kernel images. Then move back the first old files and then uninstall them as well? Or would that cause havok?

---

### Post by sisco311 on 2008-06-23
Try to (re)move the backups(files with .bak extension) from the /boot partition.

---

### Post by ThomThom on 2008-06-23
> **sisco311 said:**
> Try to (re)move the backups(files with .bak extension) from the /boot partition.

Found the same suggestion in this thread: [http://ohioloco.ubuntuforums.org/showthread.php?t=769572](http://ohioloco.ubuntuforums.org/showthread.php?t=769572)

That appeared to work. Ubuntu is now downloading updates. Thanks!

---


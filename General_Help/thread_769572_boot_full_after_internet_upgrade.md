---
title: "/boot full after internet upgrade"
date: 2008-04-26
forum: General Help
---

### Post by tuskpc on 2008-04-26
Earlier today I upgraded Ubuntu from 7.10 to 8.04 through the internet.  Toward the end I was warned that my  /boot was getting full.  How do I go about correcting this?
Here is some basic info:

$ **sudo dpkg --configure -a**
Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1


$ **df**
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             23189076  10748876  11262236  49% /
varrun                     1% /var/run
varlock                    0% /var/lock
udev                       1% /dev
devshm                     1% /dev/shm
lrm                        8% /lib/modules/2.6.24-16-generic/volatile
/dev/sda1                46633     41190      3035 ** 94% /boot**
/dev/sda6             88583232  56934172  27149256 ** 68% /home**


$ **sudo fdisk -l**
Disk /dev/sda: **120.0 GB**, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe211a2bc

   Device Boot      Start        End      Blocks   Id  System
/dev/sda1   *           1           6       48163+  83  Linux
/dev/sda2               7        4593   117170077+   5  Extended
/dev/sda5               7         456     3614593+  82  Linux swap / Solaris
/dev/sda6             457       11660    89996098+  83  Linux
/dev/sda7            1661       14593    23559291   83  Linux


Since my /boot is full I looked at the** menu.lst **and noticed this:
title		Ubuntu 8.04, kernel **2.6.24-16-generic**
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=06faa5ff-4812-469a-9a61-5ae8ec24ccbb ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=UUID=06faa5ff-4812-469a-9a61-5ae8ec24ccbb ro single
initrd		/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel **2.6.22-14-generic**
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=06faa5ff-4812-469a-9a61-5ae8ec24ccbb ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=06faa5ff-4812-469a-9a61-5ae8ec24ccbb ro single
initrd		/initrd.img-2.6.22-14-generic

---

### Post by tuskpc on 2008-04-27
Update:

$** sudo apt-get remove linux-image-2.6.22-14-generic**
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


$  **sudo dpkg --configure -a**
Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1


:confused:

---

### Post by tuskpc on 2008-04-28
Never mind, found out there was something as simple as a .bak file for the old kernel and, after deleting it, was able to remove the old kernel and thus everything went smoothly.  I'm only writing this in case someone else is going through the same confusion I went through.

---

### Post by ghost_ryder35 on 2008-04-29
> **tuskpc said:**
> Never mind, found out there was something as simple as a .bak file for the old kernel and, after deleting it, was able to remove the old kernel and thus everything went smoothly.  I'm only writing this in case someone else is going through the same confusion I went through.
thanks for the heads up.  You should mark this thread as SOLVED

---

### Post by ThomThom on 2008-06-23
> **tuskpc said:**
> Never mind, found out there was something as simple as a .bak file for the old kernel and, after deleting it, was able to remove the old kernel and thus everything went smoothly.  I'm only writing this in case someone else is going through the same confusion I went through.

Thank you so much! I got the same problem.

---


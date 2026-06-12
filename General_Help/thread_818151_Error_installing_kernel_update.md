---
title: "Error installing kernel update"
date: 2008-06-04
forum: General Help
---

### Post by Forsythe on 2008-06-04
When I turned on my computer today, the update manager told me I had system updates.  So, I opened up my console and tried to update, but got this error:

```

forsythe@sioraiocht:~$ sudo aptitude dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following partially installed packages will be configured:
  linux-generic linux-image-2.6.24-18-generic linux-image-generic 
  linux-restricted-modules-2.6.24-18-generic 
  linux-restricted-modules-generic linux-ubuntu-modules-2.6.24-18-generic 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-18-generic
 linux-ubuntu-modules-2.6.24-18-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-18-generic
 linux-restricted-modules-generic
 linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done  

```

I'm assuming, based on this line...

```

gzip: stdout: No space left on device

```

...that my /boot partition is too small for aptitude to unpack the files and configure it.  But, I'm not entirely sure, so I wanted a second opinion. =P

---

### Post by forestpixie on 2008-06-04
It would look that way to me - check space on the partition 

```
df -h
```

I that's the case remove the oldest one or resize it

---

### Post by Forsythe on 2008-06-04
Ah, yes, it is.  Thanks!

---

### Post by JiajiaX2 on 2008-06-06
But,how can i adjust its size

---

### Post by forestpixie on 2008-06-06
If you only need a small amount of space maybe clearing the apt cache would suffice - if not maybe a resize is in order.

```
sudo apt-get clean
```

---

### Post by dlmoak on 2008-06-06
Ran the following code:
sudo apt-get update
sudo apt-get install linux-image-2.6.24-18-generic

 - seemed to get the updates but when I tried to run the install I got this message:
E: Couldn't find package linux-image-2.6.24-18-generic

I'm running 64-bit Ubuntu - what do I need to do?

---

### Post by forestpixie on 2008-06-06
> **dlmoak said:**
> Ran the following code:
sudo apt-get update
sudo apt-get install linux-image-2.6.24-18-generic

 - seemed to get the updates but when I tried to run the install I got this message:
E: Couldn't find package linux-image-2.6.24-18-generic

I'm running 64-bit Ubuntu - what do I need to do?

Perhaps you could post a thread for it - I have no idea with 64bit - don't even know if it uses the same kernel.

---

### Post by JiajiaX2 on 2008-06-07
I'm runing 64bit Ubuntu as well.I've solved the problem.:)
Deleted the old 'linux-image-2.6.24-XX-generic' in the package manager in order to make room for the new kernel , and then ran the following code:
> sudo apt-get update
sudo apt-get upgrade

---

### Post by forestpixie on 2008-06-07
You need to think about the amount of room you have if a kernel stops it working - I use the proposed updates and there is another kernel on the way.

Check df -h it will tell you the stateofyour partitions.

But glad you got that sorted.

---


---
title: "[SOLVED] Hardy update/install problem"
date: 2008-06-17
forum: General Help
---

### Post by crutch on 2008-06-17
Hi, this is similar to a recent post, but I think the person that made it was just having problems with permissions, so I thought I'd start a new thread

My problem is this. I have 223 updates available but when I try to install them I get the following message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I get the same message regardless of whether I am using update manager, synaptic or the command line.

When I try to run this command I get the following response

Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
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
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: subprocess post-installation script returned error exit status 1

And nothing changes.

One thing that Ive noticed is that the error message referes to kernel 2.6.24-18-generic, while I am using 2.6.24-17. Could this be part of the problem or is it something else

Please help, I realy need to get this working properly again

---

### Post by iaculallad on 2008-06-17
Check/Post your free space using Terminal:

```
df -h
```

---

### Post by crutch on 2008-06-17
I think I may have fixed the problem (Update manager is working again anyway). I went to /var/lib/dpkg/updates and made a backup of the files in this directory and then removed them. I got the instuctions for this from linuxquestions

[http://www.linuxquestions.org/questions/ubuntu-63/dpkg-configure-a-error-361965/](http://www.linuxquestions.org/questions/ubuntu-63/dpkg-configure-a-error-361965/)

I think these must have been some temporary files left behind when I interupted update manager last time I was using it.

Thanks for the reply though

---

### Post by crutch on 2008-06-17
Sorry, Spoke a bit too soon, the problem, as iaculallad pointed out was a full boot partition (now I'm regretting seperating this out). Solved by moving old kernel images etc to a backup directory on anouther partition. May look at enlarging this partition  if it becomes a problem.

---


---
title: "Failed upgrade (linux-image-2.6.24-19-generic)"
date: 2008-06-20
forum: General Help
---

### Post by altonbr on 2008-06-20
Everytime I run apt-get or aptitude, the Linux kernel tries to upgrade itself, but fails.

I find this error message:
> Setting up linux-image-2.6.24-19-generic (2.6.24-19.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.

Here's the whole log:

Is this a known bug?

> $ sudo aptitude purge wine-doors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be REMOVED:
  wine-doors{p} 
The following partially installed packages will be configured:
  linux-generic linux-image-2.6.24-19-generic linux-image-generic 
  linux-restricted-modules-2.6.24-19-generic 
  linux-restricted-modules-generic linux-ubuntu-modules-2.6.24-19-generic 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1835kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 161962 files and directories currently installed.)
Removing wine-doors ...
Purging configuration files for wine-doors ...
Setting up linux-image-2.6.24-19-generic (2.6.24-19.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-19-generic; however:
  Package linux-restricted-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.19.21); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.19.21); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-19-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.24-19-generic (2.6.24-19.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-19-generic; however:
  Package linux-restricted-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.19.21); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.19.21); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 linux-restricted-modules-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done 

---

### Post by avtolle on 2008-06-20
Try ```
df-h
```from the console (command line) to see if your /boot partition is full. If that is the problem, then remove (via Synaptic) an older kernel or two. Then try it again.

---

### Post by altonbr on 2008-06-20
> **avtolle said:**
> Try ```
df-h
```from the console (command line) to see if your /boot partition is full. If that is the problem, then remove (via Synaptic) an older kernel or two. Then try it again.

I don't have a boot parition and all of my paritions are < 90% full.

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.3G  5.0G  3.9G  56% /
varrun               1013M  164K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   56K 1013M   1% /dev
devshm               1013M  292K 1013M   1% /dev/shm
lrm                  1013M   38M  976M   4% /lib/modules/2.6.24-18-generic/volatile
/dev/sda5             178G  137G   33G  81% /home
/dev/sda2              42G   29G   14G  68% /media/windows
gvfs-fuse-daemon      9.3G  5.0G  3.9G  56% /home/brett/.gvfs
```

---

### Post by avtolle on 2008-06-20
It was a bit of a "guess" question, but thanks for providing the output from df-h. Another thing to try```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```Perhaps, after the "sudo apt-get clean" you might run```
sudo dpkg --configure -a
``` before the remaining ones.

EDIT: OK, my memory is shot. After the dpkg --configure -a, if that doesn't work```
sudo apt-get -f
```to try to fix any broken packages. 

Hope all this helps.

And, you could do ```
sudo dpkg --remove
```to remove the kernel packages and try again, "taking it from the top".

---

### Post by dmason on 2008-06-28
> **altonbr said:**
> I don't have a boot partition and all of my partitions are < 90% full.

Wow, just wanted to say thanks! I had a problem similar to the one in this thread and found out my boot partition was full and causing the error. I would never have thought of that. Thank you very much.

---

### Post by altonbr on 2008-06-28
Turns out it was because grub wasn't installed (!)

That's that last time I try splashy over usplash!

---


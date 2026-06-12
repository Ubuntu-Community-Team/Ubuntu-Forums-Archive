---
title: "Persistent udev rules"
date: 2012-11-23
forum: General Help
---

### Post by Jason Pierce on 2012-11-23
Hi folks!

I've accidentally deleted the 70-persistent-cd.rules and 70-persistent-net.rules files. For what are these files? How can I recover them since they're not automatically recreated at boot up?


Many thanks!

---

### Post by Doug S on 2012-11-23
Those files provide rules for how the kernel should do things.
 
Edit (for future reference): The files should recover and populate with a system re-boot. One should not have to re-install udev as I detailed below.
 
There may be a better way to do the below, I don't know.
 
You should re-install udev. Depending on if udev versions have changed since your first installation, the .deb files might be in the cache. Example:
First, determine which version you have:```
doug@doug-64:/etc/udev/rules.d$ dpkg -l | grep udev
ii  libudev0                         [COLOR=red]175-0ubuntu9.2[/COLOR]               udev library
ii  udev                             [COLOR=red]175-0ubuntu9.2[/COLOR]               rule-based device node and kernel event manager
```Then, determine if the .deb is already in the cache:```
doug@doug-64:/etc/udev/rules.d$ locate .deb |grep udev
/var/cache/apt/archives/libudev0_175-0ubuntu9.2_amd64.deb
/var/cache/apt/archives/udev_175-0ubuntu9.2_amd64.deb
```Good, on my computer it is in the cache, install it:```
doug@doug-64:/etc/udev/rules.d$ [COLOR=red]sudo dpkg -i /var/cache/apt/archives/libudev0_175-0ubuntu9.2_amd64.deb[/COLOR]
(Reading database ... 108384 files and directories currently installed.)
Preparing to replace libudev0 175-0ubuntu9.2 (using .../libudev0_175-0ubuntu9.2_amd64.deb) ...
Unpacking replacement libudev0 ...
Setting up libudev0 (175-0ubuntu9.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
doug@doug-64:/etc/udev/rules.d$ [COLOR=red]sudo dpkg -i /var/cache/apt/archives/udev_175-0ubuntu9.2_amd64.deb[/COLOR]
(Reading database ... 108384 files and directories currently installed.)
Preparing to replace udev 175-0ubuntu9.2 (using .../udev_175-0ubuntu9.2_amd64.deb) ...
Adding 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
Unpacking replacement udev ...
Setting up udev (175-0ubuntu9.2) ...
udev stop/waiting
udev start/running, process 1227
Removing 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic

```O.K. but what if it wasn't in the cache? Go to the [package web site]("http://packages.ubuntu.com/") and get the .deb files. In my case I would search for "udev" in the precise-updates distribution.

---

### Post by Jason Pierce on 2012-11-23
Ok, fine. But new created files are empty and previously weren't.

Any problem with this?

---

### Post by Doug S on 2012-11-23
I have a test machine that I doesn't matter if I mess it up. So I created your exact situation and tried to recover as per what I said above.
 
Yes, the files were empty, with only comments after the re-install. However one of them filled out with the proper information when I re-booted the computer. The other one did not, but I think only because I currently have the CD-ROM drive unplugged for another test I was doing (and I forgot to plug it back in).

---

### Post by Jason Pierce on 2012-11-23
Even after reboot files are empty. Can I simply forget it? Although it doesn't make any sense to have files populated with info if they are not going to be used.

---

### Post by Doug S on 2012-11-23
When I plugged in my CD-ROM, that file populated with stuff during the subsequent boot up.
 
I don't know for sure, but I assume if your system needed stuff in the files it would have added it during boot up. Unless additionally something else is wrong.

---

### Post by Jason Pierce on 2012-11-23
Finally I've managed to restore previous rules from a Clonezilla image. I don't know if there will be differences, but I prefer keep things as they are ;)

For me this is solved. Thanks!

---


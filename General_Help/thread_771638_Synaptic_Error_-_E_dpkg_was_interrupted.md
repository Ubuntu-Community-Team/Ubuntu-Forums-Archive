---
title: "Synaptic Error - E: dpkg was interrupted"
date: 2008-04-27
forum: General Help
---

### Post by Bdanger on 2008-04-27
After updating from 7.10 to 8.04 I get the following error when running Synaptic Package Manager

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

When I run 'dpkg --configure -a' I get the following

```
sudo dpkg --configure -a
[sudo] password for brian: 
Setting up initramfs-tools (0.85eubuntu36) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1
```

Anyone know how to fix this?

---

### Post by Bdanger on 2008-04-27
..anybody?

---

### Post by ryanhaigh on 2008-04-27
You are out of room on your / or /boot partition. Do you have /boot separate from your main root partition?

If so you could try removing older kernel images from /boot.
If not you can use ```
sudo apt-get clean
``` to remove debs of installed packages from the system and make some more room. Obviously you can also delete things from your home folder if it is on the same partition as / (root).

---

### Post by Bdanger on 2008-04-28
Thanks!  I used Gparted off a live cd and increased the size of my boot from 50 megs to 100 and then ran the config -a command and everything is fine now.

---


---
title: "Unusually small kernel upgrade?"
date: 2014-04-21
forum: General Help
---

### Post by vasa1 on 2014-04-21
I got an update which previously would involve ~60MB but this one is just "6,562 B of archives":```
Fetched 97.3 kB in 21s (4,539 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,562 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/main linux-generic amd64 3.13.0.24.29 [1,780 B]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-generic amd64 3.13.0.24.29 [2,396 B]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-generic amd64 3.13.0.24.29 [2,386 B]
Fetched 6,562 B in 0s (11.9 kB/s)                  
(Reading database ... 103655 files and directories currently installed.)
Preparing to unpack .../linux-generic_3.13.0.24.29_amd64.deb ...
Unpacking linux-generic (3.13.0.24.29) over (3.13.0.24.28) ...
Preparing to unpack .../linux-image-generic_3.13.0.24.29_amd64.deb ...
Unpacking linux-image-generic (3.13.0.24.29) over (3.13.0.24.28) ...
Preparing to unpack .../linux-headers-generic_3.13.0.24.29_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.24.29) over (3.13.0.24.28) ...
Setting up linux-image-generic (3.13.0.24.29) ...
Setting up linux-headers-generic (3.13.0.24.29) ...
Setting up linux-generic (3.13.0.24.29) ...
[09:31 PM] ~ $ 

```Has anyone else seen this?

---

### Post by bapoumba on 2014-04-21
Ran my updates this morning, there was nothing. 
```
Get:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/main linux-generic i386 3.13.0.24.29 [1 784 B]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-generic i386 3.13.0.24.29 [2 400 B]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-generic-pae i386 3.13.0.24.29 [1 754 B]
Get:4 http://archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-generic i386 3.13.0.24.29 [2 388 B]

```
Here is the one I just accepted.

---

### Post by vasa1 on 2014-04-21
My point is that I've never seen kernel-related updates so tiny.
Also, the usual "post-processing" steps were missing.

---

### Post by Impavidus on 2014-04-21
It seems the kernel metapackages were updated. Usually they would pull in a new kernel image and headers, but this time for some reason the dependecies of the metapackages were unchanged.

---

### Post by vasa1 on 2014-04-21
Just for comparison, I'm used to seeing stuff like this ([http://ubuntuforums.org/showthread.php?t=2192955&p=12870988#post12870988):](http://ubuntuforums.org/showthread.php?t=2192955&p=12870988#post12870988):)
```
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 258 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 178331 files and directories currently installed.)
Removing linux-headers-3.11.0-12-generic ...
Removing linux-headers-3.11.0-12 ...
Removing linux-image-extra-3.11.0-12-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-12-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-3.11.0-12-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
update-initramfs: Deleting /boot/initrd.img-3.11.0-12-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-12-generic /boot/vmlinuz-3.11.0-12-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
[05:40 PM] ~ $
```

---

### Post by bapoumba on 2014-04-21
> **vasa1 said:**
> My point is that I've never seen kernel-related updates so tiny.
Also, the usual "post-processing" steps were missing.
I did not paste the rest of the output, I had the same as yours. We are in the same boat now. If we are never to be found again, that was a nice ride, thanks :)

Joking aside, I'll reboot to see what happens.

---

### Post by vasa1 on 2014-04-21
> **Impavidus said:**
> It seems the kernel metapackages were updated. Usually they would pull in a new kernel image and headers, but this time for some reason the dependecies of the metapackages were unchanged.
Thanks! I was worried :)

---

### Post by bapoumba on 2014-04-21
Thanks Impavidus :)

---

### Post by VanR on 2014-04-21
I got that this morning also.

---


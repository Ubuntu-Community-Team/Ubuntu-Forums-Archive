---
title: "ubuntu 18.04 - lvm2 error installing kvm"
date: 2019-05-11
forum: General Help
---

### Post by Dr Berta on 2019-05-11
Hi,
I'm trying installing qemu-kvm because the last update of android emulator in my Android Studio doesn't work. Since my processor is and AMD Phenom II, now I receive an error about SEEE3 and the emulator doesn't work. With the previous version it was working perfectly.

Doing some research on Google I found that I have to install qemu-kvm. Following a guide I installed the required packages with the command:
```
[COLOR=#333333][FONT=UbuntuMono]sudo apt-get install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils[/FONT][/COLOR]
```
After the installation I receive the following error:
```
dpkg: error elaborating package lvm2 (--configure): installed lvm2 package post-installation script subprocess returned error exit status 1
Configuration of qemu-kvm (1:2.11+dfsg-1ubuntu7.12)...
Configuration of bridge-utils (1.5-15ubuntu1)...
Elaboration of trigger for man-db (2.8.3-2ubuntu0.1)...
Elaboration of trigger for initramfs-tools (0.130ubuntu3.7)...
update-initramfs: Generating /boot/initrd.img-4.15.0-48-generic
W: initramfs-tools configuration sets RESUME=UUID=94da698b-4f3e-4ee6-8a94-8efd229427c4
W: but no matching swap device is available.
I: The initramfs will attempt to resume from /dev/sdc5
I: (UUID=e444ebd4-bd85-4900-90f6-f6bd43dd1763)
I: Set the RESUME variable to override this.
Errors during elaboration:
 lvm2
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

The partition /dev/sdc5 is the swap partition of my system so I don't understand why it says "no matching swap device is available"

Any suggestion about how to fix this issue?

Thanks
Claudio

---

### Post by Dennis N on 2019-05-11
The warning is that the UUID set for RESUME= isn't for a swap partition. Is that the correct UUID of your sdc5? If not, you can edit the value stored in **/etc/initramfs-tools/conf.d/resume** so that it matches swap on sdc5.

---


---
title: "Permissions -- Help"
date: 2007-06-22
forum: General Help
---

### Post by PaulFXH on 2007-06-22
I'm using this excellent [guide]("https://help.ubuntu.com/community/BootFromUSB") to create a boot cd to allow me to boot Ubuntu from a usb HD (computer BIOS does not recognise usb HDD).
I have successfully used this method before but I always started from a Linux system already installed on an internal HD and had few, if any, problems.
Now, I'm starting from the Feisty Live CD (as indeed is the recommendation of the guide) and cannot get into the new Ubuntu "system" installed on the usb drive which is necessary as part of the preparation of the boot cd.

When I do the following
```
sudo mount --bind /dev /media/disk/dev
sudo chroot /media/disk
```
(where "media/disk" is where the Ubuntu system installed on the usb drive is mounted on the Live CDs system.) I get
> chroot: cannot run command '/bin/bash': permission denied
I have changed the owner of  /media/disk/ (which is where I'm trying to chroot to) to "Ubuntu Live CD users", run chmod 440 /etc/sudoers" and did the chroot operation as root -- but all without any sucess.

I hope somebody can indicate where I'm going wrong.

---


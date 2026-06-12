---
title: "udevadm trigger is not permitted while udev is unconfigured."
date: 2014-09-07
forum: General Help
---

### Post by wlraider70 on 2014-09-07
I was running apt-get update ans upgrade, when I lost the ssh connection. 
I forgot about the update when I logged in again and it asked for a reboot.

now I get "udevadm trigger is not permitted while udev is unconfigured."

I can find this problem on the forum, but its all like 4 years old. [http://ubuntuforums.org/showthread.php?t=1567147&page=7](http://ubuntuforums.org/showthread.php?t=1567147&page=7)
The solution then was to chroot the drive from a live-disk, my current 14.04 disk, does not allow me to chroot. It says not fount /bin/bash


Thanks for your help.

---

### Post by steeldriver on 2014-09-08
Can you get into the system at all without chrooting (e.g. via recovery mode)?

At what point in the chroot process do you get the bash not found message?

---

### Post by wlraider70 on 2014-09-08
I haven't gotten the rescue disk to work, but that could be my fault, im not sure what to do with it when it asks for where to put the files.



I managed to make some progress by adding these
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys


When I run "update-initramfs" I get an error about it being mounted in a write only fashion.
I'm trying to work around that, but I might be barking up the wring tree...

---


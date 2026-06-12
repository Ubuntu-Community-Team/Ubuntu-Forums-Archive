---
title: "New user"
date: 2016-01-07
forum: General Help
---

### Post by Zainobee on 2016-01-07
I have ubuntu 15.10 and I am a new user. I turned on the computer and this happened (see attachment) and I dunno how. Help anyone?

---

### Post by ajgreeny on 2016-01-07
Has the OS crashed?  A hard reset or crash can cause corruption of the filesystem, though often it does not do so.

The error message you see tells you to run fsck manually, so boot to a live ubuntu OS on DVD or USB (the install medium you used will be fine).
Run terminal command ```
sudo parted -l
``` to find which is the root partition, then run command ```
sudo e2fsck -vy /dev/sda1
``` That may fix any filesystem problems and allow you to reboot to the installed OS again.

---


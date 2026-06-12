---
title: "Broke my installation"
date: 2013-05-14
forum: General Help
---

### Post by PanqueNhoc on 2013-05-14
Ubuntu 13.04 64 bits

I tryed to create a new launcher icon using this utility: [https://apps.ubuntu.com/cat/applications/create-launcher/](https://apps.ubuntu.com/cat/applications/create-launcher/)
I believe i've set the wrong path while creating the icon. After creating it, the application opened a folder containing what should be my launcher, but I couldn't drag & drop it on the bar. I tried opening the thing by double-clicking it on the folder and suddenly my screen turns black and all i can see is a static underscore on the upper-left corner. I then forced a shutdown and when I tryed to boot again I recieved some errors relating to mounting stuff (I believe it is related to me setting my windows partition to mount on startup, not the launcher thing) and the option to skip mounting. After skipping twice I am presented the same black screen with the static underscore. 

Is there anyway I can possibly fix this?

Also sorry for my english and sorry in advance if this post lacks any info or is in the wrong place.

---

### Post by PanqueNhoc on 2013-05-14
Solved. The problem was actually the mount thing, i changed the display name of a partition through the disk utilities, and it seems that option is bugged. Managed to edit /etc/fstab on windows and remove the invalid argument created by that option.

Edit: This explains it better: [http://askubuntu.com/questions/262426/boot-error-22-874755-ext4-fs-sda2-unrecognized-mount-option-x-gvfs-name](http://askubuntu.com/questions/262426/boot-error-22-874755-ext4-fs-sda2-unrecognized-mount-option-x-gvfs-name)

---


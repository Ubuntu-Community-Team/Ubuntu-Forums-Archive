---
title: "Can't boot after resizing and creating partition"
date: 2018-02-17
forum: General Help
---

### Post by micaldas on 2018-02-17
I resized a partition and created a new one, with gparted on a ubuntu installation cd, to host LFS. When i rebooted, the installation would stop in a purple screen and go no further. After looking for possible solutions I found a work-around that lets me boot to ubuntu. I open a shell in advanced options during boot mode, and write: "mount -o remount,rw /" This lets me get to ubuntu, but it is lost on reboot.
I used boot-repair but the problem persists. Below is log from boot-repair: [http://paste.ubuntu.com/p/rPTgGBCbYk/](http://paste.ubuntu.com/p/rPTgGBCbYk/)

I'm running ubuntu 16.04

Any help would be greatly appreciated

---

### Post by Impavidus on 2018-02-18
Two problems: 

First, your /etc/fstab seems incomplete. The root partition and the swap partition are not mentioned in your fstab. You can edit it using a live disk or restore a backup.

Second, your root partition is almost full. At 97% full, there may not be enough headroom for some basic operations. There's still a lot of unallocated space left on that drive. Maybe you should have partitioned it differently.

---


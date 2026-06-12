---
title: "rename GRUB entry?"
date: 2007-06-28
forum: General Help
---

### Post by kraigory on 2007-06-28
Okay, so I've got dual boot up and going, and i'm quite happy. My only problem is that "Windows NT/2000/XP" shows up twice in GRUB's menu. (just the default one, not splash or anything). So, i've booted each one, and the first is real windows XP, while the second is my dell laptop's system recovery feature that boots into a norton ghost recovery thing. 

So, is there any way I can rename the entries in GRUB so that the second one shows up as "WinXP Dell Recovery" or something, so if someone else boots my pc they won't accidentally boot that and wipe my system to factory default?

Thanks!

---

### Post by aJayRoo on 2007-06-28
Edit the file /boot/grub/menu.lst using an editor of your choice, remembering to backup the original in case something goes wrong. For example, in the terminal type:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```

Find the part (near the end) that lists other operating systems and change the second windows xp title to be whatever you want it to be.

---

### Post by mikewhatever on 2007-06-28
You may also want to prevent it from auto mounting at boot. If that's a fat partition, which is the case with my HP, there would be full read/write access to it. To stop it from mounting, comment it out in /etc/fstab
> sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

> [COLOR="Red"]#[/COLOR] /dev/sda2
#UUID=3EC6-2E70  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1

---


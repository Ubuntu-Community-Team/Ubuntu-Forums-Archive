---
title: "dual booting problem"
date: 2007-02-02
forum: General Help
---

### Post by SDF-1 on 2007-02-02
Hi! This is my first post yippee :D ! Unfortunately my first post is a problem so here it is, I hope someone can help me:

_STATUS:_

I have installed Ubuntu and XP in dual boot mode. For some odd reason, GRUB can't seem to detect XP, only Ubuntu. When I went into Menu mode on GRUB only the Ubuntu OS was found but not XP.  

This is what I did from scratch within my installation:

I have 1 x 40GB hard drive on my PC so I partitioned it equally for both OS's (20GB linux, 20GB XP)

1. Installed XP first
2. Rebooted the PC then;
3. Ran the live CD and installed Ubuntu 6.10.
4. Rebooted and installed updates;
5. Then while I'm in boot mode, GRUB doesn't ask me what OS i would like to choose, it just boots to Ubuntu directly.

I don't know why this is happening, I remember doing this once and following the same steps but this time it doesn't work. I tried back tracking on where I went wrong but can't solve it. Can somebody please give me some advice? 

From Axel

---

### Post by aysiu on 2007-02-03
Not sure if I can help with this, but maybe someone else can if you post the output of these terminal commands (just highlight the output and copy and paste it back into this thread): ```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---


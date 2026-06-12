---
title: "Dual Boot Purple Screen of Death"
date: 2013-07-06
forum: General Help
---

### Post by gc88 on 2013-07-06
I recently installed Ubuntu on my laptop and wiped the existing Windows 8 UEFI installation. Then, I installed windows 8 on the computer again, this time without UEFI, by booting from the disc and deleted the previous partitions. Then, I booted from the Ubuntu 13.04 installation disc and installed it, this time having the CD automatically create the partitions for me. Now, when I boot up the computer, I see GRUB, and Ubuntu boots up fine, but I get a purple screen whenever I try to boot into windows 8. The screen actually refreshes 2 times before freezing. Any help would be much appreciated.

Also, on startup, it gives me a black screen during startup which disappears, saying pointer to the TMDS table is invalid.

---

### Post by AbhimanyuAryan on 2013-07-06
last time when u installed ubuntu did u removed ubuntu dual boot with bootmgr(windows software) or u just cleared ur partition?

---

### Post by gc88 on 2013-07-06
The first time, I just did it automatically, with the CD. When I installed windows though, I removed all the previous partitions.

---

### Post by gc88 on 2013-07-06
Okay, problem solved itself somehow. All I did was just reboot it a couple of times.

---

### Post by Double.J on 2013-07-06
Hi there!

Purple screen sounds like it isn't handing over to windows at all (asuming it's the ubuntu purple, and your windows 8 isn't set to a purple theme??)

Best thing usually is to get a good look at how the drive's laid out right now. if you boot up ubuntu, the two best ways to see the hard drive are gparted (it will lay the partitions out like the installation program) or fdisk in the command line.

if you're comfortable in the terminal you can see your partitions with fdisk:
```
 sudo fdiskl -l
```

gparted is in the software center.

It may also be worth just refreshing grub's menu entries. in a terminal
```
 sudo update-grub
``` this will make grub check your partitions again for bootable systems. while it runs, you an get an idea for what is likely to be found from the messages popping up. You're looking for a line similar to ```
Found Windows 8 (loader) on /dev/sda1
```

---


---
title: "Ubuntu wont boot"
date: 2007-07-24
forum: General Help
---

### Post by chadwikket on 2007-07-24
I have xp and Ubuntu ff duel booted... i never really used my computer for a couple days and the next tiem i had turned it on xp will boot fine but Ubuntu will start loading but it will stop and say "program apt-get is not currently installed, to install apt-get type install apt.. or something of the like. but when I type so it says bad command or "no" basically...
any ideas?

thanks

---

### Post by kevinlyfellow on 2007-07-24
Last time that happened to me (on debian) it was because it reassigned the drive letters.  If you know which harddrive device your ubuntu is installed on, then we might be able to fix your problem.

When you enter grub, press 'e' twice.  Read the line and it should have something in it that looks like this
```
root=UUID=2342-5342...(bunch of numbers and letters)
```

Change this line to something like this (of course the device is whatever Ubuntu is installed on)
```
root=/dev/hda1
```

If this is successful, you will get another error.  You will need to fix /etc/fstab also.  Everything is listed by their UUID, but above each entry, there is a line commented out with the device names.  Replace the UUID with the device name.  You will then also need to fix /boot/grub/menu.lst so you don't need to fix grub everytime you boot.

I hope that wasn't too much to swallow.

---

### Post by chadwikket on 2007-07-24
How might I find what drive it's installed on.

haha sorry I'm a n00b.

---

### Post by confused57 on 2007-07-24
> **chadwikket said:**
> How might I find what drive it's installed on.

haha sorry I'm a n00b.
You can use the live cd to run this command in a terminal(Applications---Accessories---Terminal):
```
sudo fdisk -l
```
-l is a small "L"

I received the same error once when the UUID changed on one of my filesystems.

---

### Post by badrobot on 2007-07-24
similar thing just happened to me.  it was after i installed ubuntu server on another partition.  i had to correct the UUID of the newly installed partition in the fstab of my old feisty partition that wouldn't boot correctly.  

when the boot process fails does it say anything about fsck failing before the apt-get business?

---

### Post by chadwikket on 2007-07-26
nope only the apt-get'ness" I'll try and find my ubuntu cd

---


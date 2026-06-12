---
title: "grub error 17 cannot mount selected partition (past posts checked still deosn't work)"
date: 2008-05-05
forum: General Help
---

### Post by jieyunfu on 2008-05-05
my machine is XP + ubuntu

for some reason, my grub failed to identify my hard drive, and it displays "grub loading... error 17" and I can enter neither system. so I use live CD to boot the system, and try to restore the grub.

I type:

sudo grub
find /boot/grub/stage1 // here I got a "floating point exception" no past posts talk about how to handle it...

so I directly root (hd0,6) {where my ubuntu is installed}, and setup (hd0)

but now, I can boot xp, but still, when trying to enter ubuntu, I met "error 17, cannout mount selected partition"...

I am thinking of re-installing ubuntu, but is it going to eat another part of my hard-drive as swap? I am not familiar with the re-installation process of ubuntu. is it possible to solve this problem without re-installation?

is any way to solve this problem? thank!

---

### Post by frodon on 2008-05-06
Your menu.lst may be wrong, please post your menu.lst file and the output of "sudo fdisk -l".

---


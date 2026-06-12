---
title: "GRUB error 22, how to get dualboot (Ubuntu + Vista)"
date: 2008-03-25
forum: General Help
---

### Post by gigenieks on 2008-03-25
Hi I'm totally new to Ubuntu and here in forum. Yesterday I installed Ubuntu many times, but  with no success! It just booted on my Win Vista, with no chances **to choose to boot on Vista or Ubuntu.**
Last time I installed my Ubuntu i set
/swap
/
/boot

And when I restarted Pc I get error **GRUB loading, please wait... Error 22**

So I guess, I have to reinstall GRUB. What is weird that on my root partion (/) is just boot folder with no Grub inside, but in /boot partition is grub folder with all needed files...

**So what exactly I must do??** :confused:

---

### Post by pseudo-random on 2008-03-25
You could try booting from the windows disc into a recovery mode and type **fixmbr**
This should repair your Master Boot record.
Google for: Grub error 22 fixmbr, for a more complete guide.

---

### Post by gigenieks on 2008-03-25
Yes that I will do later ( I just give the CD to friend).

But if do in that way won't it will be like previous times when I have no choice of OS, it just booted in Win Vista??

---

### Post by milton1 on 2008-03-25
yes, you will probably need to reinstall grub after fixing the MBR.

---

### Post by gigenieks on 2008-03-25
You mean this --> [GRUB install]("http://ubuntuforums.org/showthread.php?t=224351") ??

---


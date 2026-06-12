---
title: "error /boot/grub/i386-pc/boot.mod not found grub rescue"
date: 2016-08-10
forum: General Help
---

### Post by oliver-white73 on 2016-08-10
[INDENT] 					Hello I recently updated 16.04 when I finally restarted the laptop.  It started in rescue mode with error /boot/grub/i386-pc/boot.mod not  found. I have tried google but the closest thing it finds is normal.mod  not found. I have tried BOOT= and PREFIX= but did not work. Can any one  shed any light....???? 				
[/INDENT]

---

### Post by ajgreeny on 2016-08-10
Is this about 16.10, ie a development version problem, or about 16.04?  I am not certain which version is involved from your post.

Also please do not duplicate posts as it dilutes community effort and is confusing for all.
[https://ubuntuforums.org/showthread.php?t=2333485](https://ubuntuforums.org/showthread.php?t=2333485)

---

### Post by oliver-white73 on 2016-08-11
It's 16.04 thought maybe development as lts. Ok won't duplicate but the tag helped thanks

---

### Post by oliver-white73 on 2016-08-12
fixed with a live usb and binding files from live usb to hard drive

---

### Post by ajgreeny on 2016-08-13
Great! Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

### Post by ben163 on 2016-08-22
> **oliver-white73 said:**
> fixed with a live usb and binding files from live usb to hard drive

Hi Oliver, I was wondering if you could be more specific regarding the binding procedure.
I am getting the same error with boot.mod and getting dumped into the grub rescue menu.

---

### Post by xavier24 on 2017-01-07
Oliver-white I am also stuck in same error can please elaborate the  steps it will be helpful, thanks in advance

---

### Post by hutch90 on 2017-11-07
Hello,


I recently had this problem as well. I was able to solve it earlier today, so here are the steps to the best of my memory:


1. Boot with a 64-bit Ubuntu CD
2. Repair grub. [Here]("https://help.ubuntu.com/community/Boot-Repair") is a useful webpage with instructions. I believe I did option 2. After rebooting, grub worked, but Linux seemed to get stuck, not even bringing up the loading screen. It just hung at the purplish color.
3. After shutting my machine down (using the power button) and turning it back on, I chose "Advanced options for Ubuntu" from Grub's main menu.
4. Boot in recovery mode. [Here]("https://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/") is a useful link. Look under the webpage's "Use Recovery Mode If You Can Access GRUB" section. There were a lot of versions to choose from on my machine, and I tried the first two, I think, but they didn't work. The one at the bottom of the list did.
5. I chose dpkg, since I think my problem came about because I canceled an update and rebooted without finishing it.
6. At this point, I think I resumed normal reboot.


Hope this helps!

---


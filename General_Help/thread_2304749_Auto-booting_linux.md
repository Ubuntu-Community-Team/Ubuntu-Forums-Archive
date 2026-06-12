---
title: "Auto-booting linux"
date: 2015-11-29
forum: General Help
---

### Post by hooman2 on 2015-11-29
Hello ubuntu forums.
I am in need of explanation on automatically booting Linux (ubuntu 14.04 lts 64 bit)  when I power on my PC. My PC does **NOT** have windows, and when I turn on my PC, I always have to hit F8 and select Ubuntu. How can I fix this? When I don't hit F8 it just sends me to a black screen telling me to insert media. I want to be automatically sent to the Ubuntu screen. Thank you for reading!
Please answer soon! ):P

---

### Post by SlidingHorn on 2015-11-29
> **hooman2 said:**
> Hello ubuntu forums.
I am in need of explanation on automatically booting Linux (ubuntu 14.04 lts 64 bit)  when I power on my PC. My PC does **NOT** have windows, and when I turn on my PC, I always have to hit F8 and select Ubuntu. How can I fix this? When I don't hit F8 it just sends me to a black screen telling me to insert media. I want to be automatically sent to the Ubuntu screen. Thank you for reading!
Please answer soon! ):P

Did the machine have Windows when you originally installed Ubuntu?  If so, maybe grub hasn't realized it's gone yet:  sudo update-grub

---

### Post by deadflowr on 2015-11-29
In the screen that says F8, is there another option to access a menu?
If so, you need to access the menu and look for the section for booting.
It seems you are set to boot from a cd/dvd.
You should be able to change that to the hard drive.

---

### Post by hooman2 on 2015-11-30
> **deadflowr said:**
> In the screen that says F8, is there another option to access a menu?
If so, you need to access the menu and look for the section for booting.
It seems you are set to boot from a cd/dvd.
You should be able to change that to the hard drive.
This was basically it!
I just switched from legacy to uefi and placed ubuntu with highest priority!
Great to see admins are so diligent in helping even the worst of questions!

---


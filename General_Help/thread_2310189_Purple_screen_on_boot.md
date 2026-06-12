---
title: "Purple screen on boot"
date: 2016-01-16
forum: General Help
---

### Post by niklassheth on 2016-01-16
My computer is exhibiting strange behavior. I can get into GRUB, but if I press enter on Ubuntu then I get stuck on a purple screen. However, if I press Advanced options for Ubuntu, hit recovery, then resume, I can boot just fine.

---

### Post by grahammechanical on 2016-01-16
May I make a suggestion?

Go to System Settings>Software & Updates>Additional drivers tab and try another video driver.

Regards.

---

### Post by Bucky Ball on 2016-01-17
Welcome. Failing the additional drivers, try nomodeset. When booted to the grub list, highlight the kernel and press 'e'. Look for the line that ends in 'quiet spash'. After that, put a space and 'nomodeset' so it looks like this:

> quiet splash nomodeset

Follow the instructions at the bottom of that edit screen to save and continue. Any luck? We can make it permanent if so (that option will be lost on reboot doing it this way).

Is this a fresh install or did this 'just start happening' when you try to boot the machine one day and everything was working fine previously?

---

### Post by niklassheth on 2016-01-17
This is a fresh install, the issue has always been happening.

Tried both changing drivers (both to older Nvidia one and the open source one) and trying the nomodeset. Neither worked. I found out some more info though. When I boot my PC, half the time my keyboard doesn't work. It is a back lit one, and the back light only shines at a very low brightness when it doesn't work. I can fix it by simply rebooting my PC. 

Another strange thing that happens is when I select restart from a working desktop. I go into a low resolution screen asking me to unencrypt my hard drive (my hard drive is encrypted), but my keyboard is at full brightness and does not work.

EDIT: Booting into an older version through Advanced options works fine, but text in the operating system is messed up (not in chrome though). I can provide pictures if anyone wants.

---

### Post by niklassheth on 2016-01-18
Bump... can anyone please help? This is very annoying.

---


---
title: "Need to fix Sudo [Resolved]"
date: 2007-05-21
forum: General Help
---

### Post by ronbrooks on 2007-05-21
I broke Sudo now every time i try to log in as root I get this message.

sudo: /etc/sudoers is mode 0551, should be 0440

How do I fix it.

---

### Post by yabbadabbadont on 2007-05-21
You will need to boot into recovery mode, then change the permissions of the file to 0440.

---

### Post by aysiu on 2007-05-21
Reboot into recovery mode and type ```
chmod 0440 /etc/sudoers
reboot
```

---

### Post by ronbrooks on 2007-05-21
How do I get to recovery mode with 7.04.  I know in 6.10 we got a menu to pick from on stat up but I don't see it on 7.04

---

### Post by btaub on 2007-05-21
Unless I'm mistaken, you should see a brief message saying "Hit ESC key for grub menu..." right before it goes into the boot process

---

### Post by ronbrooks on 2007-05-21
Thank you all very much I have it fixed now.  

This forum is great and thanks to all the people that help out on this site.  

I try and come here and read the post as much as I can to try and learn more about Linux.

---

### Post by rexxxlo on 2007-12-16
oddly enough when this happened to me i restarted the computer

first weird thing i noticed was the resolution of the boot sequence changed to about 600x800 or so  as soon as the screen was about to get to the place where you push escape to enter recovery mode 

i couldn't see all of the text on the screen so i waited until all the text stopped scrolling and then entered

chmod 0440 /etc/sudoers
pressed enter
reset
got back to gnome and its still not working ?

this happened when i was trying to work with /ect/fstab and sudo nautlis attempting to change the permissions on my external drives

any ideas what is happening?

---


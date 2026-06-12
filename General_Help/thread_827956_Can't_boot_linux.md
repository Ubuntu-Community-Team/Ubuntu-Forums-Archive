---
title: "Can't boot linux"
date: 2008-06-13
forum: General Help
---

### Post by mooglehat on 2008-06-13
So, I upgraded ubuntu from 7.10 to 8.04. During the install it asked to keep the menu.lst, I believe, and I said yes because I thought if I didn't keep menu.lst the same then it would not let me dual boot. 

After it installed and I restarted my laptop the menu options were 7.10 and vista. Which had me confused. I'm suspecting since I kept the menu.lst it is trying to boot the old headers thus not booting up. 

Is there a way for me to change that or should I just reinstall 8.04? 

Unfortunately, I'm a work and I can't give too many details. 

My laptop is a hp tx1000 series. 

Thanks

---

### Post by drs305 on 2008-06-13
An easy way is to check StartUp-Manager. System > Administration > StartUp-Manager. Check Boot Options, Default Operating System and see if Hardy is one of the choices.

If StartUp-Manager isn't on your menu:
```
sudo aptitude install startupmanager
```

I highly recommend using StartUp-Manager to change boot options if at all possible.
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Zorael on 2008-06-13
Can you boot your 7.10 kernel? If so, just do this in a terminal and it should generate a new menu.lst for you.
```
$ sudo update-grub
```

---

### Post by mooglehat on 2008-06-13
I select 7.10 it comes up with the loading bar then it goes to a black screen with a blinking cursor. I then just restart my laptop. 

In short, I can't even get into linux at all.

---


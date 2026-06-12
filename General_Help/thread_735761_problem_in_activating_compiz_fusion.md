---
title: "problem in activating compiz fusion"
date: 2008-03-26
forum: General Help
---

### Post by chathurangamdk on 2008-03-26
I'm using gusty gibbon 7.10 on my desktop PC. I installed compiz related packages by using a repository. But when I'm going to activate the fusion, it gives me an error message something called "nvidia-glx".
Even I can't enable the driver under "Restricted Device Manager".
So what should I do to get compiz fusion on my desktop????

My PC spec
-----------------
cpu	intel Pentium 4 3.00GHz
ram	kingston 512MB
graphic	radeon-7000 R70 series 64MB 

Thank You !!!

---

### Post by gwoodruff on 2008-03-26
Two things. Do you know what video hardware you have, and what error do you get when you try to enable the restricted driver?

---

### Post by ibuclaw on 2008-03-26
Maybe the card is rather outdated?

But before I come to that conclusion:
Try this:
```
 sudo apt-get install compizconfig-settings-manager emerald gnome-compiz-manager 
```

 Then reboot your computer.

Go into System>Preferences>Appearance.
Then Click on the Visual Effects Tab. And choose "Normal" as your choice of Compiz Effects.
If all seems right, you can go adventurous and try extra or custom.

Else, as I said before, the card may be rather outdated and may not support the higher-ended OpenGL 3D effects.

Regards
Iain

---

### Post by gwoodruff on 2008-03-26
Sorry see that you do know hardware. Try System/Screens and Graphics and select the proper video driver for your card. ctrl-alt-bcksp will log you out if needed.

---

### Post by chathurangamdk on 2008-03-26
It tells that driver can not be enable. I did not install any driver. That may be the reason. If that so, what would I do?
My VGA is gigabyte as I mention before. Monitor is Phillips 17" 16 depth.

---

### Post by ibuclaw on 2008-03-26
Maybe getting the Drivers from the Manufacturers site may fix this:
[http://http://ati.amd.com/support/driver.html]("http://http://ati.amd.com/support/driver.html")

Also, check out output of this command
```
 lsmod | less 
```

agpgart should be displayed in the list.

---

### Post by castoroil97 on 2008-03-29
thanks I will try that, I just upgraded from Feisty to Gutsy

---


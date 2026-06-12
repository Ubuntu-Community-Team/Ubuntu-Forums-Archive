---
title: "Stop grub countdown from stopping"
date: 2014-03-20
forum: General Help
---

### Post by caryb on 2014-03-20
I have a new laptop/tablet that "had" Windows 8 on it. I has been replaced with Ubuntu/Kubuntu 13.10 & Android 4.4 with grub as a dual boot. I find myself not being able to change O/S when the screen is not docked to the keyboard, I can select the different O/S with the volume up down key but I have no way of selecting the O/S & the grub countdown timer stops. What I need to do is for grub to keep counting when I change my O/S selection.
Does anyone know if or how this can be done?


Thanks Cary

---

### Post by sudodus on 2014-03-20
Do you want a longer countdown, say 60 seconds instead of the default, 10 seconds? Or do you want the menus to stay until you have selected OS (so no countdown at all)?

See this link that describes how to change the settings of grub.

[https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

Maybe you should change **GRUB_TIMEOUT**

Remember to run

```
sudo update-grub
```

after you have changed the configuration files. This propagates the changes to the file [FONT=courier new]**/boot/grub/grub.cfg**[/FONT] which is used during booting.

---

### Post by caryb on 2014-03-20
No I want it to continue the countdown when I make a change as I can change the boot order with the up down volume key but I have no way of selecting it as grub doesn't use the touch screen & once you change the selection it stops the countdown at that point I'm stuck. So what I need is for the 10s countdown to continue regardless what I'm selecting.

---

### Post by sudodus on 2014-03-20
I think I understand. Then you need to change the logic in the scripts, because the normal behaviour is to stop counting when something new is high-lighted. Or maybe there is a way to get an 'Enter' signal from the touch screen?

---

### Post by grumblebum2 on 2014-03-20
Don't have an answer if you are unable to press an enter key.
Possibly have a look at [unity-reboot]("http://www.webupd8.org/2013/01/unity-reboot-launcher-to-quickly-reboot.html") where at least you can change the default os to boot into 
 when you next reboot. 
There is also a package for 13.10 in that ppa.
I would disable that ppa after install as it contains numerous unofficial packages that may cause problems.
Means you would have to boot into ubuntu first then choose a grub menu entry from unity-reboot's quicklist.

---


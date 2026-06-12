---
title: "Ubuntu 7.10 error 17"
date: 2007-12-08
forum: General Help
---

### Post by Marfish on 2007-12-08
Heya, I just installed Gutsy Gibbon to my external hard drive. I made sure to load the bootloader to the external so that I would be able to boot without having the external plugged in all the time. So, my vista machine doesnt even detect the external drive in the bios, so I couldnt set a default. It got to the grub menu, I chose to boot linux, but it came up with error 17. How do I get around this, and is it only compatible with my computer and not others? How can I make it possible to make it work on all computers? Help would be much appreciated, this is my first time with linux.

---

### Post by Marfish on 2007-12-09
It also showed the boot options that are on my main computer on boot up. Unfortunately, I was trying it on my parents computer, so does that mean that it is now set only for my computer? Mine has vista, parents has xp.

---

### Post by confused57 on 2007-12-09
> **Marfish said:**
> Heya, I just installed Gutsy Gibbon to my external hard drive. I made sure to load the bootloader to the external so that I would be able to boot without having the external plugged in all the time. So, my vista machine doesnt even detect the external drive in the bios, so I couldnt set a default. It got to the grub menu, I chose to boot linux, but it came up with error 17. How do I get around this, and is it only compatible with my computer and not others? How can I make it possible to make it work on all computers? Help would be much appreciated, this is my first time with linux.
You probably need to change the root designation in grub...you can do this by highlighting your Ubuntu entry in your grub boot menu, press "e", then highlight the line with root, press "e" again, change root from (hdx,y) to (hd0,y), press "enter", then "b" to boot...leave the y value as it is, just change the x value to 0(zero).   This change is temporary, but can be made permanent, if it works.

Ubuntu on your external hd  may work on other computers, depending on how similar the hardware is...you'd probably need to run:
```
sudo dpkg-reconfigure xserver-xorg
```
when you boot it when connected to another computer.

---

### Post by Marfish on 2007-12-09
Thank you very much for your help, I changed the codes to hd0,0 and it started booting up. May I ask though, when do I apply the codes to make it work on other computers? Thanks again for the great help! :D

---

### Post by Marfish on 2007-12-09
Also, is it possible to use this on a mac pc, and then use it on a windows pc using codes such as the one you suggested?

---

### Post by Marfish on 2007-12-09
Unfortunately, I cannot edit the root on my main computer, so I can only do it on my parents. It will not entirely boot up yet though, it will load kernel to about where it is running local boot scripts and stop. When I come back to my computer with the changes I made on my parents computer, they have not been applied and it still reads hd1,0. Can you please tell when to apply the codes to make it work on their computer so I can get it to work on mine? I have a Poenix bios on my laptop, when I try to boot from my external, there are no options and mearly comes back with error 17.

---

### Post by confused57 on 2007-12-09
I would recommend that you download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It's only a 5-7 Mb download...use SGD to hopefully  boot Ubuntu on your external hd after you boot your computer with SGD cd inserted in your cd drive.  This should determine if Ubuntu is bootable & you might try it on your other pc also.  Using SGD to boot your external drive would be beneficial on a computer which isn't capable of booting first to USB.

---


---
title: "windows reistall got rid of OS select"
date: 2006-11-15
forum: General Help
---

### Post by TheGreenMutt on 2006-11-15
ok heres what happened i had to delete my windows partition and reinstall it when i reinstalled it the windows boot now keeps me from being able to select the OS i want to boot into. i have a live cd (friend said i would need to fix thats y i mention it) any idea on how to fix the problem?

---

### Post by RuarriS on 2006-11-15
you'll have to reinstall grub from the live cd. 

when you install windows after linux, windows copies over grub with its own bootloader/strapper/whatever

---

### Post by TheGreenMutt on 2006-11-15
sence i don't really know how to do that and wont have another computer avaliable while try i do it can someone tell me how to do that?

---

### Post by mayonaise15 on 2006-11-15
check out [this]("http://www.ubuntuforums.org/showthread.php?t=293558&highlight=reinstall+grub") post, hope it helps.

---

### Post by bulldog on 2006-11-16
Just follow this steps,
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next commands. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Finally exit the grub shell
```
quit
```
That is it. Grub will be installed to the mbr.

---

### Post by TheGreenMutt on 2006-11-17
bulldog i followed your diretions exactly i turned off the computer and turned back on after it got past the dell start screen it just freezes on a blank screen with a curser in the upper left corner i reinserted the live disk restarted ubuntu live redid your insturtions and then tried again same proplem came up now i don't even have acess to windows which i need for school so any quick help would be apreciated

---

### Post by chocbar31 on 2006-11-17
Try Super Grub from the Ultimate Boot CD: 

[http://www.ultimatebootcd.com/download.html]("http://www.ultimatebootcd.com/download.html")

It will automatically find your partitions and re-install grub to the boot partition. There is no need to guess which partitions are which. Super Grub takes out all the guess work. 

It worked perfectly for me. Or you can dig in and locate the boot partition to manually install grub as stated above.

---


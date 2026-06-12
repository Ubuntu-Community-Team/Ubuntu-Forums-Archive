---
title: "Removing Items From GRUB Menu"
date: 2007-08-29
forum: General Help
---

### Post by kh1116 on 2007-08-29
how do i remove items from the grub menu?
ex: i have 2 versions of ubuntu, i only want one.

also, how do i change the time you have to pick an os?

thanks kevin

---

### Post by divague on 2007-08-29
You have to edit the /boot/grub/maneu.lst at the end of the file are listed the operating systems

---

### Post by forestpixie on 2007-08-29
in the same file you can change the timeout
> 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

asa you can see I have 2 secs

to comment out lines you don't want to see use #

and the file yopu need to edit is  /boot/grub/menu.lst

---

### Post by kh1116 on 2007-08-29
ok alls good, thanks!

---

### Post by TheExplorer on 2007-08-29
Actually, the file is /boot/grub/menu.lst
Fire up console and type
> sudo gedit /boot/grub/menu.lst
Then enter your admin pass when asked.

At the end of the file are all your OSes you see at bootup.

Find the following lines
> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

This sets the timeuot to pick an OS.

---

### Post by aJayRoo on 2007-08-29
Before editing the grub menu file remember to back it up:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```
that way you can always recover if you make a mistake. Then open the menu file with a text editor:
```
gksudo gedit /boot/grub/menu.lst
```
(it will ask for your password since this is a system configuration file) and look for the part that looks like this:
```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1
```
and change the number after 'howmany' to how many kernel versions you would like the menu to display. Don't remove the '#' in front either it needs to be there. This method ensures the most recent kernel(s) is displayed in the grub menu. Some people advise that 'howmany' is not set to one in case a kernel upgrade is broken somehow and you are unable to boot an older kernel, but the decision is yours.

---


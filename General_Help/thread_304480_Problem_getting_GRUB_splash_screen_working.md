---
title: "Problem getting GRUB splash screen working"
date: 2006-11-21
forum: General Help
---

### Post by Antarctica on 2006-11-21
Hey I followed the guide to enable a GRUB splash screen at [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up) and after rebooting, I get an error that it cannot display the GRUB splash screen.  This problem also occurred in Ubuntu 6.06 Dapper Drake.  Can someone help me?  I had the same problem when I was running Dapper Drake also.  The instructions to enable the GRUB splash screen are displayed below:

> 
** How to display Splash Image for GRUB menu on boot-up**

[LIST]Read [#General Notes]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#General_Notes")[/LIST]
    *e.g. Assumed that hd0,1 is the location of Ubuntu boot partition*

```
wget -c http://easylinux.info/uploads/ubuntu.xpm.gz
chmod 644 ubuntu.xpm.gz
sudo mkdir /boot/grub/images
sudo cp ubuntu.xpm.gz /boot/grub/images/
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```
[LIST]Find this section[/LIST]
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#      grub-install(8), grub-floppy(8),
#      grub-md5-crypt, /usr/share/doc/grub
#      and /usr/share/doc/grub-doc/.
...
```
[LIST]Add the following line below it[/LIST]
```
splashimage (hd0,1)/boot/grub/images/ubuntu.xpm.gz
```

*NOTE: If you have seperate boot partition use this line: splashimage (hd0,1)/grub/images/ubuntu.xpm.gz*

[LIST]Save the edited file[/LIST]



---

### Post by Antarctica on 2006-11-21
How do I find out if I'm not using hd(0,1) or not?  I didn't custom install Ubuntu in any way.  I let the installer format my entire hard drive before installing.

---

### Post by Jimmy_r on 2006-11-22
> How do I find out if I'm not using hd(0,1) or not? I didn't custom install Ubuntu in any way. I let the installer format my entire hard drive before installing.

Your /boot/grub/menu.lst has a line in it that says groot=(hdx,y)

For example, my line says:

# groot=(hd0,1)

There you have it.

Btw, you may want to check my signature...SUM supports management of grub splash.

---

### Post by Antarctica on 2006-11-22
I'm going to try hd(0,0) instead of hd(0,1) and see if that works.  I looked in /boot/grub/menu.lst and didn't find anything pertaining to hd(0,1) but hd(0,0).

---

### Post by Antarctica on 2006-11-22
Okay, I switched hd(0,1) to hd(0,0) and I was kinda able to see the grub splash screen.  The trouble is that the background only occurs and shows behind the words "Press ESC to enter the menu," and it has a countdown timer.  The rest of the screen is black.  What do I do next?

---

### Post by Antarctica on 2006-11-22
Hey I kinda got the splash screen working.  in /boot/grub/menu.lst, I disabled the hidden menu option (#hiddenmenu).  I think I'm starting to understand how modifying grub works now. :)

---

### Post by Antarctica on 2006-11-22
... or not.  It turns out that when grub starts, if I press a key, it will stay at the list of boot options.  Well, when I press up and down, I can't see the highlighted entry.  It just doesn't highlight.  What can I do to get it highlighted?  Thanks.

---

### Post by Antarctica on 2006-11-22
Yay I fixed it.  At least I've got it working now.

---

### Post by bobstro on 2006-11-28
> **Antarctica said:**
> Yay I fixed it.  At least I've got it working now.

Yes, but HOW? I've got that exact same issue.

Thanks,

- Bob

---

### Post by SteveJM on 2006-12-02
Hi, first post in this forum and new to Ubuntu. Previously used Suse 10.1 so having loaded Ubuntu thought Grub looked pretty ugly...but I really like the rest of Ubuntu.

I had the same issue having followed the same info in the guide and still no joy.  As I am duel booting with winxp, the hd0,1 setting was not correct for me.

Following the later advice given, enter:-

gksudo gedit /boot/grub/menu.lst

look for #groot.... and it tells you the setting to use. [ctrl} + F opens the find box.

Thanks Jimmy_r.

Antarctica, did you finally follow this advice?  It solved the problem for me.

---


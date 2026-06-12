---
title: "Grub Boot Problem"
date: 2008-05-08
forum: General Help
---

### Post by plague27 on 2008-05-08
Hi Guys,

I am kind of new to using ubuntu but have had it to play with for awhile. I am using 8.10 (installed last night and like it somewhat) and have had a problem for awhile where in order to get ubuntu to boot at the grub startup, I have to press "e" on the ubuntu item and delete the "boot <some hdd setting here>" entry in order for ubuntu to boot. I have to do this every time i boot, is there a way to permanently set this?

---

### Post by tamoneya on 2008-05-08
you can permenantly edit those settings by editting your /boot/grub/menu.lst file.

---

### Post by Afif K fiska on 2008-05-08
Maybe you can install a new grub loader, please refer to this :

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Hope this help

---

### Post by paes on 2009-09-28
guys i got a problem 
my system has 2 HDD
in hd1 i installed xp ie (hd1,0)
then few days back i installed RED hat sever 5 in (hd0,8)
then i installed ubuntu 9.04 in (hd0,7)
 so at that time in the grub menu i got only redhat list and  windows,no ubuntu
when i installed ubuntu windows  boot went wrong also 

after that to boot ubuntu
i put the live cd and
i did these steps 
sudo grub
find /boot/grub/stage1
root (hd0,7)
setup(hd0,7)
reboot...
and i dont have seperate boot partion 

My problem is now i  have only ubuntu
How can i add red had and windows in my grub menu 
 can any body help me....................................!!!!

---


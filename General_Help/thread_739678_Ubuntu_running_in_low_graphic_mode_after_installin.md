---
title: "Ubuntu running in low graphic mode after installing VirtualBox"
date: 2008-03-30
forum: General Help
---

### Post by jonask on 2008-03-30
Help Help!
I have ubuntu 7.10 on my HP dv9700t laptop. I have used virtualbox ose with windows xp. It was working fine, However to get the usb ports to work I installed the virtualbox PUEL edition. I got the usb ports to work, but the screen started to freeze. When I restarted the computer I got the message ubuntu is running in low graphic mode. I have removed virtual box, but I cant get out of the low graphic mode. 
When I choose: system,administration,restricted driver manager to enable the nvdia drivers I get the message: 

You need to install the package linux-restricted-modules-2.6.22-14-server
for this program to work.

I have reinstalled this package in the package manager, but I still get the same message. 

Sombody have a idea to how I get out of the low graphic mode.

All suggestions would really be appreciated.

thank you very much for the help

jonas

---

### Post by wolfen69 on 2008-03-30
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```
then reset x with ctrl-alt-backspace

---

### Post by jonask on 2008-03-30
Thanks you for the suggestion. I forgot to say I am completely new in linux. 

I got following result by entering the command;

jonas@jonas-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080329210446

Then I tried ctrl alt backspace and login again, but graphic mode is still low

Am I missing something perhaps?

---

### Post by jonask on 2008-03-30
No I restarted my computer and the graphic is normal again. Thank you so much for the quick response!!!

This was great

---

### Post by jonask on 2008-03-30
Hi again.
I can still not access the restricted drivers manager (get message):
****************************************
You need to install the package

linux-restricted-modules-2.6.22-14-server

for this program to work.
****************************************

When I go to "System, Preferences, Appearence, Visual Effects" I am only able to choose none effects.

Do somebody have a suggestion?


Thank you very much

---


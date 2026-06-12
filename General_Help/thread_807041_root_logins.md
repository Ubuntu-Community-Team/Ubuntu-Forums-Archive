---
title: "root logins"
date: 2008-05-25
forum: General Help
---

### Post by zivxx on 2008-05-25
hey everyone, i want to change some stuff around my /usr file but i can't because there are no root logins here, i used ubuntu few months ago and i remember managing it after all..but i can't remember how..anyway got an idea?

---

### Post by pbpersson on 2008-05-25
> **zivxx said:**
> hey everyone, i want to change some stuff around my /usr file but i can't because there are no root logins here, i used ubuntu few months ago and i remember managing it after all..but i can't remember how..anyway got an idea?

Anytime you want to perform some function in Ubuntu that requires root access you can use the sudo command.

For instance, the following command would allow you to edit your xorg.conf file and save your changes:

```
sudo gedit /etc/X11/xorg.conf
```

When it asks for a password just use the same one you use to logon to Ubuntu

---

### Post by HalPomeranz on 2008-05-25
> **pbpersson said:**
> Anytime you want to perform some function in Ubuntu that requires root access you can use the sudo command.

And if you need an interactive root shell, you can always do this:

```
sudo su -
```

---

### Post by zivxx on 2008-05-25
how can editing my xorg.conf can help me with deleting/creating file in /usr?


Edit:
i know how to use root access in terminal, but can i delete or create folders from the terminal?

---

### Post by robertchahine on 2008-05-25
try this 
```

gksudo nautilus 
```

then you can delete move or anything you want

---

### Post by zivxx on 2008-05-25
i got the following error:

root@ziv-laptop:~# gksudo nautilus

(gksudo:11066): Gtk-WARNING **: cannot open display:

---

### Post by robertchahine on 2008-05-25
i think first you should exit the root mode from the terminal then try that

---

### Post by zivxx on 2008-05-25
thank you very much! it works :)

---

### Post by robertchahine on 2008-05-25
glad to hear that ;)

---

### Post by lovebeijgo on 2008-05-25
Wise man have their mouths in their hearts, fools have their hearts in their mouths.-------------------------Our [wow power leveling](http://www.wow-powerleveling.org) website offer Fast and Secure wow powerleveling service. [WoW Power Leveling](http://www.xowow.com) 60-70, Cheap [wow power leveling](http://www.powerlevelingweb.com) 1-70. The Professional [WoW Power Leveling](http://www.wowgoldweb.com)! Powerlevel [WoW Power Leveling](http://www.igsstar.com) now. WOrld of warcraft Power Leveling bloom of true love associated with this time of year!

---

### Post by robertchahine on 2008-05-25
glad to hear that ;)

---

### Post by pixel :-) on 2008-05-25
wait a minute what naughty things are you going to do in /usr?Don't complain if you broke something.

---


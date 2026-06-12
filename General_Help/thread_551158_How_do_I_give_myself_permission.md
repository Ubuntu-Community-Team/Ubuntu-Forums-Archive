---
title: "How do I give myself permission?"
date: 2007-09-14
forum: General Help
---

### Post by DocHolliday2006 on 2007-09-14
Hi. New to Ubuntu. My resolution is messed up. It doesn't offer me high enough options. I found an explanation for editing xorg.conf to add the resolution I want, but when I go to save it, it says I don't have permission. How do I give myself permission? Thanks

-Andrew

---

### Post by bodhi.zazen on 2007-09-14
sudo : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) # for graphical apps

Also try :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will allow you to select a differnet resolution (I hope). If that command fails, then manually edit.

You can :

```
gksu gedit /etc/X11/xorg.conf
``` for a graphical edit.

```
sudo nano -Bw /etc/X11/xorg.conf
``` for a command line (terminal) edit # helps to recover from when you manually edit xorg.conf and X fails :twisted:

Oh, MAKE A BACKUP B4 YOU EDIT

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_working_copy

---

### Post by Celegorm on 2007-09-14
Copy and paste this into the command line ```
sudo nano /etc/X11/xorg.conf
``` 'sudo' makes a command execute with root priveleges, it will ask for your password, but will not echo it to the screen, just type it and press enter. Use ctrl-x to exit when you are done editing the file. Oh, and make a backup copy of the file if you haven't already: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` This allows for easy restoration if you mess up xorg somehow. ('sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf' to restore the file from the backup)

---

### Post by rivalarrival on 2007-09-14
press alt+f2 and type this in the box:
```
gksu gedit /etc/X11/xorg.conf
```

It will ask you for your password then open the file as if you were "root" - make your changes and you should be able to save it.

---


---
title: "Server EditionUbuntu 7.04 ,Desktop Edition Ubuntu 7.04"
date: 2007-07-31
forum: General Help
---

### Post by cancee on 2007-07-31
**Hi Guys,**

I need your help to know that these 2 Version Desktop and Server how We install In Graphical Interface mode or these Both are Text mode version ?

I like Ubantu very much But I like Only GUI Mode only ***Graphical Interface ***so please help me How can I find Server and Workstation on [COLOR="Red"]Graphical Interface mode[/COLOR].

Thx
Rockey:confused:

---

### Post by aysiu on 2007-07-31
Server is text-only.

Desktop is graphical interface.

---

### Post by pofigster on 2007-07-31
You CAN install a GUI for the server edition (instructions are in the forum) but it's complicated and doesn't provide 100% support.  You're better off going with the desktop edition just installing a LAMP server and chmoding the folders for read access.

Oh, and your poll is confusing as all get out.

---

### Post by cancee on 2007-08-01
Hi Guys,

Well I think Batter we leave now Server Edition because in TEXT mode it,s looking so OLD ,Well I am Anxiously waiting when Ubuntu Eng Release GUI  Server.
But what you guys advise for High class performance in Cache and a professional server what I may use in GUI .
Thx

---

### Post by aysiu on 2007-08-01
Well, the server is in text mode, but if you want to install a GUI on top of that, you can do that quite easily, just (*gasp*) type ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---


---
title: "Run levels"
date: 2008-06-26
forum: General Help
---

### Post by cjazinski on 2008-06-26
Hello all,

First let me give you a little bit about my setup. I have an old box running an AMD 2500+ i have the latest ubuntu installed. (i should've installed the server version.. but oh well) I have it just sitting in a corner of the room, i'm using it to host my website. It works great, but i know that a gui is starting on the box and it doesn't really need to i am just thinking in the terms of ressources that it is a waste. do the standard runlevels work, exampe 'sudo init 3' i can issue the command then watch top and init is doing something, but i have come across a blog post stating that ubuntu uses upstart or something of that nature. Thanks for the help

---

### Post by rubicon on 2008-06-26
You also should've came across another article that Debian (and therefore Ubuntu) runs usually on runlevel 2: [http://en.wikipedia.org/wiki/Runlevel#Debian_Linux](http://en.wikipedia.org/wiki/Runlevel#Debian_Linux). Upstart supports different runlevels, but changing levels won't help in this situation (see the article).

If I were you, I'd just disable gdm (or kdm or slim) so X would not start. I'm not 100% sure, but it is worth trying anyway.

---

### Post by CADutch on 2008-06-26
In order to disable GDM from starting I went to /etc/rc.d (or rc2) and renamed S30gdm to K70gdm). Google K70gdm and you will find instruction on how to do this. 
Basically S means Start and K means Kill the process during init. The number 30 and 70 refers to the sequence number.

Good luck, cadutch / pato

---

### Post by CADutch on 2008-06-26
To be more complete:

Rename the file /etc/rc2.d/S30gdm to /etc/rc2.d/K70gdm like so: 
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K70gdm

---

### Post by CADutch on 2008-06-27
p.p.s. You also can try:

Edit /boot/grub/menu.lst and remove quiet splash from the 1st kernel line.
This will give you an idea of what is happening during boot.

you can add vga=791 to the end of the same kernel line to get a better resolution on you screen.

---


---
title: "Ubuntu 12.10 Login Screen"
date: 2013-01-12
forum: General Help
---

### Post by tonycm1 on 2013-01-12
I installed Lubuntu 12.10 through WUBI (since it's my work laptop and I didn't want to mess around with partitions) and then installed Ubuntu-Desktop afterwards.

I've managed to switch the splash screens from the standard Lubuntu ones to Ubuntu but can't figure out how to change the login screen from the default Lubuntu login screen (what I'm currently seeing) to the default Ubuntu one that I like.

Ideas? I've tried poking around on the web for a good hour and can't seem to get a workable solution...

---

### Post by AstroLlama on 2013-01-12
Well, the "default" login screen would be the gnome one. but i put it in quotes because it's default for the standard Ubuntu install. as you use Lubuntu, the default is different. 

you have to install the 'gdm' package.

---

### Post by tonycm1 on 2013-01-12
> **AstroLlama said:**
> Well, the "default" login screen would be the gnome one. but i put it in quotes because it's default for the standard Ubuntu install. as you use Lubuntu, the default is different. 

you have to install the 'gdm' package.

Are you sure that it's the 'gdm' package? I thought the "default" 12.10 Ubuntu login screen 'lightdm'?

Link: [http://en.wikipedia.org/wiki/LightDM]("http://en.wikipedia.org/wiki/LightDM")


Unfortunately, because I installed Lubuntu before Ubuntu-desktop, I'm stuck with the following login screen:

Link: [http://launchintolinux.files.wordpress.com/2012/07/lubuntu-12-04-login.jpg]("http://launchintolinux.files.wordpress.com/2012/07/lubuntu-12-04-login.jpg")

I'd just like to know how to have my login screen be the 'default' one that comes with Ubuntu 12.10.

---

### Post by tonycm1 on 2013-01-12
Looking into this a little further, it looks like what I really want is the "unity-greeter". I double checked in synaptic package manager that it is in fact installed.

How do I set it to be the default?

---

### Post by tonycm1 on 2013-01-12
This was a lot simpler than I thought to solve.

Installed unity-greeter:
sudo apt-get install unity-greeter

Then edited /etc/lightdm/lightdm.conf and set greeter-session=unity-greeter (was previously set to lightdm-gtk-greeter).

Rebooted and it works :)

---

### Post by AstroLlama on 2013-01-13
glad you got it straightened out! :)

---


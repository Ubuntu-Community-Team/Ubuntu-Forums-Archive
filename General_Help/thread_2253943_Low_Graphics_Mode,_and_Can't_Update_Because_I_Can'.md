---
title: "Low Graphics Mode, and Can't Update Because I Can't Connect to Internet"
date: 2014-11-23
forum: General Help
---

### Post by sean72 on 2014-11-23
Hello,

I'm new to Ubuntu, and I tried to install GNOME, but it was causing graphical problems to my desktop. So I looked up how to use the terminal to uninstall it. Then it said I had to reboot, and when I did, it said that Ubuntu is running in low graphics mode. I've looked up countless tutorials of how to fix this, but all of them require you to update Ubuntu and re download your drivers. I can't do that because I can't connect to the internet. Ubuntu made me type my internet password every time I tried to log in, and now when I try to update, it just gives me an error.

What do I do?

---

### Post by pqwoerituytrueiwoq on 2014-11-23
which driver do you need,what command could you need to run?
it may still be in the cache, if it is you can run the command and it will not even try to connect to the internet
if you tell us what release and what packages you need we can link to them and you can install them via usb

---

### Post by sean72 on 2014-11-23
My release is Ubuntu 14.10, I need the Nvidia GeForce GTX 765M drivers, and I had basically just installed the OS a few days ago so I don't really need anything else.

sudo apt-get install nvidia-current[COLOR=#333333][FONT=UbuntuRegular] - More stable/tested version [/FONT][/COLOR]sudo apt-get install nvidia-current-updates[COLOR=#333333][FONT=UbuntuRegular] - More up-to-date version

Those are the commands I would need to run to download the drivers, from here: [/FONT][/COLOR]http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error

---

### Post by pqwoerituytrueiwoq on 2014-11-23
64bit or 32bit?
that driver does not prevent you from connecting to the internet
is network manager installed?
```
apt-cache policy network-manager
```

---


---
title: "Installing ATI drivers..."
date: 2006-11-29
forum: General Help
---

### Post by Infiltraitor on 2006-11-29
I just got my internet for ubuntu working so I am downloading all the stuff I need. I think I need an ATI driver for my 9800 pro... when I go to the download site I see .bin and .rpm files, and I don't know what they are. Can somebody give me a link to a guide or something similar?

---

### Post by telovoyagarcar on 2006-11-29
I followed these steps a week ago...


First open and edit the xorg.conf file:

sudo gedit /etc/X11/xorg.conf

and add these lines at the end of the file:

Section "Extensions"
Option "Composite" "Disable"
EndSection


Then install the driver:

Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!

You can check this by looking in the sources.list file where these 2 lines need to be without the "#" at the begining:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

Then use these commands... just copy and paste like i did:

sudo apt-get update

sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed

sudo apt-get install xorg-driver-fglrx

sudo depmod -a

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv


And finally Reboot your system:

sudo shutdown -r now

That worked for my x800xl

You need to have the machine connected to internet or you won't get the packages..

Good luck.. i hope this helps

---

### Post by Infiltraitor on 2006-11-29
Um.... which driver package?

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

the first one?

---

### Post by Infiltraitor on 2006-11-29
nevermind, it worked!

---

### Post by telovoyagarcar on 2006-11-29
you don't have to download anything 

when you use this command "sudo apt-get install xorg-driver-fglrx" you are downloading and installing the driver... just follow the steps in the order i posted before..

---

### Post by beldugo on 2006-11-30
hello.. i was looking on how to do this too. i just follow your steps and it work except that i have another problem now. when i open a new window i have to scroll through it for it to show the icon.

---


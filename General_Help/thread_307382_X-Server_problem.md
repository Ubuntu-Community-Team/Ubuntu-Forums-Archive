---
title: "X-Server problem"
date: 2006-11-26
forum: General Help
---

### Post by Den-J on 2006-11-26
Hello,

I installed the latest (non beta!) NVIDIA driver 9629 for Ubuntu.
I followed all instructions, I have installed following packs..
linux-headers (version 2.6.17-0)
xorg-dev (version 1:7.1.1ubuntu6)
build-essential (version 11.3)
after that i pressed alt+strg+F1 and stopped gdm
started the installation
the installer created the missing kernel and finished sucessfuly..
every time i restart my computer an error occures with the messeger
"Error: API mismatch: the NVIDIA kernel has the version 1.0-7184, but the X module has the version 1.0-9629
I can only solve this problem with the command
"sudo rmmod nvidia && sudo modprobe nvidia"
a reconfiguration of the xserver does not help !
please help me.. i've installed ubuntu in 2 days over 14 times til I found out that it is possible to boot with this command "sudo rmmod nvidia && sudo modprobe nvidia"
but still, what do I do wrong ??

EDIT: this problem comes on every reboot !!

---

### Post by taurus on 2006-11-26
How did you install the nvidia driver anyway?

Here's an easy way...

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Radiera on 2006-11-26
you need to uninstall the restricted modules.

---

### Post by Den-J on 2006-11-26
after I uninstall it, should I reinstall the NVIDIA driver ??

---

### Post by Den-J on 2006-11-26
and i have installed now following packs.. hope this wasn't wrong..

linux-generic
linux-restricted-modules-generic
linux-restricted-modules-2.6.17.-10-generic
linux-restricted-modules-common

---

### Post by Den-J on 2006-11-26
well...
after I uninstalled the modules I couldnt boot
I had to reinstall ubuntu
someone an idea ?

---

### Post by dexter on 2006-11-26
Why do you want a manual installation of the driver ? Just get it from the repositories.

---

### Post by Den-J on 2006-11-26
repositories??
what do you mean by that?
sry im new in ubuntu

---

### Post by taurus on 2006-11-26
```
sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```

---

### Post by Den-J on 2006-11-26
ok thx...
i have al last question left...
do I have to install these packs
linux-headers
xorg-dev
build-essential
and deinstall the restricted modules?
or can i keep ubuntu like it is and only use this code :confused:

---

### Post by taurus on 2006-11-26
Just run those three lines and if the second line needs something else, it will either tell you or it will install it for you.  On the other hand, it isn't a bad idea to install build-essential package since you need it if you want to build something from source.  Another one is handy to have is called alien...

```
sudo aptitude install build-essential alien
```

---

### Post by Den-J on 2006-11-26
for what is this package "alien"
sry im so interessted in ubuntu/linux
it changed my whole computer experience and it works sure easier and faster that win xp 
wow :)

---

### Post by taurus on 2006-11-26
Alien (not from another planet) is a program to convert .rpm to .deb.  Let's say you want to install a program and it is only available either in .rpm format or a source, you can either use alien to convert it to .deb and install it on your Ubuntu machine or you can build it from source.  Of course, don't install it if you don't think you need it but if you need it later, then install it.  Either way, it's all good.

---


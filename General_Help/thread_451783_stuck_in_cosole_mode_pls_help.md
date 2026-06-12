---
title: "stuck in cosole mode pls help"
date: 2007-05-22
forum: General Help
---

### Post by midwestkid on 2007-05-22
hi im new with the whole ubuntu thing and i did a netinstall with out using and cd so far i have had no probs untill i came into the console part of ubunto, i have no idea on how to proced to the desk top from this ponit i am able tologin while in console mode though pl help :(    also my version of ubuntu is 6.10

---

### Post by mills on 2007-05-22
do you have a graphical environment installed?
if your connected to the net try these commands

```
sudo aptitude update
```

```
sudo aptitude install ubuntu-desktop
```

```
sudo /etc/init.d/gdm start
```

---

### Post by midwestkid on 2007-05-22
didevrything ubuntu load screen apeares but then there is and error message sayin that it failedtostart x server   
my graphical interface the error message is

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor

alsoit tellsmethat the x server isdisabled and to restart it when its configured correctly

---

### Post by mills on 2007-05-22
try this

```
sudo dpkg-reconfigure xserver-xorg
```

it's basically a terminal wizard that will fix your xserver-xorg if your not sure on any of the questions pick the defualt

ps sorry it took a while to get back, lost internet connection

---

### Post by RedSquirrel on 2007-05-22
> **midwestkid said:**
> hi im new with the whole ubuntu thing and i did a netinstall with out using and cd so far i have had no probs untill i came into the console part of ubunto, i have no idea on how to proced to the desk top from this ponit i am able tologin while in console mode though pl help :(    also my version of ubuntu is 6.10

In the future, you can follow this guide for using the net installer:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by midwestkid on 2007-05-22
ty for the help i really apreciate it evrything is working fine:p

---


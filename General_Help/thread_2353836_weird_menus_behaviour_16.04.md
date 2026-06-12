---
title: "weird menus behaviour 16.04"
date: 2017-02-25
forum: General Help
---

### Post by mhaylock on 2017-02-25
Hi,

Appreciate some help. Any drop down menu will not show in Ubuntu whether it be via browser or other. Some examples;

1. If i click the cog on the top right i have to hold the left mouse for the menu to show 
2. If i click volume on the top bar i can move the level but it moves itself to max
3. if i move the mouse to the top of the screen near volume the volume level pops up
4. When using chrome if i hit a drop down on a web page the menu does not display
5. In Firefox the @ symbol cause the browser to do a back to the previous page

This seemed to happen after when of the regular updates in the last two weeks. Its very frustrating and makes it almost unusable.

Cheers

Matt

---

### Post by ajgreeny on 2017-02-25
Tell us a lot more about your hardware, and the OS version and we may have some more chance to help you.
As you have told us nothing about either we are not able to assist.

---

### Post by mhaylock on 2017-02-26
Zotac Z170N motherboard socket 1151, i5-6400 processor, 8GB DDR4, Nvidia GeForce GT 730

lsb_release -a
LSB Version:	core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:cxx-4.1-amd64:cxx-4.1-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:desktop-4.1-amd64:desktop-4.1-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:graphics-4.1-amd64:graphics-4.1-noarch:languages-3.2-amd64:languages-3.2-noarch:languages-4.0-amd64:languages-4.0-noarch:languages-4.1-amd64:languages-4.1-noarch:multimedia-3.2-amd64:multimedia-3.2-noarch:multimedia-4.0-amd64:multimedia-4.0-noarch:multimedia-4.1-amd64:multimedia-4.1-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:qt4-3.1-amd64:qt4-3.1-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

Thanks

Matt

---

### Post by mhaylock on 2017-02-27
An update to 16.10 doesn't resolve the issues,

other things that don't work anymore are;

screen doesn't time out
can't click different tabs in chrome
hovering over open apps in the dock causes the screen to jump around

any suggestions appreciated, perhaps i need to re-install the window manager, or delete users desktop configuration?

---

### Post by ajgreeny on 2017-02-27
Where did all that text in the second line come from?
It's not what I expect from **lsb_release -a**
```
lsb_release -a
LSB Version:	core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:cxx-4.1-amd64:cxx-4.1-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:desktop-4.1-amd64:desktop-4.1-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:graphics-4.1-amd64:graphics-4.1-noarch:languages-3.2-amd64:languages-3.2-noarch:languages-4.0-amd64:languages-4.0-noarch:languages-4.1-amd64:languages-4.1-noarch:multimedia-3.2-amd64:multimedia-3.2-noarch:multimedia-4.0-amd64:multimedia-4.0-noarch:multimedia-4.1-amd64:multimedia-4.1-noarchrinting-9.20160110ubuntu0.2-amd64rinting-9.20160110ubuntu0.2-noarch:qt4-3.1-amd64:qt4-3.1-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
```
This is what I see
```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
```

---

### Post by mhaylock on 2017-03-06
i have done a rebuild (long overdue), back to Ubuntu LTS 16.04

i have discovered that the issue is present after the rebuild. The issue goes away if i turn off my wireless mouse (Logitech M505) and plug in a wired USB one. The mouse worked perfectly previously, either the mouse is faulty or an update has caused this issue. Any help would be appreciated.

Matt

---


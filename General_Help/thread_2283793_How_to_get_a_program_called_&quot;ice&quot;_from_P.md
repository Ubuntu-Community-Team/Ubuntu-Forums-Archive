---
title: "How to get a program called &quot;ice&quot; from Peppermint OS 6"
date: 2015-06-24
forum: General Help
---

### Post by Cody_Tellor on 2015-06-24
Hello,
My laptop is running Peppermint OS 6 and only one thing i like about it that you can make a web app and the program is called "ice" I'm running Ubuntu (istall XFCE4 on top of it) and i want take program on my system, here what ice is all about: "[COLOR=#333333][FONT=Verdana]Peppermint's handy cloud & web application management tool 'Ice' continues to put web applications on an equal footing with locally installed apps by allowing them easy integration into system menus, and delivery to the desktop via SSB's so they mimic locally installed applications." (from [/FONT][/COLOR]http://peppermintos.com/) how can i put that on ubuntu

---

### Post by QDR06VV9 on 2015-06-24
[h=2]Packages for Ubuntu 14.04 (Trusty Tahr)[/h]                           *Note: The Ubuntu packaging is experimental and subject to change in             the next Ice release, depending on user feedback.*             
                           Follow the instructions below to install Ice.             
From here [https://zeroc.com/download.html#linux](https://zeroc.com/download.html#linux)
Happy Iceing

---

### Post by mark-pcnetspec on 2015-06-25
That's not the "Ice" the OP is referring to

This is:
[https://launchpad.net/~peppermintos/+archive/ubuntu/p6-release/+files/ice_5.0.1_all.deb](https://launchpad.net/~peppermintos/+archive/ubuntu/p6-release/+files/ice_5.0.1_all.deb)

it's just a small python script so should run perfectly well in Ubuntu, but I have no idea how closely Ubuntu stick to the freedesktop.org standard spec for .desktop file menu entries .. so whether the links will display in the Ubuntu menus properly might be another matter .. can't hurt to try though ;)

Remember, to use Ice you require either Chrome or Chromium installed .. it will NOT create SSB's for Firefox (since Mozilla dropped the Prism project)

So to install in Ubuntu .. open a terminal and run these commands in sequence:
```
cd ~
```
then
```
wget [https://launchpad.net/~peppermintos/+archive/ubuntu/p6-release/+files/ice_5.0.1_all.deb]("https://launchpad.net/%7Epeppermintos/+archive/ubuntu/p6-release/+files/ice_5.0.1_all.deb")
```
then
```
sudo dpkg -i [ice_5.0.1_all.deb]("https://launchpad.net/%7Epeppermintos/+archive/ubuntu/p6-release/+files/ice_5.0.1_all.deb")
```

---


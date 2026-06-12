---
title: "Unable to change Desktop Wallpaper. Menu sends me to System Settings."
date: 2013-06-22
forum: General Help
---

### Post by sysmic on 2013-06-22
Hey, about four days ago I changed my wallpaper to the background that you get when you first install windows as a joke to confuse my friends, but starting two days ago, I was unable to change it. WHenever I right clicked on the desktop and clicked 'change desktop background,' I would get sent to the System Settings menu. I had no appearance button either. If anyone can help, I'd be grateful.

I'm on Ubuntu 12.10 x64 with Intel HD 3000 Graphics. When I first installed Ubuntu (About an hour after recieving my laptop) I tried to install the proprietary AMD Radeon graphics drivers (both fglrx and AMD's versions) and screwed up the system (Which I was able to fix after seven hours of nonstop work). I have been slightly late with receiving system upgrades (for example, I didn't get any option to upgrade to 12.10 until 13.04-13.10 was released). Would any of these cause my background to stop working?

---

### Post by dino99 on 2013-06-23
[http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/](http://www.unixmen.com/how-to-upgrade-from-ubuntu-1004-1010-1104-to-ubuntu-1110-oneiric-ocelot-desktop-a-server/)

you can change the background from the System Settings : click on the image to get the available background list, select one and validate. You need using dconf to get / set more appearance details.

---

### Post by sysmic on 2013-06-23
I don't think I have that option. I'm looking in dconf and I don't have anything for it either. And I don't know what image your talking about.

EDIT: I found a fix. I somehow overlooked an asnwer in my search yesterday. Somehow the package gnome-control-center-unity was removed from my system. Just reinstalled it and the appearance section works again.

---


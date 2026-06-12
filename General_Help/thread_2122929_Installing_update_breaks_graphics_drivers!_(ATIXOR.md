---
title: "Installing update breaks graphics drivers! (ATI/XORG)"
date: 2013-03-06
forum: General Help
---

### Post by Cam! on 2013-03-06
Whenever I install 12.10, I'm prompted to install 280 updates. Whenever I install them and reboot, I get this glitched-up purple/orange screen which obviously prevents me from logging in and using the OS. I'm certain that this is a video driver/card issue, but how do I fix it? I have an ATI Radeon HD 6850 (1GB) graphics card. Everything seems to work fine when I don't do any updates, but I really don't want to use "vanilla", unupdated 12.10.

---

### Post by Cam! on 2013-03-06
Whenever I install 12.10, I'm prompted to install 280 updates. Whenever I  install them and reboot, I get this glitched-up purple/orange screen  which obviously prevents me from logging in and using the OS. I'm  certain that this is a video driver/card issue, but how do I fix it? I  have an ATI Radeon HD 6850 (1GB) graphics card. Everything seems to work  fine when I don't do any updates, but I really don't want to use  "vanilla", unupdated 12.10.

I didn't touch ANYTHING regarding drivers. I'm looking at the Additional Drivers pane, and this is what I see: [http://i.imgur.com/nQAKRGH.png](http://i.imgur.com/nQAKRGH.png) I'm using the (what I assume to be) default, open-source drivers.

---

### Post by Cam! on 2013-03-06
Whenever I install 12.10, I'm prompted to install 280 updates. Whenever I   install them and reboot, I get this glitched-up purple/orange screen   which obviously prevents me from logging in and using the OS. I'm   certain that this is a video driver/card issue, but how do I fix it? I   have an ATI Radeon HD 6850 (1GB) graphics card. Everything seems to work   fine when I don't do any updates, but I really don't want to use   "vanilla", unupdated 12.10.

I didn't touch ANYTHING regarding drivers. I'm looking at the Additional Drivers pane, and this is what I see: [http://i.imgur.com/nQAKRGH.png](http://i.imgur.com/nQAKRGH.png) I'm using the (what I assume to be) default, open-source drivers.

---

### Post by Cheesemill on 2013-03-06
Try installing the fglrx graphics driver and rebooting before you install the updates, this *may* fix your problem.

---

### Post by Cam! on 2013-03-06
I switched to the proprietary, but when I logged in, Unity didn't appear at all.

---

### Post by mörgæs on 2013-03-06
Please don't double-post.
Merged.

---

### Post by coffeecat on 2013-03-08
Merged another duplicate. Please do not cross-post.

---

### Post by black veils on 2013-03-08
try the previous kernel from grub boot loader, if it works ok, then use [grub customizer]("https://launchpad.net/~danielrichter2007/+archive/grub-customizer") to choose the previous kernel as default.

---


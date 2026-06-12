---
title: "Stuck in low graphics mode"
date: 2008-05-06
forum: General Help
---

### Post by OsakaWilson on 2008-05-06
I'm running 64-bit Hardy with an nvidia graphics card. Everything was going fine. However I am now stuck in low graphics mode. Yesterday, I changed two things in my system. First, I configured a second monitor and that seemed to work fine. After that I went to Synaptic and downloaded a bunch of video editing stuff, Avidemux, Ubuntu Studio/Audio/Graphics, etc. It said it would take 10 or so hours, and I couldn't leave the computer on, so I had to stop the installation after a few hours. I don't know where it went wrong, but when I turned the computer on this morning, it said it couldn't find my graphics card and put me in low graphics mode. Any ideas??

---

### Post by macaholic on 2008-05-06
It might ahve uninstalled the driver for some reason. Check if it is still installed.

---

### Post by OsakaWilson on 2008-05-06
I did the following and it worked.


Code:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

Code:

sudo dpkg-reconfigure -phigh xserver-xorg

Code:

sudo reboot

---

### Post by hgordon on 2008-05-08
Thanks OsakaWilson.  I have a simple Compaq Presario C500 with Intel video at 1280x800 that seemed to get stuck in "low graphics mode" after upgrading to Hardy Heron, and your simple solution fixed my problem as well.

---


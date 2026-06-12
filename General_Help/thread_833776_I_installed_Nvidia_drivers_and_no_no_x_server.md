---
title: "I installed Nvidia drivers and no no x server"
date: 2008-06-18
forum: General Help
---

### Post by Med!c on 2008-06-18
I know this issue is common but I'm new to kubuntu and some of the stuff I've found through research a. Doesn't work. or b. makes no sense. I'm literary fresh out of the box, I installed kubuntu 3 days ago. My problem was that I couldnt change the screen res, and it was on some crazy res where half of the picture would be off my monitor. I was lucky to figure out by adding the widget thing you get an icon on the bar at the buttom and I was able to find my way to the settings. Under display settings I have all the resolutions my monitor can support, but when I select a new one the apply button is grayed out thus i can't apply it. I thought my problem was not having gfx drivers, so I downloaded the latest one off the nvidia site. It took forever to be able to instal that, after some research I figured my way out. I switched to consol mode, typed "sudo apt-get install build-essential linux-headers-$(uname -r), followed by sudo sh /home/[username]/Documents/[nvidia driver filename].run the instal seemed to go fine. I said yes to the 32-bit directories, and yes to reconfig the x server config file so the next time I loaded it, it would take advantage of NVidia stuff. However, when i restarted, x server did no load, I would get a consol login. I styped "startx" in the consol, after logging in through the consol, but it would give me fatal error 11. And I have no clue what to do now.. =( This is such a pain in the ***, I hear alot of great things about linux, and I don't want to let this experience give me the conclusion linux sucks and delete my dual boot to a single vista boot. Hopefully we can get this to work and I can get a real feel of linux.

---

### Post by Med!c on 2008-06-19
bump.

Also I'm using kubuntu 64-bit.

---

### Post by mempman on 2008-06-19
copy and paste your /etc/X11/xorg.conf

Also, just because you installed the new Nvidia driver smoothly doesn't mean that it is loaded when you are issuing the startx command.  To check what drivers are loaded, issue the "lsmod" command.  Now, if this command doesn't return "nvidia" or a similar string, then you will need to load this driver; this can be done by "sudo modprobe -i nvidia"

---


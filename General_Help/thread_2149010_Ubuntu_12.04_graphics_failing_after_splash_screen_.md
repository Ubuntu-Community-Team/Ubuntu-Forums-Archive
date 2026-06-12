---
title: "Ubuntu 12.04 graphics failing after splash screen loads"
date: 2013-05-27
forum: General Help
---

### Post by grkblood13 on 2013-05-27
Hardware: HP ProBook 4730s
GPU: Onboard Intel SandyBridge CPU

About a week ago I was trying to get google-earth to run and it wouldn't so I googled how to fix it and I believe I ended up changing something with the graphics drivers. About a week passes and I finally reboot my computer and now once the purple ubuntu splash screen is done doing its thing and is about to switch over to the log in prompt I get a black screen.

I've tried following tuts to fix this issue but nothing is getting rid of the black screen. I've gone into into grub and set "nomodeset" to go into single user mode and I've completed reinstalled the fglrx drivers and created a fresh xorg.conf which didn't work.

I've also used jockey-text to enable the xorg:fglrx drivers which hasn't worked either.

The following methods have NOT worked:

1)
sudo apt-get remove --purge fglrx-updates fglrx-amdcccle-updates
sudo apt-get install linux-headers-generic
sudo apt-get install fglrx fglrx-amdcccle
sudo amdconfig --initial
reboot

2)
sudo init 1
jockey-text --enable=xorg:fglrx
reboot

What am I missing here?

---

### Post by ajgreeny on 2013-05-27
Why are you messing around with **fglrx** when you have an integrated Intel graphics system?

Purge anything to do with **fglrx** and other **AMD** graphic drivers you may have added, and see if that gets you back to a GUI.  We can then see if anything else is needed.

---


---
title: "Save directives"
date: 2008-01-18
forum: General Help
---

### Post by dodgingspam on 2008-01-18
OK, this particular board got instant response to my previous post and right on the money. Here's another dilemma I'm dealing with:

I use Ubuntu on my laptop. In order to connect to wireless Internet I use a card, which I had to install with ndiswrapper.

Everything worked fine until I ran some sort of update in late December. From that moment on every time I need to connect to Internet I have to open Terminal and manually type the following lines:

> sudo modprobe ndiswrapper
sudo ndiswrapper -m 
Is there a way to enter it in some settings to avoid this typing in step?

Thanks.

---

### Post by PinkFloyd102489 on 2008-01-18
Sounds like the kernel module didnt install and you're having to do a temp fix every time.

---

### Post by dodgingspam on 2008-01-18
It did work fine before that update in December. Anything I can do at this point?

---

### Post by PinkFloyd102489 on 2008-01-18
If you followed a guide to install ndiswrapper drivers, do it again to reinstall the kernel module.

---

### Post by dodgingspam on 2008-01-19
I've repeated the following steps that made everything work originally:
[PHP]
sudo ndiswrapper -i <path to the .inf file>

ndiswrapper -l

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m[/PHP]

I also found a suggestion to add the word "ndiswrapper" to /etc /modules configuration file to load the module at boot, however I can't seem to be able to save the file as it is read only. How do I add a line and save it?

---


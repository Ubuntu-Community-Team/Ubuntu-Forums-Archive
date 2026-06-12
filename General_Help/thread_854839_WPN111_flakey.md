---
title: "WPN111 flakey"
date: 2008-07-09
forum: General Help
---

### Post by Patricrawley on 2008-07-09
I installed the WPN111 in hardy heron and it works, but every time I start the pc I have to unplug it and plug it back in and it also gives out randomly. I tried using the ```
sudo rmmod ndiswrapper
unplug/plug
sudo modprobe ndiswrapper

```
suggestion on the tutorial, but the first command never completes. I even let my pc sit overnight and it didn't finish. I have to restart anytime it stops working and it's really annoying. I have ndiswrapper 1.53 installed and both the chipset and card drivers installed.
```
patrick@patrick-desktop:~$ ndiswrapper -l
athfmwdl : driver installed
netwpn11 : driver installed
	device (1385:5F01) present
netwpn111 : driver installed
	device (1385:5F01) present

```

I also put modprobe ndiswrapper in my rc.local file like the ndiswrapper site said to and still no luck.

What can I do? This is really aggravating.

---


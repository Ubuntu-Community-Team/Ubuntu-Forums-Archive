---
title: "x problems under xubuntu 6.10"
date: 2006-11-11
forum: General Help
---

### Post by tdoggette on 2006-11-11
I did a fresh install of Xubuntu 6.10 on an old Dell with integrated video and a 17-inch CRT. On the LiveCD, resolution was 1024x768, but after installing, it dropped to 640x480. I tried ```
sudo dpkg-reconfigure xserver-xorg
``` but succeeded only in killing x. 

How can I fix my installation? I am a relative newbie, but do not fear the command line. (A good thing, since it's all I've got)

---

### Post by tdoggette on 2006-11-12
-

---

### Post by taurus on 2006-11-12
What does your /etc/X11/xorg.conf look like then?

```
cat /etc/X11/xorg.conf
```

---

### Post by fragos on 2006-11-12
Key to success with X is having the right video drive for your card or chipset.  The driver will limit options like resolution to what it understands.  The vesa default driver almost always supports lest features than than your video hardware and screen can accomodate.  With the right driver installed and configured in /etc/X11/xorg.conf gives you the start you need.  Resolution options can be easily edited in xorg.conf.  You had the right idea with  the command you used but may not have correctly answered all the questions.  Also this method doesn't recognise non GPL drivers like Nvidia. To start we need to look at the xorg.conf and to run lspci to see the identified hardware.

---


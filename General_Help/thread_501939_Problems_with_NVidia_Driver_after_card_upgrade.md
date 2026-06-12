---
title: "Problems with NVidia Driver after card upgrade"
date: 2007-07-15
forum: General Help
---

### Post by bsdrocker on 2007-07-15
I resently upgrade my OLD GeForce 2 to a GeForce 6200 and when I booted up into Ubuntu 7.04 I got an error saying it failed to load the driver. I'm assuming its because the driver is different. How would I change this to the right driver?

THANKS!

---

### Post by loserboy on 2007-07-16
if it drops you to a shell you can do one of two things


```
sudo nano /etc/x11/xorg.conf
```
and then change the driver to "vesa". 

OR

```
sudo dpkg-reconfigure xserver-xorg

```


step 1 would prolly be better and easier if it works, then you can get in and download the proper driver. Also there might be a better way to do it... thats just as far as my knowledge goes

---

### Post by bsdrocker on 2007-07-16
Cool - I'll try both these tomorrow. No time right now... I'll let you know what happens!

THANKS!

---


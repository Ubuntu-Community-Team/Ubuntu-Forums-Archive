---
title: "Nvidia driver problems.. weird ones"
date: 2006-10-28
forum: General Help
---

### Post by sunrex on 2006-10-28
First of all, I am running ubuntu edgy, 32bit.

there, that said and done.. let me tell you about my problem.

I recently installed the nvidia driver, and I thought everything was fine, i get 70FPS in CS, (i thought that was a bit low but it stayed at 70 the entire time), I did not notice anything out of the ordinary..

Then, today, i had my screensaver on, and I noticed the screen flash white for around 0.3 seconds, it happened every 5 seconds or so, it did not flash pure white either, it was like 50% white and 50% black, the 3d also stopped for that 0.3 seconds.

the mouse, when it starts the loading icon, also flashes, accept its really fast.

So, how can i fix this problem?

---

### Post by sunrex on 2006-10-28
I hate doing this.. but bump.

---

### Post by tronica on 2006-10-28
what driver and card are you using?

---

### Post by sunrex on 2006-10-28
im using nvidia-glx.

the card is a Nvidia 7600 GS

---

### Post by sunrex on 2006-10-28
bump

---

### Post by Perfect Storm on 2006-10-28
You could try 9xxx beta driver and see if it solves your problem.

---

### Post by sunrex on 2006-10-28
where would i get this?

---

### Post by galileon on 2006-10-28
[http://www.nzone.com/object/nzone_downloads_rel70betadriver.html](http://www.nzone.com/object/nzone_downloads_rel70betadriver.html)

---

### Post by sunrex on 2006-10-28
alright, it says i need to shutdown Xserver to install.

I have tried sudo killall Xorg, sudo killall gdm. but it didint work.

The xserver would just restart and gdm just crashed.

How do i turn the xserver off.

---

### Post by galileon on 2006-10-28
sudo /etc/init.d/gdm stop

---

### Post by Perfect Storm on 2006-10-28
<ctrl>+<alt>+<F1>


```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
cd /to/the/Nvidia/script
sudo sh NVIDIA-Linux-x86-1.0-9625-pkg1.run
sudo /etc/init.d/gdm start
```

---

### Post by sunrex on 2006-10-28
That seemed to have worked, i got thrown into a blank screen with a blinking bar, even though i could type and it appeared on the screen, nothing came back to me, so it was like the system froze.

---

### Post by galileon on 2006-10-28
did it say anything interesting when you ran the nvidia driver script?

after it you should also try to

sudo dpkg-reconfigure xserver-xorg, and select your driver...

then sudo /etc/init.d/gdm start

---


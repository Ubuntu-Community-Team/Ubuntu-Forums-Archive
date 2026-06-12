---
title: "Nvidia driver install problems, Geforce 6200 AGP"
date: 2006-11-28
forum: General Help
---

### Post by Bastanteroma on 2006-11-28
After installing the restricted kernel modules and then nvidia-glx I get the following when I enter : sudo nvidia-glx-config enable

Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

And when I tried to reboot and run dpkg-reconfigure xserver-xorg from the recovery console my card was recognized only as an unknown nvidia.

I'm not sure what I should post, but I'll follow instructions.

This is after having the nvidia-glx-legacy installed with an older card.

---

### Post by bg1256 on 2006-11-28
I spent the last two hours fussing with my nvidia drivers.  I should note that X was failing to load, and I had no graphical interface.  I'm not sure if your problem is that severe.

Here's what I did.

> sudo nano /etc/X11/xorg.conf
I changed the driver from "nvidia" to "vesa"

ctrl+x then y to exit and save.
> startx

With the vesa driver, things were not good. 

So, I installed the nvidia drivers following STEP 2: Option 1 from this [link]("http://www.ubuntuforums.org/showthread.php?t=263851").  Make sure to click the link and read about method one immediately after the title.

I followed those steps, and things are working perfectly again.

---

### Post by Bastanteroma on 2006-11-28
Thanks for the help.

I tried dpkg-reconfigure xserver-xorg and went ahead with the card being unrecognized and everything seems to work.

---


---
title: "How to optimize my video card?"
date: 2007-09-05
forum: General Help
---

### Post by goldtech on 2007-09-05
I'd like to max out the detail and quality that my video card and monitor can offer.

I have an NVIDA GForce 7900 GS, the monitor is a Samsung 226BW LCD. 

In any event how do I get the best for my card? I went to the XFX site who makes the card but no Linux drivers.

Thanks,
Lee G.

---

### Post by ray bot on 2007-09-06
Have you installed the binary nvidia drivers yet?  You'll need to install them if you want 3d acceleration.  You can do it from the command line by typing ```
sudo apt-get install nvidia-glx
```

---

### Post by BLTicklemonster on 2007-09-06
Yikes, I wonder if he'll ever get past X crashing.

I'd have told him to find Envy and use that.

---

### Post by ray bot on 2007-09-06
I've always installed the nvidia drivers through apt, and it's never caused X to crash.  The only time I've ever encountered problems with the nvidia drivers was when I used the installer from nvidia.com, which causes the driver to break after every kernel upgrade.

---


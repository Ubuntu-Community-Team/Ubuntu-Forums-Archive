---
title: "Problem on Xorg"
date: 2007-02-15
forum: General Help
---

### Post by sdil on 2007-02-15
I have update the Xorg, NvidiaGLX, Xserver-xorg-core, xutils, linux headers 11-386, linux headers 10-386, linux headers 10-386 generic and more. After I restart my computer, I can't run X. What must I do for now ?

I used : AMD Sempron 64, PCI-E Nvidia 3D Card, 191MB Ram, Philips Monitor.

---

### Post by true_friend on 2007-02-16
try Ctrl + Alt F1 to F7 may it start X.

---

### Post by n00bish on 2007-02-16
> **sdil said:**
> I have update the Xorg, NvidiaGLX, Xserver-xorg-core, xutils, linux headers 11-386, linux headers 10-386, linux headers 10-386 generic and more. After I restart my computer, I can't run X. What must I do for now ?

I used : AMD Sempron 64, PCI-E Nvidia 3D Card, 191MB Ram, Philips Monitor.

Can you please post the output for your x errors?  At least tell us what the error may be, if you can't post it.  You could boot into the Ubuntu install/livecd and mount your linux partition(s) and get the info posted that way.

---

### Post by r4ik on 2007-02-16
sudo dpkg-reconfigure xserver-xorg

follow the defaults and finish with a

sudo etc/init.d/gdm restart

If you have a visual get you're drivers here,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good luck !

---


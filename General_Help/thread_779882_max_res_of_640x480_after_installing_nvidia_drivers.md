---
title: "max res of 640x480 after installing nvidia drivers 8800gt"
date: 2008-05-03
forum: General Help
---

### Post by Chuck251 on 2008-05-03
Hello, I am trying Ubuntu out for the first time, on a new system with a 8800GT and 19inch CRT.

The defaults work, but when I install the restricted Nvidia driver and reboot, I can only pick 640x480 and 320x200 as my resolution choices.
I also tried EnvyNG, same thing.  I think the drivers are loaded fine, because while it's only 640x480 it has the effects when a window is dragged, etc.

Any ideas? Thank you!

---

### Post by Chuck251 on 2008-05-03
Anyone? :(

If it helps, the card is: EVGA 512-P3-N801-AR
Monitor is: Viewsonic PF790

Again, this is with a new install from the 8.04 CD

Thanks!

---

### Post by fraterchaos on 2008-05-03
hmmm, that is odd, I had a similar problem where it wasn't using the Nvidsia driver by default, and when I enabled it I was only able to get max resolution of 640x480, but Envy fixed it right up... 

when i rebooted after using Envy, it asked for all my video card, monitor and resolution info, which I set as I prefer it, but when it finished booting, it was still stuck on 640x480 (and the screen was all bulged out in the center) but I checked the restricted drivers and it still wasn't showing the Nvidia drivers as enabled, and once I enabled them finally after using Envy, then they worked fine..

I would suggest, (IF it gave you an Nvidia config screen after rebooting after installing and running Envy) to check the hardware drivers under System, and make sure the Nvidia has been enabled.

---

### Post by fraterchaos on 2008-05-03
hmmm, another small point, not sure if it matters as I would assume you did, but did you RUN Envy after installing it? Its on the Applications menu under system tools (I think) and once I ran it, it told me to rebot and THEN asked for the Nvidia config info... so maybe you just need to run Envy?

---

### Post by Zorael on 2008-05-03
To make sure X is using your nvidia driver, enter this in a terminal.
```
$ sudo nvidia-xconfig -d 24 --add-argb-glx-visuals --allow-glx-with-composite --randr-rotation
```

---


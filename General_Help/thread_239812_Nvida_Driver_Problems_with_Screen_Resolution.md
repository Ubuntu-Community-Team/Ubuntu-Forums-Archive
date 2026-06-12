---
title: "Nvida Driver Problems with Screen Resolution"
date: 2006-08-19
forum: General Help
---

### Post by ScottMorris on 2006-08-19
Everytime I install the Nvidia driver it screws up my display and I have to reinstall Ubuntu (last time I backed up the partion so i wouldn't loose anything.)  Is there any way I can get it to like my 1920x1200 display size?  Its an LCD notebook screen and it is fine till I reboot then its all liney and hard to navigate. :-k

---

### Post by taurus on 2006-08-19
How did you install the nVidia driver?  If you need to reconfigure your X, why reinstall when you can run this command at the prompt!!!

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ScottMorris on 2006-08-19
What will this command do?

---

### Post by taurus on 2006-08-19
Reconfigure your X, creating a new /etc/X11/xorg.conf, in case you somehow screw up X!!!

---

### Post by ScottMorris on 2006-08-19
Sorry about the small questions but do I need to restart or do it before I do.  My display works fine before and just after I install the driver, but when I restart my computer its all blocky and messed up.

---

### Post by taurus on 2006-08-19
Let's see if I get this right.  Your monitor is working fine but when you install nvidia driver for your graphic card and reboot, your screen is all messed up!  Is that right?  If that's the case, then hold down <Ctrl><Alt>F2 and log in again.  Now, type in that command to reconfigure your X instead of reinstalling the whole OS.

---

### Post by ScottMorris on 2006-08-19
That is correct, I will try that the next time I install the driver.  But what if it doesn't work?  Or should I just back up my partition again and go from there.

---

### Post by taurus on 2006-08-19
Always back up your important stuff but that should work.  Also, you can change the "Driver" from "nvidia" back to "nv" again in /etc/X11/xorg.conf from the command line with

```

sudo nano /etc/X11/xorg.conf

```
I think maybe the nvidia driver screws up your X!  By the way, how do you normally install nvidia driver on your Ubuntu?

---

### Post by ScottMorris on 2006-08-19
> By the way, how do you normally install nvidia driver on your Ubuntu?

With Synaptic, is there a better way?

---


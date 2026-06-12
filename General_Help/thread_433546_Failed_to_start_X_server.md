---
title: "Failed to start X server"
date: 2007-05-05
forum: General Help
---

### Post by christarp on 2007-05-05
Okay, first I would like to say, this is my FIRST day using linux, never tried it before.

Alrighty, so I had a 9800 pro video card in it, so I decided to get WINE running, which I managed to do, then I managed to install steam.

After remembering that ATI doesn't work well with linux systems, I shut the computer off, and put a 6600 GT video card in it, booted it up, and came upon this message:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the server output to diagnose the problem?

Y/N


I heard there was a way I could fix this by going into the config and editing it. 

I figured I could go in and just run Ubuntu without drivers, then get them and have it run better (Much like windows) 

Any help?

---

### Post by zvacet on 2007-05-05
**ctrl+alt+F1**

```
sudo dpkg-reconfigure xserver-xorg
```

select **vesa** and when you get graphic go and search for drivers.

---

### Post by Famicommie on 2007-05-05
The X server is looking for your ATI card, but your ATI card isn't there!

Boot to a commandline and run the command ```
sudo dpkg-reconfigure xserver-xorg
```

Tell it to use the open source nVidia drivers (I think they are called "nv" or somesuch), and then go ahead and boot into a graphical user mode. From there, install the proprietary nvidia drivers.

---

### Post by christarp on 2007-05-05
Okay thanks!

---

### Post by Famicommie on 2007-05-05
No, the open source drivers should be included with Ubuntu. Once you have selected those, then you can log into graphical mode and download the proprietary drivers.

---


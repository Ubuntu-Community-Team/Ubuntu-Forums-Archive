---
title: "No more video, just terminal screens."
date: 2007-11-05
forum: General Help
---

### Post by Cherub_Rocky on 2007-11-05
I'm running gutsy (kubuntu) on an AMD 64 4600+ and a Nvidia 7900GT, I bought a new monitor today, (Soyo Topaz S 24") and changed the hardware settings to Generic 1920x1600 and changed the reslution accordingly, it the requested I restart the xserver, so I did. Now all I get is the terminal screen for a login in screen and I am clueless how to get my graphics back. Please HELP!!!!

---

### Post by mpierce on 2007-11-05
Look someone can walk you thru this as I have to leave but your old file is in /etc/X11 so, you can restore it. It has been renamed, xorg.conf.bak or something like that. 

You can also from a terminal change the driver to use the generic driver, "nv" and it should/may work. 

You can also use the graphic tools for your graphics card to generate a working xorg.conf file, e.g. run nvidia-xconfig as root. You didn't mention your graphics card type. 

The problem may be as simple as your mislabeling your screen name but you are going to need to look at /var/log/Xorg.0.log to see what the trouble is. You can open another terminal and look at the original file, Xorg.0.log.old 

or
make your own file using data from both files to make the card work as your old file had everything but new resoltion, scanning range, monitor name. It's not that hard.

Hope this helps...

---

### Post by lyndaj70 on 2007-11-05
At the terminal after login have you tried typing ```
startx
```

I have learned that sometimes you have to manually restart it the first time...  If it fails to start, then type ```
dpkg-reconfigure xserver-xorg
```

Hope that helps!
~Lynda

---

### Post by Cherub_Rocky on 2007-11-05
> **lyndaj70 said:**
> At the terminal after login have you tried typing ```
startx
```

I have learned that sometimes you have to manually restart it the first time...  If it fails to start, then type ```
dpkg-reconfigure xserver-xorg
```

Hope that helps!
~Lynda

It gave me a fatal error

---

### Post by lyndaj70 on 2007-11-05
Which part?  the startx or dpkg?

---

### Post by Cherub_Rocky on 2007-11-05
the startx

---


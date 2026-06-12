---
title: "x-server refuses to start"
date: 2008-01-06
forum: General Help
---

### Post by N_nykrog on 2008-01-06
Hi everyone

When I turn on my computer, my x-server refuses to start giving me a long error-list. At first it says:

(==) log file: "var/log/Xorg.=.log"
(==) using config file: "/etc/X11/xorg.conf"

I have tried to reinstall my xserver-xorg and run dpkg-reconfigure xserver-xorg, but neither worked. 

Later the list says:
(WW) the directory "/usr/share/fonts/X11/cyrillic" does not exist. Entry deleted from font path

I've seen this on several forums, so I thougt it might be the problem.

I have tried the simple startx too

If anyone could give me an answer i would be very happy, especielly with step by step instructions as I am fairly new here.

---

### Post by taurus on 2008-01-06
I assume it would dump you to a console where you can login with your username and password.  Now, what happens when you run this command from a prompt?

```
startx
```
What is the spec of your machine, especially the graphic card and monitor?

---

### Post by N_nykrog on 2008-01-06
I'm using an Axis-monitor with a NVIDIA GeForce MX 440 graphic card. 

I might add that my x worked all right untill I wanted to install propetary drivers because my computer had trouble playing video properly.

With the startx it simply takes me to a black screen, from where i can do nothing

---

### Post by taurus on 2008-01-06
Exit window and get back to your console.  Try to reconfigure your X server again but this time, pick **vesa** as the driver for your graphic card until you get X running again.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by N_nykrog on 2008-01-06
THX it worked!

---

### Post by JohnPhys on 2008-01-07
Do you recall the steps you took to try and get the nvidia drivers working?  I have that card in one of my ubuntu boxes and it works just fine.

---


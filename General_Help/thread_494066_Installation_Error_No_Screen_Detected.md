---
title: "Installation Error: No Screen Detected"
date: 2007-07-06
forum: General Help
---

### Post by HarrisonHopkins on 2007-07-06
I'm trying to install Ubuntu 7.04 on my Dell Inspiron E1505. However, when I try to start the installation, I get an error "No Screen Detected" or something along the lines of that it can't find my screen. Any ideas on how I can get past this?

---

### Post by dabl on 2007-07-06
Use the "Alternate Install" CD, which gives you more control.  I'll assume you have a handle on disk partitioning -- here's guidance if you need it:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

The problem is undoubtedly your graphics chip.  To get a functional, if sub-optimum GUI, you need to tell it "no" when it asks if you want it to auto-detect your graphics chip.  Then tell it you want a "VESA" display.

If it happens that you get a basic system installation, but no GUI (only a text login prompt), go ahead and log in with your user name and password, then issue the following command:

```
sudo dpkg-reconfigure xserver-xorg
``` this will launch the xserver configuration script.  On the first screen, answer "no" to "autoconfigure?", and on the second screen choose "VESA".  Accept defaults for the rest of the questions, unless you have a special keyboard or mouse.  When it gets to the monitor section, choose a resolution that you can live with for awhile, like 1024x768, then choose refresh rates that your CRT or LCD will accept.  At the completion, the script will dump you back to the text prompt.  At that point, you can enter ```
startx
``` and you should have a functional GUI.  Then you can begin your search for a suitable driver for your graphics chip.

HTH  :)

---

### Post by HarrisonHopkins on 2007-07-06
> **dabl said:**
> Use the "Alternate Install" CD, which gives you more control.  I'll assume you have a handle on disk partitioning -- here's guidance if you need it:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

The problem is undoubtedly your graphics chip.  To get a functional, if sub-optimum GUI, you need to tell it "no" when it asks if you want it to auto-detect your graphics chip.  Then tell it you want a "VESA" display.

If it happens that you get a basic system installation, but no GUI (only a text login prompt), go ahead and log in with your user name and password, then issue the following command:

```
sudo dpkg-reconfigure xserver-xorg
``` this will launch the xserver configuration script.  On the first screen, answer "no" to "autoconfigure?", and on the second screen choose "VESA".  Accept defaults for the rest of the questions, unless you have a special keyboard or mouse.  When it gets to the monitor section, choose a resolution that you can live with for awhile, like 1024x768, then choose refresh rates that your CRT or LCD will accept.  At the completion, the script will dump you back to the text prompt.  At that point, you can enter ```
startx
``` and you should have a functional GUI.  Then you can begin your search for a suitable driver for your graphics chip.

HTH  :)

Darn. I was hoping that it could be fixed with the Live CD. I don't understand why it is doing it now. I used to have 6.10 on it and I never got this error.

---

### Post by n1Digenarx on 2007-07-07
Would this also work for me, I am having a similar problem where as my samsung flat screen says in a box that my resolution isent goood "not optimum mode" or something. This happens in regular start up (I have windows xp on this computer, trying to install ubuntu), but when I put it it graphics safe mode it comes to a peach screen.

 Should I do those following instrucitons and then >> startx ?

---

### Post by HarrisonHopkins on 2007-07-21
Okay, I just tried it. Chose VESA, did all of that, and now it is stopping with an error of "Caught Signal 11". What now?

---

### Post by HarrisonHopkins on 2007-07-21
Bumping. I want Ubuntu back.

---


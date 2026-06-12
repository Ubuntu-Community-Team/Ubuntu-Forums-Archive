---
title: "Problems after ATI Driver Install"
date: 2007-03-16
forum: General Help
---

### Post by Tommy S on 2007-03-16
Hello, I have spent the day trying to set up and install Ubuntu on a friends computer, but have run into a display problem that I didn't experience myself using very similar computer hardware.

My friends graphics card is an ATI X1800XL and for all purposes is very similar to my X1950pro. After installing ubuntu 6.10 32bit the first thing we thought to do was install the latest ATI drivers and stop using Vesa drivers using this guide - [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) - Which I have used myself.

I did exactly the same thing and the installation seemed to go well, but on restarting, after the initial ubuntu loading screen when you would expect to see the login screen, the monitor (17" CRT) is shacking madly with what seem like lots of smaller screens all over it. When using a different monitor (15" LCD) upon getting to that point it would just say the signal cannot be displayed. When going back to vesa everything would be ok again but is painful to use and has no 3D support. 

I know on my own computer with a 17" CRT the login in screen goes into 75k mode and then goes normal when ubuntu is loading the desktop, could this be the problem? that his monitors cant handle this display mode? Any other Ideas?
 
Thanks, Tom

---

### Post by mrmonday on 2007-03-16
Try using [envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install the drivers. That way there should be no problems. Remember to select yes when it asks about configuring Xorg.

---

### Post by Tommy S on 2007-03-16
Thanks for replying, my friend tried what you suggested but with exactly the same results. Is there a setting that says what resolution the log in screen will be loaded at? 

Cause I know from my own computer on ubuntu 6.10 that its different to that of my normal desktop. My login screen is 1024x768 @ 60hz while my desktop is 1152x864 @ 75hz.

Could it be that it has somehow set itself to a resolution that his monitor is unable to produce?

---


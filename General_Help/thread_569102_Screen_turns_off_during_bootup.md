---
title: "Screen turns off during bootup"
date: 2007-10-06
forum: General Help
---

### Post by SnakeByte29 on 2007-10-06
I tried to turn on my laptop and just after it displays the "Toshiba" screen, the screen goes black (just about when the GRUB screen should come up). I know it's still working because the sound that plays when the Ubuntu login screen comes up is still played after a minute, so I have sound but no video. Is there something I may have done (I haven't changed or installed anything recently, though, I think). Can anyone help?

---

### Post by bodhi.zazen on 2007-10-06
Which laptop exactly, and what videocard ?

---

### Post by taurus on 2007-10-06
After hearing the sound, press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```
Use **vesa** as a driver for your graphic card for now until you get X up and running again.  Then, you can install a driver for it later.

What type of video card on your laptop anyway?

---

### Post by SnakeByte29 on 2007-10-06
The laptop is a Toshiba Satellite M40 (about 2 years old) and the graphics card is an nvidia GeForce Go 6600.

---

### Post by SnakeByte29 on 2007-10-07
I just found out that if I connect an external monitor it works, but only in 800x600, but I still, haven't figured out what's wrong.

---

### Post by bodhi.zazen on 2007-10-07
You may need to install the nvidia drivers.

envy may be easiest ...

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Wartender on 2008-04-26
Same thing happened to me, i have an Emachines T5046 and my graphics card is Ati Radeon Xpress 200, but this happened to me because i tried activating the desktop effects, and it told me to install a driver for the video card, so i did, and then next time i turned the computer on, it didn't detect my graphics card, so i switched the driver to one for Ati Radeon, and then this happened.

---

### Post by Wartender on 2008-04-26
and also, what happens to me is that the ubuntu loading bar comes up and after it loads, the screen turns off, and there is no sound afterwards either. i really need help with this please! :(

---

### Post by Wartender on 2008-04-28
should i try starting ubuntu in recvery mode? i have a dual boot with windows, but i'm not sure if sarting in ecovery mode is such a good idea. somebody please help, i don't know what to do here!

---

### Post by Wartender on 2008-04-29
well, i ran ubuntu in recovery, and entered the sudo dpkg... and now after the loading screen, it displays some things on the left with [OK] on the right (or <OK> idk), and that flashes a few times, and it stays there. I don't know what to enter or what to do! when i reconfigured it, i think all the info i entered is correct but i don's know what to doooooooooooo!!! :(:(:(:(:(:(:(: heeeeeeeeeeeeeelp!
*bangs head on wall*

---


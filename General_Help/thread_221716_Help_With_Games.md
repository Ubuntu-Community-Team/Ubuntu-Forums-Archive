---
title: "Help With Games"
date: 2006-07-23
forum: General Help
---

### Post by LiquidFlame on 2006-07-23
Ok, so i've been trying to install some of the free FPS games that are out there, but I'm having trouble playing them.  At first I thought I was installing them wrong, but now I believe it is my video card.  I'm trying to get America's Army to work and when I run it I get this error: > Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I read in another post to go under /etc/X11/xorg.conf and make sure my glx was enable, and it is, it says Load "glx".  My video card is Nvidia GeForce 3, I know its old and I plan on upgrading soon when the new Conroe chips come out.  So I don't know if its my drivers that I need to setup or what.  If you could help thanks and if it is my drivers could you point me in the direction of a thread, beacuse last time I tried installing drivers, it made my screen resolution off and I had to change the vertical and horizontal seetings to make it right again.  Also I'm some what new to linux so bear with me.  I'm also using Dapper version.

---

### Post by Kilz on 2006-07-24
> **LiquidFlame said:**
> Ok, so i've been trying to install some of the free FPS games that are out there, but I'm having trouble playing them.  At first I thought I was installing them wrong, but now I believe it is my video card.  I'm trying to get America's Army to work and when I run it I get this error: 
I read in another post to go under /etc/X11/xorg.conf and make sure my glx was enable, and it is, it says Load "glx".  My video card is Nvidia GeForce 3, I know its old and I plan on upgrading soon when the new Conroe chips come out.  So I don't know if its my drivers that I need to setup or what.  If you could help thanks and if it is my drivers could you point me in the direction of a thread, beacuse last time I tried installing drivers, it made my screen resolution off and I had to change the vertical and horizontal seetings to make it right again.  Also I'm some what new to linux so bear with me.  I'm also using Dapper version.
[I think you may need to install/update you video drivers.]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") The way to test if your video card is setup is to type in 
```
glxgears
```
into a terminal. If a small window opens with 3 rotating gears in it , the card is setup. If you get errors its not.

---


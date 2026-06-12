---
title: "Screen Rotation does not work (radeon)?!?!?"
date: 2015-12-23
forum: General Help
---

### Post by hes2 on 2015-12-23
Hello all, 
I cannot get screen rotation to work on 14.04 (32-bit, LTS enablement installed, but without it, the same thing happens) on a AMD E-350 CPU with HD6310 onboard graphics. The system usesd the "radeon" driver and boots fine into fluxbox, but when I try to rotate the screen with 

```
xrandr -d ":0" --verbose -o left
```
I get first a confirmation that this should work

```

 SZ:    Pixels          Physical       Refresh
*0   1920 x 1080   ( 477mm x 268mm )  *60  
 1   1680 x 1050   ( 477mm x 268mm )   60  
 2   1280 x 1024   ( 477mm x 268mm )   75   60  
 3   1440 x 900    ( 477mm x 268mm )   60  
 4   1024 x 768    ( 477mm x 268mm )   75   60  
 5    800 x 600    ( 477mm x 268mm )   75   60  
 6    640 x 480    ( 477mm x 268mm )   75   60  
 7    720 x 400    ( 477mm x 268mm )   70  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 

```

followed by an error message
```
Reflections possible - X Axis Y Axis
Setting size to 0, rotation to left
Setting reflection on neither axis
Failed to change the screen configuration!
```

I cannot find any other log output related to that matter - it just doesn't work. 

The funny thing is, about nine months ago, I tested rotation on this very same PC using a USB-stick version of the same distribution (Lubuntu 14.04, the installation on the stick was at least a year old though, so the actual installed packages were certainly older) without a problem. But now with the installed version 14.04, it just fails. The USB stick broke a couple of months ago so I can't re-test it anymore with that stick. 

Can anyone give me any pointers as to find out the cause? Any help is appreciated. I've attached the Xorg logfile. 

Cheers, Michael.

---

### Post by deadflowr on 2015-12-23
Moved to ***General Help***.
Not a multimedia software issue.

---

### Post by hes2 on 2015-12-30
Has no one ever heard of this problem? I don't have that exotic hardware and use the standard kernel, after all.  :-(

---

### Post by DuckHook on 2015-12-30
Hi hes2 and welcome to the forums.

I use rotated screens on two of my systems, but they run Ubuntu-64 and Xubuntu-64. Lubuntu shouldn't be too different, but 32 bit may be. I have the following suggestions:

1. Use the --rotate flag instead of -o, and without extraneous options, thus:```
xrandr --rotate left
```
2. or, install arandr and let it try to set up rotation:```
sudo apt-get install arandr
```

---

### Post by hes2 on 2015-12-30
Thanks for your reply. Using "--rotate" instead of "-o" does not work without also adding "--output HDMI-1" (in my case). But it works, as it turns out, my error was trying to reconfigure the screen while I was switched to a text console (via Ctrl-Alt-Fx). The screen can only be changed while it is actively displayed.

Thanks for your help.

---

### Post by DuckHook on 2015-12-30
Glad you worked it out. Yes, of course you have to define the display that you want rotated. My bad.

Do you only rotate your monitor occasionally or do you work with it in portrait orientation all the time? If so, you may wish to define a rotation at startup. Also, you may wish to set your console framebuffer up in rotated mode as well so that <Ctrl>+<Alt>+<Fx> gives you a portrait orientation.

---


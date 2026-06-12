---
title: "X-Server not recognizing laptop display"
date: 2007-12-20
forum: General Help
---

### Post by filemonkey on 2007-12-20
I'm not sure if this belongs here or not as it seems to be more display related...

I installed Wubi, the installation worked well. When I restarted I sat through about half an hour of setting up and installing miscellaneous items. The "ubuntu" loading screen appears, loads fully, and dissapears, loading up a console which verifies different processes. Then X-Server tries to start, but it fails. It shows garbled texts, and states that X-Server could not be started. It shows me logs stating that no display was detected and that the screen was not pre-configured. It then shows me another log, which I assume must be for the display driver as it had a list of different graphics cards produced by nVidia. My laptop is currently running Windows Vista with an nVidia 8400M GS card-a DirectX 10 card. Is there any way I can get ubuntu to start properly?

---

### Post by filemonkey on 2007-12-20
So I managed to at least start up bash by hitting escape the millisecond or so that it appeared on startup. I was able to log in and try most of the basic functions from the shell, however, when I tried to start up X through root, it says:

No devices detected
Screen(s) found but none have a usable configuration.
Then it just aborts the operation, bringing me back to bash.

Anyone know how I can configure a display through bash without starting X?

EDIT: I looked on the X site and found this:
[http://www.x.org/wiki/FAQErrorMessages#head-93b1e0b56f76546d61364f789045e9c745b6cfd4](http://www.x.org/wiki/FAQErrorMessages#head-93b1e0b56f76546d61364f789045e9c745b6cfd4)

---

### Post by ago on 2007-12-20
To update the configuration: 

sudo dpkg-reconfigure xserver.xorg

You may want to try vesa driver first

---

### Post by iansen on 2007-12-20
I had a similar problem ... you need to install a new driver for your video card .... my laptop has a similar configuration.
When the installer finishes it will ask you if you want it to reconfigure xserver ...just say no :P . It worked for me . Here is a thread I started ....got a couple of answers : [http://ubuntuforums.org/showthread.php?t=582901](http://ubuntuforums.org/showthread.php?t=582901)

---

### Post by filemonkey on 2007-12-20
> **ago said:**
> To update the configuration: 

sudo dpkg-reconfigure xserver.xorg

You may want to try vesa driver first

I tried that and it said it couldn't find the package or that it wasn't installed

[QUOTE=iansen]I had a similar problem ... you need to install a new driver for your video card .... my laptop has a similar configuration.
When the installer finishes it will ask you if you want it to reconfigure xserver ...just say no :P . It worked for me . Here is a thread I started ....got a couple of answers : [http://ubuntuforums.org/showthread.php?t=582901](http://ubuntuforums.org/showthread.php?t=582901)[/quote]

The installer finished though...and it never asked me to configure or change x-server...Not only that, how would I install an nvidia driver through bash from a file outside of the file system?

EDIT: I was able to get the configuration running by using sudo dpkg-reconfigure xserver-xorg. I then restarted and it worked! It's running at a lower resolution than it probably should be at though-I'll have to fix that later. Thanks for all your help!

---

### Post by ARGMan on 2007-12-31
Hi FileMonkey, I have a similar problem to yours after installing wubi 7.04 onto my laptop that has an ATI graphics card in it. I have tried to reconfigure my xserver numerous times using the ati selection and also the Vesa selection but I don't seem to be able to get the correct combinations of answers to the numerous questions to make it work. I wondered if you might be able to provide me with some guidance about what the answers should be so that I can get into ubuntu and past the xserver problem?

Cheers, Tony.

---

### Post by ARGMan on 2007-12-31
Its okay, I have managed to figure it out by using a combination of information from various posts on this forum. It took a little while but I got it running on the laptop perfectly in the end!

---


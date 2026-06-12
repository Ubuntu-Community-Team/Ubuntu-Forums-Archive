---
title: "Help, please"
date: 2007-04-04
forum: General Help
---

### Post by MadMac on 2007-04-04
Howdy!

Okay, I am getting more and more confused by the day.

I have installed Ubuntu 6.10 four times in the last 2 days and each install comes out different.  Start up screen is sometimes at 1024Xsomething and then sometimes at  1600Xsomething.  Sometimes the final entry screen into X is 1024Xsomething and sometimes 1600Xsomething.

I install and use Envy to update my video card and wind up having to set the contrast and brightness on my monitor all the way to the top to be able to see the screen.  The screen for changing the Nvidia settings (from "Applications" then "System Tools") sometimes has lots of info and stuff you can do and sometimes has just a small configuration screen with only four boxes to check or not check.  Of course, there is no way to test 3D, on either setup - that's the luck of the draw, it seems.

One install was even not allowing me to change any of the menus through "Edit Menus".

I really want this to work, but it seems like it's not ready for the "general public".  At least, maybe, not for me (hopefully it is for me, to be honest), and I have been working with computers for over 20 years.  I can breeze through DOS and Windows but this stuff is a bit much.

Anyway, I am asking for help.  Below is my setup.

=============================
CPU = Intel 3.20 Ghz
RAM = 1 Gig
HD = 40 Gig
(There are three other hard drives with one being Windows XP Home, and the other two just storage.)
Dual booting with no problems (Grub is good, I like it).
Video card = Nvidia Geoforce4 MX440 with AGP8X
Monitor = NEC Multisync E700
=============================

I install Unbuto from the CD, then install all updates, then install Envy and go from there.

Anyone with any ideas?  (Aside from buying a new video card and/or monitor, that is.)

Thanks!

---

### Post by russo.mic on 2007-04-04
Test your 3D acceleration by running 

glxgears 

in terminal.  You'll be able to tell within a few frames if your acceleration is working or not.  Also, I have an ATI graphics card, but I followed the how-to on setting it up from the beryl project, and it worked flawlessly and easily.  I understand that NVidia is even easier to setup than ATI, so I see no reason why the same shouldn't be true.  

good luck!  and don't give up.  It took me at least 3 weeks of sticking to it until I discovered why Ubuntu is FAR better than Microblows.

Russo

---

### Post by MadMac on 2007-04-04
> **russo.mic said:**
> Test your 3D acceleration by running 

glxgears 

in terminal.  You'll be able to tell within a few frames if your acceleration is working or not.  Also, I have an ATI graphics card, but I followed the how-to on setting it up from the beryl project, and it worked flawlessly and easily.  I understand that NVidia is even easier to setup than ATI, so I see no reason why the same shouldn't be true.  

good luck!  and don't give up.  It took me at least 3 weeks of sticking to it until I discovered why Ubuntu is FAR better than Microblows.

Russo

Sorry, trying to run glxgears in terminal (sudo or not) gives the response of :  "glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or director"

Thanks for the assist, though!

---

### Post by brentoboy on 2007-04-04
use envy to remove the nvidia driver  (I have found that working with envy works best if you use a real terminal (as opposed to an X terminal)  so, click ctrl + alt + F1 and login.  then run:
```
sudo envy
```
and use it to remove whatever you have in there.  (option 1 if I remember  correctly)

then, install the nvidia drivers from the repositories
```
sudo apt-get install nvidia-glx
```

these are generally more stable,  all envy does is gets the latest driver from the nvidia website and compiles it on the spot for your computer.  but you chipset is old enough that nvidia hasnt updated the driver for your card anyway, so why not let the automatic repo update do its magic for you.

once the nvidia-glx package is installed, edit your xorg.conf and set your driver to be nvidia (not nv or vesa)

this is done by typing
```
sudo nano /etc/X11/xorg.conf
```

then scrolling down to the part that looks somewhat like this
```

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6200]"
    Driver         "nvidia"
EndSection

```
the Driver in there will either be nv or vesa (hopefully its one of those and not some other crazy thing)  change it to nvidia.

save, close (press ctrl+x, and select "y" when it asks you to save)

then restart your GUI with this command:
```
sudo /etc/init.d/gdm restart
```

the nvidia logo should pop up for a split second as it starts up
and then, glxgears should be happy (and look good to boot)

if everything is in order, install planet penguin racer and play a few rounds.  If it is not choppy, you are in business.

---


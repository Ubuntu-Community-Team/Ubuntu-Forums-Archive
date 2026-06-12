---
title: "New Install"
date: 2007-03-21
forum: General Help
---

### Post by profXavier on 2007-03-21
This has been my third install of Ubuntu, over the past few weeks.  I have been trying to over come some issues with setting up my Nvidia card.  This last install, I used the "alternative" CD and I installed my Nvidia card first, to ensure it was working fine.

Then I began to notice a few changes, which I believed is leading me back to how I setup my keyboard during my new install.  During the install, I used the "wizard" to detect my current keyboard (which I think I didnt use entirely the last two installs, so it was working correctly).

Some of these new changes are: My mouse is VERY sensative, it accelerates across the screen quickly; my keyboard only works when a key is pressed, if the button is held, it doesnt nothing, even over lengths of time; my desktop menus (Applications, Places, System) within Gnome are showing no icons (probably unrelated).

I have tried a few of the obvious things, such as System--> Preferences-->Mouse: This caused me to have an install 3a and an install 3b, when I first did my third install, I found the mouse to have these issues, so I used the Mouse menu to change the configuration, and I found my mouse's speed/acc. decreased enomously. This made it difficult to do anything, so I thought, heck, might as well do the format/install again.

As for my keyboard, I have nothing to try really, I just assumed that they were related because of the connection in xorg.conf. When talking on IRC, someone maybe suggested the incorrect driver for my mouse, as that might cause it to jump.

Ok, so the important info:

I have a Microsoft Wireless Desktop Elite Combo (k/b and mouse)
Nvidia 7600
3GB of dual channel DDR RAM
AMD-64 3500
Twinview display, 20" Samsung wide screen and a Gateway 17"

Thanks for any help,

profXavier

---

### Post by Smuve on 2007-03-21
I'm a frequent crasher and reinstaller as well.  I like to play with settings that maybe I shouldn't be messing around with.  That's why all my data lives on a separate drive ;-)

Anyway, I have an AMD64 2800 with a GeForce 6800 and a Logitech G5 mouse.  To get everything working, video card, mouse and keyboard, here's what I do:

Install Ubuntu normally following the GUI on the live cd and then allow the system to update itself.  After that's all over:
```
sudo aptitude install nvidia-glx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg
```
During the reconfigure, take it slow and read the text.  Most of the defaults are correct though.  Here are a few things that I try to remember (in no particular order):
*choose nvidia as your driver, not nv
*keyboard = usually 104 or 105. If you don't know which one you have, it's probably on the bottom of your keyboard and usually its 104.  On the next keyboard option screen, I make sure it's blank.
*mouse = IMP/2 or something like that, not Explorer.
*when it asks if you want to use the video frame buffer, choose NO
*when it asks if you want to configure the video card/screen with Simple, Medium, Advanced choose Medium and select your preferred resolution.
*choose default depth of 24

All of this will rewrite xorg.conf with your keyboard, mouse, and video card settings at the same time.  Restart X.  Hopefully this will help fix your problem.

If it blows up your system when you restart x and you end up at a command line:
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
Restart X and try again with some different settings.

Nice rig by the way.

---

### Post by profXavier on 2007-03-21
Well,  I am finding that I dont like to do: dpkg-reconfigure xserver-xorg.  I used it before and I did take my time to read through it entirely.

Maybe a new install might be a good solution :/ Isn't this fun!?!??

What are people doing to the "keyboard wizard" during the install to setup your keyboard, I have done it differently this last instal, then before, so I do have options, but I want to see what others are finding.

btw, I dont like doing the dpkg because I have spent the last week researching on how to setup my Nvidia card, that I dont like messing with xorg.conf :)

profXavier

---

### Post by Smuve on 2007-03-21
If you don't reconfigure xorg, how do you get your video card to work?

---

### Post by profXavier on 2007-03-21
Using nvidia-settings, which is used to write Twinview options into your xorg.conf.

so nvidia-xconfig then nvidia-settings

---

### Post by Smuve on 2007-03-21
Ohhhh right.  dpkg-reconfigure always worked for me and the only time I tried nvidia-xconfig (long time ago) I fubar'ed everything.  Next time I do a fresh install (official Fiesty release), maybe I'll try nvidia again.

Sorry, I don't what to tell you about the mouse and keyboard.  My speed/sensitivity always seems to be a little different after a reconfig, but they always seem to work for me.

Good luck.

Hmmm. . . I just thought of something that might help with the mouse.  I have a fairly long guide to setting up my mouse with a side note at the bottom that I don't use, but it might help.

TEST INCREASE POLLING RATE
gksudo gedit /etc/modprobe.conf or /etc/modules.d/usb (whichever ubuntu uses)
Add line (default is 10):
options usbhid mousepoll=1

---

### Post by profXavier on 2007-03-23
Ahh a good ol' format/reinstall always works

:)

---

### Post by Smuve on 2007-03-23
Glad to see you've got it all straightened out.  Your post about nvidia-settings and some recent beryl issues of my own motivated me to upgrade my nvidia driver.  I took the plunge last night and it made a huge difference in my beryl performance.

The new xorg works great and now I can use the nvidia-settings you mentioned.

If you ever need it, I followed this guide and it worked like a charm:[HOWTO: Install Latest NVIDIA Display Driver (Directly from Nvidia: current 1.0-9755)]("http://ubuntuforums.org/showthread.php?t=336412")

Thanks for the boost.

---


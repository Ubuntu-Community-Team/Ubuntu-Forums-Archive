---
title: "Gusty and Screen Resolution + Some other problems"
date: 2007-10-19
forum: General Help
---

### Post by Yes on 2007-10-19
Right now, the only options I have for my screen resolution are 1280 x 1024 and 640 x 480.  I ran the command

```
sudo dpkg-reconfigure xserver-xorg
```

and I do have other resolutions checked off, but I can't seem to be able to use them.  Any ideas?

Also, when I try to start CCSM, nothing happens.

Thanks.

---

### Post by Ek0nomik on 2007-10-19
> **Yes said:**
> Right now, the only options I have for my screen resolution are 1280 x 1024 and 640 x 480.  I ran the command

```
sudo dpkg-reconfigure xserver-xorg
```

and I do have other resolutions checked off, but I can't seem to be able to use them.  Any ideas?

Also, when I try to start CCSM, nothing happens.

Thanks.

Do you have your video card drivers installed?

What kind of video card do you have?

---

### Post by Wiebelhaus on 2007-10-19
Crtl+Alt+F2 to drop to console ,

Run:

> sudo dkpg-reconfigure xserver-xorg

Manually choose your configuration , read carefully , three finger salute to restart.

---

### Post by Yes on 2007-10-19
I assume I have my video drivers installed.  Wouldn't I not be able to use any graphics if I didn't?  My card is an ATI Radeon 9600.  

sx66gns, I already ran that command.  The screen resolution I want is checked off under the screen resolution part of the configuration, so I'm assuming that's not the problem.

---

### Post by Yes on 2007-10-19
Also, I've noticed that nothing comes up when I try to edit my menus, open "Default Printer", "Hardware Information", "Main Menu", "Language Support", "Printing" (I have two "Printing", one works, the other doesn't), "Restricted Drivers Manager", "Update Manger", "Software Sources", and "Screens and Graphics".

Edit:  When I try starting any of those from the terminal, I get these errors:

```
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents
```

---

### Post by Yes on 2007-10-19
I tried changing my resolution with 

```
xrandr -s 1024x768
```

but it said that that resolution wasn't supported.  I used it in Feisty, what could the problem be?

---

### Post by 11touche on 2007-10-19
I don't know what the problem is really about, but I have a similar problem here, with guess what? : radeon 9600

Strange huh?

I tried to roll back to my old xorg.conf, but didn't work
I also tried several drivers from the new GUI that pops when I reboot, saying that I'm running in low-graphics mode because my video card isn't supported. But under Feisty, I got it to work in 2048x768 mergedFB dual-screen.
Now I'm stuck at 800x600, poor colors.

Please, help. I mean it.

---

### Post by Yes on 2007-10-20
I'm wondering if I don't have the drivers after all.  Where would I get them?

Thanks.

---

### Post by schmelck on 2007-10-20
I'm having the same problem. 

I'm stuck at 800x600, and when I try to install the restricted drivers it doesn't seems to work (after the reboot it still isn't installed).

My graphics card: Ati radeon 9800 pro.

Someone please help!

---

### Post by Yes on 2007-10-20
It seems to be something with the ATI Radeon 9xxx cards.  Does anyone have any fixes yet?

---

### Post by PsycoGeek on 2007-10-21
> **Yes said:**
> It seems to be something with the ATI Radeon 9xxx cards.  Does anyone have any fixes yet?

I'm getting the same problem with an Nvidia 8600...  I can't even install Gutsy 64bit...

---

### Post by jms1989 on 2007-10-21
I'm having the same problem but I have a nasty yellow on the right of any white area. I'm stuck with the high contrast theme to avoid as much ugly yellow as possible. Not mention it's not filling up my 19" moniter @ 1280x1024 res.

---

### Post by MediaBlitz on 2007-10-21
> **jms1989 said:**
> I'm having the same problem but I have a nasty yellow on the right of any white area.

i have the yellow issue on 7.10 on an ATI Radeon 8500. had a load of issues installing aswell due to the ATI issues in 7.10. none of these issues were there on Feisty. hopefully a new driver will come out soon.

---

### Post by burningbed on 2007-10-21
I have had somewhat similar problems (see [http://ubuntuforums.org/showthread.php?t=583642]("http://ubuntuforums.org/showthread.php?t=583642")) and they were all solved by uninstalling xserver-xgl.
I'd try running running apt-get remove xserver-xgl and see if it helps.

---

### Post by Yes on 2007-10-21
Thank's, but apparently I never had that installed ("Package xserver-xgl is not installed, so not removed").

---

### Post by FrancoNero on 2007-10-21
why are the fonts in my login-page so big (my username and password) and why are the fonts in window titles so extremely huge?
wasn't that a bug months ago??

---

### Post by pashashome on 2007-10-21
My fonts are enormous on the login screen also. There are a few links about it and the suggestions that fix it for some don't seem to work for me. Other than the font issue, I'm quite pleased with this release.  Let me know if you find a solution for the crazy huge font issue on login.

---

### Post by Yes on 2007-10-21
I thought my login fonts looked bigger than normal, but not huge =/ .  Maybe it's a different bug.

---

### Post by Yes on 2007-10-23
Bump.

---

### Post by Yes on 2007-10-23
If it's a driver issue, does anyone know when the new ATI driver will be out?

---

### Post by Yes on 2007-10-27
I just reinstalled Gusty, and I can now chose between a number of different resolutions.  However, they are not correct - If II chose 1024x768, the resolution looks like it's 800x600.  Any ideas?

---


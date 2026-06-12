---
title: "Blank screen after login"
date: 2008-05-14
forum: General Help
---

### Post by kooldino on 2008-05-14
I upgraded from 7.10 to 8.04 via adept.

It's important to note that I was running Compiz on KDE on 7.10.

Upon install and reboot of 8.04, logging in (using KDE, failsafe, OLWM, etc) would result in just the login wallpaper being displayed and I can move the mouse pointer around.


I got down to the terminal level and removed and reinstalled compiz.  Now it does the same thing as above, except it now happens over a black screen rather than the blue login wallpaper.

Note that I am running an ATi card.

When I CTRL+ALT+F1, it says: 

Checking for nVidia xdpyinfo: unable to open display"".
not present.
Checking for FBConfig: Error: unable to open display
not present.

Apparently, I'm running the latest xserver.

What do I do?

---

### Post by NightwishFan on 2008-05-14
Perhaps try to delete the .kde folder and reboot.

```
mv /home/youruser/.kde /home/youruser/.kdebackup
```
To restore if it does not help:```
mv /home/youruser/.kdebackup /home/youruser/.kde
```

---

### Post by kooldino on 2008-05-15
I'll give that a whirl, but I suspect that it has something to do with xserver-xgl vs plain old xserver.

---

### Post by NightwishFan on 2008-05-15
If nothing do:
```
sudo dpkg-reconfigure xserver-xorg
```
Worth a try.

---

### Post by kooldino on 2008-05-15
> **NightwishFan said:**
> If nothing do:
```
sudo dpkg-reconfigure xserver-xorg
```
Worth a try.

I tried that last night, but it never gave me the options to reconfigure my video...only KB and mouse.

:(

---

### Post by NightwishFan on 2008-05-15
Try:
```
dpkg-reconfigure -phigh xserver-xorg
```
Not sure why but I hear that works.

---

### Post by ~Nightingale~ on 2008-05-15
same thing happened to me, i forgot what I had to do

---

### Post by kooldino on 2008-05-15
> **NightwishFan said:**
> Perhaps try to delete the .kde folder and reboot.

```
mv /home/youruser/.kde /home/youruser/.kdebackup
```
To restore if it does not help:```
mv /home/youruser/.kdebackup /home/youruser/.kde
```

Ok, so I booted to the graphical login screen, but then chose console login.

I ran the first file move you specified above, and then I did a "startx".

The system came up with the default wallpaper and such rather than mine, and all of my settings are gone (which I assume now reside in the .kdebackup dir)

So I tried rebooting and doing the standard graphical login, but I still get the black screen issue.

---

### Post by kooldino on 2008-05-15
> **~Nightingale~ said:**
> same thing happened to me, i forgot what I had to do

This makes me a sad panda.

---

### Post by kooldino on 2008-05-16
> **NightwishFan said:**
> Try:
```
dpkg-reconfigure -phigh xserver-xorg
```
Not sure why but I hear that works.

This didn't work for me.  What's it supposed to do, an autoconfigure?  It just ran without prompting me for anything.

---

### Post by kooldino on 2008-05-16
So here's where I got last night:

-I moved my profile back over to /dino/.kde that way I had all of my desktop settings.

-At the login screen, I would click and choose console login.  I would still see the errors at the console like in the first post where it was unable to open the display.  Once I was logged in, I would run "startx".  

This brought me to my desktop (except links to my mounted drives didn't work since the drives were no longer mounted for some reason).

The video was extremely sluggish.  I uninstalled compiz.  Using the vieffects tool in KDE, I disabled all visual effects and uninstalled the ati driver.

After rebooting, doing the console login, and running "startx" again, it used the window decorations I had set up with my old compiz setup.  The video was "fast" again.  I then reinstalled the ati driver and rebooted. Now when I manually run "startx" it loads the desktop and everything in a high resolution, and it all looks right...until the screen turns white and just hangs there. 

If I run dpkg-reconfigure xserver-xorg, it never gives me any video options short of using the framebuffer.

I'm really confused and could really use some more insight here.

:confused:

---

### Post by kooldino on 2008-05-16
Help?

---

### Post by kooldino on 2008-05-19
Bump!

---

### Post by kooldino on 2008-05-20
I turns out I had "compiz --replace" in my .profile file.  I removed the line.  I still have some other issues that I'm working out.

---


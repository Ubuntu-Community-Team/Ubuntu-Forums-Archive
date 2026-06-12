---
title: "Can't see login screen"
date: 2007-03-04
forum: General Help
---

### Post by BoneyOne on 2007-03-04
I have an older Compaq machine that has onboard video. Of course this onboard video is not the best so I installed a nvidia MX-400 card.

Once the machine finishes the boot process the screen goes black. I still have a steady light on my monitor so something is being outputted, but not correctly.

This happens with the card in the machine during the install or not.

---

### Post by taurus on 2007-03-04
Can you get to a console with <Ctrl><Alt>F2?  Log in with your name and run

```
sudo dpkg-reconfigre xserver-xorg
```
Just use the default value if you are not sure about a question and use **vesa** as a driver for your graphic card.  Once you have X running again, then you can install nVidia driver for it.

---

### Post by BoneyOne on 2007-03-04
I wasn't able to get anything before just a black screen. So before installing the card I did the configure and chose vesa, came up and I was able to get errors and go into the configure screens.

It seems the problem is that it keeps detecting the i810 instead of the MX-400 even though the i810 is disabled in the BIOS (and monitor hooked up and displaying from the MX-400). 

When I try to manually set it and then startx, it fails. :mad:

---

### Post by taurus on 2007-03-04
Boot into recovery mode from GRUB menu and run that command again at the prompt to configure your X.

```
dpkg-reconfigure xserver-xorg
shutdown -r now
```

p.s.  And did you remember to turn off the onboard graphic card in the BIOS?

---

### Post by Drake2k on 2007-09-26
Thank you for this.  I was able to recover from the same issue (well, same sympton but nothing to do with dual video).  I screwed up my X by installing nVidia legacy drivers on top of the current up to date ones.  Oops.  So I was able to use the vesa settings to get back into X, use Synaptic to remove all nvidia-glx (thanks to rykel [http://ubuntuforums.org/showthread.php?t=19562](http://ubuntuforums.org/showthread.php?t=19562))

So then I used EasyUbuntu to reinstall the up to date drivers.

Rebooted, then I did this
sudo gedit /etc/X11/xorg.conf

Then I opened a file called xorg.conf with a bunch of numbers on it.  The command you had us do in safe mode made a back up of the old conf.

I copied all the setting from the backup conf to the latest one.  Rebooted, and presto all my settings were back,  my screen resolutions and everything.

---


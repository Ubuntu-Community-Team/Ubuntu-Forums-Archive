---
title: "Complete System Won't Start - After Following Sticky Tutorial"
date: 2007-08-22
forum: General Help
---

### Post by fppl on 2007-08-22
Hey.

After following a sticked tutorial here about how to get ATI's Xsomething cards to work properly (I have the X2900XT and so far I've been using Ubuntu's default, which limited me a lot) then I couldn't disable them in the Restricted Drivers (they didn't even appear there), and also - it messed up everything. I had to point at something to see it (like an icon) and after I moved the mouse away it would disappear.

Then, I went into Synaptic (could barely see anything, but I know exactly what I did) and "Completely Removed" the xorg-fglrx(something like that) driver (It was the exact one I installed so let there be no confusions that I uninstalled the wrong thing).

After that, Ubuntu won't even start (the GUI)... It tells me there's a problem with my X server interface or something along those lines.

I'm currently running from the Live CD (thank god for it) and I checked its X11 folder and my HD's X11 folder and the sizes are exactly alike.

I need help ASAP here, I can't get it to work and I have to be working right now! :(

---

### Post by merlinus on 2007-08-22
Try this:

Boot into Recovery Mode from the grub menu.

At the command prompt, type sudo dpkg-reconfigure -phigh xsever-xorg

Then select vesa as your video driver and use the space bar to select the resolution.

Then reboot.

-merlin

---

### Post by raijinsetsu on 2007-08-22
Most likely, your xorg.conf file is still trying to use the fglrx driver.
Log in at the terminal using your username and password,
type "sudo nano -w /etc/X11/xorg.conf"
It will prompt for your password
Then go down to "Section Device"
next to driver, it probably says "fglrx", I believe you need to change it to "radeon". save (ctrl-O) and exit(ctrl-X).
then you can do one of two things:
1) restart your *dm proggy (kdm/xdm/etc.) by typing "sudo /etc/init.d/*dm restart"
only do this if you know what *dm prog you have

2) reboot

This should get you back to a desktop. If it still gives you a problem, then you need to post the contents of the Device section of your xorg.conf for your video card. :)

<EDIT>
Or you could do it the easy way above...

---

### Post by fppl on 2007-08-22
Sorry, I can't even get into the recovery mode... I have to do it via the Live CD.

---

### Post by fppl on 2007-08-22
Ok, luckily, I had made a backup of the xorg.conf file about 2 weeks ago. I just deleted all of the 'left overs' from the fglrx driver, modified it a little (since I changed some stuff in it to work with my mouse) and now it seems to work all well. Thanks for the support, anyhows. :)

---

### Post by fppl on 2007-08-22
By the way, would you recommend me to stick to my current vidcard (which is supposed to be really good and new) which currently has no 'official' drivers by ATI for Linux, or to try and sell it (it's only 4 weeks old) and get an NVidia instead?

---

### Post by fppl on 2007-08-22
Dear god... For some reason now my VPU stops responding every minute and gnome keeps restarting!!!

HELP ME PLEASE, I CANT DO ANYTHING

---

### Post by fppl on 2007-08-22
Also now when I open a new tab in Firefox it ocassionaly crashes! And my automatic spelling checker doesn't work anywhere now!

What the hell happened...

---


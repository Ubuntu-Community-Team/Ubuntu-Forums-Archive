---
title: "No idea..."
date: 2007-01-25
forum: General Help
---

### Post by LinuxforHumans on 2007-01-25
Hey guys, any help with this would be very much appreciated.

I have  an ATI Mobility Radeon x700 graphics card with 64MB. (1440x900 res.)
I'm trying to get 6.10 to work, but when I go to run the LiveCD, I get a blue screen which
produces the following error:

==Log file: "/var/log/Xorg.0.log"
==using config file: "/etc/X11/xorg.conf"
EE No devices detected

fatal: no screens found

I've been playing with it for a couple of days, I'd love to get Ubuntu running on my machine, I have no previous experience with Linux but I'd love to give it a try. Any help at all with this is really appreciated.

---

### Post by allwin on 2007-01-25
Sad but it seems to be not detecting your video card.  When that happens, you need to get back to a command prompt and then examine /etc/X11/xorg.conf and see what's up.  Maybe the driver is wrong, like it says "nvidia" or "nv" instead of "ati".  I've had problems with other distros where I had to edit xorg.conf before a live CD would come up.  If you don't know vi try "sudo tee /etc/X11/xorg.conf".  At least that editor tells you which fracking keys to press to get it to do things in command line mode.  You can also use driver "VESA" which should get you into the desktop where you can poke around a little more conveniently.

---

### Post by LinuxforHumans on 2007-01-25
When I enter the following commands, this is the output I get:

/etc/X11/xorg.conf
Produces: permission denied

sudo /etc/X11/xorg.conf
Produces: command not found

sudo tee /etc/X11/xorg.conf
Produces: nothing?

Am I just not able to have this installed on my machine?

---

### Post by taurus on 2007-01-25
```
sudo nano -w /etc/X11/xorg.conf
```

---

### Post by LinuxforHumans on 2007-01-25
So that allows me to create a new file...what should I write in it?

---

### Post by taurus on 2007-01-25
No.  That would allow you to modify /etc/X11/xorg.conf since you are having a difficulty with X.  Look in the section regarding "Driver" and make sure it says "vesa", for a generic driver for your graphic card.

---

### Post by LinuxforHumans on 2007-01-25
Well I'm not quite sure how you modify it, but I tried something else that seems to be working...

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

It was a little weird at first, the graphics didn't look like they were loading
properly, but I'm actually on the Ubuntu desktop right now, so it did work.

It's soo nice...

I hope this is a permanent fix and I don't have to go through that each time.

I have another question though...
Let's say I want to install Ubuntu and still be able to install Vista if and when I get it.
Would installing Ubuntu conflict with Vista's installation?

---

### Post by allwin on 2007-01-25
> **LinuxforHumans said:**
> Well I'm not quite sure how you modify it, but I tried something else that seems to be working...

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

It was a little weird at first, the graphics didn't look like they were loading
properly, but I'm actually on the Ubuntu desktop right now, so it did work.

It's soo nice...

I hope this is a permanent fix and I don't have to go through that each time.

I have another question though...
Let's say I want to install Ubuntu and still be able to install Vista if and when I get it.
Would installing Ubuntu conflict with Vista's installation?

Looks to me like you never had an /etc/X11/xorg.conf to begin with until you installed those proprietary drivers!  Good to see you got up.

OK, I'm kind of a noob, IMHO you should be able to install UBUNTU after you get Vista installed, but I kind of think Vista is going to mess up a good UBUNTU install.  I think you'd be better off installing Vista and THEN installing UBUNTU...BTW, they are working on a way to install UBUNTU entirely from a windows application!  It's close, prolly by the time you get Vista it will be ready to go.  Less risk of clobbering Vista with UBUNTU that way.

I do think I remember reading that if you install any Windows on top of a drive that contains a working UBUNTU, Windows will overwrite the MBR and suddenly you won't be able to boot UBUNTU any more without messing with GRUB installs.  But if UBUNTU goes on second, it plays nice!

---

### Post by 3rdalbum on 2007-01-26
Correct. But even if you install Ubuntu (it's not an acronym, no need to put it in all caps) and then Vista, you can boot up the Ubuntu Live CD and run a couple of commands and GRUB will reinstall itself, so then you'll get the boot menu again.

---

### Post by LinuxforHumans on 2007-01-26
Wow, thanks for your help.
Yeah, I guess I'll wait and see how Vista actually does
after release.

Is the LiveCD supposed to save any changes you've made to it?
Shutting down isn't normal, for some reason it freezes when I hit the
shutdown button, maybe that has something to do with it... (any idea why?)

But it won't save the desktop changes I made, or even any cookies
in firefox.

---


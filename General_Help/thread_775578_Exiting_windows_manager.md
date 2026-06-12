---
title: "Exiting windows manager"
date: 2008-04-30
forum: General Help
---

### Post by faulk28 on 2008-04-30
I'm having a lot of problems with a nVidia driver.  I've been reading that I need to exit Xwindows(?) completely and run the install application NVIDIA-Linux-x860173.08.pkg1.run.  This seems like a silly question but how do I exit the X Windows manager?  When I try to run the driver application it tells me I need to exit and try again.

---

### Post by lizzard on 2008-04-30
Log out of your X-window session, then change to console (Ctrl-Alt-F1) login and stop GDM/KDM ```
sudo /etc/init.d/gdm stop
```
To be sure GDM is really stopped, you may enter ```
sudo killall gdm
```
After that you can run the Nvidia-installer.

---

### Post by ibutho on 2008-04-30
Logout of GNOME. At the login manager screen enter CTRL-ALT-F1, login to the terminal and run
```
sudo /etc/init.d/gdm stop
```
When you have installed the driver and edited your /etc/X11/xorg.conf to use the new nvidia driver, restart X by doing
```
sudo /etc/init.d/gdm start
```

---

### Post by 3rdalbum on 2008-04-30
As you've only got one post (this one), may I just ask: Have you tried installing the Nvidia driver from the Hardware Drivers application (System > Administration > Hardware Drivers)? This will be easier than installing it manually.

---

### Post by faulk28 on 2008-04-30
Let me back up...  So I installed Ubuntu 8.04 on my desktop with a nVidia 6800 GT.  I went into the package manager and enabled the nvidia-glx-new driver.  I had to go into hardware drivers and enable the 3rd party driver.  Everything worked great, I was able to play a Linux game (Savage from S2 Games) that I was accustomed to playing on the PC.  The problem was when I rebooted I got a black screen.  I went into /etc/X11 and ran a utility that reset my X configuration.  The machine booted okay but after this point I couldn't get the driver working again.  When it was enabled I got a black screen.  I searched the issue and saw a number of forum posts stating this was a bug and that I needed to install the official Linux drivers from the nVidia site.  After I figured out how to shut down X with ./gdm stop they install and recompiled the kernel module.  When I rebooted the resolution was 800x600 and I got an error that the video card wasn't detected.  What a mess.  Any suggestions?  I think I will hold off and wait a month and see if any updates are released.

---

### Post by forrestcupp on 2008-04-30
I'm pretty sure the drivers in the Hardy repos are the same as the latest official drivers.  But it's a lot easier to install the official drivers with EnvyNG instead of trying to do it yourself.  type in a terminal
```
sudo apt-get install envyng-gtk
```Then you will find it in your System Tools menu and it will install the drivers for you.  Since you have already tried to install them, I would choose the option to uninstall the nvidia drivers first, then install them again after that's done.

---


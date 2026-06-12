---
title: "Nvidia"
date: 2006-12-31
forum: General Help
---

### Post by DetroitBaseball on 2006-12-31
My new Nvidia card won't work on Ubuntu since Ubuntu doesn't have a driver to support it. When will Ubuntu get a built-in driver included? I heard you have to go into recovery mode and download a driver for it to work. And everytime you install a new kernel you must do the same thing. Too much hassle, and not worth it. Help.

---

### Post by spockrock on 2006-12-31
hmm...the next version should contain proprietary drivers for ati and nvidia cards.

basically you need to use the alternate disc to install ubuntu, then use recovery mode, or just regular way, and after x crashes, you need to enable the restricted repositories, and then do sudo apt-get install nvidia-glx.  This will install the nvidia drivers, and wont need you to re-install, the drivers after a kernel upgrade, you will only need to do that, if you use the nvidia installer from thier site.  The only time you should do that is if you have a 8800 GTX video card.

---

### Post by taurus on 2006-12-31
You don't have to go into recovery mode to install nVidia driver.  You can just do it from a terminal!!!

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by DetroitBaseball on 2006-12-31
I don't really understand how to install it in the recovery mode.

---

### Post by DetroitBaseball on 2006-12-31
> **spockrock said:**
> hmm...the next version should contain proprietary drivers for ati and nvidia cards.

basically you need to use the alternate disc to install ubuntu, then use recovery mode, or just regular way, and after x crashes, you need to enable the restricted repositories, and then do sudo apt-get install nvidia-glx.  This will install the nvidia drivers, and wont need you to re-install, the drivers after a kernel upgrade, you will only need to do that, if you use the nvidia installer from thier site.  The only time you should do that is if you have a 8800 GTX video card.

> **taurus said:**
> You don't have to go into recovery mode to install nVidia driver.  You can just do it from a terminal!!!

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)
It won't display a GUI.

---

### Post by hikaricore on 2006-12-31
Hit ctrl+alt+f1 to get to a terminal after your system boots up.  You can then login and setup the needed drivers from there.  ^.^

(Just so you know Ctrl+Alt+F1-F6 are text terminals on ubuntu, and Ctrl+Alt+F7 is for GDM/KDM and your X gui session)

---

### Post by spockrock on 2006-12-31
right ok, so when you get to grub, you can choose the regular boot up or recovery mode or single user mode.

boot in recovery mode ok, then you should not have a gui, black screen with white text ok.

then do this...

```
nano cp /etc/apt/sources.list /etc/apt/sources.list.bak
nano /etc/apt/sources.list
```

now enabled all the ubuntu repo by having it looks kinda like this

```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

```

after you have made the changes, ctrl-x save, then enter the following command,

```
apt-get update
apt-get install nvidia-glx
nvidia-xconfig
```

this then should give you a working gui, after a reboot ofcourse.

or if that sounds a little to complicated, try this......boot into recovery mode. Then do this
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
nano /etc/X11/xorg.conf
```

some where in your configuration you should see a section, on your video card right, where the there is a line that says, Driver "nv" change it so the "nv" is now "vesa".  Ctrl-x, save and quit.  reboot and you should have a gui now.  I dunno if this works, but I have been told it does.  Now you should be able to use firefox, and go to the automatix website, and install automatix2 which should install the nvidia drivers.  

remember this is assuming you have used the alternate disc to install ubuntu.

[http://www.getautomatix.com/](http://www.getautomatix.com/) <-- the automatix website.

---

### Post by ihristov on 2007-01-23
The drivers for Nvidia I downloaded using Automatix2 did not work for me either.

However I had no problems with the drivers from NVidia. [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Just download it and follow the instructions. In my case it had to build the kernel driver from source so you have to have delopment tools installed i.e.
```

$ sudo apt-get install build-essentials

```

and your kernel headers
```

$ sudo apt-get install linux-headers-`uname -r`

```

> **DetroitBaseball said:**
> It won't display a GUI.

---


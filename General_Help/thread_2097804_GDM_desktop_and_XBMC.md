---
title: "GDM desktop and XBMC"
date: 2012-12-24
forum: General Help
---

### Post by ylafont on 2012-12-24
I have a novice question that I hope someone on the forum can help me further understand. I install Ubuntu 12.10 from usb stick, which I believe it is a minimum installation.   I have configured the machine with the default gnome desktop xbmc and a few other apps.  Although I have a few alteration ma perform the machine if pretty much ready to go.   

I have modified /etc/init/tty1.cong for auto lofon as follow:
	exec /bin/login -f USERNAME </dev/tty1 > /dev/tty1 2>&1

I have also modify the /etc/default/grub
	GRUB_CMDLINE_LINUX_DEFAULT="text"

This leaves logged in on the command line on boot-up.

On the users .bashrc file I have added the following line
   case "`tty`" in           # XBMC . start only for   tty1
   *tty1) /usr/bin/xbmc;;    # XBMC . start XBMC
   esac # XBMC . end of case

I expected to have XBMC start as the default desktop without gdm, however I get the error  “Unable to open display, install the appropriate graphics driver”.   I tried to startx however the system tells me that it is not installed. I also tried to xinit, and I got the same result.   

After some investigation I think that the xserver installed with gdm is xserver-xorg (please correct me if am wrong), which is used by GDM.  So my question is, shouldn’t xbmc use the same xserver to start or do I have to install startx and xinit?  To have XBMC as my startup application without GDM?

Can I start XBMC with xserver-xorg? If so how?  

My ultimate goal hear is to have XBMC as the startup application on startup and reboot that is able to respawn.  Thank you for all the assistance.

---


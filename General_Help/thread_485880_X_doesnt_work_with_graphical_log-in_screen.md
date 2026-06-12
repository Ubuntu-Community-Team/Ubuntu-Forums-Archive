---
title: "X doesnt work with graphical log-in screen"
date: 2007-06-27
forum: General Help
---

### Post by advoss on 2007-06-27
I just boot the system so it should go into the log-in screen it goes black and locks up (i have set it to the plain login screen and that didn't help)

If in xorg.conf i set the driver to vesa (instead of i810) it works and starts without a problem 100% of the time but i can only get 640x480@101 then.  If i boot to recovery mode then type 'startx' the desktop loads just fine (thats as root).  If i modify xorg.conf so that the server rejects it during a normal boot and returns to command line where i then fix xorg.conf, i then log-in as myself and then 'startx' it goes to my desktop just fine.  The problem only seems to present itself when it goes to the login screen, or at least thats the conclusion I've come to.

______
Here's the background information I can provide:
I have an eMachine T2040  and it has Intel i810 onboard graphics installing the -intel instead of the -i810 didn't fix the problem so i went back to -i810 since it had worked once upon a time

Starting with 6.10 (i think) the splash screen stuff wouldn't display on my computer, I'd just have to watch a black screen with flashing underscore until the desktop loaded, and once I installed I removed the splash option from menu.lst.  With the feisty CD I couldn't use any of the options on the disk because all would have no indication of what/if anything was happening, even the media check (it was a ship-it cd).  When i'd tell it to start the live desktop and just wait i still got a black screen though a computer called ubuntu did appear on the router.  So to get feisty I had to install 6.10 and then upgrade

It worked for a while. I had one time where it booted to and only gave me the option of 640x480, but a reboot fixed that.  I set up the system how I wanted then it started not always succeeding and just locking up and displaying a black screen when it was time to display the login screen.  I rebooted a few times and eveuntally booted to my 6.10 cd again and used it to force run of fsck and the next boot it was normal again.  But now even if i run fsck it still will lock up when i boot from HDD

---

### Post by Selrach on 2007-06-27
Jeez, that is old. Anyway, my old machine was a eMachines 2042. I'll see if I can help you. Have you tried compiling/installing the intel drivers for your chipset?

---

### Post by advoss on 2007-06-27
umm.... I used aptitude to install the package xserver-xorg-video-intel (and later reverted to xserver-xorg-video-i810)  but other than that I haven't, and I don't know how as well.  I just went with the default install and this is the only thing broken.

EDIT:  I googled Intel on my interpretation of what you said and got to 
[http://support.intel.com/support/graphics/sb/CS-010512.htm]("http://support.intel.com/support/graphics/sb/CS-010512.htm")

where it sayd that there are Linux drivers available for the i810 family and for more information it links
[http://www.intellinuxgraphics.org/]("http://www.intellinuxgraphics.org/")

and there it says that the driver there is for i830 onward and on another page on the site is says "If you have a 945 or older graphics controller, your distribution will already have the right drivers included. "

---


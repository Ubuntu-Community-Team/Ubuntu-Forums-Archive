---
title: "problems with Xorg and fglrx/ati drivers"
date: 2006-09-03
forum: General Help
---

### Post by oddmind on 2006-09-03
I'm having issues with the live cd of Dapper and the installed version of breezy, the X server fails to start and gives the usual message of "do you want to see the detailed log" or whatever.

I'm trying to install dapper if at all possible. breezy was plan B (no pun intended)

I'm running on an AMD 64 with 1 gig RAM

Radeon x800 GTO2 graphics card (pci express) and an avidav TFT LCD display, that has a HorizSync of 79 and a VertRefresh of 75.

I've tried using this guide, and Ive gone through the following commands, in what seems to be a successful manner.

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo sudo apt-get install xorg-driver-fglrx

I am pretty sure my wireless card isnt configured right, it never does that automatically, but the next two lines returned errors.

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Apparently the commands aren't recognized.

I edited the /etc/X11/xorg.conf file to match the following specs

screen identifier line was changed to "aticonfig-Screen[0]

Device driver line was changed to "fglrx"

I rebooted and fglrxinfo was not recognized.

I also tried the "sudo dpkg-reconfigure xserver-xorg" method, but when it auto detected ati and it gave the list of the other drivers, fglrx was no where to be found. i tried the VGA and vesa (those i was sort of familiar with from gentoo, although i was still having problems there as well) but when the wizard got to the part where you choose color depth i tried every time to select 24 and it went back to a text prompt telling me that it "might change somthing in the conf file". 

I dont see how I can even finish the reconfig if this keeps happenning.

Any help would be much appreciated, I have searched a few places before this and tried several methods to no avail.

thanks for reading,

-chaz

---

### Post by Anduu on 2006-09-03
You are better off using this method...

[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

AFAIK the fglrx driver from the repos does not work properly with newer ATI cards.

---

### Post by oddmind on 2006-09-03
sorry if I sound like a noob, but do I need internet connection to use these apt-get update things? I have never been able to get my wireless card working with linux. (gentoo, kubuntu, fedora 4 and 5, ubuntu breezy, DSL and free BSD)

It might be the fact that I have an Airnet wifi card, and not alot of things suport it I guess...

Anyhow thanks for the link, though I dont know how to get those drivers to linux, since im using a live CD and it wont install from the live CD without X starting up.

Will this work with my already installed breezy badger?

---

### Post by encompass on 2006-09-17
not sure if this would work for you from the live cd worth a try... but
```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```
when the system askes you for what driver to you select "vesa"... for everything else... just press enter for the default.
These commands should work for breezy too.

---


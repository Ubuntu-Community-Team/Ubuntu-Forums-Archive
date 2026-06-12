---
title: "DVD error driving me crazy..."
date: 2005-07-11
forum: General Help
---

### Post by fedemw on 2005-07-11
I installed all plugins from ubuntu starter guide, but i cant read dvd movies with totem or any media player (xine)

Error:

"There is no input plugin available to handle 'dvd:/'.

So i cant open any dvd movie and also can't configure dvdripper... 

i was reading other post but i cant get any solution


thanks for help, regards.

---

### Post by barsoom on 2005-07-11
Try 

sudo apt-get install libdvdcss2

Check out multimedia section in [http://ubuntuguide.org/](http://ubuntuguide.org/) the Unofficial Ubuntu 5.04 Starter's Guide

Good Luck

---

### Post by slippy on 2005-07-11
Just a thought... you might need some dvd libs from ftp.nerim.net, a debian multimedia repository that works pretty well with Ubuntu

Add these to your /etc/apt/sources.list

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

Then search in synaptic for any dvd libraries. You might be missing a few libs

By the way, if you do get it working... make sure turn on DMA on your DVD drive

sudo hdparm -d1 /dev/(your drive)

---

### Post by fedemw on 2005-07-12
hi to everyone,

well i tried to do all you said but is no solution yet. 

root@lenin:/home/marx # apt-get install gnome-volume-manager gstreamer0.8-dvd libdvdnav4 libdvdread3 dvdbackup gxine tvtime regionset vlc dvdrtools qdvdauthor

i also had installed codecs, etc

my two dvd drives has DMA on 

but i still cant open DVD and copy them. i think it maybe is a permission problem or configuration, because programs says that cant open dvd:/ and i had drives mounted on /media/cdrom0 and 1. 

try to open with these address and no solution. thanks for cooperate, waiting help , bye !

---

### Post by taldones on 2005-08-04
I would suggest running xine-check It diagnosed a couple of problems that I had been having with it and now it works great.

--T

---


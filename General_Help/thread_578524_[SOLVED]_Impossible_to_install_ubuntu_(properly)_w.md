---
title: "[SOLVED] Impossible to install ubuntu (properly) without internet???"
date: 2007-10-17
forum: General Help
---

### Post by olieviya on 2007-10-17
Ok, what I mean is for MY laptop. Basically the problem here is this:
1. I can't get gnome/kde (any graphics) working on initial install because of my laptop's graphics card needing fglrx.
2. Normally, I would just apt-get it and then aticonfig it to work, which it does perfectly. But I haven't internet, so I can't download it.
3. I can't get the internet working because I need to do wpa_supplicant (look here: [http://ubuntuforums.org/showthread.php?t=570392](http://ubuntuforums.org/showthread.php?t=570392) ) configurations first.

If I can get the gui working somehow and start up firefox I will able to make the internet work long enough to download wpa_supplicant files, but how will I download fglrx without internet beforehand to get internet?

What do you suggest? Sounds to me like, unless the new Ubuntu comes with fglrx, I'm screwed.

---

### Post by SeanTater on 2007-10-17
You can possibly download the .debs and install them separately,  in this case I /think/ you need:

fglrx-control xorg-driver-fglrx linux-restricted-modules-common

You can get them from packages.ubuntu.com

---

### Post by olieviya on 2007-10-17
> **SeanTater said:**
> You can possibly download the .debs and install them separately,  in this case I /think/ you need:

fglrx-control xorg-driver-fglrx linux-restricted-modules-common

You can get them from packages.ubuntu.com

You'd have to tell me step-by-step what and how to install this, I'm not very CLI savvy.

---

### Post by olieviya on 2007-10-18
Bump, anybody??? :confused:

---

### Post by anthonyJC on 2007-10-18
ur graphics card dont support VESA mode omg! i've been using vesa on an ati card for a year cause drivers no good.

isn't there a text mode installation option on the boot if so buy as usb-pen drive copy fglrx-install from ati.amd.com onto pen drive
can u get to a terminal with clt-alt-f2 - surely theres a terminal / cli there


create mount point: mkdir //media/pend 
mount pendrive: mount /dev/sda1 //media/pend

pendrive might be sda2 if your hdd is sata - or sda1 if hdd is ide
mount /dev/sda2 //media/pend

Practice these commands out by putting sudo in front before taking the leap (won't need sudo on install cd)

run livecd in text mode see if it gives you a cli
try it all out without doing an install by using the livecd facility 

build debs with ./ati-ins....   --buildpkg Ubunutu 7.10   (when 42 comes out - dont know if it makes 7.10 yet)


install debs with
apt-get install <name of deb>


cant u do 

wget is default installed
wget [http://www.verisign.com/support/roots.html](http://www.verisign.com/support/roots.html)

less roots.html 

to find the file name then wget the file name


or find url for atis installer and write that down and wget the ati installer if u cant buy  a pen drive

need to write in that configuration file? 'nano' is default installed

i can't see why is so difficult - i've had worse recently had to install xp on a laptop w/o a cd rom drive and no external booting bios support - try installing windows xp from a flooppy disk drive without any cdrom drive (i managed to) its much harder lol

---


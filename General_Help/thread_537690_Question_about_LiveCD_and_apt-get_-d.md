---
title: "Question about LiveCD and apt-get -d"
date: 2007-08-29
forum: General Help
---

### Post by King Buttons I on 2007-08-29
If I put the livecd into a computer and run apt-get -d will it download the files to RAM or the hard drive? One more question where will they be downloaded?
Buttons

---

### Post by ajgreeny on 2007-08-29
Certainly not to the hard drive but to the ramdisk, I think, where the whole system of the live CD operates from.  When you shutdown or restart everything will be lost and you'll have to start again.
Generally the Live CD is not for use as on OS, though you can do so to a certain extent, but rather as a repair system or to check that your machine is compatible with the OS before you attempt to install it to hard drive.

---

### Post by ddrichardson on 2007-08-29
Is there a reason you need some extra functionality in the Live CD? If so there are ways to build your own.

---

### Post by King Buttons I on 2007-08-29
No I have it installed on my PC at home and that PC has no internet connection. So I am going to download the packages at school using the liveCD and take them home and install them.

---

### Post by ddrichardson on 2007-08-29
Ah I see - if you mount a USB stick or such like then you can download the required packages only and install them manually using apt.

---

### Post by capink on 2007-08-29
apt-get -d download packages to current directory, which will usually be the home directory of the livecd user, which means that they will be downloaded to ram.

To change this, mount a hard disk (or usb disk) drive on /mnt or whatever mount point you wish, then, cd to mount point so it is you current dir before running apt-get -d

Also, check my post in this [thread]("http://ubuntuforums.org/showthread.php?t=529671"), it might provide some help for you.

---


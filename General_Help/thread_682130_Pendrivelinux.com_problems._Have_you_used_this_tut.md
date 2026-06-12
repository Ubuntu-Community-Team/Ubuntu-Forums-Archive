---
title: "Pendrivelinux.com problems. Have you used this tutorial??"
date: 2008-01-29
forum: General Help
---

### Post by belovedmonster on 2008-01-29
I've been following this [pendrivelinux.co]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/")m tutorial on putting 7.10 on a USB stick, albeit I'm trying to do with Xubuntu not Ubuntu, but I was told it wouldn't make any difference.

Along the way I came across a few problems and ending up getting "boot error" when I tried to boot from it.

The problems I encountered were:

Step 12: When it says to remove the drive and insert it again I get an error message when the drive is inserted again. "Unable to mount the volume 'Ubuntu710'" When I click the details drop down it says something about "Cant read super block"

Is this normal?

I ignored this and carried on but found another snag at step 17.

In the tutorial it says 'Ignore any "cannot create symbolic link" errors' in a big bold box so I guess its OK to get an error message here, my problem is I got a different error message it said:

"cp target: 'media/ubuntu710/' is not a directory: No such file or directory

Are these two problems contributing to my Boot error when I later try it or are these normal?

Thanks in advance.

---

### Post by dcstar on 2008-01-29
> **belovedmonster said:**
> I've been following this [pendrivelinux.co]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/")m tutorial on putting 7.10 on a USB stick, albeit I'm trying to do with Xubuntu not Ubuntu, but I was told it wouldn't make any difference.
.........

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by belovedmonster on 2008-01-29
Thanks for the link. It makes me think maybe I'm in over my head. :(

---

### Post by seventyeights on 2008-01-29
Those instructions DO work for ubuntu, but in my haste, it took me four times around to not make any typos.

Your error at step 12 needs to be resolved before step 17 can work.


Make sure you are not fdisk'ing /dev/sdx1, just /dev/sdx (you want to fdisk the device, not the devices partition)

Also make sure *all partitions* are unmounted when the instructions say so. You can check by simply typing "mount".

---

### Post by belovedmonster on 2008-01-30
I think trying to solve these problems might be a waste of time with my current pendrive after reading this comment "Note: on some usb-sticks fdisk says "Note: sector size is 2048 (not 512)", in which case you may very well be out of luck trying to boot from it" That's exactly what it says about my usb stick! 

But ignoring that for the time being I'd still like to be able to get to the end of the process without these mounting problems.

Another thing I'm coming across is the second casper partition is listed as "Linux" rather than Fat16 or something like that. I'm finding the tutorial a little hard to follow in places but I get the impression that Casper partition should not be down as "Linux". Is that right?

---

### Post by itrade on 2008-01-30
I got a diffrent error here it is:

ubuntu@ubuntu:~$ cd /cdrom
ubuntu@ubuntu:/cdrom$ cp -rf casper disctree dists install pics pool preseed
.disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz
casper/initrd.gz /media/ubuntu710/
cp: reading `casper/filesystem.squashfs': Input/output error
cp: cannot create symbolic link `/media/ubuntu710/dists/stable': Operation not
permitted
cp: cannot create symbolic link `/media/ubuntu710/dists/unstable': Operation
not permitted
ubuntu@ubuntu:/cdrom$

And ny pendrive does not boot it goes to BUSY BOX shell.

I suggest that you cut and paste the commands Thats what I did second time around and it at least got the syslinux menu up and running.

I am about ready to toss it too my only question now is do you think if I fdsik the the pendrive and make it all fat32 i can use it again on windows and get the 2gb on it??

---

### Post by belovedmonster on 2008-01-30
I've broken my pendrive now :mad: Neither Windows or Linux will mount it. I think I've totally screwed it up through trying to restore it to its original state without really know what I am doing.

When I load up Gparted it only shows the Casper partition not the other 750mb. It says the casper partition is unassigned or whatever the terminology is. When I click on it to do anything with it Gparted crashes. 

When I load it up in Windows it says its not formatted properly but when I try to format it Windows says that it cant.

---

### Post by bodhi.zazen on 2008-01-30
Sounds like time for [dban](http://dban.sourceforge.net/)

If that does not fix it, it is possible you have a defective or counterfit USB device (Yes, I have seen several counterfit usb devices, down to packaging.)

---

### Post by dcstar on 2008-01-30
> **belovedmonster said:**
> I've broken my pendrive now :mad: Neither Windows or Linux will mount it. I think I've totally screwed it up through trying to restore it to its original state without really know what I am doing.

When I load up Gparted it only shows the Casper partition not the other 750mb. It says the casper partition is unassigned or whatever the terminology is. When I click on it to do anything with it Gparted crashes. 
......

The Gparted version on the current Live CD is broken (and crashes at inconvenient time), you can go into Synaptic and upgrade the package when using the Live CD, but remember that the new version is only kept in memory and will dissapear on reboot.

In a terminal, try using **cfdisk** to delete the existing partitions on the USB device.

---


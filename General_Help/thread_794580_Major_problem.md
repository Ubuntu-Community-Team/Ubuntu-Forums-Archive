---
title: "Major problem"
date: 2008-05-14
forum: General Help
---

### Post by haran_hockey on 2008-05-14
I have a big problem. I just installed ubuntu 8.04 using wubi on my windows 2000 pro SP4, 256mg ram, 2.00 GHz. I use wireless internet so I have to do some next stuff but to complete it, I have to update ndiswrapper which you need the ubuntu cd for. So i got that from a friend but I think my cd/dvd driver doesn't support dvd cd's(it supports normal cd's and audio cd's because those work)
It's a Lite-On LTN486S 48x Max
Here's a screenshot
[http://i251.photobucket.com/albums/gg288/haran_hockey/dvd-cd.jpg]("http://i251.photobucket.com/albums/gg288/haran_hockey/dvd-cd.jpg")

So what do I do. Any possible way to install stuff that's on the ubuntu cd that I can download off the internet(using windows) and then putting it on my usb to install on ubuntu?

---

### Post by macaholic on 2008-05-14
> **haran_hockey said:**
> 
So what do I do. Any possible way to install stuff that's on the ubuntu cd that I can download off the internet(using windows) and then putting it on my usb to install on ubuntu?
You can do exactly that, you can download the package, its dependencies, and install them fro ma usb stick. See here, make sure you download the other ndiswrapper package aswell. [http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9)
I think the only other package you need is ndiswrapper-common, but it's been a while since I did it myself.

---

### Post by ibuclaw on 2008-05-14
If you can hookup via Ethernet cable first, then I'd recommend that.

Else. Search for your driver here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

It is also possible to mount ISO images as drives on Linux.

On your Windows machine, Rip the DVD your friend gave you to an ISO image file, and when you boot into wubi.
Open up a terminal, locate the ISO file, and type in:
```
sudo mount -o loop **ubuntu_dvd.iso** /media/cdrom
```
The iso can be named as anything, hence the added boldness. Just replace that with what you've named your file.

To grab the repo off the mounted ISO image:
```
sudo apt-cdrom -d /media/cdrom
```
If all is successful, then the new packages will appear in the Synaptic Package Manager.

To finally unmount the ISO image.
```
sudo umount /media/cdrom
```

Regards
Iain

---

### Post by haran_hockey on 2008-05-14
My computer doesn't recognize dvd cd's AT ALL but I do have the ubuntu cd .iso on my desktop(i downloaded the .iso off the ubuntu site, put it on my usb, and put it on my desktop)

So what would be the exact commands if I want to mount the .iso to the cdrom drive

the path of the .iso is:  **/home/haran/Dekstop/ubuntu_dvd.iso**

And to ***macaholic***, I've done that and afterwards it says to install 3 things(ndiswrapper stuff), which I need the ubuntu cd for.

EDIT: Thanks. The mounting the iso thing worked perfectly. I was able to install the updates from the cd. Only problem now is my internet..
Go here if you think you know how to solve my problem: [http://ubuntuforums.org/showthread.php?p=4925983#post4925983]("http://ubuntuforums.org/showthread.php?p=4925983#post4925983")

---


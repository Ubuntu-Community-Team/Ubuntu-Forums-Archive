---
title: "xubuntu live on usb"
date: 2008-04-17
forum: General Help
---

### Post by richardy on 2008-04-17
Hi, this question has probably been answered although i count find anything exactly the same.
Is it possible to put the live cd image onto a usb drive - is it simply a matter of copying the image that has burned onto a cd, to the USB drive (tried it and didnt work) or do i need to do something else. Any help would be much appreciated.

Cheers.

---

### Post by nicedude on 2008-04-17
Nice tutorial on how to make Ubuntu, Kubuntu or Xbuntu etc. live USB install on a pendrive.

[http://edoceo.com/liber/ubuntu-live-usb](http://edoceo.com/liber/ubuntu-live-usb) 

if the method above is looks too complicated or confusing, I also saw this guide for 7.10 gutsy ubuntu USB live setup which looks just a tad more user friendly than the first but is only instructing for Ubuntu 7.10 not Xubuntu.

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

Lots of luck man, hope this helps you get it to work. Later on  :-)

---

### Post by richardy on 2008-04-18
Hi,
Thanks for that - it will come in very handy. Actually i have another question for you:
Do you know how to get an internal card reader to set up properly under Linux. It is one of the few things that is bugging me about Linux at the moment. I have asked this question before on a couple of forums and never got an answer. Does this mean support for internal card readers is still a bit dodgy?

Cheers.

---

### Post by mendieta on 2008-04-27
Hi All

This is just beyond me. Why is it that the USB flash device is not a standard installation / live demo method ? I was hoping this would happen for hardy. Should we propose this in 

Millons of people these days are getting eeepc's, most of them running (Xandros) Linux. And every hardware vendor is coming up with an eee pc wannabe. The live CD should have an option to clone itself into a bootable, live ubuntu pendrive. And it should also be possible to do this without actually burning the iso. It's just a matter of using the steps people manually do while following the instructions in places like pendrivelinux.com 

Let's vote for this here:
[http://brainstorm.ubuntu.com/idea/16/](http://brainstorm.ubuntu.com/idea/16/)
[http://brainstorm.ubuntu.com/idea/7367/](http://brainstorm.ubuntu.com/idea/7367/)

Cheers!

---

### Post by mdurham on 2008-04-28
Here is a note that I made to myself because my brain is quickly fading!

> wget [http://www.startx.ro/sugar/isotostick.sh](http://www.startx.ro/sugar/isotostick.sh)
chmod u+x isotostick.sh

apt-get install syslinux
apt-get install mtools

sudo fdisk -l	; find the /dev/sdn address

mkfs.vfat /dev/<usbstick>

fdisk /dev/<usbstick> (make bootable)

./isotostick.sh ubuntu-7.10-desktop-i386.iso /dev/<usbstick>

That should do it.
Cheers, Mike

---


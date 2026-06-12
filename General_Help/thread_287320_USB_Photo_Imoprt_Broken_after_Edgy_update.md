---
title: "USB Photo Imoprt Broken after Edgy update"
date: 2006-10-28
forum: General Help
---

### Post by ericcmi on 2006-10-28
Yep Upgraded to edgy and now I cant import photos off of my camera. Any ideas? I get this now.

Screenshot of the error is attached

---

### Post by vibestriton on 2006-10-28
I'm just going to take a couple of stabs in the dark here... I'm not sure what the problem is. 

sudo rmmod <modules cited in error message -- type first couple of letter and use tab to complete if possible>


Next, I might run the following command and reboot if anything "significant" is removed.

sudo apt-get autoremove

---

### Post by fragos on 2006-10-28
When ever you pug anything into a USB port a device is mounted for it.  It sounds as if the device the rule say to open for your camera is already in use.  I'm not the expert on this but rules can be created that can open multiples of the same type.  For example my TV card will open as /dev/video0 and my web cam as /dev/video1.

---

### Post by goathunter on 2007-01-25
> **ericcmi said:**
> Yep Upgraded to edgy and now I cant import photos off of my camera. Any ideas? I get this now.

Screenshot of the error is attached

Have a look here [https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146)

>   Re: "Could not claim the IO device": Canon IXUS 65, Edgy   from dailyglen  at 2006-11-05 18:07:01 UTC

I have the exact same problem for a Fuji Finepix F30, to fix I did:

1) $ lsusb | grep Fuji
Bus 002 Device 006: ID 04cb:019b Fuji Photo Film Co., Ltd

2) Added to the file: /etc/udev/rules.d/45-libgphoto2.rules
SYSFS{idVendor}=="04cb", SYSFS{idProduct}=="019b", MODE="0660", GROUP="plugdev"

3) Turned off camera

4) Restart udev: /etc/init.d/udev restart

5) Turned on camera, and voila

Hope that helps

---

### Post by paulg on 2007-01-30
I have had this problem since November (among other issues) since upgrading to Edgy. Just getting around to it now and did the search before posting a question. Thanks a lot, I also have a Fuji F30 and this has fixed my problem. 

~pAul.

---


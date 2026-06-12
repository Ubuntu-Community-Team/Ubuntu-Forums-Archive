---
title: "Help - Photo Importing Error"
date: 2007-03-13
forum: General Help
---

### Post by (chubbstar) on 2007-03-13
A few days ago my Ubuntu Edgy started acting up and Import Photos stopped working. The program still pops up automatically and detects my camera (Canon IXUS65) but eventually spits out this error:

> An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

I hadn't changed any of my cameras settings nor anything that I can think of that would have effected this. Anyone know whats wrong?

---

### Post by tgone on 2007-03-15
> **(chubbstar) said:**
> A few days ago my Ubuntu Edgy started acting up and Import Photos stopped working. The program still pops up automatically and detects my camera (Canon IXUS65) but eventually spits out this error:



I hadn't changed any of my cameras settings nor anything that I can think of that would have effected this. Anyone know whats wrong?

I'm having the exact same problem with my Canon S230. I haven't changed any settings, and my camera has always worked. Now all of a sudden it doesn't.

What's going on?

---

### Post by ChanelLeigh on 2007-03-22
> **tgone said:**
> I'm having the exact same problem with my Canon S230. I haven't changed any settings, and my camera has always worked. Now all of a sudden it doesn't.

What's going on?

Again, I'm having the same problem, getting that same error message. I have a Cannon A610. Perhaps this is a problem unique to Canon cameras. Let me know if you guys figure out how to fix it.

---

### Post by hagar_am on 2007-03-22
Hi! The same error with Canon S2 IS, everything was working fine few days ago. I found fix on polish forum. Here it is:
> sudo gedit /etc/udev/rules.d/40-permissions.rules

Find line like this:
> SUBSYSTEM=="usb_device", MODE="0644"

Replace it with:
> SUBSYSTEM=="usb_device", MODE="0666"

That fix the problem, but still no idea why it happens.

EDIT:
[http://ubuntuforums.org/showthread.php?t=383058&highlight=canon](http://ubuntuforums.org/showthread.php?t=383058&highlight=canon)

---

### Post by tgone on 2007-03-22
This fixed my problem: [https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250)

---

### Post by (chubbstar) on 2007-03-22
thanks alot hagar_am! that fixed the problem perfectly. i appreciate your help.

---

### Post by rapattack1 on 2007-03-23
I have the same problem with my Olympus D535 camera and I posted about it but no one helped. Can the fix help me? How do you do it because I looked at the links above. I do not understand how to do it as I am still a beginner. Thanks!

---

### Post by (chubbstar) on 2007-03-23
just open the terminal and put in the following line of code:
> sudo gedit /etc/udev/rules.d/40-permissions.rules

then a file will open up and search within it for the following line:
> SUBSYSTEM=="usb_device", MODE="0644"

and replace that line with:
> SUBSYSTEM=="usb_device", MODE="0666"

if you have the same problem as i did this should work.

---

### Post by rapattack1 on 2007-03-24
Still got the same error unfortunately. Sorry to report!

---

### Post by (chubbstar) on 2007-03-25
welp that sucks. im a total amateur at ubuntu.. i switched less then 2 months ago so i dunno what to tell ya. 

i suppose the error might be different for you since youre using an olympus and not a canon like myself.

---

### Post by rapattack1 on 2007-03-25
Yeah that is about the same time I installed Ubuntu too and it is my first Linux experience. I am putting Debian on another machine soon so we'll see what happens there. Thanks for trying!

---


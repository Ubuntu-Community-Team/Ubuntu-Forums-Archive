---
title: "Trying to access storage on my phone"
date: 2008-03-01
forum: General Help
---

### Post by sidefx2 on 2008-03-01
I was searching and reading some other threads, and a lot of people seem to have trouble with syncing and such.  I am just looking to be able to access the content of the memory on my phone via USB.

I'm pretty novice, and I can't figure out how to access it.  Any advice anyone can give me on the subject would be appreciated.

---

### Post by Whiffle on 2008-03-01
I don't know hwo to help you at this point, but whoever does will need to know what kind of phone you have and which ubuntu you're using. :)

---

### Post by sillyxone on 2008-03-01
if it's a rather new phone, try to see if it can be put into USB Storage mode, then it will act as a USB thumb drive when connected.

---

### Post by tgalati4 on 2008-03-01
Try plugging it in and see if an icon (or 2) show up on the desktop.  If so, then double-click on the icon.

Most newer phones automatically go into USB mode when you plug them in.  Any recent Ubuntu (Feisty, Gutsy) will automatically mount the phone and put icons on the desktop.  If there is a built-in camera, sometimes a message will come up asking if you want to import pictures.

The phone is normally mounted to the /media directory:  In a terminal

>cd /media

>ls -la

It could be given one of several names:  PHONE, disk, USB, etc.

---

### Post by sidefx2 on 2008-03-02
> **Whiffle said:**
> I don't know hwo to help you at this point, but whoever does will need to know what kind of phone you have and which ubuntu you're using. :)

The phone is the Motorola Q c9, OS is Ubuntu 7.10 Gutsy.


So far I've tried just plugging it in but I don't see any icons on the desktop or anything in the media directory (aside from the CD rom).

---

### Post by sidefx2 on 2008-03-05
Well I figured it out, I needed to put the gnome-bluetooth package on my computer, and that pretty much solved everything.  

To send just type: gnome-obex-send filename
To receive just run the app and send the file on the phone side.

---


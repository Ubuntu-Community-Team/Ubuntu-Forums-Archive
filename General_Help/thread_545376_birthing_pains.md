---
title: "birthing pains"
date: 2007-09-07
forum: General Help
---

### Post by venstebank on 2007-09-07
Im sure Im not the first to post these problems, but here goes:
 
Ive been running Feisty on my machine at home, but Im having trouble installing new software like wine, vlc, compiz fusion & others 'cause I don't hav an internet connection. With XP I connect using my phone via usb & I found what seems to be the drivers (to allow my Motorola V360 to comunicate with Ubuntu via usb) but I cant install it 'cause it seems I need an internet connection to install the phone drivers. Is this really the case? or are there ways of installing software without being connected?  All of the software I want to install on Feisty doesn't seem have a file I can download in XP & install in Ubuntu they all point to a series of terminal commands.

I dont see How u can install new software by simply entering commands in the terminal without an internet connection, or does it actually work like that. All the forums seems to point in that direction without mentioning the need be connected. 

please help

---

### Post by hikaricore on 2007-09-07
I know nothing about your specific phone, but I don't believe you're going to be able to use it as a modem while running Linux.  (could be wrong)
The first place to start would be to run:  **dmesg**
After plugging it into a usb port to see if the cdma kernel module is recognizing the phone.

Onto the other topic..

It's _implied_ that you need to be online to install most things in Ubuntu.
This being said there is no need to state it in every post about installing this and that, because it's common sense.

---


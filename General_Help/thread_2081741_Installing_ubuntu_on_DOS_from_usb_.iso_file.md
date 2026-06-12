---
title: "Installing ubuntu on DOS from usb .iso file"
date: 2012-11-07
forum: General Help
---

### Post by glensgrant on 2012-11-07
Hi guys
So I'm trying to install the newest ubuntu version on a laptop with no cd rom drive or operating system outside of DOS, which I am unfortunately not very familiar with. I have a usb with which I want to install ubuntu, but am not sure how to access the file. Also, since I don't have any form of software on the other computer, is there a way in which I can prepare the .iso installation file to launch directly off the drive?
thanks in advance

---

### Post by Slim Odds on 2012-11-07
> **glensgrant said:**
> Hi guys
So I'm trying to install the newest ubuntu version on a laptop with no cd rom drive or operating system outside of DOS, which I am unfortunately not very familiar with. I have a usb with which I want to install ubuntu, but am not sure how to access the file. Also, since I don't have any form of software on the other computer, is there a way in which I can prepare the .iso installation file to launch directly off the drive?
thanks in advance
That's not DOS. That's your BIOS.
You need to figure out which key brings up the "boot" options so that you can select USB. On some systems, it's F12. Yours might be different.

---

### Post by glensgrant on 2012-11-07
I'm pretty sure it is DOS. FreeDOS kernel verson 1.1.26a. came preinstalled. Haven't figured out how to do anything past setting time and date. 
Now it taunts me with its fiendishly clean screen and C:\>.
Also is it possible to run the iso file the way it is once I finally find it?

---

### Post by Slim Odds on 2012-11-07
> **glensgrant said:**
> I'm pretty sure it is DOS. FreeDOS kernel verson 1.1.26a. came preinstalled. Haven't figured out how to do anything past setting time and date. 
Now it taunts me with its fiendishly clean screen and C:\>.
Also is it possible to run the iso file the way it is once I finally find it?
No, the ISO is a bootable image. You need to boot from it in your BIOS.

---

### Post by idoitprone on 2012-11-07
> **glensgrant said:**
> I'm pretty sure it is DOS. FreeDOS kernel verson 1.1.26a. came preinstalled. Haven't figured out how to do anything past setting time and date. 
Now it taunts me with its fiendishly clean screen and C:\>.
Also is it possible to run the iso file the way it is once I finally find it?

well you are booting into dos.

Installing ubuntu should not require you to boot into the os.
Booting goes like this

turn on->bios->bootloader-> os 

We want to intercept on the bios to choose the bootloader we wish to boot.
In this case, we want the bios to run the live cd
If you boot to dos then you cannot install ubuntu

When you see post, try to press the key that allows it go to setup

---

### Post by grahammechanical on 2012-11-07
There are a couple of things that you need to make clearer. Does this laptop let you boot from a USB memory stick?

And then there is this

> I have a usb with which I want to install ubuntu, but am not sure how to access the file.

Please explain how you put Ubuntu on this USB. Did you copy the ISO image file to it or did you write/burn the ISO image to the USB. If you have created a Live USB version of Ubuntu and if your laptop can boot from a USB drive, then Just put the USB stick in the USB port and boot Ubuntu into a live session. Then you can try it out and install from there.

This is how the install process will go:

[http://www.ubuntu.com/download/help/install-desktop-latest]("http://www.ubuntu.com/download/help/install-desktop-latest")

This is how to create a bootable Ubuntu USB on Windows:

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")

Regards.

---

### Post by glensgrant on 2012-11-07
Wicked - thanks guys. You're absolute heroes!

---


---
title: "The ubuntu installer is missing contents"
date: 2019-03-30
forum: General Help
---

### Post by logank1232 on 2019-03-30
I’m trying to install 18.04 LTS on my hard drive from my usb drive, it boots just fine but when the computer boots it opens this grub menu and I just click on ubuntu and it sends me to the installer, so the installer is missing like HALF of the stuff i've seen in videos with it, from what I know theres supposed to be an install ubuntu and try ubuntu button on the first slide, neither of those are there and its only a language selection, second off when it installs ubuntu it only installs it to my usb stick and not my hard drive (removing the stick after installation makes the entire OS non-functional) and third the installer is missing the ENTIRE wifi setup part, all I get is language, install options which always end up installing onto my usb and timezone selection, I’ve never used this OS before and I really want to try linux but I honestly have NO idea what is going on here. I thought this would be as easy as installing any other old OS but I was clearly wrong. What am I doing wrong?

---

### Post by TheFu on 2019-03-30
Did you follow these [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) instructions to create the flash boot drive?
Did you validate the stuff put on the flash drive was uncorrupted?  That should be available to check as the last choice on the boot from either flash or optical drives, if it was created correctly.  There are different guides for Linux, Windows, OSX.

How new is the hardware?  Bleeding edge stuff can have issues.  Certain vendors don't follow standards well, so if you can provide the make and specific model, someone might be able to help.  Certain storage, especially really new types, require care from the installer (person) to choose the correct locations.

Support for different wifi cards depends on the vendor.  Actually, all hardware support depends on the vendor, so if there are devices that don't work, complain to the vendor about their poor linux support.  You will learn to choose hardware carefully. That is mandatory if you run any non-Windows OS.

Installing Linux on non-UEFI hardware is still really easy.  From boot to done is 15 minutes with an 18.04 minimal install.

Assuming all that stuff above is checked and validated, can you boot into the live-Ubuntu, install boot-repair, run it, choose the button to "gather information" and post the URL is makes back here?

Welcome to the forums. We are all volunteers here.

---

### Post by CatKiller on 2019-03-30
From the description it sounds like you've not turned off Fast Boot in Windows, which means that the hard drive is marked as in-use and won't be visible, and that you're using the server or alternate install image rather than the desktop one.

---

### Post by TheFu on 2019-03-31
> **CatKiller said:**
> From the description it sounds like you've not turned off Fast Boot in Windows, which means that the hard drive is marked as in-use and won't be visible, and that you're using the server or alternate install image rather than the desktop one.

Ah - Server installer.  That would do it. 

In Linux, Servers don't have a GUI. They aren't designed to be used by people without extensive Unix knowledge and certainly shouldn't be the first install attempted by someone knew.  Servers generally don't have wifi either, so lacking wifi drivers is expected.  Use the wired ethernet connection.

If you are trying to install Ubuntu side-by-side with any other OS, there are some required steps that must be taken. I don't know if the server installer has that capability built-in for a wizard install. It can be done manually, but for someone new-to-linux, that wouldn't be a good idea.

---


---
title: "Wihich TV Tuner is the best for Ubuntu"
date: 2007-11-13
forum: General Help
---

### Post by xelapond on 2007-11-13
Hello everyone,

Which TV Tuner is the best for Ubuntu?  I would prefer one with a remote and dual tuner, if possible, but All I really want to do is be able to record TV on MythTV and Watch Live TV.

Also, are there any PCI Express X1or X4  that would would work?  Those are the only slots I have left:^)

Thanks, 

Alex

---

### Post by stimpack on 2007-11-14
Bump, I'd like to know too, having problems searching for anything. Particulary USB tv-tuners in my case as I have many computers.

---

### Post by Damanther on 2007-11-14
The Hauppage chipsets seem to work the best. Looks like several of them work ok on Feisty, but none tested on Gutsy yet. (At least no results posted yet).

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaHauppauge]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaHauppauge")

Here is a list of other multimeda devices, some other tuners etc.

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia")

Edit: Forgot to say. I use the PVR 150. Works fine, but I have not tried the USB versions.

---

### Post by stimpack on 2007-11-15
Thanks Damanther, that includes the Nova stick I was interested in.

---

### Post by oscarsfriend on 2007-11-15
Personally, I would steer clear of USB tuners (and that probably includes the Haupaugge dual tuner Nova-T 500 PCI, which is effectively two usb tuners with a USB controller on board).  The problem is that these devices will occasionally disconnect, and will fail to function until the power is cut (rebooting wouldn't fix it for me).  This problem used to be quite bad (from what I have heard), but is not too bad now.  It happened to me one or two times a month, which, especially as my machine boots up automatically to record unattended, began to become irritating.  My keyboard would fail to work properly whenever this happened.  As a result I bought a second Haupaugge Nova-T single turner PCI card, and ditched my Freecom USB stick (which also had the annoying problem of occasionally showing up as two devices, which caused untold problems with MythTV, until I hacked my way around it).  I'm using Feisty and I don't know if this has been fixed with Gutsy (this is a kernel/driver issue, afaik), but I think not.

---

### Post by starfry on 2007-11-15
I am successfully using Nebula Electronics DigiTV with MythTV.

---

### Post by anaconda on 2007-11-15
> **stimpack said:**
> Thanks Damanther, that includes the Nova stick I was interested in.

Nova stick does work, but (like with most digitv-tuners) you need to get the firmware file and copy it to /lib/firmware folder to get it working..

And kaffeine is probably the easiest program to get tv working..

---


---
title: "How to install to a different place from the normal place?"
date: 2020-11-12
forum: General Help
---

### Post by akangka on 2020-11-12
My laptop harddisk is currently broken, so I have to use try ubuntu. Since it's a live os, it means that any installation will be wiped. Is it possible if I installed the program to the different usb drive instead so that any new installation will not be lost?

---

### Post by guiverc on 2020-11-12
You haven't given any details as to which Ubuntu (or *flavor*), nor release of Ubuntu (or *flavor*). 

Ubuntu currently comes with 3 different *live* install options (chosen by which ISO you download & use), and if you're talking about an ISO that uses `ubiquity` (default installer for Ubuntu desktop) I'd suggest you use the *Something-else* option which lets you choose which device to install to.

I've used that to install to a thumb-drive for example, though you can also select any other drive or partition you wish too; something-else gives you control over what occurs.

I've not tried with `subiquity`, and a quick look on `calamares` didn't look easy so I never tried.

Details such as Ubuntu Desktop (`ubiquity` is the installer), Ubuntu Server (`subiquity` is the *live* installer) control which *installer* exists on the media. Most Ubuntu *flavors* also use `ubiquity` though some also use `calamares` but that will depend on which  release is used too.

Yes it's possible, however it'll depend on which you want to install (server/desktop/flavor/release..)


FYI:  The *live* media means it runs in memory only, and nothing is installed unless you tell it to install. ie. it's *live* media that I carry with me, that I use on other peoples computers (*who trust me*) when I borrow their machine, so I don't touch their files or anything... just borrow they screen, keyboard & box using only their power.  When I reboot, their system is untouched.

---

### Post by Impavidus on 2020-11-13
Sounds like you want a live system with persistence.

A simple live system runs completely in RAM. Nothing is saved to permanent storage, so when you reboot, all applications you installed in the live session are gone. With persistence, there is a separate partition on the live usb where documents and installed applications are stored, so they survive a reboot. Most tools that you can use to create a live disk allow you to create one with persistence.

A live usb with persistence is not a full install. It's limited in the amount of files and updates it can handle and it can't handle any kernel updates. For a longer term solution, you can use a full install to a usb drive. Just install like you normally do, but point the installer to the usb drive instead of the internal hard drive. There may be a complication as the installer may try to install the bootloader to the EFI partition of the internal hard drive anyway. Disable it in UEFI or physically remove it.

And of course, you can get a new harddrive for your laptop. Usually, although some models make it hard to replace the hard drive.

---


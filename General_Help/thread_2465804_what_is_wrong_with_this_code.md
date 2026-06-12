---
title: "what is wrong with this code?"
date: 2021-08-11
forum: General Help
---

### Post by raul-mccai on 2021-08-11
make $@ all 1>>log.txt || exit 1

This is line 31 from a realtek autorun.sh file for an ethernet driver.
When I try to run the SH file  it stops at line 31 and reports  "make: command not found"

---

### Post by GhX6GZMB on 2021-08-11
It seems a command that make needs is not installed.
.

---

### Post by Holger_Gehrke on 2021-08-11
No, if make was calling something that is missing you'd get something like 'make: xxxx: command not found' (with xxxx being the name of the missing program). It's make itself that is not installed.

Holger

---

### Post by raul-mccai on 2021-08-11
you are correct.
I checked  Can't find Build-essentials or Gcc  can't get 'em cos  no web access. 
This is a pickle
Everything I need I need the web for. I don't know how to compile it manually. And I haven't found anyone posting about it online.
There was  a time when Cannonical was not including the ethernet drivers in the distro, but I believe they do now.
I suspect what's happening is because my  On board Ethernet  functionality is broken but not lysed the install package sees it and tries to load for it and ignores the pcl-e card

I may have to let this drive take a nap until I  get a new mainboard.

---

### Post by Impavidus on 2021-08-12
I think make, build-essential, gcc and some related tools are included on the live disk, but not installed by default. Insert your live disk, enable the repository on the live disk in your settings (it may be labelled cdrom, even if it's a usb) and install from there.

---

### Post by raul-mccai on 2021-08-12
there is a Folder named Locale  and  Files named Autorun.ico,  and autorun.inf, and kernel.sys, Command.Com and Autorun.bat. and Autoexec.bat
The ones I can open  are the Locale folder and   ico image file.  The locale folder has  ega.cpx files numbered 1 - 18  and some keyboard files.  Nothing  that seems a likely candidate

---

### Post by raul-mccai on 2021-08-13
> **Impavidus said:**
> I think make, build-essential, gcc and some related tools are included on the live disk, but not installed by default. Insert your live disk, enable the repository on the live disk in your settings (it may be labelled cdrom, even if it's a usb) and install from there.

I've searched using the terms you have there and  I've found nothing about enabling the repositories on the installation disk or USB.
The only repositories I can find are the ones online like universal etc. 

You sure this is a thing?

---

### Post by grahammechanical on 2021-08-13
Open the Software & Update utility and in the Ubuntu Software tab there will be a box with the title Installable from CD-ROM or DVD. Tick the box with the label Cdrom with Ubuntu and the Ubuntu DVD or USB stick will become a repository. If you successfully install the packages you want from the USB stick then untick the box otherwise Software Updater will complain that it cannot find the repository every time you update.

Regards

---


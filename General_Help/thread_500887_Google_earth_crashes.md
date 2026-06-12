---
title: "Google earth crashes"
date: 2007-07-14
forum: General Help
---

### Post by alek66 on 2007-07-14
I recently installed google earth using Automatix2, and when I try to run it, it crashes and throws me out to log in screen. Its as if I do a ALT+CTRL+BACKSPACE.
Any ideas on how to fix this?

---

### Post by ckoester on 2007-07-15
I have the same problem after an installation from source.  (Using install instructions from the [wiki]("https://help.ubuntu.com/community/GoogleEarth"))

It seems as if Google Earth is crashing X.  I also lose my mouse pointer after the crash and have to reboot the machine to recover.  (The mouse is functional but I cannot see it.)

---

### Post by alek66 on 2007-07-15
I fixed it installing the newer Nvidia drivers.
This case is closed!:guitar:

---

### Post by ckoester on 2007-07-16
Updating Nvidia drivers also fixed my problem.  I installed the Nvidia accelerated graphics drivers with the Restricted Drivers Manager.

[INDENT]System - Administration - Restricted Drivers Manager[/INDENT]

For more information on Nvidia drivers, see the wiki page [Binary Driver Howto / Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by notoriousdbp on 2007-07-27
Mine does the same but I don't have a Nvidia card.  In previous versions of Ubuntu I have been able to run Google Earth fine with no problems.  For some reason, this build seems to be causing problems.  Can anyone help?

---

### Post by zzztownsend on 2007-08-05
I have the same problem - google earth installs OK, but when I run it I get the splash screen followed by a gnome crash and restart.

device manager tells me I have this graphics adapter (on board)
Silicon Integrated Systems [SiS]
65x/M650/740 PCI/AGP VGA Display
And restricted device manager tells me that I dont have any hardware that requires restricted drivers.

does anyone have any experience of a fix with this SiS graphics/driver?

Cheers

Matt

---

### Post by boomcat on 2007-08-06
Running Google Earth crashes my laptop back to the logon screen. This is a Thinkpad T20 running Feisty Fawn.

---

### Post by notoriousdbp on 2007-08-06
For the record, mine is an SiS chipset too

---

### Post by askantik on 2007-08-12
I'm having the same problem.  My chipset is an SiS 760GX.  Google Earth ran fine on XP on same computer, although I highly doubt that has anything to do with the problem!!

---

### Post by sddfdds on 2007-08-16
This problem exists on Gutsy as well.  It is not just Google Earth though, it's OpenGL related...I got the same crash using VLC when I changed the video output mode to OpenGL.

---


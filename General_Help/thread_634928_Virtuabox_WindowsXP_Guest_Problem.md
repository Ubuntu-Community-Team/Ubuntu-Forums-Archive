---
title: "Virtuabox WindowsXP Guest Problem"
date: 2007-12-08
forum: General Help
---

### Post by rgd55 on 2007-12-08
I get a "Fatal:Could not read from the boot medium!System halted" message
whenever I attempt to boot my Windows XP cd.
 The cdrom options are set to /dev/cdrom and I believe I need to edit 
something.I am very new to Ubuntu and not sure what Terminal commands
to use.
Thanks:confused:

---

### Post by gobbles414 on 2007-12-08
Hi rgd55,

Welcome to Ubuntu Linux! Click [here]("http://www.virtualbox.org/wiki/User_FAQ") for the VirtualBox FAQs and manual. Some ideas:

* Is your XP disk a retail copy or did it come with a computer? Even if it is a copy of Windows that came with the computer you are currently using, it may not work in VirtualBox. This is because many computer companies configure their Windows operating system disks to only work with a certain BIOS. VirtualBox emulates a BIOS, so the Windows CD may think you are trying to install on an unauthorized machine.

* There is a preference called *Enable Passthrough* in the CD/DVD-ROM settings of VirtualBox. Try enabling or disabling it as dictated by your current settings.

* What software are you trying to run in VirtualBox? You may find it easier to use [Wine]("http://www.winehq.org/"), a free Windows emulator that does not require you to own a copy of Windows. You might also consider making your computer a dual-boot system. This will put Windows on one part of your hard drive and Ubuntu on another. Then you can just reboot to switch between the two operating systems.

---


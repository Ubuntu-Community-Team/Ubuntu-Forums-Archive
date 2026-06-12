---
title: "Trying to install 15.10 with 2 problems stopping me."
date: 2015-11-05
forum: General Help
---

### Post by cylent on 2015-11-05
Starting out fresh on Ubuntu 15.10 with some odd issues.

I have a laptop that I will install Ubuntu on.
This laptop has a secondary screen attached to it via HDMI cable. So my setup in windows two screens. the laptop + and the external screen (which is my primary viewing)

_Problem 1_: if i have the HDMI cable plugged into my external screen during boot-up of the live Ubuntu USB it will forever be stuck on a black screen and the USB stick light will continue blinking ... i will get no desktop.
if i unplug the screen (HDMI cable) and boot-up it'll load just fine. Then i can plug in the HDMI cable and both screens will work.
Whats going here?

_Problem 2_: Last week on this laptop I decided to try windows 10 for which i upgraded windows 8.1 ... after a few days I did a "roll back" as offered in windows 10 to return to windows 8.1. That worked OK and i am now back in windows 8.1.
Now, when i want to install Ubuntu it gives me the option of deleting the while drive or doing a custom install. It recognizes only a few hundred megs as a windows 10 loader partition and the reset as "ntfs unknown".
I want to re-size and not mess things up. Not ready to lose all my data just yet. 
Whats going on here?

The laptop is a:

Acer R7-571G with a Core i5 processor and  a 1TB SSD drive.

Thank you

---

### Post by oldfred on 2015-11-05
Windows probably just  reset to have its always on hibernation or fast start up setting enabled. You need to turn that off.
 Fast Start up off/hibernation - Windows 8 or 10 UEFI or BIOS boot.
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)


       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screeens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---


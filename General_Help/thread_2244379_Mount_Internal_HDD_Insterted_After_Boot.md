---
title: "Mount Internal HDD Insterted After Boot"
date: 2014-09-15
forum: General Help
---

### Post by M4rotku on 2014-09-15
Hey guys,

I am trying to fix my wife's laptop, on which the windows 8 OS has crashed while trying to update to 8.1.  I want to back up her files before trying to fix windows, due to the high likelihood that windows will lose everything.  I created a ubuntu live usb and am trying to use it to recover the files.  For some reason, if the internal hdd is connected during boot, the laptop insists on going to a windows error screen even before giving me the option to boot from the flash drive.  The laptop will only consider booting to the flash drive if the internal hdd is removed.  Because of this, I am disregarding very basic rules and trying to plug in the internal hard drive while the laptop is running ubuntu via flash drive. [-X

My main problem is that when I plug in the internal hdd, I cannot get the /dev/ directory to refresh and display the internal hdd as sdb1,2,etc.  Is there some sort of command that I can run which would force the OS to recheck/repopulate the devs as though it were booting?  Then I could mount the /dev/sdb per usual and recover my wife's files.  Any and all ideas are very welcome and appreciated.

Many thanks,
M4rotku

---

### Post by PondPuppy on 2014-09-15
You've probably tried this: can you get to the BIOS? Set it to boot from USB as first option? Can you boot from a live CD/DVD, or does the laptop not have an optical drive?

Check TestDisk, usable from live media. I've found it very useful when HDDs are unresponsive: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by yancek on 2014-09-16
Have you been able to access the BIOS?  Normally, one would see a message to press ?? key to enter setup.  On my HP Desktop, F10 substitutes for the ??  You should see a Boot tab and a Boot priority and under that, you should see any harddrives or flash drives attached to the computer on boot and be able to select one by moving it to the top of that list.  The method varies but there should be instructions on the page on how to do this.

---

### Post by oldfred on 2014-09-16
If you still have secure boot on in UEFI and you may have to turn on an allow boot from USB setting. That is so you cannot boot something like your live installer.

Check your UEFI settings.

---

### Post by M4rotku on 2014-09-17
No, I have not been able to access the BIOS at all.  If the hdd is plugged in, the laptop goes straight to the Windows 8 update screen, which continues on forever because the update failed and broke the OS.  There is an option to press the f11 key, which brings up a Windows menu suggesting different ways to fix the computer.  We have tried all of the ways which don't involve fully resetting the laptop, which would delete all of my wife's files.  I would much rather back up her files before trying that option, instead of having the files be deleted and then having to recover them.

To clarify, I have been able to boot from the flash drive, so there is no setting preventing me from booting from usb.  The problem is that I can't get the /dev directory to repopulate once the hdd has been plugged in (while the OS on the flash drive is currently running).

---

### Post by rolkin on 2014-09-17
Try booting the computer without the hdd and without the usb...it may take you to the bios automatically, or maybe more likely, give you some options when it doesn't detect any bootable devices. From there, and assuming you can get into the bios by doing this, make sure to turn off any options like "Secure Boot" or "Fast Boot", and maybe even turn on something like "Legacy Support/Boot". This should at least let you plug the hdd back in, boot from the usb, then it will be automatically detected in /dev to then mount, copy, etc.

---


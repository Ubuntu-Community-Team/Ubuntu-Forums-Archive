---
title: "Live USB boot will not work"
date: 2018-08-25
forum: General Help
---

### Post by srkasdorf on 2018-08-25
I am currently trying to dual boot ubuntu with windows 10.  I created a live usb installer using both rufus and universal usb installer, but the install does not work.  I have an 8gb verbatim usb stick that I tried first, but when I try to install ubuntu it says that I do not have enough hard drive space, and it looks like it is only reading the usb and not my ssd.  I tried with a sandisk usb but the ubuntu load screen freezes before it can get to the install.  I read that some usb drives do not work well with the install so maybe that is the issue.  I also read that if a ssd is not in ahci mode then it will not recognize the drive, but I am running in raid so that should not be a problem.  I tried switching to ahci anyway but it did not help.  I also tried installing the live usb as ntfs instead of fat32 but that made it so that windows does not recognize the boot file.  I am utterly stuck with a process that I feel should not be that hard.  Any suggestions would be greatly appreciated.

---

### Post by Autodave on 2018-08-25
Did you disable *fast boot *in the BIOS?  Windows does not shut down: it hibernates. So as a result, the HD stays in use and the installer will report that there is no space found.

You will need to disable *fast boot, *then go into Windows and shut Windows down (it will take awhile) and then restart computer with you install medium.

---

### Post by srkasdorf on 2018-08-25
I did disable fast start up under power options, I do not see anywhere to disable fast boot in the BIOS.  Is that what I needed? I think this is probably the issue.  However when I shut down the computer, windows still restarts and resumes my webpage, so it's not clearing the cache like it should on a full shut down.  I've tried playing around with it and can't get the fast boot off.

---


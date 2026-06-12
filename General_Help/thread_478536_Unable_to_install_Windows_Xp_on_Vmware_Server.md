---
title: "Unable to install Windows Xp on Vmware Server"
date: 2007-06-19
forum: General Help
---

### Post by demonbro on 2007-06-19
I need help with a really annoying problem.  I followed a tutoril and installed Vmware server 1.03.  It works great, so it appears to be installed correctly, but when i create virtual machine of windows xp, it says there is no bootable disc in the drive.  The first time i did it, it installed xp be the windows activation kept coming up even though i had activated it.  So i deleted that Vm and made another one, but know it says there is no bootable disc in the drive, which is untrue.  Anyone else had this problem?  Im using Vmware server1.03 on Ubuntu Fiesty.

What im trying to do is just make a virtual machine of Xp so i can run Macromedia Flash, and Line 6 guitar software thats it.  I dont even have to use Vmware(heard it was the best), anyone have any ideas on how to accomplish this?

thanks
erik

---

### Post by mitch.c on 2007-06-20
Assuming that the disk is in fact bootable, try enabling "Legacy Emulation" for the CD-ROM drive in the Guest OS settings.
[URL="http://ubuntuforums.org/showthread.php?t=377083"][COLOR="Red"]
UAResolved[/COLOR][/URL]

---


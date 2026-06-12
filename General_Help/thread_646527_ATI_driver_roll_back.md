---
title: "ATI driver roll back"
date: 2007-12-21
forum: General Help
---

### Post by jimmyhilldrix on 2007-12-21
I ran the ubuntu update that was available a few day's ago (today is December 21st, and I think I ran it yesterday but I'm not sure) and the system required a restart.  I don't know why but I'm assuming it was because the ATI video driver that I'm using was updated.  This new update has been causing some weird issues with windowed applications run through a secure shell client.  I'm currently running a dual-head monitor setup and the lower right corner of the second screen has garbage in it (I assume that there's garbage in the video buffer) and the area around the mouse cursor also has garbage in it.  This garbage is displayed only when I switch to a desktop that has one of these applications running in it; locally run apps don't seem to have this problem.  Also the garbage disappears if I open the ATI video utility and close it (I assume this triggers some sort of global refresh). 

If there is a fix for this please let me know.  Otherwise I would be fine with simply rolling back the driver (if that's possible) I just don't know how.

Thanks for any help.

---

### Post by ajgreeny on 2007-12-21
There was a new kernel yesterday 20.12.07 which is the most likely reason for your problem.  Can't help with the ati card, however, as mine uses the OS ati driver.  All is working OK on my system since the upgrade.  With so little info on your hardware it is not possible to help further;  what graphics card have you and what driver are you using?

---

### Post by jimmyhilldrix on 2007-12-21
The info is:

Graphics Card: RADEON X600 Series
BIOS Version: BK-ATI VER008.015.144.000
Driver Version: 8.42.3

The software I got that from is ATI's Catalyst Control Center.

Again, this only occures with applications that are run though ssh.  And it only shows up on my second monitor.  So this is probably pretty difficult to reproduce.

Also, all of the apps were written with QT 3.  I doubt that that would be an issue though.

Is there any way to roll back to the previous kernel?

Thanks again,

---

### Post by ajgreeny on 2007-12-21
In synaptic I can find the current kernel and the previous linux-image 2.6.22-14.46 and 47-generic, but that my be because I have set the preferences in synaptic to keep **all** packages in the cache.  The default is to delete packages no longer available, so you may not have the same situation on your machine.  However, have a look at teh properties of the package and see if both are there.  If so force install the older one and it may solve your problem.

---


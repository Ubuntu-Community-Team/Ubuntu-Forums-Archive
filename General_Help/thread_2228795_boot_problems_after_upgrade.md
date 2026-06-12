---
title: "boot problems after upgrade"
date: 2014-06-09
forum: General Help
---

### Post by Tony T on 2014-06-09
Greetings wizards- 
 
I humbly bow before your knowledge in quest of enlightenment....

I have a 3 computer MPI cluster running ubuntu 12.04 LTS.

I did an "apt-get upgrade" on all three computers yesterday and all three broke.

Two won't boot and are stuck on a black screen after the grub menu.
I tried all of the recovery menu options and none resulted in a good boot.

Tried the boot repair disc and it replaced grub, now I get the blue ubuntu 
screen but it just hangs there.

boot repair log link is at:
[http://paste.ubuntu.com/7616156](http://paste.ubuntu.com/7616156)

I deleted the X11 xorg.conf but there was no change.


The third computer booted but I lost my flgrx propriety 
graphics driver and had to reinstall AMD Catylist. 



Any advise you can give me on reparing the boot would be greatly appreciated.


Thanks Tony

---

### Post by LastDino on 2014-06-09
I could be terribly off but;
Sounds like a graphic driver issue, was that a kernel update?

Maybe try booting from nomodeset and see if you can install different drivers.

---

### Post by Tony T on 2014-06-09
Thank you  LastDino,

You were correct it was a graphic driver issue. 
Yes, there was a kernel update.

I couldn't get nomodeset to work maybe I didn't 
do it correctly.

I changed the grub line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset", 
did sudo update-grub and rebooted. 

There was to change in the grub menu and still woudn't boot. 
What did I do wrong?

I was able to reinstall the AMD Catylist flgrx graphic driver
remotely via an ssh network.

How to I keep this from happening everytime there's a kernel update? 
Any tips?

I still have one computer to fix. I'll you know how that goes!

Thanks a million for the help!

Tony

---

### Post by Tony T on 2014-06-09
Ok, the last compter is up and running, I did the same thing, 
reinstall the AMD Catylist flgrx graphic driver remotely via an ssh network.

I need tips on how to keep this from happening everytime there's a 
kernel update!

---

### Post by QIII on 2014-06-09
Hello! 

How did you install the driver?  If you did so from the Ubuntu repo, you should have no problems.

---

### Post by Tony T on 2014-06-09
> **QIII said:**
> Hello! 

How did you install the driver?  If you did so from the Ubuntu repo, you should have no problems.

No, it's not installed from the Ubuntu repo. This is a proprietary AMD fglrx graphics driver, I downloaded it  from AMDs web site. This driver is required by the GPU computing software that I use.

---

### Post by Tony T on 2014-06-16
Greetings from Michigan!

How do you AMD Catalyst users manage your kernel updates?

My screen will go black every time on all three of my computers.
Then I jump hurdles re-installing catalyst from a recovery disc.

Is there a work around?

Here's my original thread:
[http://ubuntuforums.org/showthread.php?t=2228795](http://ubuntuforums.org/showthread.php?t=2228795)

---

### Post by QIII on 2014-06-16
*Threads** merged***.  Please don't start new threads on the same subject.

If you do not use the repo or build a .deb and use dpkg, this will happen every time.  The best thing to do would be to watch your updates for a kernel update, respond "No" to the question of whether you want to do it, uninstall your driver via amdconfig, do your updates and reinstall the driver.  There is no jumping through hoops or recovery disk necessary.  Use the same installation file you downloaded before -- which you should have kept a copy of for just this reason.

The driver in the repo, by the way, IS the Catalyst driver current at the time of the release.  Unless you need the very latest driver for some reason, installing fglrx-updates, fglrx-amdcccle-updates and xvba-va-driver from the repo will ensure that this does not happen.

---

### Post by Tony T on 2014-06-16
Thanks for the quick answer QIII

---


---
title: "Xubuntu keep uninstalling Wine"
date: 2014-09-14
forum: General Help
---

### Post by WB0HYQ on 2014-09-14
I've installed Wine three times now.  The last time (about a month ago) it ran fine and let me run a few Windows programs then, just like the previous two times, I get a notice that says the system can do a "Partial Upgrade" and do I want to do it.  If I say "no" then the notice keept nagging me, if I say "yes" then Wine and another 15 or so libraries and apps get uninstalled without my saying NO.

Strangely enough, the entry in the Applications Menu and the desktop right-click context menu BOTh still have Wine listed (along with the games/apps I've seccessfully run).  Clicking on any of them after this "partial upgrade" produces NOTHING at all - no error, and no program running.

Is this normal, or is it just the Ubuntu/Xubuntu don't like Wine running on my system?

EDIT:  WHile I'm at it, I can see now that several more apps have become uninstalled by this "partial Upgrade".  My XScreensaver is also uninstalled every time which I really don't understand.  Where is this "decision" made to uninstall items I want to keep?  Shouldn't I have some control overe what I want unistalled?

Bill

---

### Post by pissedoffdude on 2014-09-14
How are you installing wine?  Did you remove any packages when you installed it.  Also, be sure you have the xubunt-desktop meta package installed

---

### Post by grahammechanical on 2014-09-14
There are 4 reasons why we get an offer of a partial upgrade. And I know of 1 good reason for refusing the offer. But you have already worked out what that reason is. Lets us revise the 4 reasons why we get that partial upgrade offer.

1) A previous upgrade that did not complete - they mean an upgrade from one version of Ubuntu to the newest version.
2) Problems with some installed software.
3) Unofficial software packages not provided by Ubuntu.
4) Normal changes of a pre-release version of Ubuntu.

Let us assume that it is not item 1 or item 4. So, which is it? Item 2? Or item 3? Have you installed any software through a PPA? If so, now disable the PPA. Have you download any software from some web site? Is it compatible with the version of Ubuntu that you are using.

Wine and those other libraries are being removed because of conflict with other libraries.

Regards

---

### Post by WB0HYQ on 2014-09-14
I upgraded a long time ago (over 4 months) from Ubuntu 12.04 to 14.04.  That was the only "Upgrade" I ever did.  Since that time, everything has been running just fine -- except these periodic uninstalls of Wine and few other applications (like xscreensaver) from the "partial update" dialog.  In between these "partial Update" dialogs, I have quite a few other "normal" updates of the OS and other internals.  I have just about given up on having Wine on my system due to these periodic uninstalls.  I guess it makes sense to disable the PPA in an instance of a "foreign" PPA, but I install Wine from the Ubuntu Software Center - hence, no unnatural PPA.

Just now, when I tried for the fourth time to install WIne, I am now told it will have to UNinstall my NVIDIA driver and that I just cannot have.  I went through hell getting my drivers installed for my NVIDIA card and I am not about to let a Wine install remove them.  So, I guess that makes this thread "solved".

One of the things I do after utilizing a "foreign" PPA is uncheck the box for that PPA after I've installed the software.  I did that for Gambas and (so far, anyway) nothing has tried to remove Gambas.

@P.O.D: I used the Software Center to install WIne and Winetricks.  The meta-package was part of the initial install (the first time I installed Wine) and, so far as I know, it is still installed.

@G.M.:  I see those 4 reason on the "partial Install" dialog box and, in my own mind, I can see no reason to think it may be anything other than #2.  When I install, I always use the Software Center.  Once, a long time qgo, I installed from a DEB package that I shouldn't have and it messed my system up.  Never again.  I may try Wine just ONE more time, and make sure the PPA is disabled after I do.  But that may be difficult because of where I get Wine from.  WOuldn't that be just a 'normal' PPA listed?

Bill

---

### Post by WB0HYQ on 2014-09-14
This is provided by Gambas, but it does give a lot of system information (helpful???):

[System]
Gambas=3.5.3
OperatingSystem=Linux
Kernel=3.13.0-35-generic
Architecture=x86_64
Distribution=Ubuntu 14.04.1 LTS
Desktop=XFCE
Theme=QGtk
Language=en_US.UTF-8
Memory=7983M
[Libraries]
Cairo=libcairo.so.2.11301.0
Curl=libcurl.so.4.3.0
DBus=libdbus-1.so.3.7.6
GStreamer=libgstreamer-0.10.so.0.30.0
GStreamer=libgstreamer-1.0.so.0.204.0
GTK+=libgtk-x11-2.0.so.0.2400.23
OpenGL=libGL.so.1.2.0
Poppler=libpoppler.so.19.0.0
Poppler=libpoppler.so.44.0.0
Qt4=libQtCore.so.4.8.6
SDL=libSDL-1.2.so.0.11.4

Bill

---

### Post by pissedoffdude on 2014-09-14
It gets pretty complex when you add PPAs, especially if they'r not designed for that version of Ubuntu since they have dependencies that might get upgraded from the original Ubuntu repos.  Try disabling all PPAs and reinstall the xubuntu-desktop meta package via the command line.  Then see if you're still getting probed for a partial upgrade.  If you updated from 12.04 to 14.04 it might be the case that you have a PPA that only supports 12.04, in which case you should update all your PPAs accordingly.

---

### Post by WB0HYQ on 2014-09-14
I've been over on the WineHQ Forum and found that there are some glitches that need to be ironed out between Wine and Ubuntu/Xubuntu 14.04.  Until they are fixed/resolved I'll just wait and see what happens.

Thanks to those that answered this thread.

Bill

---


---
title: "Lock screen after resume"
date: 2015-04-15
forum: General Help
---

### Post by Tiry on 2015-04-15
Hi,

I am running 15.04 using gnome 3 desktop and lightdm.
 
I am using finger print to login (Thinkpad X1).  

Almost everything works as expected:

 - I had to switch from gdm to lightdm because the gdm was doing segfault on resume on a regular basis
 - I had to desactivate ecrypts otherwise I had troubles login in with finger print 
 
However since I switched to lightdm, the "screen lock" is not activated upon resume after I close and reopen the lid. 
 
I did not find any UI to configure the fact that the screen should be locked after resume.
 
I tried to add scripts in /usr/lib/pm-utils/sleep.d/ or /etc/pm/sleep.d/ : the script is indeed executed when I run pm-suspend, however when I close and open the lid it is not the case.
 
It looks like the suspend is not done using pm-suspend when I close the lid, even if looking at dmesg I see

```
[ 5339.827666] PM: resume of devices complete after 883.144 msecs
[ 5339.827822] PM: Finishing wakeup.
```

I would appreciate any hint on where to dig further :)

Tiry

---

### Post by ajgreeny on 2015-04-15
You possibly need to find the light-locker settings, or gnome-screensaver, or even xscreensaver if any one of them is installed in gnome version.

If not, I'm afraid I have no idea how you set it to do what you want; I've never used gnome-3.

---

### Post by Tiry on 2015-04-15
Hi,

Thank you for your inputs.

The only settings UI I found is Gnome Tweak Tool.

I can see the settings that "When Laptop lid is closed => Suspend ".

This settings does work : I can activate or desactivate the suspend when I close the lid

However :

 - I don't see any settings regarding lock
 - I don't see how this suspend is done (i.e. what command is done to do the suspend)

The main issue seems to be that the suspend is done by directly calling acpi rather than doing pm-suspend :

 - I don't know if I can change that
 - I don't know why switching fron gdm to lightdm changes this

Tiry

---


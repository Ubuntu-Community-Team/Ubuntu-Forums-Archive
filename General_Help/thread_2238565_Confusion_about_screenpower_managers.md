---
title: "Confusion about screen/power managers"
date: 2014-08-08
forum: General Help
---

### Post by PaulBx on 2014-08-08
I have lubuntu 14.04 now. In the preferences menu I have Light Locker, Xfce Power Manager and XScreensaver. Who knows, there may be other setup programs that also handle screen blanking and power.

Is there any use in this redundancy? What happens when they are all running, when their settings conflict?

I also wonder about the difference between "putting the display to sleep" and switching off the display, and other such esoterica. Is the jargon consistent between the applications? What is "suspend" vs "sleep" vs "hibernation" vs "standby"? Maybe someone knows of a good internet resource that will explain all this. I will dig around in the meantime...

Are there any recommendations among these for one that handles basic needs? I am thinking of uninstalling a couple of them so I have only one left.

---

### Post by PaulBx on 2014-08-08
I found this page, which explains some things:
[http://www.spencerstirling.com/computergeek/powersaving.html](http://www.spencerstirling.com/computergeek/powersaving.html)

---

### Post by ajgreeny on 2014-08-08
I use xubuntu not lubuntu, but it makes sense to totally disable lightlocker if you have xscreensaver and set the monitor to poweroff with that instead, or you will probably get conflicts.  I use xscreensaver as a method to show my photos more than as a means of saving the screen, so whilst I accept some of the comments in that linked page, it only tells half the story for me and a lot of other users, I suspect.

For the power-manager itself you can make your own settings but bear in mind that as default, hibernate is disabled in the system and must be enabled by following information at [http://ubuntuforums.org/showthread.php?t=2219403](http://ubuntuforums.org/showthread.php?t=2219403)

---

### Post by PaulBx on 2014-08-08
I uninstalled both lightlocker and xscreensaver and will see if I can survive with just xfce power manager. That should keep it pretty simple.  If for some reason that doesn't work, I can always re-install.

---

### Post by vasa1 on 2014-08-08
Maybe you have both xscreensaver and Light Locker because you upgraded and didn't do a clean install? I think a clean install would have just the latter.

---

### Post by PaulBx on 2014-08-09
Yes, I upgraded.

Well, having just xfce power manager doesn't work. Despite having a check box for locking the screen, it doesn't lock. So I re-installed xscreensaver. That seems to work or at least to lock the screen. Who knows about the other conflicting settings between the two applications.

---


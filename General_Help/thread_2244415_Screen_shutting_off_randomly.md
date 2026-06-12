---
title: "Screen shutting off randomly"
date: 2014-09-16
forum: General Help
---

### Post by jay43 on 2014-09-16
Hello all,

So yesterday my Ubuntu 14.04 install started doing this weird thing where the screen would just start shutting off at random times.  If I move the mouse it comes back on.  I've tried timing it and it's not at regular intervals.  It could be 3 minutes, could be 5 minutes, could be 1 minute later.  

I've looked at a lot of threads here and tried a lot of the suggestions (like using set to turn off the screensaver, disabling the power management of the monitor in the power settings, etc...).  I even went as far as removing the "power" packages, rebooting, and it still occurred.  

Any thoughts?  I can provide logs but will probably need help as I'm not a Linux expert.  

Thanks,
Jay

---

### Post by Y^2om&amp;#7sgP on 2014-09-16
Had the same issue on Xubuntu

[http://ubuntuforums.org/showthread.php?t=2236371&p=13083267#post13083267](http://ubuntuforums.org/showthread.php?t=2236371&p=13083267#post13083267)

Not sure if this will help, but it's somewhere to start :)

---

### Post by jay43 on 2014-09-16
I should say that I am running XFCE as my manager.  I haven't checked to see if it occurs in other managers though.  I will check your suggestion and let you know.  Thanks.

---

### Post by jay43 on 2014-09-16
So I tried the suggestions in the article you sent, no luck, still happening.  :-(  I did notice that every time it happens in the Xorg.0.log file gets a new entry of:

[ 24056.287] (II) intel(0): switch to mode 1280x800@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none

I hope that helps.  

Thanks,
Jay

---


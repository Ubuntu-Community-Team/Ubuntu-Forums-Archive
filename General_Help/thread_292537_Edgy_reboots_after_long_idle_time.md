---
title: "Edgy reboots after long idle time"
date: 2006-11-04
forum: General Help
---

### Post by Funzo22 on 2006-11-04
Ok, I have done some stuff to my installation after installing edgy, so it might not be the upgrade... but I have installed a new splash screen for gnome and a new login manager, and switched my msn client from gaim to amsn.

Now, I did all this around the same time so its hard to tell what is causing the problems, but it seems that when I leave my computer alone for a while I come back and its at the login manager, now I set it to save my session when I leave gnome, but it doesn't in this case, firefox tells me it had been not properly quit so obviously it is not a simple configuration problem where it is set to do a proper reboot after a while.

Also I have checked with my energy settings and it is NOT set to go off or on at any specific times, or hibernate/sleep at all!

I am not sure which log files might be useful or what else to say, but I appreciate any help!

Thanks

---

### Post by jallain on 2006-11-04
Have you looked at the time stamp of /var/log/dmesg? This will tell you if you were only logged off or if your computer did in fact reset itself. If you had a complete reboot I would start looking at your power supply.

---

### Post by Lizzy on 2006-11-07
Hi, i do have the same problem. My Laptop reboots after a longer idle periode.... i never had this problem in Dapper.

How does one fix the powersupply?, cause im NOT running on battery

---

### Post by Funzo22 on 2006-11-10
> **Lizzy said:**
> Hi, i do have the same problem. My Laptop reboots after a longer idle periode.... i never had this problem in Dapper.

How does one fix the power supply?, cause im NOT running on battery

Same here I am on a laptop with AC power, and its wierd because it doesn't reboot after a certain amount of time, sometimes it makes it through 2 days in a row and then I will go to sleep and wake up with it at the login screen, and I can never get to it soon enough to check the log, its always full and hard to find, but I will keep checking

---

### Post by Funzo22 on 2006-11-11
I figured out that it is just a log out, and I still have no solution... anybody know where I can look for more info?

---

### Post by Funzo22 on 2006-11-18
For anybody who has this problem... I tried deleting all my settings and everything nothing worked, the only way I fixed it was by adding a new user with a diffrent name ans just copying over all my data to the new user

---

### Post by YaacovI on 2007-12-17
I am experiencing a similar problem in Gutsy. 

Last night I set up a dual monitor for the laptop, and changed the xorg.conf file as well as using the Screens and Graphics app to adjust my settings. The dual monitor is now working fine, but when I leave my laptop idle for a long period of time, I come back to a login screen and my session has been ended.

I've checked the various power management and screen saver settings and can't find anything abnormal, nor is there anything in the xorg.conf that looks problematic.

The hardware is a Dell Inspiron 700M (so I'm using 915resolution) and a Dell E173fp monitor. I'm running Gutsy and have been since it came out, though without the second monitor. 

I'd appreciate any help people can give,
Yaacov

---


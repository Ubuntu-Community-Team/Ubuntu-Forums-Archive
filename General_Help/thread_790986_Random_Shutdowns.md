---
title: "Random Shutdowns"
date: 2008-05-11
forum: General Help
---

### Post by dgbearcat on 2008-05-11
Hey guys,

I was using Gutsy with no problems, and then updated to Hardy, and have found myself the victim of completely random shutdowns. Usually it seems to be when I'm taxing the system somewhat with multiple windows open (it's been doing it when I was trying to run Fold.it recently) but gutsy handled all kinds of crap going on with no problem. 

I had a suspicion that it was the BIOS doing it because of overheat, but I can't even find a setting for that in my boot BIOS menu, and honestly the computer has been much hotter before. I can't find any kind of temperature monitor as the one that's been suggested (lm-sensors) doesn't seem to be working with my computer (Dell inspiron 9300).

This is the most suspicious part of the system log, so if anyone can tell me what's causing the shutdowns and how to fix it I would be most grateful. 

```
May 11 19:56:31 daniel-laptop kernel: [  513.747982] ACPI: Critical trip point
May 11 19:56:31 daniel-laptop kernel: [  513.908803] pidgin[5860]: segfault at 00000030 eip b63ff070 esp b5ff0e90 error 4
May 11 19:56:31 daniel-laptop kernel: [  513.970751] compiz.real[5814]: segfault at 07730764 eip 08055a80 esp bfcef500 error 4
May 11 19:56:33 daniel-laptop kernel: [  515.102975] ip6_tables: (C) 2000-2006 Netfilter Core Team
May 11 19:56:34 daniel-laptop exiting on signal 15
```

---

### Post by Monicker on 2008-05-11
Hrmm.  I wonder if its related to what this link suggests:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113926]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113926")

From looking at that page, it seems that your laptop might be overheating and shutting down automatically to prevent heat damage.

You might want to try running "acpi -t" once in a while, to see what the temperature reading shows.  There are other tools, such as yacpi and lm-sensors, that can give you the temps for your machine.

---

### Post by dgbearcat on 2008-05-11
> **Monicker said:**
> Hrmm.  I wonder if its related to what this link suggests:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113926]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/113926")

From looking at that page, it seems that your laptop might be overheating and shutting down automatically to prevent heat damage.

You might want to try running "acpi -t" once in a while, to see what the temperature reading shows.  There are other tools, such as yacpi and lm-sensors, that can give you the temps for your machine.

Thanks, YACPI showed me some realllly high temps (around 90c) which seems pretty crazy. I know it's felt really hot at times when I've had it on my lap, but I've got it on a cooling mat, and the top of the keyboard used to actually get hot sometimes, and it doesn't seem to be the case now.

Any suggestions on keeping it within range, then? Do I need to clean the fans or add heatsink somewhere?

---

### Post by Monicker on 2008-05-11
After digging through the forum archives a bit, I found this thread:

[http://ubuntuforums.org/showthread.php?t=41927]("http://ubuntuforums.org/showthread.php?t=41927")


You could try the recommendation of enabling the polling frequency with these commands, which seemed to help several people:

```
sudo -s
echo 30 > /proc/acpi/thermal_zone/THRM/polling_frequency
exit
```

If that seems to work, you can have it enabled automatically at startup.  I believe the thread also mentions how to do that.

Another options would be to try using kpowersave, with a dynamic profile, and seeing if it does a better job of handling cpu throttling and control of the fans.

---

### Post by dgbearcat on 2008-05-11
> **Monicker said:**
> After digging through the forum archives a bit, I found this thread:

[http://ubuntuforums.org/showthread.php?t=41927]("http://ubuntuforums.org/showthread.php?t=41927")


You could try the recommendation of enabling the polling frequency with these commands, which seemed to help several people:

```
sudo -s
echo 30 > /proc/acpi/thermal_zone/THRM/polling_frequency
exit
```

If that seems to work, you can have it enabled automatically at startup.  I believe the thread also mentions how to do that.

Another options would be to try using kpowersave, with a dynamic profile, and seeing if it does a better job of handling cpu throttling and control of the fans.

Awesome, thanks!

---


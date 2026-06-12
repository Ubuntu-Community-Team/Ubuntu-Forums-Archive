---
title: "Log out panel that take a while to be shown"
date: 2008-01-14
forum: General Help
---

### Post by elekaj34 on 2008-01-14
Hi,

I'm new, and French. I post here because this takes a while that I try to resolve a problem. The French forums  about ubuntu can help me any more :(

I run Ubuntu Gutsy 64 bits edition (Core2Duo E630 on Asus P5K main board, 4Gb of memory, 250 Gb SATA disk drive, nVidia GeForce 7300GT graphics card on PCI Express bus)

All is fine only one thing. When I want to show the logout panel (icon at the right border on top of the screen), this take a while to be shown (about 45s to 1 minute)

This week end I tried to reinstall completely my system ... with no effects, the problem is already here.

On some readings over the Internet this problem seems to be related to the power management.
So I try to deactivate the power management on Gnome session preferences. The problem isn't solved.

Then I've done the followings, with no more effects.
```
root@thevenin:~# /etc/init.d/powernowd stop
 * Stopping powernowd:                                                   [ OK ] 
root@thevenin:~# /etc/init.d/powernowd.early stop
 * Stopping powernowd:                                                   [ OK ]
```

The same with ACPI
```
root@thevenin:~# /etc/init.d/acpid stop
 * Stopping ACPI services...                                             [ OK ]
root@thevenin:~# /etc/init.d/acpi-support stop
 * Disabling power management...                                  [ OK ]
```

Already the same things, the panel take a while to be shown.

About the system logs, nothing in /var/log/syslog (about the power management), but I've this in /var/log/acpid
> [Mon Jan 14 10:44:56 2008] starting up
[Mon Jan 14 10:44:56 2008] 72 rules loaded
[Mon Jan 14 10:44:58 2008] client connected from 5341[107:116]
[Mon Jan 14 10:44:58 2008] 1 client rule loaded
[Mon Jan 14 10:44:59 2008] client connected from 5543[0:0]
[Mon Jan 14 10:44:59 2008] 1 client rule loaded
[Mon Jan 14 10:45:03 2008] client connected from 5671[0:0]
[Mon Jan 14 10:45:03 2008] 1 client rule loaded
[Mon Jan 14 10:45:07 2008] client connected from 5687[0:0]
[Mon Jan 14 10:45:07 2008] 1 client rule loaded
[Mon Jan 14 10:45:12 2008] client connected from 5754[0:0]
[Mon Jan 14 10:45:12 2008] 1 client rule loaded
[Mon Jan 14 10:48:28 2008] exiting

In the directory /etc/acpid/ I've notice a lot of scripts, but I don't know which is bad (I don't touch anything in this directory)

I think (but absolutely not sure), that my problem is not in relation with power management.

Some other French users have the same problem (but not resolved) and all have nVidia graphics card. Is it a way ?

On my computer, I've tried to deactivate the nvidia (proprietary) kernel module and use the free one (nv). No effects, it is the same.

So I've put on my computer an old ATI cards (ATI Rage 128).  No effects, it is the same.

Have you a way or a more tests to resolve my problem ?

It is not very disturbing but if I can resolve it, I'll be happy :)

Thanks for your help

Elekaj34 (and sorry for my bad English but I don't have the occasion to speak English a lot)

---

### Post by pieisgood4589 on 2008-01-14
Hmmmm... I dunno...:lolflag:

---

### Post by louieb on 2008-01-14
I have seen this on my system. It occurs right after I login. Then want to log right back out. After I have been logged in for a couple of minutes the delay goes away.  

Just wondering if you wait a minute or two before trying to log out if the delay goes away too.

---

### Post by elekaj34 on 2008-01-15
Hi,

I think too that this delay occurs only for few minutes after login (via GDM), but it's not the case for me. At each logout (even if I try many minutes or hours after login), the panel takes a while to be shown.

Thanks

Elekaj

---


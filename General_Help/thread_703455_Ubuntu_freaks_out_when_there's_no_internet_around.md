---
title: "Ubuntu freaks out when there's no internet around"
date: 2008-02-21
forum: General Help
---

### Post by leenwebb on 2008-02-21
Hi all,
I live in the middle of nowhere, and have a satellite internet connection.  It is the bane of my existence for many reasons, but I've just found a new one:

When the internet connection is down (which is often), my Ubuntu machine (a plain ol' Gutsy LAMP server, with gnome GUI desktop) freaks out.  It takes a really long time (like 8 or 10 minutes) to start up, then acts generally weird (won't open programs, won't let other computers on the network look at files, etc) the whole time it's on.  When I try to shut it down (which is made harder when it refuses to show me the top taskbar), it usually hangs during shutdown.  Eventually (15-20 minutes later) it will shut down, except when it doesn't and I have to turn off the power.  

Honestly, if I didn't know better I'd think it had some sort of nasty virus.  But if the internet connection is up-and-running when it starts, everything is hunky-dory and the machine acts perfectly normal.

Does anyone know which programs in a generic Gutsy LAMP install would be trying to get to the internet, and wouldn't have the sense to fail gracefully when it wasn't there?   I don't have any widgets or other internet-y things that might freak out if there's no connection.   I've turned off the "Check for updates automatically", but I'm not sure where else to go from here.

Thoughts?  I am at a loss on this one.

Thanks!
Eileen

---

### Post by Bucky Ball on 2008-02-21
Hi leenwebb.

My first thought is this, and it is just a shot in the dark. Maybe your machine is attempting to find the UTC, international internet clock.

1/ At boot at the grub menu (or lilo), hit 'e' to edit the selection you are trying to boot unsuccessfully.
2/ Get to the 'kernel' line and hit 'e' again to edit that.
3/ at the end of that line, try adding 'noapic nolapic' (without the punctuation).

Might make a difference. Then set time on Ubuntu manually - if, of course, that works. If it does work, try removing 'nolapic' from the kernel line at boot. Better still, get into the menu.lst file and add it there. That way it is permanent. (But make sure it works first!)

Reason I mention it is because this particular problem had me stumped for a couple of days. Naturally, it may not have anything to do with your problem.

---

### Post by siddartha on 2008-02-21
Normally it shouldn't do that. Are you sure you haven't installed some extra stuff or just set up extra things? For example: if you set up the time to be syncronised over the internet, that would be done after a reboot also. This leads to stopping the whole boot up process because there is no answer from the time server. And so on.

From my recollection you are looking in the wrong place as the updates are checked in the background later on and not at the boot process (unless you are just installing the system for the first time).

---


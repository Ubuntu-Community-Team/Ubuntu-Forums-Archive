---
title: "[SOLVED] Messed up my booting sequence"
date: 2008-04-10
forum: General Help
---

### Post by jhaefner on 2008-04-10
I just upgraded to 7.10 (I know, I'm behind times) and everything went smoothly.  A few days into using the system,  I *inadvertently* unclicked (cleared) the dbus service in "system->admin->services" application.  This stopped a lot of things, but I was able to reboot and get the dbus service restarted.  Now, however, when I reboot and after logging in, I get the message:

"Unable to initialize HAL".   

Examining "ps -A", I see dbus is running, but  hal, avahi-daemon, and my network (eg dhcdbd) are not working.  I can recover all these things by manually restarting dbus (sudo /etc/init.d/dbus restart).  (/etc/default shows both dbus and avahi to be ENABLED.)  But clearly things are not as they should be.

Can someone point me to a possible solution, or reading, to fix this and return my booting to original condition?  Or even, another forum to post on?

Thanks.

Jim H.

---

### Post by bodhi.zazen on 2008-04-10
I do not know enough to "fix" the problem, but perhaps hack it :twisted:

Add any commands you need to /etc/rc.local /etc/rc.local runs as root, so no need for sudo.

> /etc/init.d/dbus restart

My guess at the problem is dbus is starting in the boot sequence either too soon, or more likely too late. dbus should start at S12:

S12dbus

---

### Post by jhaefner on 2008-04-10
[QUOTE=bodhi.zazen;4691422 ...

My guess at the problem is dbus is starting in the boot sequence either too soon, or more likely too late. dbus should start at S12:

S12dbus[/QUOTE]

This is the clue that fixed the problem.  After using  the sys->admin->services application from the menu to restart dbus (or any service), that application apparently created an arbitrary "S50dbus" link to the startup script in rc2.d.  (It did the same thing when I restarted racoon).  Since this disregards the necessary ordering of scripts (or even into which directory they should go), and, to me, is a bug.  I won't be using that gui any more...and I will now backup an image of my working /etc directory...

thanks for the help.

---

### Post by bodhi.zazen on 2008-04-10
Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


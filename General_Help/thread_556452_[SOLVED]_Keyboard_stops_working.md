---
title: "[SOLVED] Keyboard stops working"
date: 2007-09-21
forum: General Help
---

### Post by Vadi on 2007-09-21
Okay, I've ran into a very weird bug, and need some help diagnosing.

To put it short, weak wireless + firefox = keyboard simply stops working. If I close a bunch of firefox windows, I guess the ones that are needing the internet, the keyboard comes back.

There was a similar problem here ([click]("http://ubuntuforums.org/showthread.php?t=117848")), but it's over a year old, so I don't think this should be tied to it.

Is there any place where I can check what errors occured or something? This is really odd.

---

### Post by geraldm on 2007-09-21
The similar problem that was mentioned does not appear similar.
That was using module ndiswrapper, which WILL cause problems on some kernels because
it requires 16k kernel stack, and that has to be built into the kernel.  The last available 
kernel that can be used is 2.6.21.1.  If you are using ndiswrapper, say so, and also
mention the kernel version being used, and also the type of keyboard, ps/2, usb.
The place to check is in the log, usually /var/log/syslog
I have seen other posts that suggest changing the wireless channel to see if the problem
goes away with a different channel.

Gerald

---

### Post by Vadi on 2007-09-21
I removed network-manager altogether, and got wicd instead, because NM was really frustrating with wireless.

So ignore the topic then, or if you get a similar problem, look into [WICD]("http://wicd.sourceforge.net/").

---

### Post by Student Driver on 2007-10-29
I just want to bump this as I believe I am getting the same issue.  However, after closing all of the applications running I still didn't get my keyboard back (running Gutsy on a Dell D610) and had to hard reset the system.  I noticed that the wireless icon was gone when the Gmail chat control in Firefox showed it was offline.  After that, I couldn't type anymore even though the hibernate key (Fn+F1) still worked.  It would go to screensaver and lock, and I couldn't logon anymore since I couldn't type my password.  I get weak wireless in the livingroom, which never seemed to be an issue with Vista on this same laptop.  I might bump it up a bit since it's using DD-WRT anyway.

---

### Post by Vadi on 2007-10-29
Tried WICD? That solved it for me.

---

### Post by Student Driver on 2007-10-29
Not yet, but that's going on when I get home.  Network manager bombed overnight and wouldn't work with my wireless router when I woke up (and I was at 98% of my Top Gear download).  It seems to be a fragile application, so if the wireless network isn't the strongest, it will croak if there's a fair amount of network traffic.

---


---
title: "Sudo always active"
date: 2007-07-07
forum: General Help
---

### Post by Hark3n on 2007-07-07
Hi,

A while back I started noticing that commands requiring root privileges doesn't ask for the password anymore.  I started looking into the problem, but could not find a concrete solution to the problem.

What I did find was one guy with the same problem, and someone commented that it is something to do with the sessions.  As far as that;s concerned I'm quite clueless.

I f anybody know how to fix this problems, please tell me, as I feel my computer might be at risk.

Regards,
E

---

### Post by johnsd8 on 2007-07-07
You likely need to change your sudo timeout, which is in your /etc/sudoers file

You should edit with file with care, preferably with visudo if you're comfortable with vi. This will auto-check your syntax and refuse to save the file if yoour syntax is invalid. (Having a bad sudoers file makes things difficult if you dont know the root password).

From a console, type:

[FONT="Courier New"]sudo visudo[/FONT]

Look for a line something like:

[FONT="Courier New"]Defaults:USER timestamp_timeout=-1[/FONT]



If it doesn't exist, add one with a reasonable timout vlaue (in minutes), replacing your username in USER. A time of -1 would mean forever, which sounds like your problem.

---

### Post by Hark3n on 2007-07-09
Thanks johnsd8.  I wil try it as soon as I'm in front of my pc again.

E

---


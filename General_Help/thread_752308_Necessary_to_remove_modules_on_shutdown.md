---
title: "Necessary to remove modules on shutdown?"
date: 2008-04-11
forum: General Help
---

### Post by BradC78 on 2008-04-11
Hello,

I've added "modprobe ndiswrapper" to /etc/rc.local to load the module at startup.  Is it necessary to remove it by adding "rmmod ndiswrapper" to a shutdown script somewhere to ensure a tidy shutdown?  Does anyone know where I would find this shutdown script?  THANKS! :)

---

### Post by ibuclaw on 2008-04-11
Personally, I'd leave it as it is.

I've been doing some work with ndiswrapper the past few weeks (There's been an awful amount of new spyware that's been circulating round my friends PCs, so I've been using BackTrack with ClamAV to get rid of them).

And when working with ndiswrapper for their wireless USB sticks, I've found that the command **rmmod ndiswrapper** infact crashes the whole system to a complete freeze (not even the mouse moves).
And the only way out is to hard reboot. (This is true for all OS' I tried, also including Ubuntu, SUSE and RedHat).

So I would advice not to do it, in the case that it freezes your computer in the middle of the shutdown routine.

Besides the point, if your computer is shutting down, one would expect it to be unloaded in the process anyway! (If not unloaded with rmmod, then removed when the RAM is wiped before poweroff).

So it really is not something to worry about.

Regards
Iain

---

### Post by warp99 on 2008-04-11
Unless the module is hanging at shudown I believe the answer is no.

---

### Post by Whiffle on 2008-04-11
No need to do so, they get unloaded automatically.  Good question though :)

---

### Post by BradC78 on 2008-04-11
Thanks for the quick replies, everyone!

---

### Post by prshah on 2008-04-11
> **BradC78 said:**
> Hello,

I've added "modprobe ndiswrapper" to /etc/rc.local to load the module at startup.  Is it necessary to remove it by adding "rmmod ndiswrapper" to a shutdown script somewhere to ensure a tidy shutdown?  Does anyone know where I would find this shutdown script?  THANKS! :)

No need to remove it; in fact, rather than use the /etc/rc.local file, better you add the word ```
ndiswrapper
``` to your > /etc/modules

OK, may not ACTUALLY be better but seems more _relevant_ that way... to me? Note that there's nothing really WRONG with your method.

---

### Post by BradC78 on 2008-04-15
Thanks for the tip prshah.  This does seem more appropriate for /etc/modules.

---


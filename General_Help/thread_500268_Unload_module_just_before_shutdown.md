---
title: "Unload module just before shutdown"
date: 2007-07-13
forum: General Help
---

### Post by ThrobbingBrain66 on 2007-07-13
I have an issue where my laptop doesn't shut down completely after choosing "Shut Down".  After tons of research and tinkering, I've found a solution.  It seems that snd_hda_intel isn't unloading correctly (or at all).  If I manually remove the module and then choose Shut Down, everything works great.  What can I do to automatically remove this module just before my laptop attempts to shut down?

---

### Post by yabbadabbadont on 2007-07-13
Copy /etc/init.d/rc.local to a new name, say /etc/init.d/rc.localstop.  Edit it and change it so that instead of reading and executing /etc/rc.local it reads and executes /etc/rc.localstop.  Change it so that it does this when passed the "stop" command.  (just swap the stop and start cases is the easiest way)   Copy /etc/rc.local to /etc/rc.localstop and edit it so that it contains the command to remove the module.  Use update-rc.d to create a stop link for /etc/init.d/rc.localstop in the zero runlevel (/etc/rc0.d).  Use a high number like 99 so that it is the first thing run on shutdown.

---

### Post by ThrobbingBrain66 on 2007-07-14
Thanks for the help.  I've been a bit busy so for now I just added 'rmmod snd_hda_intel' to the halt script in /etc/rc0.d

Your way certainly looks more elegant though:)

---

### Post by yabbadabbadont on 2007-07-14
I almost suggested what you ended up doing.  :D

However, I figured that I would provide a more generic solution that wouldn't be wiped up by the next update to the system init scripts.  dpkg will probably complain if there ever is an update to the halt init script.  Just be prepared to handle it if it happens.  You would probably just need to run something like "sudo dpkg-reconfigure -p high <insert complaining package name here>" to force it to replace the file with the new one.  Then you would need to make your change again.

---

### Post by paulle on 2007-07-25
i have stationery box (with AMD) and shutdown, reboot and halt don't work.

---

### Post by yabbadabbadont on 2007-07-25
> **paulle said:**
> i have stationery box (with AMD) and shutdown, reboot and halt don't work.

I think you made your post in the wrong thread...   :D

---


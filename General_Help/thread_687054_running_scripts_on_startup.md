---
title: "running scripts on startup"
date: 2008-02-03
forum: General Help
---

### Post by Mr.Johnny on 2008-02-03
Hi!

How do I run startup scripts on ubuntu?

I'm a newbie, so that runlevel thing didn't fit yet (if you could elaborate a bit on that I would be grateful, I'm used to that pretty "Startup" entry in the windows progs menu).

Thanks.

---

### Post by Tenken on 2008-02-03
Go to System->Preferences->Sessions, click new give it a name and the path to your script, and when you're done make sure the box next to it is checked. You don't need to worry about run levels for something like this.

---

### Post by yabbadabbadont on 2008-02-03
If you want them to run when the computer starts up, but before the graphical login manager is displayed, (they have to be text based commands), then add them to /etc/rc.local.  In a terminal, "sudo nano /etc/rc.local".

If you just want them to run once you login, then add them to your Session.  In Gnome, System->Preferences->Sessions.

Edit: Too slow.  :)

---

### Post by Mr.Johnny on 2008-02-03
> **yabbadabbadont said:**
> If you want them to run when the computer starts up, but before the graphical login manager is displayed, (they have to be text based commands), then add them to /etc/rc.local.  In a terminal, "sudo nano /etc/rc.local".

If you just want them to run once you login, then add them to your Session.  In Gnome, System->Preferences->Sessions.

Edit: Too slow.  :)

Hey thanks to both! :lolflag: Actually the matter was going go be how to run it before getting to the xserver, but I didn't want to push my luck.

Lucky me, this time I know what "sudo nano" means :lolflag::lolflag::lolflag:

So, I just add the full path to it?

---


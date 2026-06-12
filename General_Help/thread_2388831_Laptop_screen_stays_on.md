---
title: "Laptop screen stays on"
date: 2018-04-07
forum: General Help
---

### Post by charlie_bravo2 on 2018-04-07
I just ran (April 5th, 2018) the most recent update of the Ubuntu Base which I received an alert on.  After the update, I have discovered a minor issue.  Used to be when I closed my lid on my Dell Laptop, the screen would go black and the system would suspend.  Now, none of that happens.  I close th lid, the screen stays lit, and the system keeps processing whatever it's processing when I'm not looking (probably working on actualizing SKYNET).  I pick up my hours-idle laptop and it's uncomfortably hot to the touch, the monitor is already lit up, and the system doesn't reestablish wireless connectivity, having not dropped the connection.

Doctor Google offers me a large number of questions from people wanting to make their laptops do this thing.  I want it to stop, and Google is silent on the matter.  I've looked at my Settings from the Ubuntu desktop, but am seeing nothing that looks useful.  I looked at the Power Settings, but there is nothing about behavior when the laptop lid is closed, it just offers an automatic suspend after X minutes.  This is new behavior, I had a problem about a month ago and ended up buying a new HDD and loading Ubuntu 17.10 Artful from DVD,

Thanks in advance for the help.

---

### Post by TheFu on 2018-04-08
For systemd-based Ubuntu installs, there is a file which controls this stuff.

/etc/systemd/logind.conf - which has yes/no settings you can tweak.  Use **sudoedit** to modify the file safely.
It has a manpage that explains each setting, but it is part of systemd, so what the manpage claims may not actually work. ;)  I haven't noticed the Lid controls not doing what they say. Should be fine, unless there is a bug.

---


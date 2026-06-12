---
title: "brightness changes by itself"
date: 2008-02-01
forum: General Help
---

### Post by Libertad on 2008-02-01
Hello all,
I am a new ubuntu user, i dont have much experience with Linux systems.
I downloaded the latest Ubuntu version 7.10, installed it and updated it to its latest version.
I have a problem. 
Sometimes brightness decreases by itself ( for ex: when i am watching videos or reading pdfs especially ) I increase it , and in a few minutes it decreases again. what can i do to prevent it?

Thanks in advance.

---

### Post by Het Irv on 2008-02-01
Are you on a laptop?  Have you had power surges recently?

If you are on a desktop the problem might be with your monitor.  Check all your power cables and the settings on your moniter.

---

### Post by cdaringe on 2008-02-01
My computer (laptop) also does this frequently.  It never bothered me enough to make  post of it.  It never did it on my desktop.  I'm assuming it has something to do w/ the power services.  Any help here would be great.  It doesn't decrease brightness DRASTICALLY--it will (seemingly) randomly slowly darken a little and later undarken without cause.  it does not darken due to inactivity**
I can post any file or output if someone thinks they have an idea.

---

### Post by Libertad on 2008-02-01
Yes, I use a laptop. I checked the power settings, and brightness is adjusted to %100 when it is on AC Power. But it still does it and it bothers me. I dont think that I have a problem with the monitor, because vista work flawlessly

---

### Post by Rocket2DMn on 2008-02-01
In terminal run
```
gconf-editor
```
and navigate the tree to /apps/gnome-power-manager/backlight and uncheck the box for "idle_dim_ac" (and "idle_dim_battery" if you want)

---

### Post by Libertad on 2008-02-02
thanks for your reply, but it is already unchecked, brightness changing constantly and it is really annoying
i installed ubuntu again, but again the problem persists.

---

### Post by Rocket2DMn on 2008-02-02
OK, it might be something in your BIOS then that Ubuntu's configurations can't override.  Reboot your computer and hit the hotkey to get into your BIOS (it should show you briefly, but you will only have a second to do it).  Common keys are F2, F12, ESC, but it varies between computers.  Search around in there for display control brightness and idle times.  Report back afterward and we'll see if that fixes it.

---

### Post by Libertad on 2008-02-05
I think I found the reason of the problem. When my laptop battery is fully charged, Ubuntu stops somehow the charging of the battery and brightness decreases eventough I disabled "Dim when idle on both AC Power and Battery Power" Please help me it is really annoying!
And i dont think that i have a problem with BIOS because vista doesnt do this

---

### Post by Libertad on 2008-02-05
yes, i think i solved it, as i mentioned above, the problem is linux thinking that i displugged the ac power when the battery is full. I still dont know how to solve it but i set "dim display brightness to 0%"

---


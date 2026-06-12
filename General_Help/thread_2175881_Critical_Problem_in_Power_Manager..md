---
title: "Critical Problem in Power Manager."
date: 2013-09-21
forum: General Help
---

### Post by lanser2 on 2013-09-21
alright, so the xfce4-power-manager isn't working, I have it installed, and I even re-installed & purged it, but that didn't solve the problem.

even, when I type "xfce4-power-manager" into the console, it didn't make it work.

I also tried selecting "Power Manager" in Autostart Applications settings, but the power manager still isn't appearing at my panel.

how can I fix this problem? can anybody help?

---

### Post by Toz on 2013-09-21
> **lanser2 said:**
> alright, so the xfce4-power-manager isn't working, I have it installed, and I even re-installed & purged it, but that didn't solve the problem.
What version of Xfce/Xubuntu are you running?

> even, when I type "xfce4-power-manager" into the console, it didn't make it work.
Do you get any error messages when you try? 

Can you also try running it ike this:
```

xfce4-power-manager --no-daemon
```
...and post back what ever messages are displayed?

> but the power manager still isn't appearing at my panel.
The power manager icon is displayed by the notification applet. Do you have the notification applet added to the panel?

---

### Post by lanser2 on 2013-09-22
Xfce 4.10 and Xubuntu 12.04.  running xfce4-power-manager --no-daemon gives me: Xfce Power Manager: Another power manager is already running  but it isn't displaying, and yes, notifications applet is enabled.

---

### Post by lanser2 on 2013-09-22
I tried installing elementaryOS's pantheon environment once by doing "sudo apt-get install elementary-desktop", but I removed it in some time when it didn't work, and I think that might have caused the disappearing of the battery-icon, is this a problem with my icon theme?

---

### Post by Toz on 2013-09-22
> **lanser2 said:**
> Xfce 4.10 and Xubuntu 12.04.  running xfce4-power-manager --no-daemon gives me: Xfce Power Manager: Another power manager is already running  but it isn't displaying, and yes, notifications applet is enabled.

Which power-manager is currently running:
```
ps -ef | grep power
```

---

### Post by Toz on 2013-09-22
> **lanser2 said:**
> I tried installing elementaryOS's pantheon environment once by doing "sudo apt-get install elementary-desktop", but I removed it in some time when it didn't work, and I think that might have caused the disappearing of the battery-icon, is this a problem with my icon theme?
Which icon theme are you using? Have you tried changing icon themes to see if it appears?

---


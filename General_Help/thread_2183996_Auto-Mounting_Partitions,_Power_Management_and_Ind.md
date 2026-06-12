---
title: "Auto-Mounting Partitions, Power Management and Indicator Applets"
date: 2013-10-27
forum: General Help
---

### Post by Jeremy Reid on 2013-10-27
Hello Ubuntu Community!

I've recently made the switch, replacing my Windows 7 installation with Lubuntu 13.10 (x64) - after making a few modifications and customizations, I can say I am very pleased with this sytem! However, I have come across a few issues with the system that I can't seem to find a solution to.
[B]
Issue #1 - When partitions are automatically mounted on login, authentication is required (SOLVED):[/B]

I have set two partitions to auto-mount upon login, as they are depended on by both my music manager (Clementine) and Steam (I have my steam directory installed on another hard drive). However, I am required to input my password after I've logged in to allow the automatic mount to take place. This is a small inconvenience, but one that I hope has a simple fix.

_SOLUTION: > **vasa1 said:**
> See if this helps: [https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002875.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002875.html) although things may have changed since then._
**Issue #2 - Xfce Power Manager doesn't do anything (SOLVED):**

Lubuntu comes with Xfce Power Manager as the default power management application. It automatically starts up - I can see it in the task manager. However, I have set my displays not to go to sleep ever, but they do. The settings I have set withing the power manager are ignored/do not work, even though the service is running.

_SOLUTION: > **Jeremy Reid said:**
>  However, just by checking the box labelled "monitor power management control" within xfce power management, my issue has been resolved. My screens haven't gone to sleep at all, after being left for three hours. They used to go to sleep every 15 minutes or so._
**Issue #3 - Indicator Applets (SOLVED):**

The indicator applet panel item does not seem to change it's background colour to the colour of my panel - see here (bottom right): [https://dl.dropboxusercontent.com/u/49669128/desktop%201_002.png](https://dl.dropboxusercontent.com/u/49669128/desktop%201_002.png)

Is there a way to either make the background to the indicator applet transparent or change the colour manually?

_SOLUTION: > **Dennis N said:**
> To be sure everything changes properly, you need to keep the theme (under the wigets tab) as "Lubuntu default"_ (i.e. themes cause this issue)

----

Thanks for your support everyone!

Jeremy

---

### Post by vasa1 on 2013-10-27
> **Jeremy Reid said:**
> ...
Issue #1 - When partitions are automatically mounted on login, authentication is required:

I have set two partitions to auto-mount upon login, as they are depended on by both my music manager (Clementine) and Steam (I have my steam directory installed on another hard drive). However, I am required to input my password after I've logged in to allow the automatic mount to take place. This is a small inconvenience, but one that I hope has a simple fix.

...
See if this helps: [https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002875.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002875.html) although things may have changed since then.

---

### Post by Jeremy Reid on 2013-10-27
> **vasa1 said:**
> See if this helps: [https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002875.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-October/002875.html) although things may have changed since then.

Trying this out now - I've installed it and will now reboot.

UPDATE:

It worked - thanks for that!

---

### Post by Jeremy Reid on 2013-10-27
I still need some help with **Issue #2** and **Issue #3** if anyone has some time... :-)

---

### Post by Dennis N on 2013-10-27
Your #3:

Set panel background to solid color (panel settings > appearance tab) , and choose a color in the color selector dialog. Indicators and clock background will change also. Set opacity to 0 (zero), and all become transparent to the wallpaper (including any window buttons). The pager stays as is. Just checked on 13.10 to be sure.

---

### Post by Jeremy Reid on 2013-10-27
> **Dennis N said:**
> Your #3:

Set panel background to solid color (panel settings > appearance tab) , and choose a color in the color selector dialog. Indicators and clock background will change also. 

Hasn't changed at all - am I missing something?

[https://dl.dropboxusercontent.com/u/49669128/bar.png](https://dl.dropboxusercontent.com/u/49669128/bar.png)

---

### Post by Dennis N on 2013-10-27
> **Jeremy Reid said:**
> Hasn't changed at all - am I missing something?

[https://dl.dropboxusercontent.com/u/49669128/bar.png](https://dl.dropboxusercontent.com/u/49669128/bar.png)

To be sure everything changes properly, you need to keep the theme (under the wigets tab) as "Lubuntu default" or possibly one of the others offered there. I tried "Clearlooks" and "Crux" and they both work too. If I try one not in the default selection, like greybird, I get results like yours. (I did not check all the default themes; I leave that to you). But, outside themes that you install are problematic to be sure.

---

### Post by Jeremy Reid on 2013-10-27
> **Dennis N said:**
> To be sure everything changes properly, you need to keep the theme (under the wigets tab) as "Lubuntu default"

You're right - changed the theme to Lubuntu Default and it fixed it right up. It was one of my custom themes that was causing the bother. Do you know what I would need to modify to make the theme work? (If you don't know, don't worry)

---

### Post by Jeremy Reid on 2013-10-27
Now we just need to find out why power management doesn't work! (**Issue #2**)

---

### Post by Dennis N on 2013-10-27
> **Jeremy Reid said:**
> Now we just need to find out why power management doesn't work! (**Issue #2**)

I see the same problem with the monitor not staying on. In my case, when I open the power manager dialog, it informs me that power manager is NOT running. Task manager confirms this - no xfce4-power-manager shows. No solution yet.

On my Lubuntu 12.10 machine, power manager does start monitoring at boot up. To keep the monitor from sleeping, I just unchecked "monitor power management control" and set everything else to never. Otherwise, monitor would sleep in 10-15 mins. The screensaver is set to blank in 30 mins and functions as expected.

---

### Post by Jeremy Reid on 2013-10-27
I made it so that the power manager starts up by using "lxsession-edit". "monitor power management control"  was unchecked by default - I've now checked it to see if it makes a difference.

Thanks for your help - I'll report back if it works/doesn't work.

---

### Post by Dennis N on 2013-10-27
Ok, I think I have fixed the Monitor sleep problem. I first installed xscreensaver, and mention this only because it played a role in my test. I set up the screensaver to go on in 20 minutes, with the Fiberlamp activated. Then:

**Preferences > Default applications for LXSession**

In the dialog window, 

[FONT=Courier New][B]Screensaver set to: xscreensaver. Press Apply Button
Power Manager set to: no. Press Apply Button[/B]
[/FONT]
(if you don't use apply, they won't be set)

Restarted. Previously, monitor entered sleep or standby mode after 10 minutes, This time, monitor remained on, and after 20 minutes, Fiberlamp came on as it should. Let it run 5 more minutes. Ended test at that point.

---

### Post by Jeremy Reid on 2013-10-27
Thank you, Dennis N, for your continued input. I assume that works for you because xscreensaver took over the role of screen power management. However, just by checking the box labelled "monitor power management control" within xfce power management, my issue has been resolved. My screens haven't gone to sleep at all, after being left for three hours. They used to go to sleep every 15 minutes or so.

Thank you once again for your support Dennis, and to everyone else throughout this thread!

All my problems with my installation are resolved (for now! :P).

---


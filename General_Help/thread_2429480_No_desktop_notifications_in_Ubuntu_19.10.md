---
title: "No desktop notifications in Ubuntu 19.10"
date: 2019-10-18
forum: General Help
---

### Post by Dennis N on 2019-10-18
I did a fresh installation of Ubuntu 19.10. I noticed that there are no popup desktop notifications from the system or any application, even though notification popups are enabled in Settings > Notifications. Instead, I find all notifications are being sent to the date/time drop-down window. Google search produced no hits on this being a problem, so I wonder if anyone has noticed this? Could I be overlooking some other setting to enable the popups? If so, what?

---

### Post by uRock on 2019-10-18
My Facebook notifications are showing up in the typical notifications/calendar drop down. I haven't run it long enough to get any other notifications yet.

---

### Post by #&amp;thj^% on 2019-10-18
Just checking with a look in dconf-editor: "org/gnome/desktop/notifications" (enable/disable)
Mine was disabled, but I do that first thing on my end. :)

---

### Post by Dennis N on 2019-10-18
> **1fallen said:**
> Just checking with a look in dconf-editor: "org/gnome/desktop/notifications" (enable/disable)
Mine was disabled, but I do that first thing on my end. :)

I have no enable/disable option in org/gnome/desktop/notifications. See attached screen shot.

---

### Post by #&amp;thj^% on 2019-10-18
My Goodness, It slays me to see such a difference from one machine to another. (But then again I tweak the crap out of my systems. :))
Note: you might need to enable/disable notifications also on a per-app basis, e.g. to disable Nautilus notifications:
```

gsettings set org.gnome.desktop.notifications.application:/org/gnome/desktop/notifications/application/org-gnome-nautilus/ enable false
```
To be clear, for myself I have installed Nemo as my file manager.
let me know if this one works Dennis N

---

### Post by Dennis N on 2019-10-18
> **1fallen said:**
> My Goodness, It slays me to see such a difference from one machine to another. (But then again I tweak the crap out of my systems. :))
Note: you might need to enable/disable notifications also on a per-app basis, e.g. to disable Nautilus notifications:

I can open the 'applications' folder (seen in previous screenshot) to set notifications for individual applications. I checked them all - they all have an 'enable' key set to true. See screenshots.
To reiterate, there are notifications being sent, but only to the date/time/calendar drop-down, none appear in a popup window as expected.

---

### Post by #&amp;thj^% on 2019-10-18
> **Dennis N said:**
> 
To reiterate, there are notifications being sent, but only to the date/time/calendar drop-down, none appear in a popup window as expected.

That was very clear to me from the beginning.;)\
We are just trying to find out why yours is different.
Do you see/have "**Panel OSD**" extension from the GNOME Extensions website:
Its been reported: Note that on Gnome 3.34, enabling this extension causes the notification popups to completely fail to show. Disabling the extension and logging in again fixes the problem

---

### Post by Dennis N on 2019-10-18
> Its been reported: Note that on Gnome 3.34, enabling this extension causes the notification popups to completely fail to show. Disabling the extension and logging in again fixes the problem
Yes! That was the cause. That extension now disabled. Thanks very much!

UPDATE: 21 Oct 2019 - This extension has now been updated and fixed for gnome-shell 3.34.

---


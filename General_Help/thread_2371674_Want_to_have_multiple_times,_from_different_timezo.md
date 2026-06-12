---
title: "Want to have multiple times, from different timezones displayed on title bar."
date: 2017-09-17
forum: General Help
---

### Post by jackc83 on 2017-09-17
It seems like the only way to view a different timezone, is if I add additional timezones to the Time and Date settings. The problem with this, is that I can only view other timezones by clicking on the clock in the titlebar... and looking at the drop down menu. I DONT WANT TO HAVE TO DO THAT, everytime I want to know what time it is in another timezone. My wife is currently overseas, and I want to be able to simply glance up to the title bar, without interrupting what I am doing, in order to have a quick idea of what time it is over there.

On my chromebook, running GalliumOS (which I think is based on xubuntu or lubuntu), I am able to add as many "clocks" to the title bar (or is it called the status bar?), and each one correspond to a different timezone. How come I can't seem to be able to edit the title bar at all in Ubuntu 17.04?

Is there anyway to add an additional clock to the titlebar?

Any help would be appreciated :)

---

### Post by Bucky Ball on 2017-09-17
Welcome. There may be an easy way of doing this in Ubuntu, but for what it's worth ... Looks like [Gallium's built on Xubuntu]("https://galliumos.org/") so to use the same desktop environment, simply:

```
sudo apt install xfce4
```

Log out or restart and choose the 'xfce4 session' from the login screen ... but you may not want to do that. You may want to find out what app you are using in Gallium and look in the Ubuntu repos to see if it's available there. If it is in Gallium it quite possibly is in Ubuntu. Good luck. ;)

(* Note: think you want Orage clock. You'll find that in the repos I think. I use Xubuntu-core and just tried the two clock thing without issue. I would assume that Orage is the default clock in Xubuntu. ;)

A further note is that not sure how Orage would go on Unity DE in Ubuntu. Never used it. You may need to install the xfce4 desktop environment to use it, or something like xfce4.)

---


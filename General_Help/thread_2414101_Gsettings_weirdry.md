---
title: "Gsettings weirdry"
date: 2019-03-05
forum: General Help
---

### Post by 0tyugh on 2019-03-05
Hey,
I'm trying to make a script for fast preconfiguration to my users. But I don't get the logic in the latter behaviour.


I want to disable the "lock screen"; initially we get that :
> $ gsettings get org.gnome.desktop.lockdown disable-lock-screen
false
$ gsettings get org.gnome.desktop.screensaver lock-enabled 
true

So I did those two commands :
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
gsettings set org.gnome.desktop.screensaver lock-enabled 'false'
```

Now, it work : each parameters were successfully changed.
> $ gsettings get org.gnome.desktop.lockdown disable-lock-screen
true
$ gsettings get org.gnome.desktop.screensaver lock-enabled 
false


Now comes the weird part : when I go to gnome-control-center to the Privacy tab, and now I check the same parameters with gsettings get and what do I get ? All my parameters are reverted back.
> $ gsettings get org.gnome.desktop.lockdown disable-lock-screen
false
$ gsettings get org.gnome.desktop.screensaver lock-enabled 
true


What is the logic in this ? How can I prevent it ?

Thanks

---

### Post by 0tyugh on 2019-03-06
Any other way to change the "lock screen" setting would save me thought. I really don't find out a "script way".

---

### Post by 0tyugh on 2019-03-12
I found the problem.
I had to export DBUS_SESSION_BUS_ADDRESS and sudo -iu wasn't doing it. Solved.

---


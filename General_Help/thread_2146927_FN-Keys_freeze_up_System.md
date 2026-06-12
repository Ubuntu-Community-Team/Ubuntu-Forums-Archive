---
title: "FN-Keys freeze up System"
date: 2013-05-20
forum: General Help
---

### Post by Elvis99 on 2013-05-20
Hi all,

I'm running XFCE 4.10 on Xubuntu 13.04 on an ancient Gericom notebook. Everything is running fine, but when I use FN keys to adjust the volume or display brightness the system locks up - I can use the mouse, but can't klick on any system menues so I have to use the power button to kill the entire system. 
Is there any way to fix this? Can somebody please help me? 

Thanks for your time!

---

### Post by dentaku65 on 2013-05-20
Already answered somewhere here.
For the functional keys seems that Xubuntu (or Xfce 4.10/4.12) is not able to manage them natively; I suggest to solve in this way:
```
sudo apt-get install gnome-settings-daemon
```
Reboot.
Then under Setting manager -> Session and Startup -> Application Autostart
> Enable Gnome Settings Daemon
Disable XFCE Volume Daemon
In Setting manager -> Keyboard -> Application Shortcuts
```
Remove the shortcuts sets for xfce4-display-settings
```
Reboot. Done.

---

### Post by Elvis99 on 2013-05-20
> **dentaku65 said:**
> Already answered somewhere here.
For the functional keys seems that Xubuntu (or Xfce 4.10/4.12) is not able to manage them natively; I suggest to solve in this way:
```
sudo apt-get install gnome-settings-daemon
```
Reboot.
Then under Setting manager -> Session and Startup -> Application Autostart

In Setting manager -> Keyboard -> Application Shortcuts
```
Remove the shortcuts sets for xfce4-display-settings
```
Reboot. Done.

Caro dentaku65,

mille grazie per la riposta. It solved the problem partially, as of I can now manipulate the display brightness without lockup, but the volume keys still seem to freeze xfce. I've followed all your steps, and would kindly ask for any other idea.

Thanks,

Elvis

---

### Post by dentaku65 on 2013-05-21
Hi,
please check in Setting manager -> Keyboard -> Application Shortcuts if there is any set for:
VolumeUp
VolumeDown
Mute
If so, remove these shortucuts

---


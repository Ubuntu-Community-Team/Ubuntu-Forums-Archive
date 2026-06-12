---
title: "lxsession-logout always locks screen when resuming."
date: 2014-03-28
forum: General Help
---

### Post by Plurtu on 2014-03-28
In LUbuntu 13.10 the xfce4-power-manager has an option to disable the lock screen which works for inactivity timeout, laptop lid close and the tray menu, but not the power button (lxsession-logout) which always shows a lockscreen when returning from suspend/hibernate.

Things I've tried to prevent lxsession-logout from locking without success:

[LIST]
[*]xfce4-power-manager lock screen on resume option disabled.
[*]Installed xscreensaver with ~/.xscreensaver lock=False.
[*]Purged xscreensaver.
[*]/etc/default/acpi-support LOCK_SCREEN=false (deprecated but tried anyway)
[*]x.org screensaver off
[/LIST]
```
xset s off
```


[LIST]
[*]xfce4-session according to [http://askubuntu.com/questions/259190/xubuntu-no-password-request-after-suspension](http://askubuntu.com/questions/259190/xubuntu-no-password-request-after-suspension)
[/LIST]
```

xfconf-query -c xfce4-session --create -t bool -p /shutdown/LockScreen -s false

```


[LIST]
[*]gsettings
[/LIST]
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen true 
gsettings set org.gnome.desktop.screensaver lock-enabled false
gsettings set org.gnome.desktop.screensaver ubuntu-lock-on-suspend false
```


[LIST]
[*]Installed [this fix]("https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1205384/comments/55") that replaces lightdm lock with xscreensaver lock and then set lock=False in the xscreensaver settings.
[*]I also noted that neither of the following methods of suspending display a lockscreen regardless of above settings.
[/LIST]
```
sudo pm-suspend
dbus-send --print-reply --system --dest=org.freedesktop.UPower /org/freedesktop/UPower org.freedesktop.UPower.Suspend 

```

---

### Post by Plurtu on 2014-04-04
After much digging and many false leads I finally discovered the script 'lxlock' (/usr/bin/lxlock) which LXDE's lxsession-logout uses to control what program locks the screen. Various programs can do this so they are given a ranked priority, lightdm is ranked the highest and most preferred.

```
# Try to lock the screen with those applications (in this order) :
# lightdm, xscreensaver, gnome-screensaver, slock, slock, i3lock and xdg-screen$


if test x"`which dm-tool 2>/dev/null`" != x""; then
    dm-tool switch-to-greeter
elif `dbus-send --system --print-reply --dest=org.freedesktop.DBus /org/freedes$
    seat="$XDG_SEAT_PATH"
    dbus-send --system --print-reply --dest=org.freedesktop.DisplayManager "$se$
              2> /dev/null
elif test x"`which xscreensaver-command 2>/dev/null`" != x""; then
    xscreensaver-command -lock 
elif test x"`which gnome-screensaver-command 2>/dev/null`" != x""; then
    gnome-screensaver-command --lock
elif test x"`which slock 2>/dev/null`" != x""; then
    slock
elif test x"`which xlock 2>/dev/null`" != x""; then
    xlock $*
elif test x"`which i3lock 2>/dev/null`" != x""; then
    i3lock -d
# In the end, try to fallback to xdg-screensaver. Don't do at the first try, 
# because if lxlock is called by xdg-screensaver, we may enter a loop.
else
    xdg-screensaver lock 
fi
exit 0

```

So it looks like the only way to disable locking is to manually edit the script. Since I know lightdm is installed with lubuntu 13.10 and is the most preferred choice I simply commented out the command option like so: 

```
dm-tool #switch-to-greeter
```

No more lock screen.

---


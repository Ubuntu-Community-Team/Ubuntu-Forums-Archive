---
title: "Cannot use gsettings set to work with cron, anacron, or autostart"
date: 2013-01-30
forum: General Help
---

### Post by hackaxle on 2013-01-30
I am trying to "lock down" the computer by running a script at boot that turns lock on, lock screen after 10 min and require password, etc. I am using Ubuntu 12.04

I have tried editing crontab, anacrontab as well as rc.local to either run my script or actually inserted the code from the script into the files and I cannot get anything to work.

Any ideas?

* this is the only way I can get the commands to run in a script manually *

```
(su - $(logname) -c "gsettings set org.gnome.desktop.screensaver lock-enabled true")

(su - $(logname) -c "gsettings set org.gnome.desktop.screensaver lock-delay 600")

(su - $(logname) -c "gsettings set org.gnome.desktop.screensaver ubuntu-lock-on-suspend true")

(su - $(logname) -c "gsettings set org.gnome.desktop.screensaver user-switch-enabled false")
```

* These commands work if entered into terminal manually *

```
gsettings set org.gnome.desktop.screensaver lock-enabled true
gsettings set org.gnome.desktop.screensaver lock-delay 600
gsettings set org.gnome.desktop.screensaver ubuntu-lock-on-suspend true
gsettings set org.gnome.desktop.screensaver user-switch-enabled false
```

I also tried inserting the following code from other posts about using gsettings in cron with no luck:

```
DISPLAY=:0 
GSETTINGS_BACKEND=dconf
sessionfile=`find "${HOME}/.dbus/session-bus/" -type f`
export `grep "DBUS_SESSION_BUS_ADDRESS" "${sessionfile}" | sed '/^#/d'`
```

Also I double checked my script was executable and created /home/username/.config/autostart/screenlock.desktop:

```
[Desktop Entry]
Type=Application
Exec=/path/screenlock.sh
Terminal=False
Hidden=true
NoDisplay=true
X-GNOME-Autostart-enabled=true
Name[en_US]=screen lock
Name=screen lock
```

---

### Post by dcstar on 2013-02-01
> **hackaxle said:**
> I am trying to "lock down" the computer by running a script at boot that turns lock on, lock screen after 10 min and require password, etc. I am using Ubuntu 12.04

I have tried editing crontab, anacrontab as well as rc.local to either run my script or actually inserted the code from the script into the files and I cannot get anything to work.
.

[http://ubuntuforums.org/showthread.php?t=185993](http://ubuntuforums.org/showthread.php?t=185993)

---


---
title: "trying to run a script after ubuntu 18.04 has started"
date: 2020-04-25
forum: General Help
---

### Post by glubbish on 2020-04-25
I created a script called set_screen_resolution.sh


```
#!/bin/bash
xrandr --output DP-1 --mode 1920x1080  --rate 60
pactl set-card-profile 0  output:hdmi-surround
```

  I tried to automate this script using crontab -e including

 ```
@reboot sleep 90 && /home/chris/set_screen_resolution.sh
```

But it does not do anything and xrandr shows the wrong resolution
but if I do   
 ```
$./set_screen_resolution.sh
```
it works fine.                 

I tried increasing the the sleep time, to no avail.

---

### Post by lvm on 2020-04-25
xrandr needs to know which X display to use. When you start it from active X session it can read it from DISPLAY variable, but cron is not associated with X display and you have to specify it explicitly. If you are always the only X user on this computer you can hardcode -d :0 in the script, a better way is to start X-related scripts not from cron but from desktop autostart manager. There should be a GUI interface for adding autostart items e.g. in KDE it is settings-workspace-startup and shutdown-autostart or you can create a .desktop file manually and place it into ~/.config/autostart/

---


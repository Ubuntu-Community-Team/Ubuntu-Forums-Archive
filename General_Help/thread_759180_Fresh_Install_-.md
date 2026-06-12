---
title: "Fresh Install -"
date: 2008-04-18
forum: General Help
---

### Post by skymera on 2008-04-18
Hi there

I just installed a command line system and i want to build it up to get a GUI.
I have installed Xorg, the nvidia driver, and GDM and Gnome-core

When i run sudo dpkg-reconfigure xserver-xorg it givesme no options to adjust the monitor, only the keyboard =S

Any packages i have missed?

Thanks

---

### Post by ibuclaw on 2008-04-18
This is actually a [bug in Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409").

Apparently, Ubuntu has taken the Windows route of automatically detecting your screen.

Not sure on how to reset this stuff in the /etc/X11/xorg.conf file. But:
```
xrandr
```
displays all your display settings.

And this script outputs your current graphics card/driver.
```

#!/bin/bash

XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"
XORG_DEFAULT_LOG="/var/log/Xorg.0.log"

LOG=$(xset q 2>/dev/null|grep "Log file"|awk '{print $3}')
if [ "$LOG" = "" ]; then
    printf "xset q doesn't reveal the location of the log file. Using fallback $XORG_DEFAULT_LOG \n" 1>&2
    LOG=$XORG_DEFAULT_LOG;
fi
if [ -z "$LOG" ];then
    printf "Error: no Xorg log file found \n"
    printf "$(xset q) \n"
    exit 1
fi


for driver in $(egrep "Loading ${XORG_DRIVER_PATH}.*_drv\.so" $LOG | \
    sed -e "s/^.*Loading .*\///" | \
    sed -e "s|_drv\.so||") ; do
  if ! egrep "Unloading ${XORG_DRIVER_PATH}${driver}_drv\.so" $LOG ; then
      echo $driver
  fi
done

```

Not much else you can do on that at the moment, sorry.

Regards
Iain

---

### Post by noynac on 2008-04-18
Since you have an nVidia video card, you can install and use the nvidia-settings utility to detect your video card and monitor and to save the appropriate settings to xorg.conf.  Nvidia-settings is in the repo's and you run this by typing "sudo nvidia-settings" in a terminal window.

---


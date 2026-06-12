---
title: "Monitor power save timeout in console"
date: 2005-06-12
forum: General Help
---

### Post by lozzd on 2005-06-12
Where is the value that changes how long the monitor switches to power save mode when sitting in the console waiting for logon? I know you can change it in gnome, but I'm not sure if thats the same value used for sitting in the console.

Thanks
Laurie

---

### Post by elvis on 2005-06-24
Do you mean within the actual console (ie: before X or GDM starts) or when waiting at the GUI logon screen (GDM)?

For your console, 

```

sudo setterm -blank 0

```

Turns off blanking.  The number is a value for minutes.  Valid values are 0-60, with 0 meaning "off".

For GDM, from memory this is controlled by your Xorg's config file.

Within your /etc/X11/xorg.conf edit the values:

```

Section "ServerFlags"
    Option      "blank time"    "30"    # 30 minutes
    Option      "standby time"  "60"
    Option      "suspend time"  "60"
    Option      "off time"      "60"
EndSection

```

And change each of them to "0" to turn off blank/standby/suspend/off modes.

---

### Post by dare2dreamer on 2005-08-30
Is there a way to set this to happen at boot-time?

---

### Post by dare2dreamer on 2005-08-31
A little googling answered my question, so I thought I'd reply to myself. In order to disable console screen blanking on bootup, simply edit the  /etc/console-tools/config as follows:

```

# screen blanking timeout.  monitor remains on, but the screen is cleared to
# range: 0-60 min (0==never)  kernels I've looked at default to 10 minutes.
# (see linux/drivers/char/console.c)
# Old Value
#BLANK_TIME=30
# Disables Blanking Completely
BLANK_TIME=0

```

---


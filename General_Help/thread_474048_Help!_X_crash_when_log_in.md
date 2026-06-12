---
title: "Help! X crash when log in"
date: 2007-06-14
forum: General Help
---

### Post by maybee on 2007-06-14
I have been using Feisty for a while, everything was fine. But suddenly, I can't log in after a restarting X anymore. I can use safe mode though.

Tonight, I did several thing. The most probable thing that might cause the problem is I edit xorg.conf to enable SHMConfig. I removed that line, but not helping.

Here is my .xsession-erros: (I mark serveral abnormal thing bolded.)
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "chuan"
[B]/etc/gdm/Xsession: Beginning session setup...
[: 12: closing paren expected[/B]
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/scim.
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
[B]Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Failed to load theme "T-ish-Ubuntulooks": Failed to find a valid file for theme T-ish-Ubuntulooks[/B]

Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.4

Starting SCIM as daemon ...
SCIM has been successfully launched.
Smart Common Input Method 1.4.4

[B]Window manager warning: Lost connection to the display ':0';
most likely the X server was shut down or you killed/destroyed
the window manager.[/B]

```

Plz, help me! I hate to reinstall the system.

---

### Post by steveneddy on 2007-06-14
Run this command from the command line. If you don't get a CLI logon interface, type 

CTRL+ALT+F1

and log on, then type this in and run it.

```
sudo dpkg-reconfigure xserver-xorg
```

This should reset your xorg.conf file.

---

### Post by Crafty Kisses on 2007-06-14
> **maybee said:**
> I have been using Feisty for a while, everything was fine. But suddenly, I can't log in after a restarting X anymore. I can use safe mode though.

Tonight, I did several thing. The most probable thing that might cause the problem is I edit xorg.conf to enable SHMConfig. I removed that line, but not helping.

Here is my .xsession-erros: (I mark serveral abnormal thing bolded.)
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "chuan"
[B]/etc/gdm/Xsession: Beginning session setup...
[: 12: closing paren expected[/B]
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/scim.
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
[B]Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Failed to load theme "T-ish-Ubuntulooks": Failed to find a valid file for theme T-ish-Ubuntulooks[/B]

Loading socket FrontEnd module ...
Starting SCIM as daemon ...
Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
GTK Panel of SCIM 1.4.4

Starting SCIM as daemon ...
SCIM has been successfully launched.
Smart Common Input Method 1.4.4

[B]Window manager warning: Lost connection to the display ':0';
most likely the X server was shut down or you killed/destroyed
the window manager.[/B]

```

Plz, help me! I hate to reinstall the system.

You should also try to backup the X server file, so next time something happens like this you can easily recover it. ;)

---


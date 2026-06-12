---
title: "How to replace Gnome 3.4 Screensaver with Xscreensaver"
date: 2012-12-10
forum: General Help
---

### Post by hzFVOW00pw on 2012-12-10
The Gnome 3 screensaver is nothing compared to Xscreensaver so I replaced it.

All the following commands can be run from a Terminal, like for instance gnome-terminal. You can easily select and copy a command from this page, then paste it in a terminal, and hit enter.

Remove Gnome Screensaver and install Xscreensaver:

```
sudo apt-get remove --purge gnome-screensaver
sudo apt-get install xscreensaver
```

Remove old autostart entry for gnome-screensaver.

```
rm -fv ~/.config/autostart/gnome-screensaver.desktop
```

Create a link gnome-screensaver-command > xscreensaver-command to enable screenlocking with Crtl-Alt-L.

```
sudo ln -fs /usr/bin/xscreensaver-command /usr/bin/gnome-screensaver-command
```

Put the following code in ~/.config/autostart/xcreensaver.desktop by running:

```
gedit ~/.config/autostart/xcreensaver.desktop
```

Then copy/paste the following code in gedit and save the file.

```
[Desktop Entry]
Name=Screensaver (xscreensaver)
Comment=Start screensaver
Type=Application
Icon=preferences-desktop-screensaver
TryExec=xscreensaver
Exec=xscreensaver -no-splash
NotShowIn=XFCE;KDE;
Hidden=false
X-GNOME-Autostart-enabled=true
```

You can of course also do this with gnome-session-properties, but if you also run XFCE be sure to edit the xscreensaver.desktop file to contain NotShowIn=XFCE; . That is because XFCE starts Xscreensaver from /etc/xdg/xfce4/xinitrc and not with an autostart xscreensaver.desktop file.

Now there's one thing left: To make the "Lock screen" menu entry in Gnome 3 work, we have to create a file /usr/local/bin/xscreensaver-dbus-screenlock.py with the following content:

```
sudo gedit /usr/local/bin/xscreensaver-dbus-screenlock.py
```

Paste the following code in gedit, and save the file.

```
#!/usr/bin/python
# Make the Gnome 3 screenlock menu entry work with xscreensaver and dbus
# Call this script with an autostart entry from ~/.config/autostart/
import dbus
import dbus.service
import dbus.glib
import gobject
import os
class ScreenDbusObj(dbus.service.Object):
    def __init__(self):
        session_bus = dbus.SessionBus()
        bus_name=dbus.service.BusName("org.gnome.ScreenSaver",bus=session_bus)
        dbus.service.Object.__init__(self,bus_name, '/org/gnome/ScreenSaver')
    @dbus.service.method("org.gnome.ScreenSaver")
    def Lock(self):
        os.system( "xscreensaver-command -lock" )
if __name__ == '__main__':
    object=ScreenDbusObj()
    gobject.MainLoop().run()
```

Make the file executable:

```
sudo chmod +x /usr/local/bin/xscreensaver-dbus-screenlock.py
```

Finally, add an autostart entry in ~/.config/autostart/xscreensaver-dbus-screenlock.desktop with the following content:

```
gedit ~/.config/autostart/xscreensaver-dbus-screenlock.desktop
```

Paste the code in gedit and save.

```
[Desktop Entry]
Type=Application
Name=Xscreensaver Lock Screen
Comment=Make Xscreensaver screenlocklock work with Gnome 3 menu
TryExec=xscreensaver-dbus-screenlock.py
Exec=xscreensaver-dbus-screenlock.py
X-GNOME-Autostart-enabled=true
Hidden=false
OnlyShowIn=GNOME;Unity;
```

---

### Post by OrangeVixen on 2013-05-15
Thanks, most of that works, I can get xscreensaver installed and gnome-screensaver out.

The lock screen keyboard shortcut works, however the Lock Screen menu item from the panel does not do anything now (does not lock the screen). That's the only thing not working (I'm using Precise 12.04).

---


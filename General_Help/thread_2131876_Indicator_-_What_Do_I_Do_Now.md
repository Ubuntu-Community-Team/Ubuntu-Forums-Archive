---
title: "Indicator - What Do I Do Now?"
date: 2013-04-03
forum: General Help
---

### Post by Quarkrad on 2013-04-03
Running 12.10 gnome classic. I've just installed the ubuntuone indicator via this page: **[http://www.noobslab.com/2012/11/indicators-collection-for-ubuntu.html](http://www.noobslab.com/2012/11/indicators-collection-for-ubuntu.html)**.  Having installed it I don't know what to do to 'see' it.  (On a general theme - a lot of pages show you how to install but hardly ever what to press to launch). Any suggestions how to launch it much appreciated.

---

### Post by wojox on 2013-04-03
Open a terminal and try ```
ubuntuone-indicator
```

---

### Post by Quarkrad on 2013-04-03
liz@lizubuntu:~$ ubuntuone-indicator
Initializing Application...
Initializing Indicator...
Initializing Client...
ERROR:dbus.proxies:Introspect error on com.ubuntuone.Authentication:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name com.ubuntuone.Authentication was not provided by any .service files
org.freedesktop.DBus.Error.ServiceUnknown: The name com.ubuntuone.Authentication was not provided by any .service files

---

### Post by Quarkrad on 2013-04-03
Stop Press:  Restarted pc, rather than log on/off and indicator icon appeared on top panel.  Thanks for your help.

---

### Post by Quarkrad on 2013-04-03
Sorry - I didn't really understand what is happening.  It was not rebooting the pc that put the icon in the panel but the terminal command.  I was hoping the indicator icon would be in the panel all the time.  Is it the case that you have to run the terminal command (or make a desktop script) to activate this indicator?

---

### Post by wojox on 2013-04-03
> **Quarkrad said:**
> Is it the case that you have to run the terminal command (or make a desktop script) to activate this indicator?

You shouldn't have to. Reboot again to see if it comes up. You may have to check with the folk's over at noobslab.

---


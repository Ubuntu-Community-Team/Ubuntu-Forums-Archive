---
title: "hal problem"
date: 2004-11-03
forum: General Help
---

### Post by Nikola on 2004-11-03
I've noticed that automounting of my usb disk and cd rom stopped working.
I've tried to run Computer-Desktop Preferences-Removable Storage but got this error:
```

Volume Management not Supported

The "hald" service is required but not currently running. Enable the service and rerun this applet, or contact your system administrator.
```

lshal gives this output:
```

ubuntu:~# lshal
lshal version 0.4.0
libhal.c 644 : Error connecting to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Input/output error
error: hal_initialize failed
```

Tried to update hal, but got this error:

```
Setting up hal (0.4.0-1ubuntu2) ...
Installing new version of config file /etc/hal/hald.conf ...
 Removing any system startup links for /etc/init.d/hal ...
   /etc/rc0.d/K20hal
   /etc/rc1.d/K20hal
   /etc/rc2.d/S20hal
   /etc/rc3.d/S20hal
   /etc/rc4.d/S20hal
   /etc/rc5.d/S20hal
   /etc/rc6.d/K20hal
 * Restarting system message bus...
 * Stopping Hardware Abstraction Layer...                                [ ok ]
Failed to start message bus: Failed to bind socket "/var/run/dbus/system_bus_soc ket": Address already in use
invoke-rc.d: initscript dbus-1, action "restart" failed.
dpkg: error processing hal (--configure):
```

Anyone has any idea?

---

### Post by randy on 2004-11-04
Make sure that dbus is running.  You can start /etc/init.d/messagebus status

---

### Post by Nikola on 2004-11-04
I got it to work... numerous thinks got borked, dbus-1 file in etc/init.d/ was 0kb size..
Anyway, everything is back to normal, including automounting of cd rom, except USB thumbdrive that worked before all this mess started.
Nautilus pops up with content of usb thumbdrive after I manualy mount it, but not automaticly (checked all options in Removable Storage).

---

### Post by boobytrapped on 2004-11-19
Hi All.   I am running into the same problem that I am unable to get my CDROM automounted when I insert it.  When I try to go into "Removable Storage" setting,  I get the same error message about "Volume Management not supported", and that hald might not be running.  I know that hald is running (ps afx) displays it.

The above instructions mentioned that I should try checking the messagebus status by running `/etc/init.d/messagebus status` -- however that init-script does not exist in the /etc/init.d directory.  Instead I can find /etc/init.d/dbus-1, I tried to restart it, but got the following error:

> 
ali@bina:/etc/init.d $ sudo invoke-rc.d dbus-1 restart
 * Restarting system message bus...
 * Stopping Hardware abstraction layer...                                                                  [ ok ]
 * Starting Hardware abstraction layer...
 *sr/sbin/hald already running.                                                                                             [fail]
run-parts: /etc/dbus-1/event.d/hal exited with return code 1
invoke-rc.d: initscript dbus-1, action "restart" failed.


Does anyone have any clues on what is wrong with hald?  (On gentoo hald is a independant init-script.. )

---


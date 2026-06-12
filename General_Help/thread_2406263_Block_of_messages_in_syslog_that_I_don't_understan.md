---
title: "Block of messages in syslog that I don't understand"
date: 2018-11-18
forum: General Help
---

### Post by David_Partridge on 2018-11-18
Here's a sample of thje messages in question:

```
Nov 18 14:04:44 Charon at-spi-bus-launcher[2814]: dbus-daemon[2820]: Activating service name='org.a11y.atspi.Registry' requested by ':1.124' (uid=1000 pid=4100 comm="/usr/lib/ibus/ibus-ui-gtk3 " label="uncon
Nov 18 14:04:44 Charon at-spi-bus-launcher[2814]: No protocol specified
Nov 18 14:04:44 Charon at-spi2-registr[4241]: Could not open X display
Nov 18 14:04:44 Charon at-spi-bus-launcher[2814]: dbus-daemon[2820]: Successfully activated service 'org.a11y.atspi.Registry'
Nov 18 14:04:44 Charon at-spi-bus-launcher[2814]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Nov 18 14:04:44 Charon at-spi-bus-launcher[2814]: No protocol specified
Nov 18 14:04:44 Charon at-spi2-registr[4241]: AT-SPI: Cannot open default display
Nov 18 14:04:44 Charon at-spi-bus-launcher[2814]: dbus-daemon[2820]: Activating service name='org.a11y.atspi.Registry' requested by ':1.137' (uid=1000 pid=4147 comm="nm-applet " label="unconfined")
Nov 18 14:04:44 Charon at-spi-bus-launcher[2814]: No protocol specified
Nov 18 14:04:44 Charon at-spi2-registr[4243]: Could not open X display
Nov 18 14:04:44 Charon at-spi-bus-launcher[2814]: dbus-daemon[2820]: Successfully activated service 'org.a11y.atspi.Registry'
Nov 18 14:04:44 Charon at-spi-bus-launcher[2814]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Nov 18 14:04:44 Charon at-spi-bus-launcher[2814]: No protocol specified
Nov 18 14:04:44 Charon at-spi2-registr[4243]: AT-SPI: Cannot open default display
Nov 18 14:04:44 Charon dbus-daemon[2716]: [session uid=1000 pid=2716] Activating service name='com.canonical.indicator.application' requested by ':1.276' (uid=1000 pid=4123 comm="lxpanel --profile Lubuntu " 
Nov 18 14:04:44 Charon dbus-daemon[2716]: [session uid=1000 pid=2716] Successfully activated service 'com.canonical.indicator.application'
Nov 18 14:04:45 Charon pkexec[4262]: amonra: Error executing command as another user: Not authorized [USER=root] [TTY=unknown] [CWD=/home/amonra] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: dbus-daemon[2820]: Activating service name='org.a11y.atspi.Registry' requested by ':1.148' (uid=1000 pid=4271 comm="lxterminal --geometry=120x43 " label="unc
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: No protocol specified
Nov 18 14:04:51 Charon at-spi2-registr[4273]: Could not open X display
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: dbus-daemon[2820]: Successfully activated service 'org.a11y.atspi.Registry'
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: No protocol specified
Nov 18 14:04:51 Charon at-spi2-registr[4273]: AT-SPI: Cannot open default display
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: dbus-daemon[2820]: Activating service name='org.a11y.atspi.Registry' requested by ':1.148' (uid=1000 pid=4271 comm="lxterminal --geometry=120x43 " label="unc
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: No protocol specified
Nov 18 14:04:51 Charon at-spi2-registr[4285]: Could not open X display
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: dbus-daemon[2820]: Successfully activated service 'org.a11y.atspi.Registry'
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: No protocol specified
Nov 18 14:04:51 Charon at-spi2-registr[4285]: AT-SPI: Cannot open default display
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: dbus-daemon[2820]: Activating service name='org.a11y.atspi.Registry' requested by ':1.131' (uid=1000 pid=4137 comm="update-notifier " label="unconfined")
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: No protocol specified
Nov 18 14:04:51 Charon at-spi2-registr[4287]: Could not open X display
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: dbus-daemon[2820]: Successfully activated service 'org.a11y.atspi.Registry'
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Nov 18 14:04:51 Charon at-spi-bus-launcher[2814]: No protocol specified
Nov 18 14:04:51 Charon at-spi2-registr[4287]: AT-SPI: Cannot open default display


```

What's the problem here please?

Thanks
David

---

### Post by David_Partridge on 2018-11-20
Bump - these happen every time in login ... Surely someone knows what's wrong here?

D.

---

### Post by QIII on 2018-11-20
Hello!

Do you mean every time you log in, or every time you start up?

You really don't want to suppress syslog logging.  If these are showing up before you get to your login screen at startup, you can simply choose not to have them displayed by modifying your kernel boot options by adding "quiet splash" ("quiet" suppresses the ***display*** all of the logging info and "splash" means to present pretty eye-candy while all the kernel loading process completes).

There isprobably nothing "wrong" there if you can successfully reach the login and get to your Desktop.

---

### Post by David_Partridge on 2018-11-20
This is every time I login, not once at startup.   As for there being nothing wrong, they sure look like error messages to me.

Dave

---


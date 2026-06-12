---
title: "lightdm is killed by systemd upon unlocking from lightlocker (xubuntu)"
date: 2017-11-13
forum: General Help
---

### Post by edruid on 2017-11-13
I recently started having the problem of the unlock screen (from light-locker) is *flickering*, that is, it shows like normal for a few seconds and then the screen goes black except for the pointer for a second or so. Any input I enter while the screen is black is discarded. If I manage to type in my password correctly the screen flickers a bit and then I'm at the *login*-screen. Logging in from there I'm at a fresh session having had any applications that where running shut down. This problem only appears if my monitors have gone to sleep while the system was locked.

These problems started after I bought a new monitor and started daisy chaining two monitors on the displayport.

So far I have tried to config lightdm to run varios versions of xrandr commands in a script from the [SEAT:*] section of /etc/lightdm/lightdm.conf. All that has got me is a black screen whith no possibility to login.

I run xubuntu 17.10
I lock my screen using xflock4:

In my syslog I find the following
```

Nov 13 13:55:43 druids-desktop systemd[1]: session-c7.scope: Killing process 15056 (lightdm) with signal SIGTERM.
Nov 13 13:55:43 druids-desktop systemd[1]: session-c7.scope: Killing process 15070 (lightdm-greeter) with signal SIGTERM.
Nov 13 13:55:43 druids-desktop systemd[1]: session-c7.scope: Killing process 15071 (lightdm-gtk-gre) with signal SIGTERM.
Nov 13 13:55:43 druids-desktop systemd[1]: session-c7.scope: Killing process 15073 (at-spi-bus-laun) with signal SIGTERM.
Nov 13 13:55:43 druids-desktop systemd[1]: session-c7.scope: Killing process 15087 (dbus-daemon) with signal SIGTERM.
Nov 13 13:55:43 druids-desktop systemd[1]: session-c7.scope: Killing process 15092 (at-spi2-registr) with signal SIGTERM.
Nov 13 13:55:43 druids-desktop systemd[1]: Stopping Session c7 of user lightdm.
Nov 13 13:55:43 druids-desktop systemd[1]: Stopped Session c7 of user lightdm.
Nov 13 13:55:43 druids-desktop systemd[1]: Stopping User Manager for UID 112...
Nov 13 13:55:43 druids-desktop systemd[15059]: Stopping D-Bus User Message Bus...
Nov 13 13:55:43 druids-desktop systemd[15059]: Stopped target Default.
Nov 13 13:55:43 druids-desktop systemd[15059]: Stopping Virtual filesystem service...
Nov 13 13:55:43 druids-desktop systemd[15059]: Stopped D-Bus User Message Bus.
Nov 13 13:55:43 druids-desktop systemd[15059]: Stopped Virtual filesystem service.
Nov 13 13:55:43 druids-desktop systemd[15059]: Stopped target Basic System.
Nov 13 13:55:43 druids-desktop systemd[15059]: Stopped target Sockets.
Nov 13 13:55:43 druids-desktop systemd[15059]: Closed D-Bus User Message Bus Socket.
Nov 13 13:55:43 druids-desktop systemd[15059]: Stopped target Timers.
Nov 13 13:55:43 druids-desktop systemd[15059]: Stopped target Paths.
Nov 13 13:55:43 druids-desktop systemd[15059]: Reached target Shutdown.
Nov 13 13:55:43 druids-desktop systemd[15059]: Starting Exit the Session...
Nov 13 13:55:43 druids-desktop systemd[15059]: Received SIGRTMIN+24 from PID 15296 (kill).
Nov 13 13:55:43 druids-desktop systemd[1]: Stopped User Manager for UID 112.
Nov 13 13:55:43 druids-desktop systemd[1]: Removed slice User Slice of lightdm.
Nov 13 13:55:44 druids-desktop lightdm[2812]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Nov 13 13:55:44 druids-desktop systemd[1]: Created slice User Slice of lightdm.
Nov 13 13:55:44 druids-desktop systemd[1]: Starting User Manager for UID 112...
Nov 13 13:55:44 druids-desktop systemd[1]: Started Session c8 of user lightdm.
Nov 13 13:55:44 druids-desktop systemd[15311]: Reached target Paths.
Nov 13 13:55:44 druids-desktop systemd[15311]: Starting D-Bus User Message Bus Socket.
Nov 13 13:55:44 druids-desktop systemd[15311]: Reached target Timers.
Nov 13 13:55:44 druids-desktop systemd[15311]: Listening on D-Bus User Message Bus Socket.
Nov 13 13:55:44 druids-desktop systemd[15311]: Reached target Sockets.
Nov 13 13:55:44 druids-desktop systemd[15311]: Reached target Basic System.
Nov 13 13:55:44 druids-desktop systemd[15311]: Reached target Default.
Nov 13 13:55:44 druids-desktop systemd[15311]: Startup finished in 26ms.
Nov 13 13:55:44 druids-desktop systemd[1]: Started User Manager for UID 112.
Nov 13 13:55:44 druids-desktop systemd[15311]: Started D-Bus User Message Bus.
Nov 13 13:55:44 druids-desktop dbus-daemon[15328]: Activating via systemd: service name='org.gtk.vfs.Daemon' unit='gvfs-daemon.service'
Nov 13 13:55:44 druids-desktop systemd[15311]: Starting Virtual filesystem service...
Nov 13 13:55:44 druids-desktop dbus-daemon[15328]: Activating via systemd: service name='org.a11y.Bus' unit='at-spi-dbus-bus.service'
Nov 13 13:55:44 druids-desktop systemd[15311]: Starting Accessibility services bus...
Nov 13 13:55:44 druids-desktop dbus-daemon[15328]: Successfully activated service 'org.gtk.vfs.Daemon'
Nov 13 13:55:44 druids-desktop systemd[15311]: Started Virtual filesystem service.
Nov 13 13:55:44 druids-desktop dbus-daemon[15328]: Successfully activated service 'org.a11y.Bus'
Nov 13 13:55:44 druids-desktop systemd[15311]: Started Accessibility services bus.
Nov 13 13:55:44 druids-desktop org.a11y.atspi.Registry[15339]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Nov 13 13:55:45 druids-desktop indicator-sound[3302]: volume-control-pulse.vala:735: unable to get pulse unix socket: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.PulseAudio1 was not provided by any .service files
Nov 13 13:55:45 druids-desktop indicator-sound-service[3302]: Invalid MIT-MAGIC-COOKIE-1 keyxcb_connection_has_error() returned true
Nov 13 13:55:45 druids-desktop pulseaudio[15370]: [pulseaudio] client-conf-x11.c: xcb_connection_has_error() returned true
Nov 13 13:55:45 druids-desktop rtkit-daemon[3055]: Successfully made thread 15373 of process 15373 (n/a) owned by '1000' high priority at nice level -11.
Nov 13 13:55:45 druids-desktop rtkit-daemon[3055]: Supervising 1 threads of 1 processes of 1 users.
Nov 13 13:55:45 druids-desktop pulseaudio[15373]: [pulseaudio] pid.c: Stale PID file, overwriting.
Nov 13 13:55:45 druids-desktop indicator-sound-service[3302]: Invalid MIT-MAGIC-COOKIE-1 keyInvalid MIT-MAGIC-COOKIE-1 keyxcb_connection_has_error() returned true
Nov 13 13:55:45 druids-desktop indicator-sound[3302]: accounts-service-access.vala:218: unable to sync volume 1,000000 to AccountsService: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: No such interface 'com.ubuntu.AccountsService.Sound'

```

Thanks in advance for any help!

---

### Post by Perfect Storm on 2017-11-13
Thread moved to General Help.

---


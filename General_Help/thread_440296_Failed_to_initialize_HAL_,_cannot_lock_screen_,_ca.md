---
title: "Failed to initialize HAL , cannot lock screen , cannot access users and groups..."
date: 2007-05-11
forum: General Help
---

### Post by theschles on 2007-05-11
Hi! I have Ubuntu 6.10 / Edgy on this work PC.

I'm getting "failed to initialize HAL" each bootup, I can't lock the screen, I can't access System > Administration > Users and Groups.  I also get a gnome bug buddy crash re: CD/DVD creator each bootup, here's the link: [http://bugzilla.gnome.org/show_bug.cgi?id=404133](http://bugzilla.gnome.org/show_bug.cgi?id=404133)

I recently updated dbus and its dependencies in an attempt to install terminal.os-cillation.de, as that's the terminal I use on my home PC (but that requires dbus-1, which is not used anymore by the looks of it).

I also should note that I have a NVidia GeForce 7300LE with two screens running the latest Linux driver from NVidia - but only one screen comes up on bootup.  If I then go into the NVidia panel to activate the second monitor, it works.  If I then click the save config button, it saves it, but upon reboot, I'm back to one monitor.

I've tried a bunch of stuff as listed in various posts on this forum:

```
$ sudo /etc/init.d/dbus restart
Password:
 * Stopping System Tools Backends system-tools-backends                  [ ok ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [fail] 
 * Stopping Hardware abstraction layer hald                              [ ok ] 
 * Stopping system message bus dbus                                      [ ok ] 
 * Starting system message bus dbus                                             Failed to start message bus: The pid file "/usr/var/run/dbus/pid" exists, if the message bus is not running, remove this file
$
```

Once I delete /usr/var/run/dbus/pid, this happens:

```
$ sudo /etc/init.d/dbus restart
 * Stopping System Tools Backends system-tools-backends                  [ ok ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [fail] 
 * Stopping Hardware abstraction layer hald                              [ ok ] 
 * Stopping system message bus dbus                                      [ ok ] 
 * Starting system message bus dbus                                      [ ok ] 
 * Starting Hardware abstraction layer hald                                    
run-parts: /etc/dbus-1/event.d/20hal exited with return code 1
 * Starting System Tools Backends system-tools-backends                  [ ok ] 
$
```

I tried removing and reinstalling the hal and haldaemon users as well as
the hal package per: [https://launchpad.net/ubuntu/+source/dbus/+bug/31517/](https://launchpad.net/ubuntu/+source/dbus/+bug/31517/)

...with no luck either.

Tried this per [https://launchpad.net/ubuntu/+source/dbus/+bug/19577](https://launchpad.net/ubuntu/+source/dbus/+bug/19577)
```
sudo hald --daemon=no --verbose=yes > hald.output 2&>1
```
(files are attached)

Anybody have a clue as to how to fix these problems?

---


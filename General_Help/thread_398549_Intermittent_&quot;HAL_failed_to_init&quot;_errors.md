---
title: "Intermittent &quot;HAL failed to init&quot; errors"
date: 2007-04-01
forum: General Help
---

### Post by BobSelby on 2007-04-01
I've been running Ubuntu 6.10 now for a while on a DELL Dimension and its proved very stable and "feature" free :-)

However, I havent used the box for about 4 weeks and when I did an upgrade yesterday I suddenly started getting an error window on the desktop after boot time along the lines of "Hall failed to initialize".  There was no other info.

Oddly the system seems to run happily afterwards and a reboot is usually successful .

Any ideas ??

TIA
Bob

---

### Post by jmrasor on 2007-04-17
Bob,

I got the same thing on Feisty after a clean install (no problem there), and an upgrade (HAL problem cropped up then). My workaround:

sudo mkdir /var/run/dbus
sudo chown messagebus:messagebus /var/run/dbus

Then I told dbus-daemon to make a message bus with the standard configuration file, and re-configured hal:

sudo dbus-daemon --system
sudo dpkg-reconfigure hal

Details on my post to [bug #81670]("https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/81670").

:D HTH.

---

### Post by BobSelby on 2007-04-21
Hehe - now thats what I call an obvious fix for the problem ;-)

I'm a bit of a Linux virgin :-) but reading the whole thread for the problem clarified it, mostly.

Thanks for the info :-)
Bob

---


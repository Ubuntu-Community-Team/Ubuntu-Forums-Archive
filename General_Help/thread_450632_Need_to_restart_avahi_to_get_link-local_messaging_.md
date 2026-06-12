---
title: "Need to restart avahi to get link-local messaging to work in gajim"
date: 2007-05-21
forum: General Help
---

### Post by Florob on 2007-05-21
Hello everybody,
maybe I should just file a bug report about this, but I figured I'd ask first in case I'm just being stupid.

If recently started using Gajim and think link-local messaging is a pretty cool feature.
The first thing I had to do was enabling dbus in avahi's configuration. I then restarted avahi and everything worked just fine.
But after a reboot Gajim is always complaining about not running. invoke-rc.d avahi-daemon status and ps -A say it is running though.
As soon as I restart (invoke-rc.d avahi-daemon restart) avahi Gajim suddenly is able to connect to the daemon.

Any pointers what to do to make this work immediately after booting? (I'd prefer non hackisch ways if possible ;) )

---

### Post by mcg on 2007-05-23
I can confirm that this bug effects me as well.  A bug report is probably in order.

---

### Post by Florob on 2007-05-27
It is now [Bug #116984]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/116984")

---

### Post by huygens on 2007-06-17
Just to be sure. When you do 'ps -A | grep avahi' you see at least one process named avahi-daemon?
Also, what do you mean by you have enable DBUS in Avahi configuration? Because, I think it is available by default... at least on Ubuntu.

If you're problem is that Avahi is not running after boot. Try to verify the file /etc/default/avahi-daemon. For further information, you can read this [blog post about activating avahi on Ubuntu]("http://www.berthon.eu/ice_and_fire/?p=110").

At least, I manage to [use the link-local with Pidgin]("http://www.berthon.eu/ice_and_fire/?p=100") that way...

---


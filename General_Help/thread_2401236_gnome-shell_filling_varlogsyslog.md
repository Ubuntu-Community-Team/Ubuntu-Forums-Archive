---
title: "gnome-shell filling /var/log/syslog"
date: 2018-09-15
forum: General Help
---

### Post by neocode on 2018-09-15
My Ubuntu 18.04.1 installation is killing my disk space.
It is filling /var/log/syslog with about 5gb of messages per day.
I did a tail on it:
PS: already upgraded to the latest packages


tail of /var/log/syslog:
Sep 15 10:07:52 marte gnome-shell[1104]: Object St.BoxLayout (0x56493ee54c50), has been already finalized. Impossible to set any property to it.
Sep 15 10:07:52 marte gnome-shell[1104]: Object St.Icon (0x56493e3717c0), has been already finalized. Impossible to set any property to it.
Sep 15 10:07:52 marte gnome-shell[1104]: Object St.BoxLayout (0x56493e00d150), has been already finalized. Impossible to set any property to it.
Sep 15 10:07:52 marte gnome-shell[1104]: Object St.Icon (0x56493e2f7ef0), has been already finalized. Impossible to set any property to it.


I already posted the bug here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1792702](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1792702)
However, is there a way to temporary stop the file from growing?
Maybe redirect the messages to /dev/null or something?

The bug is turning my system unusable and wearing out my ssd at the same time.

Thanks in advance

---

### Post by jeremy31 on 2018-09-15
Moved to General Help as it is not a development version, please use default font and color

---


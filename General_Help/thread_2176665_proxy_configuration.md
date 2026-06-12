---
title: "proxy configuration"
date: 2013-09-25
forum: General Help
---

### Post by tt3 on 2013-09-25
i recently installed ubuntu 13.04, i wanted to configure proxy settings via the terminal but when i type sudo gedit /etc/apt/apt.conf i get the following error
** (gedit:2100): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-uAAwWmHtTh: Connection refused

(gedit:2100): IBUS-WARNING **: The owner of /home/regan/.config/ibus/bus is not root!


please help

---

### Post by bkline on 2013-09-25
This is a known bug.  See [https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1125944](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1125944)

---


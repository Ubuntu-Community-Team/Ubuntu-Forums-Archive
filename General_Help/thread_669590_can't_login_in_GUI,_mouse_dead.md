---
title: "can't login in GUI, mouse dead"
date: 2008-01-16
forum: General Help
---

### Post by cristi.falcas on 2008-01-16
Starting from yesterday, when I tried to login in console mode I get something like this: 
  *bash: /dev/null: Permission denied *
If I hit Ctr+C I get the bash prompt.
The file /dev/null had the permissions 600.

In gdm the mouse is not moving at all and if I try to login, the desktop is crashing immediately.

The last thing I did was to install KDE4. I put kdm to be the default login manager, but after the problems I removed kdm-kde4 and gdm was the default again.

What I tried: 
1. Changing the permissions for /dev/null to 666 and tried to login. Failed to login.
2. Changing the permissions for /dev/null to 666 via rc.local. Failed to login. (console login is OK now, thou)
3. Changing the permissions for /lib/udev/devices/null to 666. Failed to login.
3. Checked /etc/udev/rules.d/40-permissions.rules for KERNEL=="null", MODE="0666". It was present.
4. Tried to kill gdm, startx from console. Desktop loaded, but mouse is dead.
5. Checked "ls /etc/rcS.d" and "ls /etc/rc2.d" (and all /etc/rc#.d) for udev. It is only present in /etc/rcS.d.

Also /dev/input/mice is 600. Changed it to 666, but still no mouse in X.

I tried to login in X as my user and also as root. It was the same.

---


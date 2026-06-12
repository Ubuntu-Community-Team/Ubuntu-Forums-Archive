---
title: "Prevent users from shutting down Ubuntu desktops"
date: 2020-03-29
forum: General Help
---

### Post by kladizkov on 2020-03-29
I'm looking for a way to disable the shutdown button in Ubuntu desktop to prevent my users from shutdown their desktops. They can logout, reboot etc, but not shutdown. I couldn't find a working way to get it done using polkit.

How can I get this done? Please help.

---

### Post by The Cog on 2020-03-29
I don't know if this would work, but perhaps rename /usr/sbin/shutdown and sym-link it to /usr/sbin/reboot instead?
Of course, that depends on the button calling the executable which I don't know if it works that way.

---

### Post by cmcanulty on 2020-03-29
don't know if this will help but in xubuntu you can right click on user name in top right,\, select properties and uncheck shutdown and any other entries.

---

### Post by kladizkov on 2020-03-31
There are 50+ users in the box. The configuration should effect all users in order prevent them from shutting down. Polkit seems to be the best way to do it. Can some one help specifically in polkit?

---

### Post by kladizkov on 2020-03-31
I managed to get it working.

Create a file /etc/polkit-1/localauthority/50-local.d/10-onlyrestart.pkla with below content

```
[OnlyRestart]Identity=unix-user:*
Action=org.freedesktop.consolekit.system.stop;org.freedesktop.login1.power-off;org.freedesktop.login1.power-off-multiple-sessions;org.xfce.session.xfsm-shutdown-helper;org.freedesktop.login1.suspend;org.freedesktop.login1.suspend-multiple-sessions;org.freedesktop.login1.hibernate;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.consolekit.system.stop-multiple-users
ResultInactive=no
ResultActive=no

```


This will only enable Logout and Restart button in the dialog box.

---


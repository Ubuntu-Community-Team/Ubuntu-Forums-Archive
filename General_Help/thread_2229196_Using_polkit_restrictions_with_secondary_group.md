---
title: "Using polkit restrictions with secondary group"
date: 2014-06-11
forum: General Help
---

### Post by Murukesh on 2014-06-11
Hi, I'm trying to restrict shutdown powers using instructions from [http://askubuntu.com/a/454230/158442](http://askubuntu.com/a/454230/158442).
I used group based restrictions ([FONT=courier new]unix-group:*[/FONT]) to disable shutdown. 
To enable shutdown, using my primary group works.
However, using the secondary group doesn't work. I tried with the [FONT=courier new]sudo[/FONT] group.
Am I doing something wrong?
Here are the settings I'm using:
```

root@mohanan-laptop:/etc/polkit-1/localauthority/50-local.d# cat 00-test-allow.pkla 
[Enable lightdm PowerMgmt]
Identity=unix-group:sudo
Action=org.freedesktop.login1.reboot;org.freedesktop.login1.reboot-multiple-sessions;org.freedesktop.login1.power-off;org.freedesktop.login1.power-off-multiple-sessions;org.freedesktop.login1.suspend;org.freedesktop.login1.suspend-multiple-sessions;org.freedesktop.login1.hibernate;org.freedesktop.login1.hibernate-multiple-sessions
ResultAny=yes
ResultInactive=yes
ResultActive=yes

root@mohanan-laptop:/etc/polkit-1/localauthority/50-local.d# cat 01-test.pkla 
[Disable lightdm PowerMgmt]
Identity=unix-group:*
Action=org.freedesktop.login1.reboot;org.freedesktop.login1.reboot-multiple-sessions;org.freedesktop.login1.power-off;org.freedesktop.login1.power-off-multiple-sessions;org.freedesktop.login1.suspend;org.freedesktop.login1.suspend-multiple-sessions;org.freedesktop.login1.hibernate;org.freedesktop.login1.hibernate-multiple-sessions
ResultAny=no
ResultInactive=no
ResultActive=no

root@mohanan-laptop:/etc/polkit-1/localauthority/50-local.d# groups mohanan 
mohanan : mohanan adm cdrom sudo dip plugdev lpadmin sambashare



```

I'd like to use the secondary groups so that I can implement this in a lab.

EDIT:
I apologize, I forgot to mention that I am using Ubuntu 14.04 with all the latest updates as of 11 June, 2014.

---


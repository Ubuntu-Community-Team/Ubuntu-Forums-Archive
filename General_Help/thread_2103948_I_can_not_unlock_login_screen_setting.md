---
title: "I can not unlock login screen setting"
date: 2013-01-11
forum: General Help
---

### Post by predato on 2013-01-11
Hi dear Ubuntu members, 
A few weeks ago I set passwordless login, now I noticed that I can not revert it on Control Center-> Users and Groups. When I untick "don't ask password on login", nothing happens. When I run it as root "users-admin" it freezes. I think I can not have elevated privileges, or I messed up with settings. I tried to run Ubuntu-Tweak, when I enter login settings I can  not unlock it.
I found a similar bug 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/570885](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/570885)
But no fix posted.
I trust you Ubuntu gurus.
 Please don't ignore my message. 
Regards.

---

### Post by Muratturat on 2013-01-11
> **predato said:**
> Hi dear Ubuntu members, 
A few weeks ago I set passwordless login, now I noticed that I can not revert it on Control Center-> Users and Groups. When I untick "don't ask password on login", nothing happens. When I run it as root "users-admin" it freezes. I think I can not have elevated privileges, or I messed up with settings. I tried to run Ubuntu-Tweak, when I enter login settings I can  not unlock it.
I found a similar bug 
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/570885](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/570885)
But no fix posted.
I trust you Ubuntu gurus.
 Please don't ignore my message. 
Regards.

Which ubuntu version you use`?

---

### Post by predato on 2013-01-11
It's Ubuntu natty 64 bit

---

### Post by predato on 2013-01-12
I fixed it at last. Some time ago I played with /etc/xdg/autostart/ and /home/kenn/.config/autostart/ folders and removed some files in order to speed up start-up processes, I think I deleted "/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1"
After I run it problem fixed. Thanks to this link [http://ubuntuforums.org/showthread.php?t=1705547](http://ubuntuforums.org/showthread.php?t=1705547)

---


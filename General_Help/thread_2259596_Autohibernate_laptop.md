---
title: "Autohibernate laptop"
date: 2015-01-05
forum: General Help
---

### Post by pingaan on 2015-01-05
Hi,

I'm wondering if it's possible to make my laptop automaticly hibernate when not charging. I mean if the power goes out due to bad weather I'd like for the device to hibernate instantly.
Is this possible?

Regards.

---

### Post by ajgreeny on 2015-01-05
You can set different suspend/hibernate configuration in the power-manager of a laptop so it should be possible to hibernate if on battery but suspend if on mains power.  I don't think it will be possible to move from suspend to hibernate if power goes off whilst suspended, but I am aware that there is a hybrid suspend/hibernate system which may be something worth investigating.
[http://www.webupd8.org/2012/11/how-to-use-hybrid-suspend-in-ubuntu.html](http://www.webupd8.org/2012/11/how-to-use-hybrid-suspend-in-ubuntu.html)

You will need to make sure you have enabled hibernation first, however, as it is disabled by default now in Ubuntu by making a new text file in a text editor with contents:-
```
[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes

```
and  save it as as /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla

---

### Post by pingaan on 2015-01-07
I haven't checked your link yet, but when I say hibernate I don't really care what happens to the computer, so to speak. I mean it can hibernate, suspend or even shut down, for all I care! ;-) I just don't want it to be running during the power failure.
I'm really picky when it comes to my identity and while I'm always connected to a VPN server it won't automaticly reconnect when the power returns and the router starts running again.

---


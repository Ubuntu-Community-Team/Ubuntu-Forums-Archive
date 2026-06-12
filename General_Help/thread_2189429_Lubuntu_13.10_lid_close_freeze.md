---
title: "Lubuntu 13.10 lid close freeze"
date: 2013-11-22
forum: General Help
---

### Post by kalehrl on 2013-11-22
I have a Dell latitude d505 laptop running Lubuntu 13.10.
When I close the lid, the screen becomes blank and the mouse cursor freezes and can't be moved.
The backlight is still on but the system is completely unresponsive.
I can't even ssh into the laptop to shut it down properly but have to pull the plug.
When I go to suspend from the logout menu, it suspends fine and I can close the lid and when I lift it it wakes properly.
I tried changing the options in xfce-power-manager to disable suspend but to no avail.
I also tried editing the /etc/systemd/logind.conf but nothing worked.
Whenever the lid is closed system hangs.
I found similar threads but there is no definite solution.

---

### Post by grier-devon on 2013-11-22
hmmmm...... I remember having a similar problem with Ubuntu 10.04 but I just assumed they fixed it. Sorry to hear and I will be checking the web to see if I can find anything.

---

### Post by kalehrl on 2013-11-22
I reported the bug here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1254131](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1254131)
I also found the similar bug but it was closed as 'won't fix' because the ubuntu version was no longer supported.
I hope devs will take more notice of it now.

---


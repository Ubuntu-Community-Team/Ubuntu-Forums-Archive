---
title: "VNC Server only starts when i log in"
date: 2013-08-21
forum: General Help
---

### Post by desi_villanueva on 2013-08-21
hi guys,

new to forum.  I installed the VNC server on Ubuntu 12.04 LTS...  

the problem is the VNC server only works when I login to the workstation locally first.

for example when I reboot and I try to use VNC before logging in locally.  VNC does work.

please help.

thanks

---

### Post by scbingham on 2013-08-21
I haven't tried this yet but looks promising:

[http://www.havetheknowhow.com/Configure-the-server/Run-VNC-on-boot.html](http://www.havetheknowhow.com/Configure-the-server/Run-VNC-on-boot.html)

Let others know how you get on, I'm sure we're not the only ones looking for this.

Good luck

---

### Post by CaptainMark on 2013-08-22
Depends on the VNC server, some (including Vino, the Ubuntu default server) only let you connect to an existing desktop session, think of it as a shared desktop
Some let you connect to any existing screen whether a user is logged in or not,
and some let you connect to a computer and start your own session, independent of what a user is doing physically at the computer

See here for details of the differences and examples of each but be very wary of sharing a VNC session over the internet, it's not secure by default and needs a bit of Linux know how to get it secure (detailed on the link)
[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

---

### Post by prodigy_ on 2013-08-22
[http://askubuntu.com/questions/229989/how-to-setup-x11vnc-to-access-with-graphical-login-screen](http://askubuntu.com/questions/229989/how-to-setup-x11vnc-to-access-with-graphical-login-screen)

---


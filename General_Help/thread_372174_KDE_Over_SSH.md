---
title: "KDE Over SSH"
date: 2007-02-27
forum: General Help
---

### Post by mmxbass on 2007-02-27
I am attempting to run the command "ssh -CX [email]username@host.edu[/email] startkde". The problem being the obvious problem that the remote KDE proceeds to vomit itself all over my desktop, leading to the issue that I have two desktops running simultaneously, somewhat of a usability problem. Is there a quick and easy way to force the system to start the remote KDE in another tty such as tty9?

---

### Post by bettlebrox on 2007-02-27
You could try tunnelling VNC over ssh, or using NX. Alternatively, start a new X session (use the User Switcher Applet), select the Failsave Terminal. SSH from the failsafe terminal and startkde. Unless your on a local network this could be mighty slow. NX works really well, but you also need it installed on the Server:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---


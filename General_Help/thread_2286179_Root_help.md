---
title: "Root help?"
date: 2015-07-10
forum: General Help
---

### Post by georgetoon on 2015-07-10
Well, folks, I'm back.:)  I've been away for some time and it looks like Ubuntu has changed quite a bit.  I' still a Linux user, but gravitated more to KDE and an RPM distro.

Anyhow, i picked up a used computer that already has Ubuntu 12.04 installed.  It came with a root user and password.  All I wan to do is change the root password.  Is this difficult to do? Can it be done using the GUI? 

BTW, Unity is pretty darn slick!  It only took minutes to get the feel for it.  However, Ubuntu's approach to root is a bit diffenet than what I'm usd to..at least this is my first impression.

---

### Post by dino99 on 2015-07-10
welcome back ):P

[http://askubuntu.com/questions/294946/how-to-change-root-password-in-ubuntu](http://askubuntu.com/questions/294946/how-to-change-root-password-in-ubuntu)
[http://askubuntu.com/questions/228696/how-to-change-administrator-username](http://askubuntu.com/questions/228696/how-to-change-administrator-username)

---

### Post by Vladlenin5000 on 2015-07-10
Welcome back...
And yes, the approach to root is different. The first user is also root (with sudo). Root graphical login is discouraged and such discussion isn't even allowed in this forum (for very good reasons).

If you already have the main user's password then that's also the root password. You can change it at System Settings > User Accounts. Whenever you need elevated privileges you should precede your command with *sudo*.

---


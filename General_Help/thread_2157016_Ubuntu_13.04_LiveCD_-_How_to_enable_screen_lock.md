---
title: "Ubuntu 13.04 LiveCD - How to enable screen lock?"
date: 2013-06-23
forum: General Help
---

### Post by carmen2012 on 2013-06-23
On the Ubuntu 13.04 LiveCD, the screen lock does not work.  I did a Google search on this and discovered a blog post on another website where one user suggest that it may have been disabled because people that are just trying out the LiveCD may not know what the default password is if they lock their screen.

This same person suggested running the below command to enable it which worked:

gsettings set org.gnome.desktop.lockdown disable-lock-screen false

I had two questions in regards to this:

1.  What I'm wondering is could the function of this command have also been performed using a system settings icon somwhere in Ubuntu 13.04 and if so, how?

2.  Also, I notice that the command makes a reference to gnome, but I thought Ubuntu moved away from gnome towards Unity?

Thank you

---

### Post by Cheesehead on 2013-06-24
1) Yes. Using the system called dbus. Dbus is the system that glues together lots of different processes, including menu entries and desktop shortcuts and launcher buttons...and gsettings.

If you learn how to use dbus, you can figure out how to send a command to gsettings to change (almost) any setting. The trigger for setting that command can come from any dbus-aware application, including the one you write.

2) Oversimplification. Still lots of under-the-hood gnome components in Unity. A lot of Gnome is not about creating windows at all, but about how to move data around in a standard way. In this case, Gnome developed a perfectly nice settings database, and Unity developers had no reason to reinvent it.

---


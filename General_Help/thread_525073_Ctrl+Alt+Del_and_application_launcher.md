---
title: "Ctrl+Alt+Del and application launcher"
date: 2007-08-13
forum: General Help
---

### Post by XogGyux on 2007-08-13
I would like to know how to assign a program a shortcut (i have xfce 4 task manager and i would like to assing a shortcut like Ctrl+Alt+Del, to have the equivalent of the task manager in windows). Also i would like to know about a application launcher like Katapult (or quicksilver in mac) but with the possibility of improve with plugings, since katapult isnt that smart (e.g when i type Firefox it will suggest me Customize Firefox, it wont recognize web pages address etc.)

---

### Post by gfixler on 2007-08-14
I'm in GNOME/Metacity, so this will likely be entirely useless to you on Xfce, but in the off-chance it provides any insight, I was able to do this using the following how-to:

[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

For the command_# value I put in:

gnome-system-monitor

For the run_command_# value I gave it:

<Ctrl><Alt>Delete

I had commands 1 and 2 taken up, so my #s were both 3. It worked immediately upon setting the second value. I hit Ctrl+Alt+Delete, and the system monitor - the closest thing to the Task Manager - popped up. I can't tell it which tab to pop open to, but at least it uses the last on viewed.

Good luck.

---


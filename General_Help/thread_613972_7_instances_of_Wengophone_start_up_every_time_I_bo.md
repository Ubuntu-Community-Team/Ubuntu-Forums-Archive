---
title: "7 instances of Wengophone start up every time I boot up"
date: 2007-11-15
forum: General Help
---

### Post by little_penguin on 2007-11-15
I've had this odd problem for a couple of days: Every time I boot up I get 7 instances of Wengophone start up, and even though I close all these windows before I reboot, they are all back again when I restart the computer. 

There is no setting in Wengophone itself that autostarts the program, that I'm aware of, and I haven't put it it any autostart folder.

Does anyone know how I can get stop this? I'm using KDE in Ubuntu Feisty.

---

### Post by little_penguin on 2007-11-15
It's OK, I solved it, had to remove all references to Wengophone in the file:

.kde/share/config/ksmserverrc

which is located in the user's home directory.

Followed this thread: [http://www.linuxforums.org/forum/linux-applications/7028-kde-autostart-programs.html]("http://www.linuxforums.org/forum/linux-applications/7028-kde-autostart-programs.html")

---


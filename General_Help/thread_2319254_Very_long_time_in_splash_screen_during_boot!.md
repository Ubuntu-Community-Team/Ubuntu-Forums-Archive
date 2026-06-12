---
title: "Very long time in splash screen during boot!"
date: 2016-04-02
forum: General Help
---

### Post by elson3 on 2016-04-02
[COLOR=#000000][FONT=Consolas]Hello! My Xubuntu 15.10 (all updates/upgrades applied) is taking a very long time (100 seconds+) displaying the splash screen during boot. It wasn't always like this, but now it is... and I didn't install any weird program, but I used Boot Repair in a live USB. My hardware is a Dell Inspiron 14R 5421. Thanks![/FONT][/COLOR]

---

### Post by Dennis N on 2016-04-02
You can possibly learn what the system is doing during that delay by pressing ESC when you see the splash screen and look at the most recent system message on the monitor. Or, you can check the system logs to see any obvious time gaps - older systems have logs in /var/log, while systemd has a "journal" you can look at from the terminal with **journalctl -b** (no sudo) for the most recent boot. With this command, you can redirect to a text file so you can more easily read them:

**[FONT=Courier New]journalctl -b > ~/Desktop/journal.txt[/FONT]**

saves the results to a file on your Desktop named journal.txt.

---

### Post by elson3 on 2016-04-02
Hi! I did what you said. And I pasted journal.txt content here for you to look and give me any ideas: [https://paste.ubuntu.com/15588328/](https://paste.ubuntu.com/15588328/)

---

### Post by elson3 on 2016-04-03
I don't know what to do anymore. :<

---


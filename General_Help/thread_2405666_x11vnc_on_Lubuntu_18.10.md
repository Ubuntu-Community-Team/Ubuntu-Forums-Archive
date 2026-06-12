---
title: "x11vnc on Lubuntu 18.10?"
date: 2018-11-09
forum: General Help
---

### Post by Alexander_Lilljebj on 2018-11-09
Hey,
I've noticed that Lubuntu now used Lxqt instead of Lxde. I was wondering how to go about to autostart x11vnc in lxqt? 
Any help would be very helpful.
Thanks!

---

### Post by #&amp;thj^% on 2018-11-09
Will this work:
To have X applications start on login, click the main menu from the LXQt > Preferences > LXQt Settings > Session Settings. Alternatively, this can be launched with:

```
lxqt-config-session

```
From this window, click on AutoStart on the left side. Here you can add a new application to either the global autostart (launched in all sessions implementing the XDG Autostart specification) or your local autostart (labled LXQt Autostart) (See issue 746 for a bug related to this option). For each item you add, lxqt-config-session will create a Desktop entry (.desktop file) in the appropriate XDG Autostart directory.

The distinction between "Global Autostart" and "LXQt Autostart" does not depend on the directory in which the corresponding .desktop file is located, but rather on the OnlyShowIn setting. If it is OnlyShowIn=true, it is considered an "LXQt Autostart". Furthermore, if X-LXQt-Module=true, the item is not shown in lxqt-config-session.
This is taken from the Arch Wiki: [https://wiki.archlinux.org/index.php/LXQt#Autostart](https://wiki.archlinux.org/index.php/LXQt#Autostart)

This site may be helpful also: [http://c-nergy.be/blog/?p=10426](http://c-nergy.be/blog/?p=10426)

---

### Post by Alexander_Lilljebj on 2018-11-09
> **1fallen said:**
> Will this work:
To have X applications start on login, click the main menu from the LXQt > Preferences > LXQt Settings > Session Settings. Alternatively, this can be launched with:

```
lxqt-config-session

```
From this window, click on AutoStart on the left side. Here you can add a new application to either the global autostart (launched in all sessions implementing the XDG Autostart specification) or your local autostart (labled LXQt Autostart) (See issue 746 for a bug related to this option). For each item you add, lxqt-config-session will create a Desktop entry (.desktop file) in the appropriate XDG Autostart directory.

The distinction between "Global Autostart" and "LXQt Autostart" does not depend on the directory in which the corresponding .desktop file is located, but rather on the OnlyShowIn setting. If it is OnlyShowIn=true, it is considered an "LXQt Autostart". Furthermore, if X-LXQt-Module=true, the item is not shown in lxqt-config-session.
This is taken from the Arch Wiki: [https://wiki.archlinux.org/index.php/LXQt#Autostart](https://wiki.archlinux.org/index.php/LXQt#Autostart)

This site may be helpful also: [http://c-nergy.be/blog/?p=10426](http://c-nergy.be/blog/?p=10426)

Thank you so much 1fallen! Will try asap :)

---

### Post by Alexander_Lilljebj on 2018-11-09
So, I've tried to add:
sudo x11vnc -auth /run/user/1000/gdm/Xauthority -forever -loop -noxdamage -repeat -rfbauth /etc/x11vnc-passwd -rfbport 5900 -shared
And with -auth guess.
In both local and global autostart. It seems to be running, but I can't connect. 
The password file has right permissions. 
Any ideas?

Edit: 
I just realized that I might have messed something up when trying to get it going the first time around. Will reset everything tomorrow and try from scratch.

---

### Post by #&amp;thj^% on 2018-11-09
Try without "sudo" putting a sudo command in an autostart script (which is not connected to the terminal) you are guaranteed to fail.

---

### Post by Alexander_Lilljebj on 2018-11-09
> **1fallen said:**
> Try without "sudo" putting a sudo command in an autostart script (which is not connected to the terminal) you are guaranteed to fail.

Thanks again! 
As quite apparent I'm not very familiar with linux(yet).

---

### Post by mixtutor on 2018-11-09
I am using this and it works


sudo systemctl daemon-reload && 
sudo systemctl start x11vnc && 
sudo systemctl enable x11vn

---

### Post by Alexander_Lilljebj on 2018-11-10
> **mixtutor said:**
> I am using this and it works


sudo systemctl daemon-reload && 
sudo systemctl start x11vnc && 
sudo systemctl enable x11vn

Thanks mix! I will try that as well.

Edit:
It just says service not found.

Edit2:
Made a service, ran your commands. Still not working.

---

### Post by Alexander_Lilljebj on 2018-11-10
Alright, at last!
Did like 1fallen suggested. The problem was that I was placing the password in /etc/x11vnc.pass with sudo. 
When placing it without sudo in home folder it work. Silly me...

---


---
title: "Startup"
date: 2008-06-19
forum: General Help
---

### Post by KickThem on 2008-06-19
Hello, I need help with making my kubuntu enter automaticaly without asking for login and password, and also, after start i want it to initiate a program automaticaly too. Help pls. Thanks for your time if you're goin to spend it answering.

---

### Post by KickThem on 2008-06-19
I've tried to search in the forum for something like that and i didnt find anything...

---

### Post by KickThem on 2008-06-19
can someone ple help me??

---

### Post by manfer on 2008-06-19
If you are using Kubuntu you must be using kdm as login manager so you have to change it options to get the automatic startup.

"You can use the graphical configuration tool provided by the KDE Control Center (under System Administration->Login Manager)"

"**Automatic Login**

Automatic login will give anyone access to a certain account on your system without doing any authentication. You can enable it using the option Enable Auto-login.

You can choose the account to be used for automatic login from the list labeled User:.

Automatic login can be suppressed by pressing the Shift key immediately after the X-Server switches to graphics mode and releasing it when kdm's hourglass cursor appears."

All that from the kde docs on the web:
[http://docs.kde.org/stable/en/kdebase-workspace/kdm/configuring-kdm.html](http://docs.kde.org/stable/en/kdebase-workspace/kdm/configuring-kdm.html)

Which ones must be the help kde docs in your system too I think.

---

### Post by manfer on 2008-06-19
If you want an application to run at startup create symlink for that application putting it in the folder:

/home/your_username/.kde/Autostart

For knotes, as an example, you would do this:

ln -s /usr/bin/knotes /home/your_username/.kde/Autostart/

---

### Post by KickThem on 2008-06-19
Thanks for the time Manfer. I'll do it right away.

---


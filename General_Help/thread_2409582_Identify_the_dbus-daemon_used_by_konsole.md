---
title: "Identify the dbus-daemon used by konsole"
date: 2019-01-04
forum: General Help
---

### Post by shnadav on 2019-01-04
I have two konsole processes on my machine. Each have many open windows and tabs.
From some not good reason I have a lot of dbus-daemon processes opened.
I want to close all of them except for the two dbus-daemon used by the two konsoles processes.
For that I would like to know which dbus-daemon is used by any of my two konsoles so I can close all the others.

Thanks

---

### Post by clementc on 2019-01-04
Hi [**[COLOR=#000000]shnadav[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115451"),

You can use the command below to list processes using the D-Bus message bus daemon:
dbus-send --system --print-reply --dest=org.freedesktop.DBus /org/freedesktop/DBus org.freedesktop.DBus.ListNames

And use this command to obtain the associated PID:
dbus-send --system --print-reply --dest=org.freedesktop.DBus /org/freedesktop/DBus org.freedesktop.DBus.GetConnectionUnixProcessID 'string::1.11'

---

### Post by shnadav on 2019-01-05
Thanks clementc,

However, I think you missed my intention here.
With the combined commands above I can list the pid of any process using the same dbus-daemon as my current konsole.
I want the pid of the dbus-daemon itself.

---

### Post by clementc on 2019-01-05
Hi [**[COLOR=#000000]shnadav[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115451"),

Running the following command in Terminal will give the the PIDs of running dbus-daemons:

ps ax | grep dbus-daemon

---

### Post by shnadav on 2019-01-06
Thanks again,

However, you missed again :grin:.
I am familiar with ps and used your suggestion before.
My problem as I stated before is that I have many (many many) dbus-daemon processes. 
I need to identify the one that is used by my Konsole.

Perhaps  there is a way to connect to a dbus-daemon process just by knowing its  pid, or getting the address of a dbus-daemon just from its pid.
Then I  could connect to them one by one and from inside shouldn't have any  problem figuring out whether it's the one used by my Konsole.

Thanks,
Nadav

---


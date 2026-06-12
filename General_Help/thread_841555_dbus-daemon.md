---
title: "dbus-daemon"
date: 2008-06-26
forum: General Help
---

### Post by anv on 2008-06-26
I don't know what is dbus-daemon, but after opening taskmanager, the manager window starts to fillup with dbus-daemon lines??

---

### Post by sdennie on 2008-06-26
Check the man page for information on what it is:

```

man dbus-daemon

```

I'm not completely sure what problem you are having.  Can you provide a screenshot?

---

### Post by mali2297 on 2008-06-26
Post the output of
```

ps aux | grep dbus

```

---

### Post by anv on 2008-07-04
:~$ ps aux | grep dbus
107       6595  0.0  0.0  21460  1276 ?        Ss   03:40   0:00 /usr/bin/dbus-daemon --system
anv       7376  0.0  0.0  25768   660 ?        S    03:41   0:00 dbus-launch --autolaunch d40c3778da549a356670334f482cab7d --binary-syntax --close-stderr
anv       7378  0.0  0.0  21188   952 ?        Ss   03:41   0:00 /usr/bin/dbus-daemon --fork --print-pid 20 --print-address 22 --session

---

### Post by mali2297 on 2008-07-05
> **anv said:**
> :~$ ps aux | grep dbus
107       6595  0.0  0.0  21460  1276 ?        Ss   03:40   0:00 /usr/bin/dbus-daemon --system
anv       7376  0.0  0.0  25768   660 ?        S    03:41   0:00 dbus-launch --autolaunch d40c3778da549a356670334f482cab7d --binary-syntax --close-stderr
anv       7378  0.0  0.0  21188   952 ?        Ss   03:41   0:00 /usr/bin/dbus-daemon --fork --print-pid 20 --print-address 22 --session

The header to these columns is
```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND

```
I think the output is normal. The memory usage is way higher than on my system, but you seem to have the capacity for it (the processes use 0.0% of the available RAM).

Do you find the system slow? ...or are you just asking out of curiosity?

I don't know that much about dbus, but it is used by printing utilities, removable disk managers and such. You can find some information here:
[http://www.freedesktop.org/wiki/Software/dbus](http://www.freedesktop.org/wiki/Software/dbus)

---

### Post by chrisccoulson on 2008-07-05
Those outputs are normal.

You should have one system dbus-daemon, and then a session dbus-daemon per user session open. So, if you've got one user logged in, then you'll have dbus-daemon's running

---

### Post by anv on 2008-07-05
taskmanager after 8-9 seconds opened, filling with d-bus:

[http://img390.imageshack.us/my.php?image=attatchmentdi1.jpg](http://img390.imageshack.us/my.php?image=attatchmentdi1.jpg)


no I don't experience system slow


just one user

---

### Post by chrisccoulson on 2008-07-05
They all have PID of zero, which is not possible.

When task manager fills up with those dbus-daemon lines, could you have a look at the output of 'ps aux' again please.

Thanks

---


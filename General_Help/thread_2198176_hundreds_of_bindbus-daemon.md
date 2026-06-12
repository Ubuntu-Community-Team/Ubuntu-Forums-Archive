---
title: "hundreds of //bin/dbus-daemon"
date: 2014-01-07
forum: General Help
---

### Post by b3nw on 2014-01-07
Any ideas why so many processes are spawning for //bin/dbus-daemon ?

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise

$ uname -a
Linux ben-wsl 3.2.0-57-generic #87-Ubuntu SMP Tue Nov 12 21:35:10 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


```

root     32616  0.0  0.0  28204   476 ?        Ss   Jan02   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32625  0.0  0.0  28204   476 ?        Ss   Jan03   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32627  0.0  0.0  28204   484 ?        Ss   Jan02   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32637  0.0  0.0  28204   480 ?        Ss   Jan03   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32638  0.0  0.0  28204   484 ?        Ss   Jan02   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32649  0.0  0.0  28204   480 ?        Ss   Jan02   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32650  0.0  0.0  28204   476 ?        Ss   Jan03   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32653  0.0  0.0  28204   476 ?        Ss    2013   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32662  0.0  0.0  28204   468 ?        Ss   Jan03   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32664  0.0  0.0  28204   484 ?        Ss    2013   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32675  0.0  0.0  28204   476 ?        Ss    2013   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32686  0.0  0.0  28204   476 ?        Ss    2013   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32696  0.0  0.0  28204   476 ?        Ss   Jan01   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32707  0.0  0.0  28204   484 ?        Ss   Jan01   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32718  0.0  0.0  28204   476 ?        Ss   Jan01   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
root     32729  0.0  0.0  28204   476 ?        Ss   Jan01   0:00 //bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session

```

---

### Post by ian-weisser on 2014-01-07
--session means that it's a user-level process (not system-level).
A user-level dbus-session is spawned at every GUI user login.
Those sessions are a month old or more.

Did you have any problems on Jan 01, 02, and/or 03?
When time comes to logout, how exactly are you doing it?
How many users do you currently have logged in?

---

### Post by b3nw on 2014-01-07
Thanks for the feedback, I don't remember any problems, but its possible, I assume a reboot would clear this all out? Is there any harm in killing all of the sessions?

---

### Post by ian-weisser on 2014-01-07
Yes, a reboot will eliminate them all.

There is not harm killing a session that you are not using.
There **is** harm killing a session that you are using. It will end your session not-gracefully, risking data loss unless you have closed all applications first.

---

